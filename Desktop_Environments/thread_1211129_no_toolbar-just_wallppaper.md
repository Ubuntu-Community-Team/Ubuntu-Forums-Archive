---
title: "no toolbar-just wallppaper"
date: 2009-07-12
forum: Desktop Environments
---

### Post by jesse c on 2009-07-12
All of a sudden i noticed that there was no toolbar on the top edge of my screen to log off or do anything else for that matter-no application/system/pref menu.i did a power off restart thinking it would restart as normal,but nooo,no my desktop is now just my jaunty wallpaper and nothing else,i cant even get to the terminal not that i would know what to do if i could.Could it be just so big that everything is offscreen? Any thoughts before i reinstall from disk? Also on that subject when i sent for Jaunty i purchased (OS-Disc) both a 32bit and 64 bit disc and installed 32,is it time to try my 64?Is the environment up to the 64 world yet?

---

### Post by hansdown on 2009-07-12
Hi jesse c.

A couple things to try;  

- Hold alt+left mouse button to see if you can drag the window down.

- Right click an area where the top panel should be, and see if you get a drop down box. If yes, click add new panel.

---

### Post by jesse c on 2009-07-12
thanks for the try handsdown but no luck.alt/lft mouse does nothing and the right click at top edge brings down a box that has a 'create launcher' option but doesnt seem applicable to my problem

---

### Post by hansdown on 2009-07-12
One more thing. Click alt+F2.

If you get a terminal, run ```
sudo apt-get install gnome desktop
```

Hope this saves a re-install.

---

### Post by caryb on 2009-07-12
Try adding a new user & log in as that user, you might find it is just a profile problem. In Kubuntu you run this rm -r ~/.kde/config/share

This wont work on Ubuntu but there should be a .gnome folder in your home directory with a similar config folder.

I would try the new logon 1st & it that works then you know it's a profile problem hopefully a gnomie will know where the config file/folder lives.


Cary

Just found [this]("http://ubuntuforums.org/showthread.php?t=1149587")

---

### Post by jesse c on 2009-07-13
hansdown-no luck again-i did get a window to run the terminal but no change
caryb-i have auto log in so it goes directly to the wallpaper any ideas how to get to another log in option?










/

---

### Post by hansdown on 2009-07-13
I should have probably asked you to alt+F2, and run

```
sudo apt-get install gnome-desktop
```

as the thread that caryb linked to.

[http://ubuntuforums.org/showthread.php?t=1149587](http://ubuntuforums.org/showthread.php?t=1149587)

---

### Post by UbuntuNerd on 2009-07-13
what happens if you hit Ctrl +alt+f2? hit ctrl+alt+f7 to get back to the GUI

---

### Post by jfvb1225 on 2009-07-14
I have posted and have found several posts related to panels disappearing. It seems to be a known issue. One fix I have found is to create a new session. Another is in this thread:

[http://ubuntuforums.org/showthread.php?p=7614385#post7614385](http://ubuntuforums.org/showthread.php?p=7614385#post7614385)

---

### Post by jesse c on 2009-07-15
The F2 prompt brings up a log/password in text page that loads some text and then stops at a ~$ text and then i dont know what to do so i power off kill and restart.I have found that if i F1 i get a drop down box that lets me access all my desktop options and i can get to terminal/internet/administration/preferences/etc. so i can use my computer but its the GUI toolbar that i would like to get back somehow

---

### Post by Ugluk on 2009-07-15
Try removing content of the ~/.cache/sessions folder.

---

### Post by jesse c on 2009-07-15
ugluk can you give me step by step tutor on removing that file?

---

### Post by UbuntuNerd on 2009-07-15
> **jesse c said:**
> The F2 prompt brings up a log/password in text page that loads some text and then stops at a ~$ text and then i dont know what to do so i power off kill and restart.I have found that if i F1 i get a drop down box that lets me access all my desktop options and i can get to terminal/internet/administration/preferences/etc. so i can use my computer but its the GUI toolbar that i would like to get back somehow

if you can type those commands again and access the terminal try this command:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by BinaryFeast on 2009-07-15
How about alt+F2 and:

```
gnome-panel
```

Have had a "missing panel"-problem in xfce several times. There I just need to type "xfce4-panel" to start it. If it keeps disappearing then add the command to the startup items or auto-save the running apps of every session.

---

### Post by UbuntuNerd on 2009-07-16
try the command I gave you it should reset and restore your panels to default, if you have to copy it to a piece of paper and then type in the terminal.  make sure to write it exactly as it is or it won't work

---

### Post by jesse c on 2009-07-17
SOLVED-Ubuntu nerd:I think your code did the trick.I copied/pasted code into terminal and the terminal said it couldnt execute the command because something or another wasnt empty,i thought it was a failure until i noticed everything was back to 'normal'and my desktop is back again thanks to all for help  JESSE C

---

### Post by UbuntuNerd on 2009-07-18
im glad is working again Im 100 percent sure the code I gave you works :D

---

### Post by intangodelta on 2009-07-18
Hi, I've got a similar problem but your solution isn't working for me.

Alt-F2 does nothing, but I can right click and add a launcher for gnome-terminal.

I tried the code here and ran gnome-panel (and gnome-panel --replace to test that version) and both times it shows the panel but I can't close the terminal without it disappearing again. Also, windows don't have the title bar on them with the various buttons for close, minimize, etc.

Also, no menus in the panels. Any ideas??

Thanks

---

### Post by UbuntuNerd on 2009-07-18
> **intangodelta said:**
> Hi, I've got a similar problem but your solution isn't working for me.

Alt-F2 does nothing, but I can right click and add a launcher for gnome-terminal.

I tried the code here and ran gnome-panel (and gnome-panel --replace to test that version) and both times it shows the panel but I can't close the terminal without it disappearing again. Also, windows don't have the title bar on them with the various buttons for close, minimize, etc.

Also, no menus in the panels. Any ideas??

Thanks
did you try Ctrl+Alt+f2 it should take you the a login screen press Ctrl+Alt+f7 to get back to your desktop GUI

---

### Post by intangodelta on 2009-07-18
Yep, did that but the code had no effect at all in a console. If I ran gnome-panel or gnome-panel --restart in a console the error was 'Cannot open display'

---

### Post by jesse c on 2009-07-20
i was getting access to a gui by using alt/F1 Ubuntu nerds code got it back to a tool bar on the top edge where it used to be

---

### Post by UbuntuNerd on 2009-07-24
> **intangodelta said:**
> Yep, did that but the code had no effect at all in a console. If I ran gnome-panel or gnome-panel --restart in a console the error was 'Cannot open display'

if the code I gave you didn't work the only thing I can think is to reinstall your desktop, if you want to give it a try copy and paste this code in a terminal:
```
sudo apt-get install ubuntu-desktop
```

---

