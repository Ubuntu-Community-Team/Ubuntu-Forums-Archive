---
title: "how to change start up screen from Kubuntu back to Ubuntu?"
date: 2008-04-30
forum: Desktop Environments
---

### Post by boddhisatva on 2008-04-30
Hi
I've installed KDE alongside Gnome and even though Gnome is my primary desktop environment, the startup screen (when the system is loading and closing) is the Kubuntu screen. I'd like to change it back to Ubuntu - any help?
Thanks

---

### Post by warp99 on 2008-04-30
> **boddhisatva said:**
> Hi
I've installed KDE alongside Gnome and even though Gnome is my primary desktop environment, the startup screen (when the system is loading and closing) is the Kubuntu screen. I'd like to change it back to Ubuntu - any help?
Thanks
Open a terminal and issue the following:
```
sudo update-alternatives --config usplash
```
then choose 'ubuntu' as your splash screen. If it's not available then:
```
sudo apt-get install usplash-theme-ubuntu
```
then run the previous command again.

Edit:

I just remembered that your initrd.img may not update after you run 'sudo update-alternatives --config usplash' so if your initrd.img is not updated, just look at the screen you'll see if this happens or not, run the following:
```
sudo update-initramfs -u 
```
this will update the initrd.img to include the correct usplash image at boot.

---

### Post by boddhisatva on 2008-05-01
> **warp99 said:**
> Open a terminal and issue the following:
```
sudo update-alternatives --config usplash
```
then choose 'ubuntu' as your splash screen. If it's not available then:
```
sudo apt-get install usplash-theme-ubuntu
```
then run the previous command again.

Edit:

I just remembered that your initrd.img may not update after you run 'sudo update-alternatives --config usplash' so if your initrd.img is not updated, just look at the screen you'll see if this happens or not, run the following:
```
sudo update-initramfs -u 
```
this will update the initrd.img to include the correct usplash image at boot.

Thanks Warp99. I'm afraid it doesn't help, though :(. When I run "sudo update-alternatives --config usplash" it says there are no alternatives for usplash, even after I've run "sudo apt-get install usplash-theme-ubuntu". Also "sudo update-initramfs -u" doesn't help.

---

### Post by warp99 on 2008-05-01
> **boddhisatva said:**
> Thanks Warp99. I'm afraid it doesn't help, though :(. When I run "sudo update-alternatives --config usplash" it says there are no alternatives for usplash, even after I've run "sudo apt-get install usplash-theme-ubuntu". Also "sudo update-initramfs -u" doesn't help.

Then run the following:
```
sudo apt-get remove --purge usplash*
```
this will remove all of the artwork for Ubuntu/Kubuntu and the usplash configuration files. It will also remove the packages kubuntu-desktop and ubuntu-desktop, but these are only meta packages and the actual desktops will not be removed, then:
```
sudo apt-get install usplash usplash-theme-ubuntu
```
this should create a new initrd.img with the correct splash theme, if not then:
```
sudo update-initramfs -u
```
or
```
sudo dpkg-reconfigure usplash
```
one of these commands will update the initrd.img file.

---

### Post by boddhisatva on 2008-05-01
That's worked. Thanks a lot!
So nice to see the old Ubuntu screen again :)

---

