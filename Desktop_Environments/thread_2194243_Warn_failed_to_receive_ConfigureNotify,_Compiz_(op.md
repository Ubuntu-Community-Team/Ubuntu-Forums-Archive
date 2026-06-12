---
title: "Warn: failed to receive ConfigureNotify, Compiz (opengl) - Fatal: glXQueryExtensionsS"
date: 2013-12-17
forum: Desktop Environments
---

### Post by kevkn on 2013-12-17
I am having issue with display. I searched the forum and tried to repair, re-install and update but still getting error as shown below. The issue started when I repaired Ubuntu.


  ```
  Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following package was automatically installed and is no longer required:
      libprotoc7
    Use 'apt-get autoremove' to remove them.
    0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
    Need to get 1,289 kB of archives.
    After this operation, 0 B of additional disk space will be used.
    Get:1 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main unity amd64 5.20.0-0ubuntu2 [1,289 kB]
    Fetched 1,289 kB in 5s (240 kB/s)
    (Reading database ... 271480 files and directories currently installed.)
    Preparing to replace unity 5.20.0-0ubuntu2 (using .../unity_5.20.0-0ubuntu2_amd64.deb) ...
    Unpacking replacement unity ...
    Processing triggers for man-db ...
    Setting up unity (5.20.0-0ubuntu2) ...
    kevin@kevin-Lenovo-G570:~$ sudo apt-get install --reinstall ubuntu-desktop
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following package was automatically installed and is no longer required:
      libprotoc7
    Use 'apt-get autoremove' to remove them.
    0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
    Need to get 4,016 B of archives.
    After this operation, 0 B of additional disk space will be used.
    Get:1 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main ubuntu-desktop amd64 1.267.1 [4,016 B]
    Fetched 4,016 B in 1s (3,949 B/s)         
    (Reading database ... 271480 files and directories currently installed.)
    Preparing to replace ubuntu-desktop 1.267.1 (using .../ubuntu-desktop_1.267.1_amd64.deb) ...
    Unpacking replacement ubuntu-desktop ...
    Setting up ubuntu-desktop (1.267.1) ...
    kevin@kevin-Lenovo-G570:~$ sh amd-driver-installer-12.6-legacy-x86.x86_64.run
    sh: 0: Can't open amd-driver-installer-12.6-legacy-x86.x86_64.run
    kevin@kevin-Lenovo-G570:~$ git clone https://github.com/phanimahesh/unity-revamp.git
    The program 'git' is currently not installed.  You can install it by typing:
    sudo apt-get install git
    kevin@kevin-Lenovo-G570:~$ unity-reset
    unity-reset: command not found
    kevin@kevin-Lenovo-G570:~$ unity
    Checking if settings need to be migrated ...no
    Checking if internal files need to be migrated ...no
    Backend     : gconf
    Integration : true
    Profile     : unity
    Adding plugins
    Initializing core options...done
    compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2800004
    
    compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4200082
    
    compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600002
    
    compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2800621
    
    compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3c00032
    
    compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1400002
    
    compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4400003
    
    Initializing composite options...done
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    compiz (opengl) - Error: initScreen failed
    compiz (core) - Error: Couldn't activate plugin 'opengl'
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Initializing decor options...done
    Initializing vpswitch options...done
    Initializing snap options...done
    Initializing mousepoll options...done
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Initializing resize options...done
    Initializing place options...done
    Initializing move options...done
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (core) - Error: InitPlugin 'wall' failed
    compiz (core) - Error: Couldn't activate plugin 'wall'
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Initializing grid options...done
    Initializing session options...done
    Initializing gnomecompat options...done
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (core) - Error: InitPlugin 'animation' failed
    compiz (core) - Error: Couldn't activate plugin 'animation'
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (core) - Error: InitPlugin 'fade' failed
    compiz (core) - Error: Couldn't activate plugin 'fade'
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (core) - Error: InitPlugin 'unitymtgrabhandles' failed
    compiz (core) - Error: Couldn't activate plugin 'unitymtgrabhandles'
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Initializing workarounds options...done
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (core) - Error: InitPlugin 'scale' failed
    compiz (core) - Error: Couldn't activate plugin 'scale'
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (core) - Error: InitPlugin 'expo' failed
    compiz (core) - Error: Couldn't activate plugin 'expo'
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (core) - Error: InitPlugin 'ezoom' failed
    compiz (core) - Error: Couldn't activate plugin 'ezoom'
    compiz (core) - Error: Plugin 'opengl' not loaded.
    
    compiz (core) - Error: InitPlugin 'unityshell' failed
    compiz (core) - Error: Couldn't activate plugin 'unityshell'
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a0!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a3!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a3!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a6!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a9!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a9!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a3!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a9!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000ac!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a3!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000a9!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000af!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000b2!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000ac!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000ac!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000ac!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    compiz (core) - Warn: unhandled ConfigureNotify on 0x38000ac!
    compiz (core) - Warn: this should never happen. you should probably file a bug about this.
    Initializing animation options...done
    Initializing expo options...done
    Initializing ezoom options...done
    Initializing fade options...done
    Initializing opengl options...done
    Initializing scale options...done
    Initializing staticswitcher options...done
    Initializing unitymtgrabhandles options...done
    Initializing unityshell options...done
    Initializing wall options...done
    Setting Update "main_menu_key"
    Setting Update "run_key"
    compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4400003
    
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
    

```

---

