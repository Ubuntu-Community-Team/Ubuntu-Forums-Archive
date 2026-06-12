---
title: "Various Newbie Questions"
date: 2007-07-05
forum: Dell  Ubuntu Support
---

### Post by andy675 on 2007-07-05
HI...I am very new to Ubuntu and absolutely love the concept. I have a Dell Dimension 5150 Desktop with Dell KM5150 Bluetooth Wireless Keyboard & Mouse, & Dell 810 All In One Printer. At this stage, I have installed Ubuntu(via Wubi) and have set up Evolution as my email client. I have never run a command line option in my life, and would greatly appreciate simple, step by step instructions for the following problems-(I have searched the forums over 9 days without success, or I simply could not understand the solutions-sorry)-

1.My Bluetooth Mouse & Keyboard are unable to connect. I have to use my older Dell USB Mouse/Keyboard. Is there (praying) a sinmple way to get these automatically detected.

2. I cannot seem to connect my Printer. After following what I thought was the correct process (via forum), it picked up that my Dell 810 Printer was connected via USB Port(which it is), but then the next installation page said 2 drivers- MD... & KS...from memory were applicable. I tried installing both of these withoput success.

I know i sound VERY NEW (which I am), but please advise any solutions .....I am hoping.

Many Thanks:D

---

### Post by Arrdee on 2007-07-05
For the bluetooth mouse and keyboard: [http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057) 

Should do the trick.

---

### Post by andy675 on 2007-07-06
Thanks for that reply..... I will try this and let you know.

Could someone please advise help in relation to the Dell 810 Printer...


Thanks

---

### Post by PurplePenguin on 2007-07-06
It doesn't look good... According to the [OpenPrinting.org database]("http://openprinting.org/show_printer.cgi?recnum=Dell-Photo_AIO_Printer_810"):

> 
As noted for the Dell AIO 944, none of the Dell/Lexmark Multifunction/All-In-One printers will work under Linux due to them being Host-based printers (offloading processing to the OS, much like Winmodems), which make them cheaper by not requiring a powerful processor in the printer. Along with their use of proprietary print data streams, that makes them difficult to support without official drivers, which are Windows-only. 

Thankfully, though, for $50 you can get a printer that will work.  Maybe you could give your Dell 810 away as a birthday gift to some Windows user. :D

---

### Post by el_poderoso on 2007-07-06
I use an HP deskjet 940c and it works well. Without using a command line, the safest bet is to find a cheap and common printer to use "plug and play" until you find drivers (if ye search and know thy command lines such as tar, alien, etc, worlds will eventually open up to you.

If you must have all-in-one, Epson products are supported through this site

[http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm)

However, you will find that most of the the driver files will be .RPM or .tar, which means you must use the terminal. I downloaded the RPM files and then installed alien through the Synaptic Package manager. Alien will reformat RPM files to .DEB files for Ubuntu and install the file in one short command line.

The command line is (this is from memory, don't test me) $ alien -d -i [name of file.RPM] This will convert the RPM to DEB and do the install in one command. Cool. -d = debian -i = install

But let's hold your hand through the first few commands. (experienced users don't giggle) To get started, open your terminal and type. 

sudo apt-get install alien 
(sudo = superuser do. Use it when you have to do "superuser stuff" like installing programs)

sudo apt-get install mozilla-thunderbird (better than Evolution for email only, IMHO)

When you feel a little more ambitious, go to Adobe.com and try to download and install the Adobe Acrobat reader. As these things go, Adobe makes it pretty easy with step by step instructions.

This should give you a taste of the terminal.  Once you figure out that programs can be downloaded, configured and install in a few minutes with one line of text, you'll be hooked. Windows will piss you off filling out endless forms on 10 screens, press next, enter a 25 digit passkey you can never find...ugh. Gimme my Linux please

sudo apt-get install getonwithlifealready

---

### Post by andy675 on 2007-07-07
Thanks for all the replies.:

---

### Post by andy675 on 2007-07-07
I am still trying to get my Bluetooth Keyboard & mouse working with some success, but have to keep trying. All part of the learning curb, I guess. I am able to get them working in Ubuntu, but not to work at boot up. 

It does appear that the Dell 810 Printers do not work on Linux at all. It will not do any good, but I have emailed Dell Support, asking for any suggestions. I find it a bit strange that Dell now issue Linux on some new systems but that are unable to provide a relevant Driver for my problem. I will advise their reply.....I am sure it will be negative.....but oh well.

---

### Post by hgebbia1 on 2007-07-07
> **andy675 said:**
> I am still trying to get my Bluetooth Keyboard & mouse working with some success, but have to keep trying. All part of the learning curb, I guess. I am able to get them working in Ubuntu, but not to work at boot up. 

It does appear that the Dell 810 Printers do not work on Linux at all. It will not do any good, but I have emailed Dell Support, asking for any suggestions. I find it a bit strange that Dell now issue Linux on some new systems but that are unable to provide a relevant Driver for my problem. I will advise their reply.....I am sure it will be negative.....but oh well.

I got the direct # to dell Ubuntu support and the guy told me,   "  Just get 7.04 and install on your 1505 and your good to go ".    NOT!

---

