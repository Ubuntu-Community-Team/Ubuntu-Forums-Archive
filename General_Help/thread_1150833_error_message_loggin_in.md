---
title: "error message loggin in"
date: 2009-05-06
forum: General Help
---

### Post by itslindseytime on 2009-05-06
i know this threat was already up a year ago but no one fixed the problem or helped and i dont want to reinstall ubuntu.

the problems is when i login it gives me this message: Users $HOME/.dmrc file is being ignored. This prevents the defualt session and language from being saved.
File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.

what does this mean? and why is it happening? it doesnt seem to do anything though, it boots just fine, the only problem im having is i cant download anyhthing with add remove programs without an error saying stuff like:

E: ttf-mscorefonts-installer: subprocess post-installation script returned error exit status 1

and it says that no matter what program it is.

---

### Post by sisco311 on 2009-05-06
> **itslindseytime said:**
> i know this threat was already up a year ago but no one fixed the problem or helped and i dont want to reinstall ubuntu.

the problems is when i login it gives me this message: Users $HOME/.dmrc file is being ignored. This prevents the defualt session and language from being saved.
File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by other users.

what does this mean? and why is it happening? it doesnt seem to do anything though, it boots just fine, the only problem im having is i cant download anyhthing with add remove programs without an error saying stuff like:


[thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

> 
E: ttf-mscorefonts-installer: subprocess post-installation script returned error exit status 1

and it says that no matter what program it is.

try:
```
sudo apt-get install -f && sudo apt-get update
```

---

### Post by itslindseytime on 2009-05-07
> **sisco311 said:**
> [thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]



try:
```
sudo apt-get install -f && sudo apt-get update
```
i tried that and it gave me this message:

lindsey@LinuxPrincess:~$ sudo apt-get install -f && sudo apt-get update
[sudo] password for lindsey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  phonon libswt-gnome-gtk-3.4-jni libswt-cairo-gtk-3.4-jni
  libswt-mozilla-gtk-3.4-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

