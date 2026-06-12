---
title: "Lost control of Gnome application font"
date: 2005-06-09
forum: Desktop Environments
---

### Post by RyaninZion on 2005-06-09
I installed Kubuntu-desktop over my Ubuntu to test out KDE.  I also installed gtk2-engines-gtk-qt so that my gtk applications would look decent in KDE.

After some time in Kubuntu, I decided GNOME is for me, at least for now.  So, I got back in GNOME and removed all the Kubuntu/KDE parts.  

BUT - for some reason the "Application Font" in Gnome remained the default for KDE.  Meaning the font used in my Gnome panel and all gtk applications is still Helvetica, or Bitstream vera sans, or whatever KDE used.  And its at a larger size than I would want.

I am unable to change the application font in System>Preferences>Fonts.  It doesn't matter what I change application font to, it remains as it is.

Any idea why I have lost control over this?

---

### Post by desdinova on 2005-06-09
[QUOTE=RyaninZion]I installed Kubuntu-desktop over my Ubuntu to test out KDE.  I also installed gtk2-engines-gtk-qt so that my gtk applications would look decent in KDE.

After some time in Kubuntu, I decided GNOME is for me, at least for now.  So, I got back in GNOME and removed all the Kubuntu/KDE parts.  

BUT - for some reason the "Application Font" in Gnome remained the default for KDE.  Meaning the font used in my Gnome panel and all gtk applications is still Helvetica, or Bitstream vera sans, or whatever KDE used.  And its at a larger size than I would want.

I am unable to change the application font in System>Preferences>Fonts.  It doesn't matter what I change application font to, it remains as it is.

Any idea why I have lost control over this?[/QUOTE]
 look for files .gtkrc, .gtkrc-2.0 or named equivalently in your home directory

---

### Post by RyaninZion on 2005-06-09
OK, I found .gtkrc-2.0.  Should I delete it?

---

### Post by RyaninZion on 2005-06-09
Nevermind... I got impatient and deleted it.  Worked like a charm, and all is as it should be again.

Thanks a ton.

---

### Post by RyaninZion on 2005-06-12
I think I spoke a little bit too soon.  This solution did fix the fonts for almost everything, but a few programs are still displaying very large fonts.

The two main offenders are Firestarter (even the tooltip when I put the mouse over Firestarter's tray icon is huge) and the Ubuntu Update Manager.

Any idea why these two programs continue to use a style and size of font different from that I have chosen for my system?

---

### Post by RyaninZion on 2005-06-13
Any suggestions?  I know there must just be some KDE config files floating about that are conflicting with their GNOME equivalents.  

On top of the minor font issue that remains, I am also having strange problems with Evolution following my test of Kubuntu.  

For some reason whenever I mark new mail as spam or otherwise delete it, those messages completely disappear.  They are not placed in the Spam or Trash folders, but are just gone.

---

### Post by desdinova on 2005-06-13
[QUOTE=RyaninZion]Any suggestions? I know there must just be some KDE config files floating about that are conflicting with their GNOME equivalents. 

On top of the minor font issue that remains, I am also having strange problems with Evolution following my test of Kubuntu.  

For some reason whenever I mark new mail as spam or otherwise delete it, those messages completely disappear. They are not placed in the Spam or Trash folders, but are just gone.[/QUOTE]

IIRC theres a gtkrc in $HOME/.kde/share/config you may need to get rid of as well

---

### Post by shakin on 2005-06-13
[QUOTE=desdinova]IIRC theres a gtkrc in $HOME/.kde/share/config you may need to get rid of as well[/QUOTE]

May as well dump the whole .kde directory, no?

---

### Post by desdinova on 2005-06-13
[QUOTE=shakin]May as well dump the whole .kde directory, no?[/QUOTE]
 Depends - are you dumping kde?

---

### Post by desdinova on 2005-06-13
Also try running the offending app in a console by

strace appname

and look in the output for what gtkrc file's its looking for

---

### Post by RyaninZion on 2005-06-13
OK, I have dumped the entire .kde directory.  Didn't help.

I tried running the offending apps (Firestarter and Synaptic) via console.  Firestarter spits out, and continues spitting out, an enormous amount of data, I guess cause its actively monitoring.  What I did notice, however, was that the instance of Firestarter started by the console did NOT have the font problem.

Same with Synaptic.  The amount of data is spits out using strace is far too much to go through (is there a find feature in the GNOME Terminal?).  But the instance of Synaptic started by the console again does NOT have teh font problem.

Also, any suggestions on my Evolution problems?  I am really stumped on that one.  None of my trash or spam gets put in the appropriate folders, but just disappears completely.

---

### Post by RyaninZion on 2005-06-13
Never mind on the Evolution problem.  Turns out I was just an idiot.  I had used the search feature in both the spam and trash folders, and had failed to clear the search field.  So it was showing me only the search results, which were 0.

---

### Post by DLF on 2005-06-13
I have the same issue with Thunderbird and Synaptic package manager.  Strace reveals "(Gecko:18405): Pango-WARNING **: Cannot open font file for font Tahoma 8".   Changing the font to Bitstream Vera solves the problem (unless I want Tahoma of course.

---

### Post by RyaninZion on 2005-06-13
[QUOTE=DLF]I have the same issue with Thunderbird and Synaptic package manager.  Strace reveals "(Gecko:18405): Pango-WARNING **: Cannot open font file for font Tahoma 8".   Changing the font to Bitstream Vera solves the problem (unless I want Tahoma of course.[/QUOTE]

Hmmm, I'm afraid the same is not working for me.  I am using Arial 8 by the way.  I tried changing to Bitstream Vera, but the application fonts in Synaptic and Firestarter just did not change at all.  They seem stuck with whatever font they are using.

---

### Post by desdinova on 2005-06-13
[QUOTE=RyaninZion]Hmmm, I'm afraid the same is not working for me.  I am using Arial 8 by the way.  I tried changing to Bitstream Vera, but the application fonts in Synaptic and Firestarter just did not change at all.  They seem stuck with whatever font they are using.[/QUOTE]
 Hang on - they're apps that run (naturally) as root

look for .gtkrc files in /root

---

### Post by DLF on 2005-06-13
[QUOTE=RyaninZion]Hmmm, I'm afraid the same is not working for me.  I am using Arial 8 by the way.  I tried changing to Bitstream Vera, but the application fonts in Synaptic and Firestarter just did not change at all.  They seem stuck with whatever font they are using.[/QUOTE]
Have you tried restarting them?  Some are more stupid than others, probably an indication of how integrated they are with gnome  :roll:.  In Ubuntu there is a package mozilla-firefox-gnome-support and no thunderbird equivalent so hmmm.  At the moment I am using OpenOffice and that isn't playing nicely with fonts at the moment either!

---

### Post by RyaninZion on 2005-06-14
[QUOTE=desdinova]Hang on - they're apps that run (naturally) as root

look for .gtkrc files in /root[/QUOTE]

That did the trick!  Thanks so much.

---

