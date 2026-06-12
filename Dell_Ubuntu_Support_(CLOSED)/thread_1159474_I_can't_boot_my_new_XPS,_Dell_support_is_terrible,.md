---
title: "I can't boot my new XPS, Dell support is terrible, please help"
date: 2009-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by captainron042 on 2009-05-14
I just got the Dell XPS in the mail two days ago. That day it ran fine as far as I could tell. I didn't use it for much though. Later on, I had an updates notification. The update manager was acting kind of funny and would sometimes just exit. The updates would download, but would not install, saying that something needed to be done manually. The most I can remember of that was config --a

So I shut down the computer, and from then on, I get an error messege that says "Kernel panic not syncing attempted to kill init". This is as far as it gets, it does not load to the desktop.

So, I call Dell, who instead of Canonical, is handling their own Ubuntu support. They have me run the diagnostics test of the memory and hard drive, ect, and everything passes. We tried to startup in the different versions and in recovery modes, but nothing.

The next morning, I turned on the computer, and surprisingly, I the machine seemed to be running fine. I opened Amarok and played a song, but then the computer shut down and I was in kernel panic hell again. This was the only instance where I got to the desktop since I had this problem.

I called Dell again and tried to get more help. We put in the Ubuntu disk to re-install the software, but the status bar either freezes, or I get the same kernel panic error messege. sometimes, I get a bunch of text that pauses on "segmentation fault", but then goes on for more text until it says "Fixing recursive fault but reboot is needed!"

I have also tried to install from a thumb drive, but that did not work, either.

please help.

---

### Post by coffeeaddict22 on 2009-05-14
Hi,
What is the system doing at present?  Can you consistently boot into a desktop?  Can you get into a recovery console?  
If you can't, does it do the same thing every time now or does it seem to have a new mood for every boot?  
Does it feel hot when its been running for a bit (Power supply/ fan could be your problem, especially if it's hard to pin down...)
If you can get into a console, what's the output of ```
dmesg
```

---

### Post by captainron042 on 2009-05-15
Everytime I booted, I was getting one of three different errors, as explained above. The computer is not hot or overly warm. I was able to get to the desktop just once, and the recovery mode reacts the same.

I tried the DVD I made from the dell reinstall image, and it finally worked even though I didn't do anything differently. It asked me to type erase if I really wanted to format the HDD and install Ubuntu. I did and it is now at an Ubuntu splash screen with the orange bar moving side to side. It says this should take 15 to 60 minutes, but that was just over an hour ago. I will continue to let it run, I guess.

---

### Post by captainron042 on 2009-05-15
The computer did not complete the task after about 5 hours, so I shut it down. 
Dell is asking if I have an XP disk so that I can format the HDD, but I do not have one.
Can anyone help me to format the HDD without an XP disk and without me getting to the desktop (since I can't)? 
Thanks in advance.

---

### Post by Z0014ND3l2 on 2009-05-15
This will take a few hours on the phone with Dell Support:

I also have a Dell as well and Dell Support only follows a flow chart scenario. The best thing to do is call Dell Support. Tell them this is your 5th, 6th, whatever time calling about your problem and obviously the HDD (Hard Disk Drive) is broken if it won&#8217;t even format. Tell them you want to speak to their boss. They will send you a new HDD, and if they don&#8217;t you need to speak to their Boss. Eventually you will get to the right person and what they will do is send it and you have like 15 days to send them the messed up one or they make you pay for the new HDD. 

They tried this with me when my DVD Drive was broke and I had the XPS for a week. Took me 3 weeks to finally get to the right person (Constant Disconnects with DSN Phones in Iraq) and get a new drive and guess what.... it worked perfectly after I swapped the DVD Drives. 

But yeah, tell them your HDD is Bad and you want a new one. And don't settle to talk to some lackey, go straight to the top of their chain. 

Good luck and hopefully that will be the only problem with your computer.

---

### Post by captainron042 on 2009-05-15
Thanks for the advice. I have a dell desktop that I got a year and a half ago with ubuntu. It works great. I wih they'd stayed with contracting their support to Canonical, but it's kinda cool that they decided to do their own support. They just need to learn some more about it.

The last guy I talked to today said that he is going to take on the problem personally, and research it. He tried to get them to send another HDD, but said that the XPS dept. wouldn't make approve the service request. He said he's going to research the problem some more and get back to me tomorrow. 

We did the test on the memory and HDD, but it passed all tests.

---

### Post by captainron042 on 2009-05-15
Occasionally, instead of an error, I get BusyBox v1.1.3 Built in shell.

(initramfs) 

is there a command I can enter here to either format the HDD or fix my problem?

---

