---
title: "Bluetooth &amp; Sound Problems"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by andy675 on 2008-05-09
Hi,
   I have a Dell Dimension 5150 dual core desktop and have recently installed Xubuntu 8.04, and now dual booting with Windows XP. I use a Dell Bluetooth mouse & keyboard and the only way it seems to work is for me to unplug/plugin my bluetooth adapter at the Xubuntu login screen. Is there a workaround for this to have it automatically detected every time I login?
   I also cannot find my volume contols re sound levels. I have previously trialled Ubuntu 7.10 & the bluetooth/sound icons were located at top of screen......not the case with Xubuntu. 
   I guess, while I am asking......could someone please advise how I maybe able to place my Thunderbird email icon on my desktop (or next to Firefox icon on top left of screen)?.....to enable easier access rather than having to go to applications/network/Thunderbird.
   I am certainly a newbie to Linux/Xubuntu and any advice would be greatly appreciated. (My soundcard is Sigmatel)

Thanks

---

### Post by linuxfan5246 on 2008-05-09
have you tried reinstalling xubuntu or try a different driver.

Thanks

---

### Post by andy675 on 2008-05-10
thanks for reply........install went fine & dont think a reinstall is the solution.

Anyone else with any thoughts.

Many thanks

---

### Post by andy675 on 2008-05-10
bump......anyone have any ideas......thanks

---

### Post by theZoid on 2008-06-22
> **andy675 said:**
> Hi,
   I have a Dell Dimension 5150 dual core desktop and have recently installed Xubuntu 8.04, and now dual booting with Windows XP. I use a Dell Bluetooth mouse & keyboard and the only way it seems to work is for me to unplug/plugin my bluetooth adapter at the Xubuntu login screen. Is there a workaround for this to have it automatically detected every time I login?
   I also cannot find my volume contols re sound levels. I have previously trialled Ubuntu 7.10 & the bluetooth/sound icons were located at top of screen......not the case with Xubuntu. 
   I guess, while I am asking......could someone please advise how I maybe able to place my Thunderbird email icon on my desktop (or next to Firefox icon on top left of screen)?.....to enable easier access rather than having to go to applications/network/Thunderbird.
   I am certainly a newbie to Linux/Xubuntu and any advice would be greatly appreciated. (My soundcard is Sigmatel)

Thanks

Have you tried the Bluetooth setup in my sig (blog link)?  Let me know.

---

### Post by karasuman on 2008-06-22
I'm not familiar with the model you mention.  Does it have internal bluetooth?  If not, I don't know if this will help.

I had this problem with my Inspiron 1525 with internal bluetooth.  I had to unplug the receiver every time I started up my computer, and I HAD to have the receiver plugged in.

This is what I typed in the terminal to fix it:

```
sudo hidd -s
```

Then, push the bluetooth button until the device flashes, wait a moment, and voila.  It detects it.  It usually does this automatically, now, though, every once in a while, it loses the connection and I have to reconnect.  It seemed to get better with time.

I don't know if this will help if your PC doesn't have internal bluetooth, but I don't think it can hurt to try, since all that command seems to be doing is instruct your computer to look for and connect to a bluetooth device.

I run Ubuntu, not Xubuntu, but I don't think that would make a difference for this.  Unfortunately, I can't tell you how to do anything with the desktop because, as I understand it, that's the major difference between the different versions.  :-/  On mine, you just right click on the panel and add things to it.  

As for sound, I fixed my sound problems by installing alsamixer, I think by doing

```
sudo apt-get alsamixer
```

and then ran it with

```
alsamixer
```

and adjusted settings in there.  The master volume was, by default, turned way down.  I only had to fix this once.

I hope something I said helped.  Good luck!

---

### Post by bmar on 2008-07-18
> **karasuman said:**
> 
This is what I typed in the terminal to fix it:

```
sudo hidd -s
```



Hi,

I also have a Dell Inspiron 1525 and can't get the bluetooth work.
Could you post the output of what you typed to compare with what I get ? It would help me to understand.
This is what I get :
```
bruno@bruno-laptop:~$ sudo hidd -s
Searching ...

```
...nothing else, and nothing tells me that the bluetooth is working.
Shame on me, I had to go back under Vista to make it work :cry:

Thank you in advance from a french user.

---

### Post by jordan420 on 2008-10-25
I Have a Vostro 1400, and my bluetooth isnt even detected in lsusb.. i do have config options for it in my bios though.. so im pretty sure i have one.. any suggestions?

---

