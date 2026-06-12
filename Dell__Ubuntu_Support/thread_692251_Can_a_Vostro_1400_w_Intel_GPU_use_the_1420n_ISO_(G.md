---
title: "Can a Vostro 1400 w/ Intel GPU use the 1420n ISO (Gusty)"
date: 2008-02-09
forum: Dell  Ubuntu Support
---

### Post by ross82694 on 2008-02-09
I am a ***TOTAL*** novice to Linux.  At first I wanted to use Wubi...but I got a "Server X" failure...but now I want to do, maybe, a 20gb/Whatever is left partition (unless I can get some help with the Wubi) of Ubuntu and Windows.  Could I use the ISO on the Dell-Linux Wiki for my ISO when I install or will I have to do the regular install and do driver searching?

Thanks

Ross

---

### Post by RudolfMDLT on 2008-02-09
Hi Ross,

I recommend a dual boot install. But if you don't mind - please make sure that all your hardware is Linux Compatible.

Just to confirm,

[http://www.dell.com/content/products/productdetails.aspx/vostronb_1400?c=us&cs=04&l=en&s=bsd](http://www.dell.com/content/products/productdetails.aspx/vostronb_1400?c=us&cs=04&l=en&s=bsd)

You have a couple of options on that laptop. EXACTLY what graphics card and Wifi card do you have in your system?

If you give me that info I may be able to give you some "no bull" advice on whether or not you might have some hardware headaches! :)

Please post detailed errors and information. the more you tell us, the easier we may be able to help.

Thanks,

Rudolf

---

### Post by ross82694 on 2008-02-09
I have the 1.6 Ghz C2D, the *ugh* Dell 1390 Wireless, 1 Gb RAM, and i think 80Gb HDD, CD R/W-DVD-R

---

### Post by RudolfMDLT on 2008-02-09
And what graphics card? If you are not sure where to check. Boot into windows and rightclick on My Computer, click "manage". In the left hand pane, select "device manager". now under display adapter you should be able to read off the name of the graphics card.

Anyway - It seems that your wireless adapter is going to cause trouble! The driver does not seem stable yet - though people have had some success. :) my best advice would be dual boot install and then tackle any problems patiently, one by one.

---

### Post by ross82694 on 2008-02-09
Whoops, sorry.  Its the Intel X3100.  Back to the Wubi.  Is there any advice on why i get the server x crash?

---

### Post by RudolfMDLT on 2008-02-09
:( The intel card isn't going to be a smashing succes either! Sorry!

Here is my advice:

Get rid of Wubi, take some time and read the advice on this website:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Now do a dual boot install and learn how to use linux the right way - Wubi doesn't do it justice.

Non of your hardware is completely irrevocably incompatible. All I'm saying is that it is going to take some time from your part to get it sorted and working. Everybody has been able to get their wireless working, it's just that it's not 100%. Usually Ubuntu installs ALL hardware and you never have to worry about a thing.

The most important advice that I can give you is to give more info in your posts. Tell us exactly what you did, exactly what the computer tells you and then lastly, where you want to end up.

In either case - start a new thread on whatever you choose. Choose a detailed title, for example - "Wubi boot error - Xserver".

Best of luck and post back if you have any questions.

Cheers,

Rudolf

---

### Post by ross82694 on 2008-02-09
I'm having the same problems as this guy:
[http://ubuntuforums.org/showthread.php?t=641684]("http://ubuntuforums.org/showthread.php?t=641684")

I tried what was recomended (Ctl-Alt-F1 then codes, but nothing)

Any ideas.

P.S.-
If I do the partition, can I delete it if it becomes too much and still maintain my Windows partition?

---

### Post by RudolfMDLT on 2008-02-09
When booting up, in the boot menu list, there should be an option for booting Ubuntu in Recovery mode?

Boot into recovery mode. enter the root password - the one you used to install wubi.

now enter this command:

> sudo dpkg-reconfigure xserver-xorg 

Follow the steps in the setup. Look for the Intel driver. Use [TAB] to jumparound in the menu and [SPACEBAR] to check and select things. When selecting a resolution, for now, lets keep the max at 1024x768.

when setup is done, issue the following command

> shutdown -r now

This should work. If it doesn't - Start a new thread dedicated to solving the Xorg issue. The problem is that Xorg(the thing that controls what you see in Ubuntu) can't load as it's not talking to your intel card. I am not too experienced with intel graphics cards and this thread's title does not match this problem so the right people won't be able to help. :) 

PS: I'm off to bed, it's 1 in the morning this side of the world :) post back and I'll see where i can help in about 6 or 7 hours! ;)

---

### Post by fragos on 2008-02-09
Speaking as someone that has a 1420n with the Intel X3100 video card, it works well and does 3D rendering.  Frames per second with glxgears was over 1,100fps.  Compiz blacklists this video because although it works in normal use it won't do "video output".  I haven't bothered to try the workaround to ignore the blacklist so I can't accurately comment on what I haven't used.  I run Compiz on my desktop.  If you aren't all excited about 4 screen images on a spinning cube you won't really miss it that much.  This is particularly true with the smaller screen of a laptop.  Don't forget that all that eye candy video processing uses battery power.

---

### Post by neptho on 2008-02-10
I used the 1420 Intel Video DVD ISO to install Ubuntu on my 1400 when I put a new hard disk in it.  It worked relatively well.

---

### Post by ross82694 on 2008-02-10
Did you have any issues with the wireless and sound?

I'm using the Live CD right now, and I love Ubuntu.  Using it first hand, it's amazing...my computer was fast before, but WOW.  I'm also tempted to try Ubuntu Studio.  It looks amazing, and the software is great.  

I'm thinking about getting another HDD and installing Ubuntu on it, and just switching.

Also, bad place to ask, but are there any software that would allow me to use my zune in ubuntu?

---

