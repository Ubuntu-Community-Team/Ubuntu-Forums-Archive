---
title: "Ubuntu start-up, Blank Screen, Laptop - Dell Inspiron 6000 (Intel Graphics)"
date: 2007-07-13
forum: Dell  Ubuntu Support
---

### Post by hc_haven on 2007-07-13
[FONT="Arial"][SIZE="3"]Specs:

Dell Inspiron 6000 Laptop, Intel Celeron M Processor @ 1.5 GHz
512 MB RAM (400 MHz)
Integrated Intel Media - Accelerator 9000 Graphics for Inspiron 6000 UMA
60 GB Ultra ATA Hard drive
8 X DVD+/-RW Drive
Integrated 10/100 Network Card & Modem
Intel PRO/ Wireless 2200 Internal[/SIZE][/FONT]

[FONT="Book Antiqua"][SIZE="4"][B]I installed Ubuntu Ver. 5.04 for Intel x86 on my laptop and everything went smoothly.  Nearing the end it gave me the prompt that it will restart and them configure the rest of my setting and I will be ready to use Ubuntu.  No errors or conflicts were shown during this process.  When it restarted and loaded the screen was BLANK were I should be prompted for my user name and password.  I could hear the 'drum' sounds as that happened.  I then (with the BLANK screen) typed my selected username and password and then heard the startup/ introduction sound.  I thought that my visuals will maybe return here BUT dit not!  How, where and what should I configure to get my BLANK screen to a pretty, visual inviroment?

Any help will be appreciated.

P.S.  I actually wanted to keep my Windows XP too, but thought that I should get Ubuntu running first and then experiment running different operating systems together.  Is there a specific format Linux/Ubuntu needs to run efficiently?  [/B][/SIZE][/FONT]

---

### Post by NilsE on 2007-07-13
I assume you mean version 7.04... not 5.04 correct

When you get logged in blindly hit ctrl-alt-f2 which should bring you to the shell.  Log in if it asks you to then run:

sudo dpkg-reconfigure -phigh xserver-xorg

When prompted pick the i810 driver and the resolutions your display supports.  Reboot and see what happens.  If that did not work try again and pick vesa and reboot.

---

### Post by hc_haven on 2007-07-13
The CD I have says Version 5.04 for Intel x86 on it.   I should probably try to get hold of the latest version.

I tried configuring my settings by typing:

***sudo dpkg-reconfigure -phigh xserver-xorg***

and tried variations of that line, BUT it keeps on prompting:

[B][I]sudo: unable to lookup ubuntu via gethostbyname()
Password:postdrop: warning: unable to look up public/pickup: No such file or directory[/I][/B]

I am not familiar with ubuntu's command keys at all.  Please advise if I should type something else first...

---

### Post by NilsE on 2007-07-13
It looks like sudo is having a hard time finding you, or anyone for that matter,  in the user file. If sudo was working you would have gotten a prompt to enter your password.  

I would however abandon all other attempts and download the 7.04 iso file and burn the cd and reinstall from that.  It may just automatically fix all your problems since there is better support for most of the Dell stuff in it.

---

