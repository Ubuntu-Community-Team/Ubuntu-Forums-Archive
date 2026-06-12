---
title: "after ubuntu boots it just starts flahing scrambled colors"
date: 2009-05-10
forum: General Help
---

### Post by nathang1392 on 2009-05-10
hi,

last night before i went to bed i shut down my computer as regular and everything seemed fine, but today when i turned it on it went to the jaunty loading screen and after it finished it just started flashing scrambled colors and thats all it would do. anyone ever seen this happen, or know how to fix it without reformat?

---

### Post by Triptol on 2009-05-10
Happened to me as well. On that PC I had an nvidia card. Something probably messed with your xorg.conf. You could try to move it out of the way:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
To do this you need access to your console. Let us know if you can reach that point.

---

### Post by nathang1392 on 2009-05-10
im not sure if i can make it to anything, i cant get passed the loading screen.

---

### Post by flummoxed on 2009-05-10
My brother is having the exact same problem on his computer. I looked at the XORG log in /var/log, but it didn't seem to have anything out of the ordinary. 

I tried sudo dpkg-reconfigure xserver-xorg on the recovery console, but it didn't do anything.

---

### Post by nathang1392 on 2009-05-10
i really dont want to have to install ubuntu again. i hope i can find a solution.

---

### Post by KhurramM on 2009-05-10
Can u run the liveCD?

boot into live mode,

compare the /etc/X11/xorg.conf of live and installed ubs?

if different: then copy paste live xorg.conf file to the installed one, hope this works.

Else also try the auto recover of X in the rescue mode.

Hope u can solve this.

---

### Post by nathang1392 on 2009-05-10
would i have to have the 9.04 live cd or would the 8.10 work as well? i upgraded.

---

### Post by Triptol on 2009-05-11
They should both work.

---

### Post by nathang1392 on 2009-05-11
so if i boot the live cd and enter the command in listed in this post it will fix the loading of jaunty that is on my hard drive? im just wondering because i thought that the live cd couldnt touch your hard drive.

---

### Post by nathang1392 on 2009-05-11
i tried going into the rescue mode to repair the graphics but it didnt work. im going to try the live cd next but where is the x org file that i need to replace located?

---

### Post by nathang1392 on 2009-05-12
i located the x org file from both the live cd and the original that is on the hard drive but i dont have the right permission to replace the original. how do i get these permissions, i forgot how to login as root.

---

### Post by nathang1392 on 2009-05-12
please you guys, i need some help. my desktop is now useless without a live cd that im using to type this post.lol.

---

### Post by superjer on 2009-05-31
I had the same problem and I found a solution!

Short version: Remove xserver-xorg and reinstall it.

Long version:

1. Press Escape when GRUB starts and choose the first "(recovery mode)" option.
2. Once you get a menu, choose "netroot" to get a command prompt.
3. Remove X with: **apt-get remove xserver-xorg**
4. You may want to write down the packages to be removed if you are paranoid.
5. Type **Y** to continue.
6. Once it's done, type **reboot** to reboot (this may not be necessary, I don't know).
7. Repeat steps 1 and 2 to get back to a command prompt.
8. Install X *and the stuff that got taken out with it* with: **apt-get install ubuntu-desktop**
9. Type **Y** to continue.
9. Type **exit**
10. Choose "resume" and everything should be good again.

This is probably overkill but I can't test for a shorter solution now that it's fixed. For the record, running xfix or removing xorg.conf did not help.

I hope this helps the next victim!

---

