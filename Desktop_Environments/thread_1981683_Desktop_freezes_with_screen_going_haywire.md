---
title: "Desktop freezes with screen going haywire"
date: 2012-05-17
forum: Desktop Environments
---

### Post by gfc2012 on 2012-05-17
Hi there everyone.

I've only just started having a problem with my Ubuntu 11.04. My screen randomly flickers and fills with garbage and then freezes. I can still move the pointer but cannot click on anything when this happens. I'm not sure what I did that is causing this, but I did an update earlier. I wondered if it was compiz mucking up so I tried reinstalling that but had no luck. 

If anyone has any suggestions, I'm all ears. :)

Rob

---

### Post by kc1di on 2012-05-17
> **gfc2012 said:**
> Hi there everyone.

I've only just started having a problem with my Ubuntu 11.04. My screen randomly flickers and fills with garbage and then freezes. I can still move the pointer but cannot click on anything when this happens. I'm not sure what I did that is causing this, but I did an update earlier. I wondered if it was compiz mucking up so I tried reinstalling that but had no luck. 

If anyone has any suggestions, I'm all ears. :)

Rob

hi Rob,
did it upgrade the kernel?  and what is your video card?

if the Kernel was upgraded then chances are that's what is doing it. Actually I think it's xorg's new version that may be the problem. doesn't work well with some Nvidia and other video cards.
you can try fall back mode. that may get you by for the moment.

In any event give us the particulars of your video card and will see if we can help.

---

### Post by gfc2012 on 2012-05-17
Hey thanks for the reply.

My graphics card is the Asus EN8600GT. And I honestly couldn't tell you if the kernel was updated or not, I'm sorry. I'm relatively new to Linux. Lol.

Rob

---

### Post by kc1di on 2012-05-17
hi again,
the  Asus EN8600GT uses Nivida graphics and may be affected by the problem I mentioned before.

have you ever installed the drivers from the additional driver tool?  if so go there and uninstall them. 

reboot and try again.

---

### Post by gfc2012 on 2012-05-17
Ok I brought up the Additional Driver Tool, and it has the choice of version 173 and the current version. I deactivated the current version, which I had selected previously. Neither of them are selected now. I assume that's what you meant?

Again sorry if I'm coming across as being a noob. Lol.

Rob

---

### Post by kc1di on 2012-05-17
> **gfc2012 said:**
> Ok I brought up the Additional Driver Tool, and it has the choice of version 173 and the current version. I deactivated the current version, which I had selected previously. Neither of them are selected now. I assume that's what you meant?

Again sorry if I'm coming across as being a noob. Lol.

Rob

that correct Rob it when you reboot it should be work with the open source driver which may have some limits. but should not freeze up on you.  

I'll post another post and tell you how you can install and try the latest nvidia driver which may also cure the problem.

---

### Post by gfc2012 on 2012-05-17
Thanks Dave, I tried that and rebooted. No dice I'm afraid. Still got a messed up screen and freezing. :(

Rob

---

### Post by kc1di on 2012-05-17
OK here's what I want you to try in a teminal

```
sudo apt-get purge nvidia
sudo apt-get install xserver-xorg-video-nouveau
```
copy them one line at a time.
reboot and let me know if that helps

---

### Post by gfc2012 on 2012-05-17
Ok I'll give them a go. Thanks. :)

Do I enter them in Recovery Mode?

Rob

---

### Post by kc1di on 2012-05-17
you can but you need to be in a teminal.

---

### Post by gfc2012 on 2012-05-17
All righty, I did as you instructed, in Recovery Mode so it wouldn't crash on me. Lol. Here's what it came up with:

$ sudo apt-get purge nvidia
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia
$ sudo apt-get install xserver-xorg-video-nouveau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-nouveau is already the newest version.
xserver-xorg-video-nouveau set to manually installed.
The following packages were automatically installed and are no longer required:
  ubufox libevent-1.4-2 libboost-serialization1.42.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Rob

---

### Post by kc1di on 2012-05-18
and I take it there is no difference. 
Well the crash is being caused by something other than the video driver. if that is the case.  
Try doing another update but this time from the command line.
in terminal do the following.

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```
Lets see if that produces anything.

---

### Post by kc1di on 2012-05-18
Also you may want to check the log files they may contain some information on the crash itself.
first I'd check the xorg log it's found at
/var/log/Xorg.0.log  post the results here if you can.
also look and xorg -old.  

you can veiw them in any text editor or in terminal
by typing:
```
sudo nano /var/log/Xorg.0.log
```
do not make any changes in them though.

---

