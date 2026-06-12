---
title: "steam missing dependencies"
date: 2017-05-07
forum: Gaming &amp; Leisure
---

### Post by micahpage on 2017-05-07
I think this is a result of me accidentally deleting python2.x. How can i install these to run steam? These are not listed in apt search?

```
metulburr@ubuntu:~$ steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Error: You are missing the following 32-bit libraries, and Steam may not run:
libgobject-2.0.so.0
libglib-2.0.so.0
libgtk-x11-2.0.so.0
libgdk_pixbuf-2.0.so.0
[2017-05-07 16:21:47] Startup - updater built Apr 25 2017 22:45:11
Looks like steam didn't shutdown cleanly, scheduling immediate update check
[2017-05-07 16:21:47] Checking for update on startup
[2017-05-07 16:21:47] Checking for available updates...
[2017-05-07 16:21:48] Download failed: http error 0 (client-download.steampowered.com/client/steam_client_ubuntu12)
[2017-05-07 16:21:48] Download failed: http error 0 (media.steampowered.com/client/steam_client_ubuntu12)
[2017-05-07 16:21:48] failed to load manifest from buffer.
[2017-05-07 16:21:48] Failed to load manifest
[2017-05-07 16:21:48] Error: Download failed: http error 0
[2017-05-07 16:21:48] Verifying installation...
[2017-05-07 16:21:48] Performing checksum verification of executable files
[2017-05-07 16:21:48] Verification complete
[2017-05-07 16:21:54] Shutdown

```

---

### Post by Perfect Storm on 2017-05-08
Moved to Gaming & Leisure.

Try with
```
sudo apt install libgtk2.0-0:i386 libglib2.0:i386 libgdk-pixbuf2.0-0:i386
```

---

### Post by micahpage on 2017-05-08
```
[sudo]
metulburr@ubuntu:~$ sudo apt install libgtk2.0-0:i386 libglib2.0:i386 libgdk-pixbuf2.0-0:i386
 password for metulburr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libglib2.0-0-refdbg:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-cil-dev:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-tests:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-0-dbg:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-bin:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-cil:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-dev:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-doc:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-data:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-0:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-doc' instead of 'libglib2.0-doc:i386'
Note, selecting 'libglib2.0-data' instead of 'libglib2.0-data:i386'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libglib2.0-cil:i386 : Depends: cli-common:i386 (>= 0.5.6) but it is not installable
                       Depends: libmono-corlib4.5-cil:i386 (>= 4.2.0) but it is not installable
                       Depends: libmono-system4.0-cil:i386 (>= 4.2.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Perfect Storm on 2017-05-08
```
sudo apt install -f
```
Then try again.

---

### Post by micahpage on 2017-05-08
it didnt seem to change anything

```
metulburr@ubuntu:~$ sudo apt install -f
[sudo] password for metulburr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-image-4.4.0-72-generic
  linux-image-extra-4.4.0-72-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


metulburr@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-image-4.4.0-72-generic
  linux-image-extra-4.4.0-72-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


metulburr@ubuntu:~$ sudo apt install libgtk2.0-0:i386 libglib2.0:i386 libgdk-pixbuf2.0-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libglib2.0-0-refdbg:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-cil-dev:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-tests:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-0-dbg:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-bin:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-cil:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-dev:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-doc:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-data:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-0:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-doc' instead of 'libglib2.0-doc:i386'
Note, selecting 'libglib2.0-data' instead of 'libglib2.0-data:i386'
libglib2.0-data is already the newest version (2.48.2-0ubuntu1).
libglib2.0-data set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libglib2.0-cil:i386 : Depends: cli-common:i386 (>= 0.5.6) but it is not installable
                       Depends: libmono-corlib4.5-cil:i386 (>= 4.2.0) but it is not installable
                       Depends: libmono-system4.0-cil:i386 (>= 4.2.0) but it is not installable
E: Unable to correct problems, you have held broken packages.


```

---

### Post by Perfect Storm on 2017-05-08
```
sudo apt install -f cli-common:i386 libmono-corlib4.5-cil:i386 libmono-system4.0-cil:i386
sudo apt install -f libglib2.0:i386
```

---

### Post by micahpage on 2017-05-08
```
metulburr@ubuntu:~$ sudo apt install -f cli-common:i386 libmono-corlib4.5-cil:i386 libmono-system4.0-cil:i386
[sudo] password for metulburr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cli-common:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cli-common-dev

Package libmono-corlib4.5-cil:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libmono-system4.0-cil:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  mono-reference-assemblies-4.0 mono-devel

E: Package 'cli-common:i386' has no installation candidate
E: Package 'libmono-corlib4.5-cil:i386' has no installation candidate
E: Package 'libmono-system4.0-cil:i386' has no installation candidate
metulburr@ubuntu:~$ sudo apt install -f libglib2.0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libglib2.0-0-refdbg:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-cil-dev:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-tests:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-0-dbg:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-bin:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-cil:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-dev:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-doc:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-data:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-0:i386' for regex 'libglib2.0'
Note, selecting 'libglib2.0-doc' instead of 'libglib2.0-doc:i386'
Note, selecting 'libglib2.0-data' instead of 'libglib2.0-data:i386'
libglib2.0-data is already the newest version (2.48.2-0ubuntu1).
libglib2.0-data set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libglib2.0-cil:i386 : Depends: cli-common:i386 (>= 0.5.6) but it is not installable
                       Depends: libmono-corlib4.5-cil:i386 (>= 4.2.0) but it is not installable
                       Depends: libmono-system4.0-cil:i386 (>= 4.2.0) but it is not installable
