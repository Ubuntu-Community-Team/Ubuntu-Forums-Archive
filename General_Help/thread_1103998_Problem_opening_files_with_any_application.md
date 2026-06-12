---
title: "Problem opening files with any application"
date: 2009-03-23
forum: General Help
---

### Post by joseace on 2009-03-23
Hello,

I have a problem opening files with any application.

When I try to do "File" - "Open", the window to select the file hangs, and only responds to "Cancel"

I tried with any applicaction (Firefox, Thunderbird, Evolution, Toem, etc.

Any ideas?

Thanks in advance

---

### Post by rendon on 2009-03-23
when did this begin happening?

is this a new fresh install of ubuntu?

what release number are you using? (7.10, 8.04, 8.10, ...)

---

### Post by joseace on 2009-03-23
I found why it happens: Setting the desktop visual effects to normal or extra.

I'm running ubuntu 8.10 64 bit version.

---

### Post by Kevbert on 2009-03-23
Welcome to Ubuntu.
What are your system specs ? (in particular RAM, display adapter/video memory).

---

### Post by joseace on 2009-03-23
I have Nvidia geforce 9300 512 MB. The processor is a Intel dual core with 4GB RAM

---

### Post by mikechant on 2009-03-23
> I found why it happens: Setting the desktop visual effects to normal or extra.

I've had too many assorted weird problems with Compiz/Effects etc. (I have an NVidia 8300 card). I just keep it all turned off and everything works fine.

I think you probably only have two options 
1/ Turn the effects down or off as you mention.
2/ Try the latest Nvidia driver from their website if you haven't already.

---

### Post by Kevbert on 2009-03-23
Compiz shouldn't give you any problems with those specs (I'm only using a Nvidia 7600 GS). What driver are you using ? You can find this by going to System-Administration-Restricted Drivers. It may be, if you have a choice, that you are using the wrong one.
If you open terminal and enter
```
compiz
```
what errors do you get ?
I've dug a little bit further and it may be one of these [[COLOR="Red"]bugs[/COLOR]]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=compiz%2Bnvidia%2Bslow&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") shown in Launchpad.

---

### Post by joseace on 2009-03-23
I have 2 options to choose:

NVIDIA accelerated graphics driver (173)
NVIDIA accelerated graphics driver (177)[Recommended]

I selected the 2nd.

Results of compiz are:

~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by Kevbert on 2009-03-24
Nothing unusual there, right driver used.
The only other thing I can suggest is to take a look at your xorg.conf file. Go to Applications-Accessories-Terminal and type in
```
gksu gedit /etc/X11/xorg.conf
```
Check the following is in this file (probably at the end):
```
Section "Module"
	Load		"glx"
EndSection
```
You'll need to add this, if its not there,then save the file and reboot for the changes to take effect.

---

### Post by mikechant on 2009-03-24
> I have 2 options to choose:

NVIDIA accelerated graphics driver (173)
NVIDIA accelerated graphics driver (177)[Recommended]

I selected the 2nd.

There is apparently a version 180 available from Nvidia's website (I've seen other posts mention it), so that could be worth a try.

---

### Post by joseace on 2009-03-24
I checked the file xorg.conf file and it's like you told me.

I installed the last driver from nvidia (180.29) and the result is still worse: the system hangs when I try to open a file in normal or extra desktop visual effects...

---

### Post by Kevbert on 2009-03-25
It may be that you've got one or two broken packages. Please go to terminal and enter
```
sudo apt-get update
sudo apt-get install -f
```
Please post back the result.
Please also run memtest86+ (from the grub boot menu) for a couple of passes.

---

### Post by joseace on 2009-03-25
Nothing to do with apt-get...

~$ sudo apt-get update
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid Release.gpg
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates Release.gpg
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Translation-es
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid Release      
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates Release                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-es    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-es  
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                    
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/main Sources 
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) intrepid-updates/multiverse Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Leyendo lista de paquetes... Hecho

~$ sudo apt-get install -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

---

### Post by joseace on 2009-03-25
.... and no errors with memtest86+

---

### Post by Kevbert on 2009-03-26
Please take a look at [[COLOR="Red"]this[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=95804") on the Nvidia forums (it may be what your seeing).

---

