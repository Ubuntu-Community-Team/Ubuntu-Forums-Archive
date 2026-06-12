---
title: "Vostro 1500 Hardy Upgrade Problems?"
date: 2008-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by h218design on 2008-05-04
Hello All,

First post, so before I begin, I'd like to say thank you to all who read this.  My beautiful Vostro 1500 wouldn't be up and running (with no problems) without the help of people like "Paganemolator" and the how-to's and tutorials you all post so regularly.  I've been running Ubuntu for over a year now and it's amazing.  Thank you.

Ok, here's the deal:  My Vostro 1500 is my baby... and my primary work/school/play computer.  I was just wondering if anyone has been having any major problems with upgrading to Hardy?

My specs are:
XP/7.10 (upgraded from 7.04 - no problems) dual-boot setup
Core Duo 1.6 GHZ
Dell 1390 (Broadcom 4312 rev 1) wifi
NVIDIA 256mg 8600M GT video card
and all the rest are standard bits and bobs

My concerns lie primarily in the wifi card, the video card, the hard-drive clicking issue, and the fans.

I remember that when I did the initial install I had to use ENVY to get the video card working right, and download a driver from some guy's website to get my wifi working (and BIG thanks for it!).  Also, the fans seemed to be an issue for some, so I installed GKRELLM and a plug-in from DELL to get them under control.  Later, we all noticed that the hard-drive was clicking and hard-parking the heads at shut down... luckily one of you wonderful people figured out why, and shared how to make the problem go away.

I'm totally cool with the idea that with Linux you have to be willing to work for the perfect install, but with finals coming up I can't afford to invest tons of time to get it right.  I was hoping that Hardy would address/fix most of these problems... has it?

I have seen Hardy on a desktop... it's awesome and I want it!  Could you please share with me the status of 8.04 and Vostro 1500?  If need be I can back my data up and do a fresh install, rather than upgrade if it would work better.

I'd appreciate your advice, and thank you all again for being such a great/helpful group of people.

-Cheers

---

### Post by bucketwet on 2008-05-05
Hi

Hardy 64bit installed pretty easy for me on a Vostro 1500.

Wifi(iwl3945)/video installs fine, and the nosebleed causing awful hard drive clicking can be solved with a  sudo hdparm -B 254 /dev/sda  (Search forums for info on how to do this automagically on each boot).

Fans have not been an issue for me (even with Gutsy) its always been quiet (and loud) when it needs to be - got heaphone/microphone working pretty easily also.

My main problems relate to virtualisation (have performance issues with Vmware/Virtualbox) but that might not affect you.

I wont be buying Dell in future - the MediaDirect (button 'o death) junk and the hard drive click is just not on!! Otherwise I kinda love my 1500 too.

BW

---

### Post by snowjm on 2008-05-05
I had a lot of the same issues you had h218design. Though the upgrade to Hardy seems to have fixed a lot of things (and tweaked others). My fans work fine for me. Hardy detected my broadcom wifi card and offered to download the driver and install it for me, now that works fine. I also had a problem with my sound in 7.10 where i had to rebuild alsa I believe and even then, the volume control was very sporadic. Now my sound scales more accordingly when you increase and decrease the volume. However the sound produced overall is much more quiet than it used to be. Everything else works great.

I also noticed the sound volume decrease issue on my fiance's 1321 (came with vista). When before in 7.10 the sound card was detected and functioned correctly and at a louder consistant volume.

EDIT: Figured out my sound problem. My front speakers set to be at a much lower volume. o.O

---

### Post by h218design on 2008-05-05
bucketwet, snowjm,

Thanks for the quick replys.  I'm thinking a clean install of 64bit after finals... just in case.

snowjm - are you running 64 or 32 bit?  

bucketwet - the clicking is still there after upgrading?!  Thanks for the fix info.

Thank you both for the input, maybe this will help others waiting on the fence about upgrading Hardy on their 1500.

cheers,

h218

---

### Post by bucketwet on 2008-05-05
Hi 

I went for a clean install and the clicking *seemed* to occur a little more often than Gutsy. However, the sudo hdparm command completely stops any clicking, so its all good.

FYI, for me it also clicks in Vista, just not as often as Ubuntu.  Note: sudo hdparm doesnt seem to work in Vista, hopefully Service Pack 1 fixes that.
:lolflag:

Have fun!

BW

---

