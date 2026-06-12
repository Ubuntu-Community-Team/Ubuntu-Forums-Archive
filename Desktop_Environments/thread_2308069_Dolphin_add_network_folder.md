---
title: "Dolphin add network folder"
date: 2015-12-30
forum: Desktop Environments
---

### Post by peterroots2 on 2015-12-30
I have just recently installed Kubuntu 15.10 (using kde mint 17 previously)
Today I tried to add a network folder (for the first time on this install) for an ftp site by clicking on the Add Network Folder icon in the remote:/ folder - rather than bring up the dialogue I am used to seeing in Mint and older versions of Kubuntu it opens in Kate. Searching the net I found one other user with the same issue but opening in LibreOffice. File associations show that x-desktop is associated with Kate, LibreOffice Writer, Okular, Calibre and e-book viewer - for file patterns *.desktop and *.kdelnk
These are either the default settings for my new system or something I have installed has set these associations as I have not manually been into the settings before now.
How do I get back the expected behaviour?
Thanks

---

### Post by SeijiSensei on 2015-12-31
Are you using Dolphin for this task?  Try going into the address bar and typing the URL [ftp://server/share/](ftp://server/share/).  You should be prompted for the username and password.  If that works, you can drag the share folder into the left-hand navigation panel.

---

### Post by peterroots2 on 2016-01-01
Thanks for your reply but no quite what I was asking
Yes using Dolphin
and yes I can open an ftp site by entering the URL in the address bar
My question was why the add network folder icon provided in dolphin no longer works, but opens in Kate, and how do I restore the functionality

---

### Post by SeijiSensei on 2016-01-02
I can't help with that because I never use such features in Dolphin.  I find it a lot quicker to type URLs into the address bar than a lot of pointing and clicking.  In fact, I don't even see an "add network folder" icon in my copy of Dolphin on 14.04.

---

### Post by peterroots2 on 2016-01-03
Ah, it is a more general problem than I first thought - Dolphin opens any .desktop file in Kate rather than running the program it is linked to such as Abiword:abiword.desktop I would expect to open AbiWord (and does on other KDE installations) rather than open itself in Kate. Comparing settings in both Dolphin and file associations on my current Kubuntu 15.10 and my old machine running Mint17 I can see no obvious differences.

---

### Post by SeijiSensei on 2016-01-03
See if you can change the settings from System Settings > File Associations.

I've stuck with KDE 4 on 14.04 because the implementation of KDE 5 in Kubuntu 15.x was too buggy.  Maybe this is another example?  I plan to give it another try when 16.04 comes out later this year.

---

### Post by peterroots2 on 2016-01-03
> **SeijiSensei said:**
> See if you can change the settings from System Settings > File Associations.
Any idea to what? As I said I can't see any difference between my current settings and those in a working Mint17 set up

---

### Post by SeijiSensei on 2016-01-04
Kate is the default for .desktop files in 14.04 as well followed by LibreOffice Writer, Okular (?), and Abiword.  What do you see when you look at the corresponding File Associations in Mint17?

---

### Post by peterroots2 on 2016-01-04
see post #5 - they are exactly the same in Mint 17 and Kubuntu 15.10<br>Apparently there is a pop up on clicking on something executable like a .desktop file - I never saw this, and have only just found out about it - possibly because my touch pad is a bit over sensitive and so I may have inadvertently accepted a default suggestion. This determines whether Dolphin runs executables like .desktop or opens them. The default action is to open them. so now problem is to find out where this setting is stored and change it.<br>At least I now know what the problem is, so far several possible config files related to Dolphin have not provided an answer.<br>More searching tonight to see if I can find out where this setting lives.<br><br>Thanks for taking the time to help

---

