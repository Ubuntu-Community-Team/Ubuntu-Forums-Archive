---
title: "AMD 64 install failed! Won't boot from hard drive!"
date: 2007-04-13
forum: Colorado Team - US
---

### Post by Mike Dolan on 2007-04-13
Hi, Dave, yes it's me. I downloaded Ubuntu 6.06.1 Desktop for AMD 64 and immediately burned the ISO to a CD which I used to install Ubuntu on my Western Digital 40GB. I did a full erase for the install. 

My Biostar system uses Nvidia GeForce 6100 for its video. The only part of the Ubuntu installation that failed was when it tried to install drivers for an ATI Raid display. When the install finished I removed the CD and restarted Ubuntu to see what I had.

What I had was bupkes. Biostar took almost a minute to try and find the hard drive, then told me "Disk Boot Failure, Install Boot CD." 

Help!! I'm going back to my Windows XP Pro machine until someone can tell me what happened!!

Signed, Bewildered in Bewnie

---

### Post by Mike Dolan on 2007-04-14
I'm replying next day to my own previous message.

Apparently my problem was with the hard drive I was trying to use, a Western Digital 40GB. I tried both the 6.06 and the 6.10 versions of both the Kubuntu and Ubuntu installation CD, all without success. The computer refused to boot from the hard drive each time.

So my next question is, how can I completely erase all programming, and formatting, from a hard drive using Kubuntu? Windows won't even recognize a Linux-formatted hard drive.

---

### Post by basketcase on 2007-04-15
Do you have a live CD?  If you can boot into live mode, try and format it into FAT.  My Maxtor 40GB HDD died the other day with 6.06 installed, it's 7 years old though.

---

### Post by bsg on 2007-04-23
I sympathize with your problem but unfortunately don't have the background with Ubuntu to help.  I was considering trying Ubuntu on an older sacrificial computer but was unsure what minimal requirements are for installation.  I have a Compaq with 192 RAM and a 6.0 G hard drive.  Is it possible to install Ubuntu on this and try it out to see if I want to risk putting it on a better computer?

---

### Post by Keen101 on 2007-08-10
bsg, I would give it a shot. It doesent appear you have anything to loose by tring it out on your old machine. Not sure if it has enough memory for Ubuntu though. You could try xubuntu, which doesent require as much memory.

E..And don't forget that you can always try a live-CD on any machine to see if you like it/if it works, without ever having to install it. If your not happy with it during Live-CD, then just pop it out, and no harm done.


and for Mike Dolan, 
	
Re: So my next question is, how can I completely erase all programming, and formatting, from a hard drive using Kubuntu? Windows won't even recognize a Linux-formatted hard drive.

>The easiest way I have found to re-partition/un-partiton is to use the Gparted Live-CD. You can burn it to a cd from the .iso just like kubuntu, and it has a nice GUI for easy partitioning. Gparted is on kubuntu/ubuntu too, but I think the Live-CD version is easier to use.

-keen101

---

