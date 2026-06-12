---
title: "Remote Desktop Without Monitor Connected"
date: 2013-04-08
forum: Desktop Environments
---

### Post by neutronforrest on 2013-04-08
Dear Forum,

I have a fresh install of Ubuntu 12.04 on a new system I just built.  I plan to use this for a media server without a monitor attached.  My issues is accessing the desktop from another computer.  I plan to use the desktop sharing.  However, the desktop will not work unless a monitor is connected.  I don't understand what is going on.  I tried the following with no luck,

I opened /etc/default/grub

then I added 

GRUB_CMDLINE_LINUX="nomodeset"

I did

sudo update-grub

This did not work.  I hope someone can help me.

---

### Post by Ice On Fire on 2013-04-09
Hi neutronforrest, 

I have a similar setup - I'm running Ubuntu 12.10 with Plex Media Server for streaming my media over a network to the Xbox 360. 

All I did was enabled desktop sharing and made sure a password was required to login. Took off option that I needed to accept the connection. 
From my Mac, I used a VNC client and this worked just fine. No monitor attached. 

What happens when you try connect without the monitor?

p.S: As a side note - I enabled port 5900 for VNC on the router. However, I think if you can connect remotely already - this isn't an issue. 

I hope this helps.

---

### Post by neutronforrest on 2013-04-09
Dear Ice On Fire,

When I connect the monitor and boot the machine it works fine.  I am able to remote desktop into the machine from another computer.  Even more interesting is that I can turn off the monitor attached to my server and still remote desktop in from any computer.  It has something to do with the boot process and Ubuntu seeing if a monitor is attached.

I had another motherboard with the same setup and I had no issues with remote desktop.  This is a new intel motherboard and I also think that has something to do with it.  

I have read online that I need to FIRST,

 opened /etc/default/grub

then I added 

GRUB_CMDLINE_LINUX="nomodeset"

Then run sudo update-grub

SECOND,

I have to write a x server file or xconf...not sure here.  I am not sure why I need to do this.  I am hoping someone can explain this to me.

---

### Post by Ice On Fire on 2013-04-10
Very interesting. 

I have my media centre connected to the TV - however, when I rebooted last night, I was denied access when trying to log back in. 
Let me do some testing tonight and see what causes this and how we fix it. I too have an Intel motherboard. I will get back to you tonight. 
(It's 9:34am here, in South Africa. )

---

### Post by cybergalvez on 2013-04-12
I use x2go, no monitor is needed

---

### Post by Ice On Fire on 2013-04-20
I have tried this out. Sorry it took me so long to get back to you. 

I experience the same issues as you. if I logout of my session or reboot + unplug the monitor, I can no longer VNC back into the computer. I recieve a "Low graphics mode" error when I plug monitor back in to see where the Ubuntu is at. Odd. 

I will see if x2go will solve this issue.

---

### Post by QIII on 2013-04-20
Hello!

I've always had good luck using the xserver-xorg-video-dummy package running headless.

Worth a try.

Best wishes!

---

### Post by Ice On Fire on 2013-04-20
I think that might be a solutions. I'll give this a go later on today. Thanks for the tip.

---

### Post by neutronforrest on 2013-04-28
Dear group....I just installed Ubuntu 12.04 onto another desktop, my wife's, to see if my issue was the motherboard.  Unfortunately, the same issue happens.  I tried the following,

Sudo apt-get install xsever-xorg-video-dummy 

I got an error when I tried this.  Did I have something wrong?

---

