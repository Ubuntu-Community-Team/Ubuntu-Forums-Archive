---
title: "no splash at startup"
date: 2009-03-17
forum: Desktop Environments
---

### Post by Dawei87 on 2009-03-17
ever since i installed jaunty to a new partition to try, i have lost my intrepid splash screen at startup. i now get the text at startup instead. i have ran startup manager and changed my splash screen but to no avail. can anyone help with this?

---

### Post by Zorael on 2009-03-17
Mmkay. Terminal output of the following commands? (Copy/paste to get it right.)
```
$ grep "# defoptions" /boot/grub/menu.lst
$ file /etc/alternatives/usplash-artwork.so
$ apt-cache policy usplash-theme-ubuntu
```
They should should return something like:
```
$ grep "# defoptions" /boot/grub/menu.lst
# defoptions=quiet **splash**

$ file /etc/alternatives/usplash-artwork.so
/etc/alternatives/usplash-artwork.so: symbolic link to `/usr/lib/usplash/usplash-theme-ubuntu.so'

$ apt-cache policy usplash-theme-ubuntu
usplash-theme-ubuntu:
  Installed: [COLOR="Lime"]**0.21**[/COLOR]
  Candidate: 0.21
  Version table:
     0.21 0
        500 http://se.archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status
```
If they don't, something went wrong. The version numbers are irrelevant on the last one; you just want to make sure it's actually installed. So post your output and we'll see.

---

### Post by O-pos on 2009-03-17
I have similar problem - just texts during boot. I tried to isntall Atari splash, but did not work. Here is my output:

~$ grep "# defoptions" /boot/grub/menu.lst
# defoptions=splash vga=791
~$ file /etc/alternatives/usplash-artwork.so
/etc/alternatives/usplash-artwork.so: symbolic link to `/usr/lib/usplash/atari-splash.so'
~$ apt-cache policy usplash-theme-ubuntu
usplash-theme-ubuntu:
  Installed: 0.19
  Candidate: 0.19
  Version table:
 *** 0.19 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status

---

### Post by Dawei87 on 2009-03-17
ok, here's my output.

david@master:~$ grep "# defoptions" /boot/grub/menu.lst
# defoptions=quiet splash
david@master:~$ file /etc/alternatives/usplash-artwork.so
/etc/alternatives/usplash-artwork.so: symbolic link to `/usr/lib/usplash/usplash-theme-sunset.so'
david@master:~$ apt-cache policy usplash-theme-ubuntu
usplash-theme-ubuntu:
  Installed: 0.19
  Candidate: 0.19
  Version table:
 *** 0.19 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
david@master:~$ 

it looks like everything should be ok to me. i hope this helps

---

### Post by Zorael on 2009-03-17
> **O-pos said:**
> I have similar problem - just texts during boot. I tried to isntall Atari splash, but did not work. Here is my output:

~$ grep "# defoptions" /boot/grub/menu.lst
# defoptions=splash vga=791
EDIT: This post assumes verbose boot overrides splash. I think it does?


Hmm, you're missing *quiet* in your defoptions. Open up **/boot/grub/menu.lst** in a texteditor *with superuser permissions*.

GNOME: **gksu gedit /boot/grub/menu.lst**
KDE: **kdesudo "kate /boot/grub/menu.lst"**
Terminal: **sudo nano /boot/grub/menu.lst**

Find the following part and make sure to add *quiet* as highlighted.

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=791 _**quiet**_
```
Save the file, then run the following in a terminal.
```
$ sudo update-grub
```
Your new output for the first command should now look like this.
```
$ grep "# defoptions" /boot/grub/menu.lst
# defoptions=splash vga=791 **quiet**
```
Restart and see if it worked.

---

### Post by Zorael on 2009-03-17
> **Dawei87 said:**
> david@master:~$ grep "# defoptions" /boot/grub/menu.lst
# defoptions=quiet splash
david@master:~$ file /etc/alternatives/usplash-artwork.so
/etc/alternatives/usplash-artwork.so: symbolic link to `/usr/lib/usplash/usplash-theme-sunset.so'
david@master:~$ apt-cache policy usplash-theme-ubuntu
usplash-theme-ubuntu:
  Installed: 0.19
  Candidate: 0.19
  Version table:
 *** 0.19 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
Nothing seems wrong there, no. You seem to have a different usplash installed; perhaps it could just be broken?
```
$ sudo aptitude reinstall usplash-theme-ubuntu
$ sudo update-alternatives --config usplash-artwork.so
```
Pick "usplash-theme-ubuntu.so" or whatever else it offers there containing "ubuntu". (It may already be pointing there because of the first command (aptitude reinstall).)
```
$ cat /etc/usplash.conf
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1024
yres=768
```
Make sure that file (/etc/usplash.conf) defines an acceptable resolution, perhaps 800x600 or 1024x768, whatever suits your monitor. Edit it in a text editor with superuser permissions if need be. (See previous post.)
```
$ sudo update-grub
```
Reboot and see if it helped.

---

### Post by Dawei87 on 2009-03-17
ok. i changed back to the original splash and it was good again. (i must not have noticed it worked before i changed it) and i tried another splash as well and it worked (it was the one i originally used when splash broke) but the sunset splash still doesnt work. i dont think it is broken though. i am using startup manager. should a change my resolution? would i need to do that to get different splash screens to work?

---

### Post by O-pos on 2009-03-17
OK, I did and the terminal output now indicates "quiet", but there is no splash and when the computer loads, it is still as verbous as hell. Here is the output:

~$ grep "# defoptions" /boot/grub/menu.lst
# defoptions=splash vga=791 quiet
~$ file /etc/alternatives/usplash-artwork.so
/etc/alternatives/usplash-artwork.so: symbolic link to `/usr/lib/usplash/atari-splash.so'
~$ apt-cache policy usplash-theme-ubuntu
usplash-theme-ubuntu:
  Installed: 0.19
  Candidate: 0.19
  Version table:
 *** 0.19 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status

---

