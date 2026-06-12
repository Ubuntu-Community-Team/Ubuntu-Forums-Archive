---
title: "How to reconfigure an xserver that is not Installed?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by grazianda on 2006-08-16
:-? Here is the situation:  The automatic configuration of my graphics card failed during installation.  So I follow the instructions to configure the GUI manually...  I reboot the computer in recovery mode like the manual says, and get to the root@ubuntu:  I type the command to reconfigure the xserver, but then a message pops up that there is NO xserver installed... I tried reinstalling and going through the same nonsense and I get the same results...  :-? At the very least I am bewilderd and am not so sure where to go from here.  At this point all I did is partition my disk space to a smaller size when I tried to boot from the CD-ROM... Can someone help?  
         Thanks a million in advance!
            Grazianda

---

### Post by tonym on 2006-08-17
Which xserver package are you using?  eg is it xserver-xorg?

---

### Post by taurus on 2006-08-17
Boot up normal and log in with your user account.  Then at the prompt, type

```

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

---