E: Unable to correct problems, you have held broken packages.


```

---

### Post by Perfect Storm on 2017-05-08
```
sudo apt remove --purge steam
sudo apt auto-remove && sudo apt autoclean
sudo dpkg --configure -a
sudo apt install -f
sudo apt install steam
```

---

### Post by micahpage on 2017-05-08
i stil have the same issue

```
metulburr@ubuntu:~$ sudo apt remove --purge steam
[sudo] password for metulburr: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-image-4.4.0-72-generic
  linux-image-extra-4.4.0-72-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  steam:i386*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 2,662 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 318756 files and directories currently installed.)
Removing steam:i386 (1:1.0.0.48-1ubuntu3) ...
Purging configuration files for steam:i386 (1:1.0.0.48-1ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...


metulburr@ubuntu:~$ sudo apt auto-remove && sudo apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-image-4.4.0-72-generic
  linux-image-extra-4.4.0-72-generic
0 upgraded, 0 newly installed, 4 to remove and 1 not upgraded.
After this operation, 297 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 318738 files and directories currently installed.)
Removing linux-headers-4.4.0-72-generic (4.4.0-72.93) ...
Removing linux-headers-4.4.0-72 (4.4.0-72.93) ...
Removing linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-4.4.0-72-generic (4.4.0-72.93) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del mysql-server-core-5.7 5.7.17-0ubuntu0.16.04.2 [7,564 kB]
Del mysql-client-5.7 5.7.17-0ubuntu0.16.04.2 [1,666 kB]
Del mysql-server-5.7 5.7.17-0ubuntu0.16.04.2 [2,466 kB]
Del youtube-dl 1:2017.04.17-1~getdeb1 [877 kB]
Del mysql-client-core-5.7 5.7.17-0ubuntu0.16.04.2 [6,516 kB]
Del mysql-server 5.7.17-0ubuntu0.16.04.2 [10.8 kB]


metulburr@ubuntu:~$ sudo dpkg --configure -a


metulburr@ubuntu:~$ sudo apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
metulburr@ubuntu:~$ sudo apt install steam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  steam:i386
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 874 kB of archives.
After this operation, 2,662 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/multiverse i386 steam i386 1:1.0.0.48-1ubuntu3 [874 kB]
Fetched 874 kB in 0s (1,580 kB/s)  
Preconfiguring packages ...
Selecting previously unselected package steam:i386.
(Reading database ... 286430 files and directories currently installed.)
Preparing to unpack .../steam_1%3a1.0.0.48-1ubuntu3_i386.deb ...
Unpacking steam:i386 (1:1.0.0.48-1ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up steam:i386 (1:1.0.0.48-1ubuntu3) ...


metulburr@ubuntu:~$ steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Error: You are missing the following 32-bit libraries, and Steam may not run:
libgobject-2.0.so.0
libglib-2.0.so.0
libgtk-x11-2.0.so.0
libgdk_pixbuf-2.0.so.0
[2017-05-08 15:36:19] Startup - updater built Apr 25 2017 22:45:11
Looks like steam didn't shutdown cleanly, scheduling immediate update check
[2017-05-08 15:36:19] Checking for update on startup
[2017-05-08 15:36:19] Checking for available updates...
[2017-05-08 15:36:19] Download failed: http error 0 (client-download.steampowered.com/client/steam_client_ubuntu12)
[2017-05-08 15:36:19] Download failed: http error 0 (media.steampowered.com/client/steam_client_ubuntu12)
[2017-05-08 15:36:19] failed to load manifest from buffer.
[2017-05-08 15:36:19] Failed to load manifest
[2017-05-08 15:36:19] Error: Download failed: http error 0
[2017-05-08 15:36:19] Verifying installation...
[2017-05-08 15:36:19] Performing checksum verification of executable files
[2017-05-08 15:36:20] Verification complete
[2017-05-08 15:36:37] Shutdown


```

---

### Post by Perfect Storm on 2017-05-09
Try uninstall steam.
```
sudo apt remove --purge steam
```

and install the version from their web: [http://store.steampowered.com/about/](http://store.steampowered.com/about/)

---

### Post by micahpage on 2017-05-09
after that if i click the steam icon on unity i get a dialog saying
> Couldn't set up Steam data - please contact technical support
If i type steam in terminal i get:
```
metulburr@ubuntu:~$ steam
Setting up Steam content in /home/metulburr/.local/share/Steam
rm: cannot remove '/home/metulburr/.steam/steam': Is a directory

```

---

### Post by Perfect Storm on 2017-05-09
```
rm -rf ~/.steam
```

---

### Post by micahpage on 2017-05-09
That allows me to install steam. Thank you. 

I do have another question. I cant get to the steam store. I get an error
> [h=1]Error Code: -130[/h][COLOR=#939393][FONT=Arial]Failed to load web page (unknown error).
[/FONT][/COLOR]

IS this related to a package missing, or only steam related?

---

### Post by Perfect Storm on 2017-05-09
I don't know and google didn't come up with any useful.
Do anything else works in steam?

---

### Post by micahpage on 2017-05-09
everything but the store seems to work

---

### Post by genericvii143 on 2017-05-09
Hello, I had issues with my Steam when you click on the icon, is not just going? Here is my solution to my problem. Also for some reason make sure your Wine settings are straight. .

(ctrl+alt+t to open the terminal) and try to start steam again.

rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6

rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1

rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libgcc_s.so.1

rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6

rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libxcb.so.1

---

