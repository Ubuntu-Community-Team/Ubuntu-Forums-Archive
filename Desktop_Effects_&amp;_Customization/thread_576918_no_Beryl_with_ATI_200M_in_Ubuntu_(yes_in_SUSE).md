---
title: "no Beryl with ATI 200M in Ubuntu (yes in SUSE)"
date: 2007-10-15
forum: Desktop Effects &amp; Customization
---

### Post by drjiga on 2007-10-15
This is very odd, 

I have HP zv6000 with the Radeon 200M. Recently I've transitioned from openSUSE to Ubuntu. In suse I managed to get Beryl and compiz going with the latests proprietor drivers from ATI. Fairly easy.

Now what puzzles me, is why Ubuntu is refusing to run those two. 
I've looked through everything that pertains to this topic, but haven't had much success. 
I have installed proprietory driver iand XGL. However desktop effects refuses to launch in gnome, I get an obscure message saying can't run effects . When I enter Ubuntu through XGL session, my screen is scrambled. So I can't do much. 

This may be the issue with 200M's weird 3D support, but if it runs Beryl in suse just fine, shouldn't it do the same in Ubuntu. Please help, greatly appreciate it.

I am running 32-bit Ubuntu 7.04

---

### Post by xxrealmsxx on 2007-10-15
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

It usually works for me if I follow this guide, use the desktop effects that come with ubuntu, do a system update and move on to compiz-fusion after a restart.

---

### Post by drjiga on 2007-10-16
Tried that, however XGL session looks scrambled. I can't really see the desktop, so something must be going wrong. Thanks for a reply though.
Any other suggestions are appreciated.

---

### Post by drjiga on 2007-10-16
I have noticed one interesting thing. 
If I go into Restricted Drivers Manager and deselect the ATI driver, then logout and enter in XGL session, I actually can enable the desktop effects but nothing happens.

---

### Post by drjiga on 2007-10-18
Problem partially solved: 

1. Re-install Ubuntu 7.04 

2. Enable ATI driver in Restricted Drivers Manager

3. Install XGL and create Gnome XGL session 

4. Download Compiz Manager 

6. Reboot and log in to Gnome XGL session

7. Enable desktop effects 

8. Compiz is now running. 

One problem that remains is when Beryl-manager is launched nothing happens. Compiz continues running but Beryl effects do not appear.

---

