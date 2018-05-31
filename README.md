# pcl-for-android

Bash scripts for cross compiling PCL ( https://github.com/PointCloudLibrary/pcl ) and its dependencies for Android.
Scripts were tested for

* Fedora 23, 24
* Ubuntu 16.04
* Cmake 2.8 (Fails with 3.*)
* Android NDK 10e, 11c, 12b

## Install Requirements

Ubuntu

```
$ sudo apt-get install git make cmake
```

Fedora

```
$ sudo dnf install git make cmake
```

## Cross-compilation

```
$ git clone https://github.com/bashbug/pcl-for-android.git
$ export ANDROID_NDK=PATH_TO_YOUR_LOCAL_ANDROID_NDK_FOLDER
$ ./download-setup.sh
$ ./pcl-build-for-android.sh
```
The compilations within the pcl-build-for-android.sh needs at least 4GB RAM + 4 GB Swap or 8GB RAM.

Default uses for make -j the number of CPUs.

The number of CPUs and thereby the memory usage can be reduced by setting the option as follows.

```
$ jobs=NUM_OF_CPUS ./pcl-build-for-android.sh
```


### download-setup.sh

This script downloads the dependencies:

- EIGEN 3.2.9
- FLANN 1.8.4
- BOOST 1.61.0
- PCL 1.8

### pcl-build-for-android.sh

This script cross compiles FLANN, BOOST and PCL for android. Add the following folders to your Android.mk file:

- eigen
- flann-android
- boost-android
- pcl-android
