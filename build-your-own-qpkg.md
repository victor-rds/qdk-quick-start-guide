# Build Your Own QPKG

* ### Generate environment for QPKG

  * Use SSH client to connect to your NAS

  * Issue below commands to create an environment of your own QPKG \(assuming to-be-built QPKG name is “MyQPKG”\)

  * ``# cd `getcfg QDK Install_Path -f /etc/config/qpkg.conf` ``

`# qbuild --create-env MyQPKG`

* A folder named “MyQPKG” is then generated  

`[/share/HDA_DATA/.qpkg/QDK] # ls`  
`MyQPKG/ bin/ qdk* scripts/ template/`  
`[/share/HDA_DATA/.qpkg/QDK] # cd MyQPKG/`  
`[/share/HDA`_`DATA/.qpkg/QDK/MyQPKG] # ls  
  arm_64`_`arm-x19 arm-x31/ arm-x41/ build/ icons/ qpkg.cfg x86/  config/ package_routines shared/ x86_64/  x86_ce53xx/`

![](/assets/2016-09-12_145747.png)

* ### Configure QPKG

  * QPKG\_NAME: Name of the QPKG

  * QPKG\_VER: Version of the QPKG

  * QPKG\_AUTHOR: Author of the QPKG

`[/share/HDA_DATA/.qpkg/QDK/MyQPKG] # vi qpkg.cfg`

`# Name of the packaged application.`

`QPKG_NAME="MyQPKG"`

`# Version of the packaged application.`

`QPKG_VER="0.1"`

`# Author or maintainer of the package`

`QPKG_AUTHOR="admin"`

![](/assets/2016-09-12_150308.png)

* ### Customize QPKG routines

  * Content of file “package\_routines”

  * pkg\_pre\_install\(\) : routines before install

  * pkg\_install\(\) : routines during install

  * pkg\_post\_install\(\) : routines after install

  * PKG\_PRE\_REMOVE : routines before uninstall

  * PKG\_MAIN\_REMOVE : routines during uninstall

  * PKG\_POST\_REMOVE : routines after uninstall

  * Content of file “shared\/MyQPKG.sh"

  * Start : routines when starting the QPKG

  * Stop : routines when stoping the QPKG

![](/assets/2016-09-12_151010.png)

* ### Add files to QPKG

  * Put files in below folders for different purposes:

  * shared\/: Platform-independent files and folders

  * arm-x19\/ arm-x31\/ arm-x41\(TS-x31+\)\/ x86\/ x86\_ce53xx\/ x86\_64\/: Platform-dependent files and folders

  * icons\/: icon files

  * config\/: config files

![](/assets/2016-09-12_152737.png)

* ### Generate QPKG file

  * ### Use below command to build the QPKG file

`[/share/CACHEDEV1_DATA/.qpkg/QDK/MyQPKG] # qbuild`

`Creating archive with data files...`

`Creating archive with control files...`

`Creating QPKG package...`

* ### The QPKG file will be generated in the build folder
```
[/share/CACHEDEV1_DATA/.qpkg/QDK/MyQPKG] # cd build/
[/share/CACHEDEV1_DATA/.qpkg/QDK/MyQPKG/build] # ls
MyQPKG_0.1.qpkg
```

![](/assets/2016-09-12_153354.png)

