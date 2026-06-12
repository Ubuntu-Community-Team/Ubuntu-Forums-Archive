---
title: "X-server doesn't start and doesn't error"
date: 2005-12-21
forum: General Help
---

### Post by mbollenb on 2005-12-21
Hello and thanks in advance for any help! 

  I am new to linux and have a few problems my sound HDA intel I can't get to work following any guide!  But thats not the most important my xserver doesn't start on its own and I do not get an error.  Basically when I fire up my box it loads everything then just goes straight to the command line requesting user/password.  Now I can user 'startx' to load and run fairly fine.  I have tried a few things to no avail.  I have run dpkg-reconfigure xserver-xorg as to reload a brand new xorg, this did nothing!  So I loaded the old one back in that works with my dual monitors.  Seondly I restored my /etc/fstab and again this did nothing.  I have tried to undo everything I think that I may have done and I cannot figure it out!  I am getting so frustrated.  I believe that this problem occured when I was trying to get the sound working with alsa but I may be wrong.  I don't want to revert and have to re-install and trasfer everything that I have done.  Please help!  Let me know any ideas you may have.

Bonus Question:  haha!  if anyone knows how to get my sound working thats a plus I have an asus P5GL-MX motherboard and am just trying to use the onboard sound

---

### Post by kaamos on 2005-12-21
One thing you could try.. if you have gnome:
```
sudo dpkg-reconfigure gdm
```
if you have kde:
```
sudo dpkg-reconfigure kdm
```
Hope this helps!

---

### Post by mbollenb on 2005-12-21
Thank you!  This didn't fix the problem fully after that I had the error "Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File sould be owned by user and have 644 permissions."  

I adjusted the permissions on my home folder and error gone and everything loads perfectly.  Thank you for all of your help!

---

### Post by mmarkvillanueva on 2006-07-22
I also have ASUS P5GL-MX and I'm having a lot of trouble installing Linux with it. I've tried different versions of Ubuntu and SUSE (including the recent versions Ubuntu 6.06 and SUSE 10.1) but still experience shutdown problems. Everytime I log-off from the X-Server, the screen turns blank just like a virtual console and it becames idle, as if it crashed. I have to manually press the power button on the CPU just to shutdown the PC.

I'm just wondering if you have experienced the same problem before.  I'm not sure but I think the problem has something to do with the driver for the Intel 915GL chipset. Because I'm not experiencing problems in the console mode, and I haven't experienced that problem since I've tweak X to provide 1280x1024 resolution. you see, by default, the maximum resolution I get is 800x600 in my 17" monitor.

You see, I really want to run Linux in my PC. I've been going in circles trying to figure out how to fix things for aroung 6 months.

---

