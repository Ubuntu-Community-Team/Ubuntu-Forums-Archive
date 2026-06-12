---
title: "Gnome panels not behaving properly"
date: 2010-05-20
forum: Desktop Environments
---

### Post by MrStill on 2010-05-20
I am having an issue with the notification Area, Indicator Applet, and Indicator Applet Session and the way they appear in the top gnome panel. The icons are scrambled at log in and I have to delete them and replace them to get things looking right. I didn't have this issue in Karmic; it has only occurred since upgrade to lucid. I have reset my gnome config files and the problem still occurs.

As a side note, the issue only seems to occur when the icons in the notification area or session indicator are abnormal. ie, sound is muted, lap top is unplugged, and so forth.

---

### Post by quadrantids on 2010-05-22
> **MrStill said:**
> I am having an issue with the notification Area, Indicator Applet, and Indicator Applet Session and the way they appear in the top gnome panel. The icons are scrambled at log in and I have to delete them and replace them to get things looking right. I didn't have this issue in Karmic; it has only occurred since upgrade to lucid. I have reset my gnome config files and the problem still occurs.

As a side note, the issue only seems to occur when the icons in the notification area or session indicator are abnormal. ie, sound is muted, lap top is unplugged, and so forth.

I have this problem with 10.04 too and I used to have it in Karmic at the beginning. It seems to be a long-standing problem (several years: I've seen somewhere it's said to be a display problem associated with certain video cards. I have a DELL inspiron 1525 with an integrated INTEL card). The NetworkManager applet and the Indicator applet are the two that usually get scrambled. I noticed the problem seemed to get worse when I set up a second (French) keyboard through the keyboard preferences.

---

### Post by compres on 2010-05-22
I have the same problem.  I am running ATI binary drivers, wonder if it's related to that.  

Really annoying since time becomes unreadable and to reboot or shutdown have to issue a sudo console command.

---

### Post by BeRA on 2010-05-23
> **compres said:**
> I have the same problem.  I am running ATI binary drivers, wonder if it's related to that.  

Really annoying since time becomes unreadable and to reboot or shutdown have to issue a sudo console command.

Same problem here (except that I have problem only with Indicator Applet Session)... I have ATI x1300 mobile (default-binary drivers)... and Karmic was always OK for me- so problems started with Lucid...

And the only way I can fix things (besides restarting Indicator Applet Session) is to increase panel size by at least 4 pixels (after everything returns back to normal I can decrease my panel size back to normal 24 pixels)... and same procedure every time it fails again (and it fails 1-2 times per day... :confused:

---

### Post by BeRA on 2010-05-23
Just saw this thread:

[http://ubuntuforums.org/showthread.php?t=1486694]("http://ubuntuforums.org/showthread.php?t=1486694")  

...so... I left some space between applets... I'll inform you if is changes anything...

---

### Post by BeRA on 2010-05-24
I'm back with results:

Today was my first day (since 29.04.) without any problem... so 1-2 pixels (you could try with more if needed) of free space between applets (and between Indicator Applet Session and top right corner) fixed all my problems...  :cool:

---

### Post by quadrantids on 2010-06-01
I've tried increasing the spacing between the applets but this hasn't worked for me... It's a pity because when you fire up Ubunntu this is the panels are the first thing one sees and it gives a bad impression before one even starts working with the system.

---

### Post by xpluto on 2010-06-01
> **quadrantids said:**
> I have this problem with 10.04 too and I used to have it in Karmic at the beginning. It seems to be a long-standing problem (several years: I've seen somewhere it's said to be a display problem associated with certain video cards. I have a DELL inspiron 1525 with an integrated INTEL card). The NetworkManager applet and the Indicator applet are the two that usually get scrambled. I noticed the problem seemed to get worse when I set up a second (French) keyboard through the keyboard preferences.
same problem here  i removed second keyboard that i can click on network manager!!?
and the place of items is changing after each reboot

look this post [http://ubuntuforums.org/showthread.php?t=1497137](http://ubuntuforums.org/showthread.php?t=1497137)

---

### Post by xpluto on 2010-06-02
any idea's?

---

