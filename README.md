mfg
===
Multi-Layer Feature Graph Implementation


Dependencies
------------
Below is a list of all dependencies required, and links to relevant information such as downloads.
* Qt5: http://qt-project.org/
   ```
   sudo apt-get install qt5-default
   ```
* OpenCV: http://opencv.org
   * Note that on Ubuntu-based systems, the nonfree module has been removed to avoid potential patent issues (https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=734373)
   * This means OpenCV should be installed manually from source on Ubuntu systems
* Line Segment Detector from IPOL (Image Processing On Line)
   * Website link: http://www.ipol.im/pub/art/2012/gjmr-lsd/
   * Download link: http://www.ipol.im/pub/art/2012/gjmr-lsd/lsd_1.6.zip
   * A copy of the LSD header (version 1.5 lsd.h) currently resides in this repository
   * *Version 1.5 is required for the current state of this project*
   * The latest version (1.6), moved many of the header's declarations out of the lsd.h and into lsd.c
* LevMar, an implementation of Levenberg-Marquardt Nonlinear Least Squares Algorithms
   * Website link: http://users.ics.forth.gr/~lourakis/levmar/
   * Download link: http://users.ics.forth.gr/~lourakis/levmar/levmar-2.6.tgz
   * Requires lapack, f2c and OpenBlas
   ```
   sudo apt-get install liblapack-dev f2c openblas
   ```
   * Note that some issues have arisen during the LevMar compilation regarding an `undefined reference to symbol 'exp@@GLIBC...'`, which can be fixed by adding ` -lm` to the `TARGET_LINK_LIBRARIES` line in the levmar CMakeLists.txt file, making it look like:
   ```
   TARGET_LINK_LIBRARIES(lmdemo ${LIBS} -lm)
   ```
   * ~~Also note that copies of the levmar-2.6 headers have been included in this project~~
   * Also note that levmar-2.6 has been included and will build with MFG, and includes a slightly modified CMakeLists.txt from the original in order to link correctly
* Eigen3: http://eigen.tuxfamily.org/
   ```
   sudo apt-get install libeigen3-dev
   ```
* g2o: A General Framework for Graph Optimization
   * Website link: https://openslam.org/g2o.html
   * GitHub download link: https://github.com/RainerKuemmerle/g2o
   * Note that the github code includes CSparse (http://people.sc.fsu.edu/~jburkardt/c_src/csparse/csparse.html)
   * On a UNIX system:
   ```
   git clone https://github.com/RainerKuemmerle/g2o
   cd g2o
   mkdir build
   cd build
   cmake ..
   make
   make install
   ```

There is a script to automate the process of installing dependencies in bin/install-deps.sh
* **TODO: create this script**


Build Instructions
------------------
This project uses CMake (http://www.cmake.org), a cross-platform build system.
* mkdir build
* cd build
* cmake ..
* make


TODO
----
0. compile and build cross-platform
   0. include copy of all libraries that cannot be installed via package managers
   1. check licenses for above step
   2. create an APT package
   3. create a MacPorts package?
   4. create an RPM package
1. apply g2o to lba
2. speed up: feature points types?
3. feature points distribution?
4. plane detection
5. when use lk track, still need to detect blur image

