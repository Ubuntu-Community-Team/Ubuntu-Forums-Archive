---
title: "Gutsy on Dell 531S w/ nvidia 8400 GL - Complete Success"
date: 2007-11-12
forum: Dell  Ubuntu Support
---

### Post by Fanless_Puppy_Fan on 2007-11-12
I've toyed with linux since I first bought redhat 6.0 in retail package. I can find my way around, but am still a complete noob by  most measures. I do a little tech work and have been falling behind in my skills because I was dreading the switch to Vista. So I bought a Vista loaded 531S AMD 64X2 3800+ from the dell outlet and started playing with Vista. I got all my Data and most my Aps transferred from my XP machine to Vista using MS easy transfer companion. This is what MS made of Aloha Bob which they purchased a while ago. Anyway, it took me about 10 minutes to figure out that Vista was just more of the same with a few extra clicks.

Then I found UBUNTU. I downloaded the AMD 64 bit install and burned the disk. Shrunk my Vista partition using Vista's included partition shrinker and installed Gutsy AMD64 and Grub. Fired up and installed restricted drivers and it worked pretty good right out of the box. The graphics were a little jumpy, but otherwise, everything worked.

Well back to Vista... I thought I needed to keep Vista so I could run to essential pieces of software - ventrillo and quickbooks.

I loaded up wine on UBUNTU and had ventrillo working in about 10 minutes. Tried to install quickbooks under wine and no go. Downloaded crossover and my quickbooks problem was also solved. At this point, I realized it was now time to send Rich Uncle Bill packing. I was a little dissatisfied with the video clarity and responsiveness on my dell 22WFP LCD. The VGA input didn't seem to be cutting it so I looked for a cheap yet satisfactory solution.

I ordered the nvidia 8400gs ($49.99-$20 rebate) and a slim mount bracket kit ($11.99) from zipzoomfly.com. Stuck it in, connected the DVI and downloaded the compiz config package. Enabled the cube and have been happy as a clam. I then proceeded to mount my Vista partition and grabbed ALL of my data to my home folder. I installed thunderbird and grabbed all my mail data off the Vista partition as well.

Now here is where it gets even better. I told my wife that the computer was now going to be a dual-boot and I was going to linux full time, but she could use the Vista OS if she wanted. She groaned. Within a 3 days, she was plunking away at her emails and digital photos. I asked her if she was going to use Vista and she said, "What for? This works fine." I even see her using the upper right corner fast window switcher.

Anyway, maybe everyone complaining on this board doesn't have as compatible of hardware as me or are trying to do a lot more stuff than me. I've been dubbing movies, running quickbooks, jamming internet and ebay, voice chatting on ventrillo, editing, uploading and downloading digital pictures and every other thing that I use a computer for that I can't think of.

I have not run into a snag and I am very happy to set my grub menu to default to Gutsy.

My only fear is that things might break when upgrading to Hardy, but if everything I do works good under Gutsy, I probably won't even upgrade once it's availble.

I use my computer as a tool, not a hobby. So when "it just works" seems to be the case, I'm happy to scrap Windows Vista for a not only suitable, but preferable alternative. I'm also happy to buy Crossover to make the switch possible for me. 

GTH MS!!!   <------ I've been waiting 8 or 9 years to say that.

---

### Post by derby007 on 2007-11-17
Interesting thread, I also got my Dell on the outlet site, an Inspiron 531, AMD X2 3800+, 2G ram, 250G hd, ATI x1300 Pro graphics card. 

But I couldn't get any live CD to boot. Did it boot into the live CD for you?
ie. I've seen threads about slooooooow boot-ups, taking minutes. I wonder if this is the issue.....

I had to eventually use the Alternate CD, and even with that I had to edit xorg.conf to get it into graphical mode.

---

### Post by Fanless_Puppy_Fan on 2007-11-19
I'm sure your problems have to do with that ati card. It just cd-booted right in with the onboard  nvidia 6150le or whatever comes on that mobo. When I upgraded the video card to the 8400GS, I think I just had to rerun nvidia-settings. It seems to me from what I have readthat nvidia is better supported under linux than ATI.

---

### Post by bigfootnmd on 2008-03-16
Hi,

I bought the very same xFx Geoforce 8400 graphics card and today I have tried to install it in my Inspiron 531s.  As far as I can tell the card is properly seated.
However, neither VISTA basic or Ubuntu see it.  The quick install manual
mentions that some PCI Express cards need to have a power lead connected.
I did not know this before.  So, I was wondering if you encountered this problem?  Right now the xfsfgore web page is down so I can't check there.
Maybe I will reopen the case and  check the  card again.  

Also, what is your BIOS setting for graphics is it PCI or the other setting?


OK all,  the new card was not completely seated.  This was due to the cheap design of the Inspiron 531S card holder.  I of course had to remove the full size bracket and replace it with the half height one.  Unlike every other PC I have had in the past 22 years DELL did not put in screw holes so you could screw the card tab down.  The half-height bracket did not quite fit (even though) it appeared that the card was completely seated.  When I booted up neither Vista or Ubuntu saw the card (I did verify that the card cooling fan was running).  So, what do you do when something doesn't quite fit?  You hit it gently with a hammer until it does.  By tapping the tip of the card bracket I was able to close the card retention arm and put the cover back on.  All is well.


Thanks

---

### Post by Fanless_Puppy_Fan on 2008-03-18
> **bigfootnmd said:**
> ..OK all,  the new card was not completely seated.  This was due to the cheap design of the Inspiron 531S card holder. ...
I think there is a clearance issue with a capacitor on that specific MOBO. I had to bend it a little to get mine to snap in. I assumed it was just my particular unit, but your experience suggests otherwise.

---

### Post by Brad29579 on 2008-05-08
I put in a 8600gt low pro card in my dell 531s and run gutsy with compiz, I love it, although it does run hot sometimes up to 100c.

---

