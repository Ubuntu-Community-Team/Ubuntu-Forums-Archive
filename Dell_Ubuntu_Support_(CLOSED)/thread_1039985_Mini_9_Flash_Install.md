---
title: "Mini 9 Flash Install"
date: 2009-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sirebral on 2009-01-15
I have my Mini 9 and I want to rid it of the Dellbuntu.  All I have is an SD Card and I've tried to flash the ISO to the SD card, but the PC won't read it during boot.  I don't have a USB Drive big enough for Xubuntu.  Can anyone help?

I woulnd't ask but during my attempts I installed the Master Boot Record (MBR) to the flash device and now it won't mount.  All the advice I've seen is for USB Sticks.

---

### Post by armandh on 2009-01-15
the first thing I did was to buy a cheap usb cd/dvd drive case and put a drive from the good spares in to it.

later I discovered that my desktop [8.04] could down load the needed [put os on usb] software.  a 1Gb usb memory stick is needed to load the non dell Ubuntu OS from cd to usb. I now have the Ubuntu live cd on a usb memory stick. of course if you want the "restore dell Ubuntu" on a usb you probably need more than 1 gig as it is on a dvd.

I never tried any of the Xubuntu. only the regular and only 8.04.1 and later worked.

---

### Post by sirebral on 2009-01-15
well that just sucks.  I thought I could do this with a flash drive.  Seriously no help for the flash drive?

---

### Post by anjilslaire on 2009-01-15
Does Unetbootin not work with SD cards?

On my 8.10 desktop I used the built-in "create a usb startup disk". I've installed the right tools on 8.04 as well, but I can't recall what it is atm.

After buying the mini, a $20 usb drive is well worth it IMO to install an OS at will.

---

### Post by sirebral on 2009-01-15
right now I am stuck with the DELL Ubuntu release.

I have some likes and dislikes.

I like:

The stability.  I had to allow the laptop to connect to the router but after I updated it fixed a lot of problems.  I seem to have no problems with Java, Flash, audio, or any of the other problems I might see with a fresh install.  

Out of the Box is OK.  From what I was reading the updates fixed the broken LPIA links.  I also managed to download WINe, Skype, Eclipse, and the other usual suspects for my regular computing and schooling.  I am pretty pleased with the out of box experience.

I dislike:

The stuck in a box feel.  While the distro is really stable, it is also blocking some cool features.  I cannot change the Appearance fully (no Effects), I cannot choose to update the kernel (Maybe I can just not certain), the extra fluff takes time to remove (Adobe?), and other stuff like that.

For some reason my window frames colors get messed up when I use certain tool bars.  I don't like that at all.

The OS seems jerky.  It kinda lags a little during certain processes.  I am not sure what causes that.  I know another poster mentioned this, and while mine doesn't exactly gray out I do notice the slight lag when performing certain tasks.


I am actually pretty pleased with the Dell Ubuntu.  It looks like they worked out the kinks and have a really stable OS.  I think after playing around with it and enjoying how stable the OS was right out of the box I might just stick with it.

Weird that I would turn around like that, but my main argument was what I was hearing about it's broken ness.  I am actually typing on the little Mini right now and I totally love the keyboard.  I know when we were talking about it on Idea Storm that people had problems with it, I still kinda do.  They were talking about dropping the F keys altogether, but thankfully they heard us and mapped them with the Fn key.  They could have removed the border around the sides a little more and made the keys a little bigger.  Punctuation is the hardest.

Yet overall I really like this distro.  I am happy with the DELLBuntu and I think I will keep it.

---

### Post by anjilslaire on 2009-01-16
Yes, the keyboard is great, and the Dellbuntu was fine, but I just don't care for preinstalled OSes. Just my thing, I guess.

I'm running the vanilla 8.10, plus the Netbook Remix, so its essentially the same as the DEll version, but as you said, I'm out of the box, so to speak. Knowing that I can install anything I want is nice, and upgrade to 9.04 in th spring is a warm fuzzy feeling in itself :)

I'm not a fan of gnome, but I'm really digging the Remix feel.

Regarding your lag, how much ram you have?

---

### Post by snowpine on 2009-01-16
I recommend using Unetbootin to copy the .iso file to the SD card. Reformat the SD card if you've used it for other experiments in the past so you start with a "blank slate".

---

### Post by sirebral on 2009-01-16
> **anjilslaire said:**
> 
Regarding your lag, how much ram you have?

Just 1 GB.  I have no extra money right now to spend on RAM, so I am just going to live with it.  

I myself am not a 'pre-installed OS' kinda person either, so I completely understand you.  I mentioned this before that I will probably just wipe the SSD in the future, so I have a question for you.  

Dell Drivers, easy install?

I thought the answer could be, "Duh n00b, it's Linux.", but I wanted to know if the drivers add to stability also.

> **snowpine said:**
> I recommend using Unetbootin to copy the .iso file to the SD card. Reformat the SD card if you've used it for other experiments in the past so you start with a "blank slate".

Did this snowpine.  Problem is that the OS is not reading the flash card on boot.  It is weird because the BIOS says I should be able too, I think.  "Removable Drives" is an option.  I thought maybe there was a setting I could change that would force the laptop to boot from the SD Card.

Thanks for the comment though.

---

### Post by anjilslaire on 2009-01-16
> **sirebral said:**
> so I have a question for you.  

Dell Drivers, easy install?

I thought the answer could be, "Duh n00b, it's Linux.", but I wanted to know if the drivers add to stability also.

No drivers needed. Install the OS, get all updates, accept the Restricted driver for the Broadcom wireless driver. Add one line to a config file to get sound working.

My webcam works, everything seems good. I've even upgraded my BIOS to A03, even though its apparently not recommended if you're running Linux instead of windows :???:

The only thing I've noticed is, it seems to like wpa2, but not wpa. Thats fine with me, tho...

---

### Post by sirebral on 2009-01-16
8.10 is pretty nice.  Alright.  I still plan on flashing Xubuntu on her, I am just sticking with this for now.

---

### Post by armandh on 2009-01-16
> **sirebral said:**
> 8.10 is pretty nice.  Alright.  I still plan on flashing Xubuntu on her, I am just sticking with this for now.

save that 8.10 on the thumb drive you may want to go back after X

---

### Post by sirebral on 2009-01-16
How come? X comes in 8.10 now.

---

