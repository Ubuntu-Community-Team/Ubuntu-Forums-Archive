---
title: "vista and unbuntu: wireless works with vista but not with ubuntu"
date: 2009-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spookycoop on 2009-11-09
I just purchased a new dell inspiron that came with Vista.  I chose to install Ubuntu and to erect a partition between vista and unbuntu.  Two problems to begin with.
 
1. ubuntu reports that I have bad errors on my new hard drive, while a hard drive examination using vista shows no errors.  I sure hate to think that my new computer's hard drive is already damaged.
 
2. wireless connection is fine with vista, but isn't working with ubuntu. I've googled this problem, but am finding it difficult because the advice involved typing in commands in dos.  I'm a novice.
 
Any help will be deeply appreciated.  Thanks.

---

### Post by mikewhatever on 2009-11-09
Welcome to the forums,

> **spookycoop said:**
> I just purchased a new dell inspiron that came with Vista.  I chose to install Ubuntu and to erect a partition between vista and unbuntu.  Two problems to begin with.

Mentioning the model would have been nice. I may have helped people identify problematic hardware.
 
> 1. ubuntu reports that I have bad errors on my new hard drive, while a hard drive examination using vista shows no errors.  I sure hate to think that my new computer's hard drive is already damaged.

This is probably a false positive, so nothing to worry about.
 
> 2. wireless connection is fine with vista, but isn't working with ubuntu. I've googled this problem, but am finding it difficult because the advice involved typing in commands in dos.  I'm a novice.

Dell uses a lot of Broadcom cards with proprietary drivers, not included in the default Ubuntu installation. There is a program to download and install the driver under System->Admin -> Hardware Drivers, but it requires internet connection to work. In short, you'll need to plug in a cable for about five minutes.

---

### Post by spookycoop on 2009-11-11
Thanks, Mikewhatever

I connected via a wired connection, and followed your instructions. As a result, I was able to connect via my wireless network.  However, when I tried to reconnect, I could not.  I tried repeating what I did before, but to no avail.  What do you think?

---

### Post by spookycoop on 2009-11-11
Also, couldn't connect to wireless via Vista, which has never been a problem

---

### Post by efflandt on 2009-11-16
If you want more help post the model of your computer.  And in a terminal type:

**sudo lspci -v**

And copy and paste the part that applies to your wireless device here.

Also see if System, Administration, Hardware Drivers shows any special drivers for your computer.  But do not activate all of them, because sometimes if more than one applies to same hardware activating both will not work.

Someone else who had an issue with their wireless did not have it turned on (probably using blue Fn key like shift key one that looks like radio tower).  Although, you may need to make sure that it is turned on in Vista first, because wireless LED does not always work in Linux if your wireless uses a special driver.

---

### Post by life2short1971 on 2009-11-20
I had alot of problems with my wifi also until i installed Wicd network manager instead of the default network manager

---

