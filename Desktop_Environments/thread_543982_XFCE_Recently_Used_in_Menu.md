---
title: "XFCE Recently Used in Menu"
date: 2007-09-05
forum: Desktop Environments
---

### Post by mastermindg on 2007-09-05
I'm new to the Forums, have recently installed Xubuntu after a stint with Debian.

FYI:

I am running a Dell E-521 AMD64 X2 with multiverse enabled.
I am using XFCE exclusively, hands down the fastest WM.

I would like to integrate the recently-used functionality that is available in Gnome and KDE with XFCE4.4. I have both .recently-used and .recently-used.xbel in my home dir. 

I would like to integrate this functionality into my MAIN MENU, not as a seperate menu. I know that this is possible, I'm just not sure how probable.

If anyone has any tips or apps that would assist in this integration I would be most greatful.

If not, I will be forced to parse the xml and import manually.

Thanks for any help.

---

### Post by mastermindg on 2007-09-06
After 7 hours pouring over sed commands and unix.com crashing on me, I had finally hit a brick wall.

Alast, there was some hope for poor old me: GIMMIE

Luckily they had a package already made, so I installed it (and the xfapplet-plugin for XFCE), and am now looking at my recently used documents. 

Not only does it solve my first problem, but it also addressed the issue of not having CrossOver Office in my menu. It's got a nice interface and it's not in my way too much. I've got it setup in the panel to one side. Works great.

FYI: It didn't work too well running solo, not even after installing the Python bindings for XFCE.

However, it works great in the panel.

I will also continue to work at porting over the recently-used.xbel to a usable freedesktop format.

I've almost got it except for this one last thing:

<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
      <title name="Recently Used" icon="xfce4-backdrop"/>
      <separator/>
  <app name="file:///home/ken/Desktop/ff32-3in1/Readme" cmd="gedit 
</xfdesktop-menu>

I am stuck on how to move the file path to cmd="gedit file.... and also to take the filename after the last / and use it as app name=...

This is how it should look

<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
      <title name="Recently Used" icon="xfce4-backdrop"/>
      <separator/>
  <app name="Readme" cmd="gedit file:///home/ken/Desktop/ff32-3in1/Readme">
</xfdesktop-menu>

Obviously, I am not too far off here, but it's nice to know that I can relax for a little now that I have a workaround.

---

