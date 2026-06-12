---
title: "Why Does Beryl Blackscreen after Inactivity?"
date: 2007-07-12
forum: Desktop Effects &amp; Customization
---

### Post by markclewis1 on 2007-07-12
Hello All!  I would like some help if you can provide it.  I am running Feisty with Beryl installed.  Everything is working satisfactorily except that Beryl black screens my display after a period of inactivity.  I am wondering if there is any way to avoid this.  If I set my screensaver to come on earlier than 10 minutes, then the screensaver comes up for a time period, then Beryl black screens it with the screensaver still running underneath the black screen.  If I don't have my screensaver set to come on, I still get a black screen after a period of inactivity.


If there is a solution to this, can someone please advise!  I have a presentation to give on Monday and I would like to use my Feisty notebook to demonstrate during the presentation, but if it is going to keep 'blacking' out on me, then I don't want to do it.

Thanks!!

Mark

---

### Post by Waappu on 2007-07-12
Hi

Are you sure that is caused by Beryl? Do you use Beryl screen saver plugin? If you change to Metacity does same occurs ?

---

### Post by markclewis1 on 2007-07-12
No, I am not sure that it is caused by Beryl.  But, prior to installing and setting up Beryl, I did not have this problem.  I am not using the Beryl Screensaver plugin.  Just one of the screensavers from gnome.

A little more explanation maybe:  If I set my screensaver to come on after 10 mins, a black screen pops up about 10 minutes in to inactivity, if I swipe my mouse, there is my screensaver running underneath the black screen.  If I set the screensaver earlier, it comes on and runs, but after 10 minutes of inactivity, the black screen comes up over the screensaver.

Basically, no matter what happens, after approximately 10 minutes of inactivity, black screen.  Switch screensaver to 2 hours or off, to watch a movie, black screen after about 10 minutes.  Goes away with a mouse swipe, but not the most appealing thing.  Work in VM with windows, black screen after a period of time.

I am giving a presentation to people that have never seen Linux.  I want to run the powerpoint out of VM with Windows so that when I wrap up, I can show them Feisty and Beryl.

Thanks!

Mark

---

### Post by markclewis1 on 2007-07-12
Ok, I switched off Beryl manager and went to Metacity (which worked before).  Got the same thing.  After about 10-15 minutes my screen goes black.

Any ideas?

Mark

---

### Post by Waappu on 2007-07-12
Hi

I don't have any other ideas than check power preferences
Press Alt+F2 and type```
gnome-power-preferences
```

---

### Post by markclewis1 on 2007-07-12
Yeah, I thought of that too just before you posted that.  I have all of my power settings set to never and even changed the 'lid closed' option to 'do nothing'.  Still didn't change anything.  This is just really strange because I didn't have this problem until I started using Beryl.  May have something to do with the AIGLX graphic set that I had to go to for Beryl to work with my ATI graphics card.  Dunno.

Thanks for your help though!

Mark

---

### Post by Death &amp; Taxes on 2007-07-14
I've got the same problem after my reinstall yesterday. Screen goes black after a period of inactivity. I removed all screensaver-related components I could find and turned off power saving, but it still goes blank (very annoying when you're watching a movie).

I remember having that problem in the past, but I solved it somehow. Don't remember how though...

---

### Post by WowMike2002 on 2007-07-14
> **Death & Taxes said:**
> I've got the same problem after my reinstall yesterday. Screen goes black after a period of inactivity. I removed all screensaver-related components I could find and turned off power saving, but it still goes blank (very annoying when you're watching a movie).

I remember having that problem in the past, but I solved it somehow. Don't remember how though...

If you are running a certain type of LCD, it will auto-blackscreen to make sure you dont accidently burn in the LCD.. most newer monitors do it nowadays, and a few older monitors for desktop/laptops.   If there is a way to fix it.. I am not too sure, might have to stab around on the laptop's forums to see if anyone has found a way to get around this.

---

### Post by Death &amp; Taxes on 2007-07-14
> **WowMike2002 said:**
> If you are running a certain type of LCD, it will auto-blackscreen to make sure you dont accidently burn in the LCD..

I have a CRT, and it certainly doesn't have such a feature. It is definately software-related.

---

### Post by bobbuilder on 2007-07-14
This is what worked for me... may be worth a shot
Post #6 in particular

[http://ubuntuforums.org/showthread.php?p=2160598](http://ubuntuforums.org/showthread.php?p=2160598)

---

### Post by Death &amp; Taxes on 2007-07-14
> **bobbuilder said:**
> This is what worked for me... may be worth a shot

It works! Thanks so much for the tip.

---

### Post by markclewis1 on 2007-07-17
Well, that definitely stopped the blacking of the screen.  Thanks very much for the tip!!  Now if only I could get a screensaver to work, then all would be excellent.  Oh well, maybe in the future those bugs won't be there and I can reverse the settings.

Thanks!!!

---

