---
title: "quicken 2007"
date: 2006-09-10
forum: Desktop Environments
---

### Post by thomasbaker on 2006-09-10
has anyone got quicken 2007 to work on ubuntu either with wine or codeweavers.  I have used kymymoney and like it the best out of all the linux money programs. But I really love qiucken 2007. I would like to stop dual booting. This is the only thing stoping me.

thanks 
thomas

---

### Post by yeehawjared on 2006-09-21
have you got this working?  I want to run Q2k7 as well.

---

### Post by thomasbaker on 2006-09-24
no i have not. I have got quicken 2006 to work with codeweavers but 2007 will not.  so i am still booting back to windowsxp to use quicken 07.  I sent a letter to quicken about making a linux version, they make a mac version.  I love linux and use it about 90% of the time but still use windows for quicken and battlefield2.

---

### Post by hptasins on 2007-04-04
There has been some recent progress documented over on the codeweavers forums.  See:

[http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;tips=1](http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;tips=1)

[http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;forum=1;msg=5622](http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;forum=1;msg=5622)

Using those fixes, I now have Quicken 2007 running on Ubuntu 6.10 reasonably well.

---

### Post by scohar70 on 2007-06-04
I see from the CodeWeavers support site that Quicken 2007 supposedly works in Feisty now.  I am going to try it tonight.

[http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;tips=1](http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;tips=1)

(See the tip at the very bottom of the page.)

---

### Post by scohar70 on 2007-06-04
Quicken 2007 is working in Feisty 7.04 using Crossover Office 6.1.0!  :p

I meticulously performed the last two Tips on the [CodeWeavers site]("http://www.codeweavers.com/compatibility/browse/name/?app_id=2634;tips=1"):

[LIST]
[*]Combined workaround for Fonts & One Step Update issues
[*]Ubuntu 7.04 Workaround[/LIST]

The good news is that Quicken 2007 seems to work, but the bad news is that there are three things I notice are still wrong/not optimal:

[LIST]
[*]Graphics (esp. graphs) paint really S-L-O-W-L-Y.   #-o
[*]I can't get it to register my copy, and hence, One Step Updates don't work yet.  :-(
[*]There appear to be missing fonts/text in the tabs and dialog buttons. :???: [/LIST]

I'll keep playing with it and post here if I learn anything more.

---

### Post by scohar70 on 2007-06-05
I got the fonts working in Quicken 2007.  I still have the registry line that says, "Tahoma"="Times New Roman", but I also did the following, which made the fonts start working in the pop-up buttons and dialogs:

```
sudo apt-get install msttcorefonts
```

Now, I just need to get online banking working, and I am done.

---

### Post by Peter Ker on 2007-06-07
I need Quicken in Ubuntu.

Loaded ies4linux, I think properly
than I loaded Quicken, I think properly.
Both IE and Quicken is on my desktop.

However when I start running I get the following screens:
 Activate Quicken , I key in the activation code. nd click on OK.
Quicken online service: tell quicken how to connect to the net/ Quicken can detect most info.
I click on continue.
 Next screen is back to desktop.

Anyone has any suggestions?

---

### Post by krevuru on 2008-05-11
All,
I finally got Quicken 2007 working on my UBUNTU HARDY.
It works perfectly with all the One-Step Updates.
Over the next day, I will put out all the steps I took to get it working.
Thanks,
Krishna

---

### Post by thomasbaker on 2008-05-11
I'm using quicken 2006 with codeweavers 6.2 and it works perfectly.  Hopefully I can get 2007 or even 2008 preferably.  I have heard that crossover office 7 is gonna support quicken 2008.  I'm crossing my fingers!

Thanks

Thomas 

Post what you did to get 2007 working.

thanks again

---

### Post by krevuru on 2008-05-15
[FONT="Verdana"]I followed the below steps and I got Quicken 2007 working in UBUNTU Hardy Heron. 
Couple of steps that I did were purely out of a common-man's understanding and may not actually bear any rationale.

**Pre-UBUNTU Installation Steps**
[LIST]
[*]If moving from a Windows PC, then perform a backup to a NAS Drive or another HD-Location accessible to the UBUNTU PC.
[*]I have not gotten a clean setup of Quicken file to work, but only restoration of a backed-up version.
[/LIST]
**Pre-Quicken Installation**
[LIST]
[*]I followed the steps listed at [http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html) to install the Microsoft True Type Fonts, including the Tahoma and anti-aliasing part.
[*]I followed the steps listed at [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation) to install Microsoft Internet Explorer 6.
[*]I **DID NOT** make the changes mentioned in the Code-Weavers Quicken 2007 &#8220;Tips and Tricks&#8221; to add the line:
&#8220;Tahoma&#8221; = &#8220;Times New Roman&#8221;
[*]When installing IEs4Linux, I gave the base location for installs as /home/[*yourusername*]/.wine/drive_c/Program Files/Internet Explorer.
[*] Open directory /usr/share/fonts/truetype.
Move the entire arphic directory to /home/[yourusername]/temp
[/LIST]
**Quicken Installation**
[LIST]
[*]Open WINE-Config and add &#8220;rsaenh"="native, builtin&#8221;
[*]Install Quicken 2007 using wine.
[*]Copy gdiplus.dll from the Quicken Installation-CD to ~/wine/drive_c/windows/system32
[*]Open Quicken 2007, **BUT DO NOT **select from the Options: New User / Existing User.
[*]Instead close the Pop-up from the top-corner.
[*]From the File menu, do a restore from back-up of your backed-up Quicken File.
[*]All the One-Step Update should work exactly as before.
[/LIST]
My personal observation has been that it works perfectly when doing a restore from backup. And doing a fresh Quicken does not actually work within WINE.

[/FONT]

---

### Post by bebasakan on 2008-05-26
I followed the above post (excellent instructions - thanks!) and got Quicken 2008 H&B working on Ubuntu Studio Hardy.  I omitted a few steps but did the following:

Backup quicken data file

Pre-Quicken
Installed ms true type fonts but not Tahoma nor the anti-aliasing part
Installed ies4linux to .wine/drive_c
Did not copy the true type fonts

Wine
Open WINE-Config and add “rsaenh"="native, builtin”
# Install Quicken 2007 using wine
# Copy gdiplus.dll from the Quicken Installation-CD to ~/wine/drive_c/windows/system32

Launched Quicken and opened the existing quicken data file.

It insisted on re-registering so I did this trick (compliments of quicken support) Shift-Control-click on the One-Step update button.  If you did it right you'll see a message box saying something like "Quicken will no longer prompt you to register".

Did some basic testing last night and app seems to work, online updates worked.  Screen flickers and paints slowly but it's usable.

---

### Post by krevuru on 2008-05-27
Thanks for the tip to fix the Registration annoyance.

---

