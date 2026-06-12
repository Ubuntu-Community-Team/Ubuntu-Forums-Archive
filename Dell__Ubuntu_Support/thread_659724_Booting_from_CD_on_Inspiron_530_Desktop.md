---
title: "Booting from CD on Inspiron 530 Desktop"
date: 2008-01-06
forum: Dell  Ubuntu Support
---

### Post by Antone on 2008-01-06
I can not get this computer to boot from the CD drive does anyone have a procedure I can follow?

---

### Post by gbrainin on 2008-01-06
There are two ways to get the system to boot from the CD; both require catching the computer right at the beginning of the boot process.

When you get the very first splash screen (the one that says "Dell"), in the upper right corner it will say to press F2 for setup or F12 for boot menu.  (I may have the exact text wrong, but that's the gist of it.)

If you press F12 at the right time (not too early, not too late), you will be presented with a list of bootable drives which you can select from.  This allows you to do a one-time boot from any drive you select.  The computer will not remember this selection next time you boot.

If you press F2, you get the BIOS setup menu.  In there, you can make a more permanent selection of the order of boot devices, if, for example, you want to boot from the CD several times in a row.  You can then, of course, change it back when you're done.

---

### Post by Antone on 2008-01-06
Thanks for that, it worked just fine except that my bluetooth mouse and keyboard don't work on the opening screen so I still can't access the example folder.

---

### Post by gbrainin on 2008-01-07
What CD are you using?  The standard Ubuntu CD does not have all the drivers necessary to fully take advantage of all Dell hardware.  You may need to download and burn the Dell modified CD (actually, for 7.10, it's a DVD) if you want all your hardware to work in that mode.

You can get the downloads at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10")

---

### Post by Antone on 2008-01-09
Thanks again, am now up and running

---

### Post by boyofford on 2008-01-09
> **gbrainin said:**
> What CD are you using?  The standard Ubuntu CD does not have all the drivers necessary to fully take advantage of all Dell hardware.  You may need to download and burn the Dell modified CD (actually, for 7.10, it's a DVD) if you want all your hardware to work in that mode.

You can get the downloads at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10")

I've got 7.10 running on  my inspiron 530s, everything seems ok so far, occasional crashs with some applications but assuming just because its not the LTS (i.e hardy heron). 

My question is, should I have used the Dell iso instead? would this have worked better? 
If so I think I'll wait till hardy heron, presumably Dell will be releaseing a Hardy heron iso as well?

---

### Post by gbrainin on 2008-01-09
I am actually using the generic version of 7.10 on my 530n also, without any issues.  The only reason I recommended the Dell iso is because the OP is using a bluetooth mouse and keyboard.

AFAICT, the main purpose of the Dell iso is to tweak compatibility with the specific hardware they ship.  For example, the Dell 7.10 530/nVidia iso comes with the nVidia proprietary driver installed and enabled by default.  (I just enabled it manually after installing.)

Long story short, if your computer doesn't have hardware/driver issues, I don't think you need the Dell iso.  But that's just my understanding.

What applications are crashing?  LTS just means that updates are available longer; it's not a guarantee of any greater stability at the beginning.  (Though, of course, each release does try to address issues with the previous release.)

---

### Post by boyofford on 2008-01-10
[QUOTE=gbrainin;4103176
What applications are crashing?  LTS just means that updates are available longer; it's not a guarantee of any greater stability at the beginning.  (Though, of course, each release does try to address issues with the previous release.)[/QUOTE]

doh.. LTS does not garantee greater stability, I knew what LTS ment but for some reason got it in my head that it would be more stabile! don't know why i suppose!

Does the dell iso have flash as a default as well? that was a bit of a pain to setup, but by no means unsolveable (I am a novice so probably made more of a meal of it than should!)

Mainly problems with compiz-fusion, but only got nividia 8300 128mb graphics card so maybe to be expected.

might try dell's hardy heron, but might go 64-bit route (dell might not release a 64-bit iso though).

---

### Post by gbrainin on 2008-01-10
I thought I read somewhere that things like flash were enabled by default, but I don't see any reference to that on the wiki.

Oddly, the downloads specify the 8400 and 8600 cards, though the download seems to be identical (same MD5 sum).  Does that mean it won't work with other cards, or just that they've only tested it with those two?  I don't know.

I wouldn't think you should have big problems with compiz-fusion; it looked okay on my machine with the 7300 card, but I disabled it for other reasons (didn't work & play well with WINE).

---

### Post by Antone on 2008-01-20
> **gbrainin said:**
> I am actually using the generic version of 7.10 on my 530n also, without any issues.  The only reason I recommended the Dell iso is because the OP is using a bluetooth mouse and keyboard.

AFAICT, the main purpose of the Dell iso is to tweak compatibility with the specific hardware they ship.  For example, the Dell 7.10 530/nVidia iso comes with the nVidia proprietary driver installed and enabled by default.  (I just enabled it manually after installing.)

Long story short, if your computer doesn't have hardware/driver issues, I don't think you need the Dell iso.  But that's just my understanding.

What applications are crashing?  LTS just means that updates are available longer; it's not a guarantee of any greater stability at the beginning.  (Though, of course, each release does try to address issues with the previous release.)


Is it possible to download the nVidia driver?  Is there also a driver for an HP PSC 1410? Mine is working but in a limited fashion.

---

### Post by gbrainin on 2008-01-20
> **Antone said:**
> Is it possible to download the nVidia driver?

   Yes.  If your card is recognized by the system (most are), you just go to System > Administration > Restricted Drivers Manager and select it.  The download will happen automatically.  If your card is not recognized (I had this happen with an 8300 card under 7.04), you need to identify and download the correct driver yourself.  I found that Envy was the easiest way to do this.

> Is there also a driver for an HP PSC 1410? Mine is working but in a limited fashion.

I don't know about this particular piece of hardware.  I would start by checking the [hardware list]("https://wiki.ubuntu.com/HardwareSupport") to see what others have done.

---

### Post by puzzledinmn on 2008-01-24
Once you do that you may find this thread useful to use it.

[http://ubuntuforums.org/showthread.php?t=569491&highlight=dell+530](http://ubuntuforums.org/showthread.php?t=569491&highlight=dell+530)

---

