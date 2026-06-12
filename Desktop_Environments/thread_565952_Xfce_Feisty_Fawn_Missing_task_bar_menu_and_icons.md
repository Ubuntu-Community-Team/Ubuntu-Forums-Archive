---
title: "Xfce Feisty Fawn Missing task bar menu and icons"
date: 2007-10-02
forum: Desktop Environments
---

### Post by Jerinaw on 2007-10-02
This has happened two times already, and I've done some searching and haven't found a solution. (Probably should mention I'm a noob)

I just installed XUbuntu Feisty Fawn. Updated it. Added a few icons to the task bar, install a few apps (wine, samba and some others). 

The short version is the Application menu (and after lossing the application menu i added the Xfce Menu which was lost) went missing after i logged back in from the screen saver. Actually i logged back in and the task bar and quick launch bar were blank. All my windows were missing. Only the desktop and the icons on the desktop were there. I restarted my pc and when my desktop came back up the Application menu was missing and an icon i had added to the task bar. As well as a note i had on my desktop. It was one of those postIt programs i can't remember the name.

Long version:

The first time this happened i really didn't pay to much attention (probably because i'm a windows user and just so used to restarting my pc). After leaving my computer for work, or most of the day i came back, powered on my monitor and moved the mouse around to bring up the login screen to get past the screen saver.  I can't remember how long i had to wait the first time the application menu went missing but the second time this happened it took forever for the login screen to show up. And my hard drive like was flashing like crazy. After i guess 5mins i was able to login but the desktop was taking forever to load (after logging back in from the screensaver).  I ended up getting tired of waiting and went back to work. I came back after work expecting the screensaver to have come back and for it to take forever to log back in. But it didn't it popped up and i logged in. But once i was logged back in the Xfce Menu was missing again! (The first time it was called Applications) I also noticed that firefox had closed, and again the Notes window was closed. Also after this happened the first time i set my right click to be the applicaitons menu. Right click no longer worked. Oh and the first time this happened everything was blank. The task bar and quick launch bar were both just gray all windows were closed/missing . there were only icons on my desktop.  Anyway both times i restarted the computer and once i was logged in the Application/Xfce Menu were missing. 

Does anyone have a solution to this problem? I'm sorry if this post was a long read i wanted to make sure i gave as much detail as possible.

---

### Post by davidshere on 2007-10-02
Generally this type of thing seems to happen when Nautilus crashes, or has trouble running.  Nautilus is roughly the Linux equivalent of "explorer".  It also seems like you're low on memory.  How much memory do you have?

---

### Post by Gremlinzzz on 2007-10-02
I am using xubuntu for about a week with no problems its great. the thing i did that most likely you didn't was upgrade the kernel to 2.6.22-12-generic. if you reinstall xubuntu try it.
do the upgrade on a clean install working for me.
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by santiagoward2000 on 2007-10-02
Too bad I hadn't seen this post before you reinstalled everything. Normally, running xfce4-panel should open the panels.
> **davidshere said:**
> Generally this type of thing seems to happen when Nautilus crashes, or has trouble running.  Nautilus is roughly the Linux equivalent of "explorer".  It also seems like you're low on memory.  How much memory do you have?

Actually, Xubuntu uses Thunar, not Nautilus. But you are right about the problem.

---

### Post by Enedok on 2007-10-03
Heh, having a old computer I'm  trying to get up. Got xubuntu running into live cd (Took some time, old computer with new ram and nivida card) and I'm missing the two bars. Wierd, but i could do the install from the desktop icon so i did. Hoping that it would be ok after the install. Nope. At the bootup its taunting me with a blue flickring where it should be and then its gone.

xfce4-panel don't work. I dont remember the error message now. Im going to try an update tomorrow and see if that fix the problem.

---

### Post by avantgardaclue on 2007-10-05
Similar happened to me too this morning. I am currently evaluating the various ubuntu desktops and was sort've settling on xubuntu for when release 7.10 came out. It went like a rocket on my 6yr old 256 m ram 1.7 mh dell machine. Then huge disappointment, the panel and the task bar at the bottom  of the screen disappeared. OK I had quite a few apps open but certainly no more than i have had open whilst in KDE or Gnome. Closed the open apps and then rebooting had no effect, still no panel or task bar.

How do i get these back? Has Xfce terminally crashed, surely it's not so flaky that a few too many progs blows it out of the water.

This will be a shame as it made my Dell go like a rocket. Hmmmm, would slackware based vectorlinux be more stable?

Typed from gnome ubuntu

Simon

---

### Post by reset3x on 2007-10-05
You could always delete your panel folder in /home/your-user-name/.config/xfce4. Then ctrl-alt-bkspace. This will return you to the default panel set up... you can rebuild your launchers etc. from there.... 


After you do the above go into Sessions/Sessions and Startup Settings check off Automatically save session on logout.

This is what worked for me when I had this problem...

Good Luck!!!

EDIT: Duh.. You probably have to ctrl-alt-F2. Login then```
cd .config/xfce4
```
then ```
rm -R panel
```

Then Ctrl-Alt-F7

---

