---
title: "how would i play interactive fiction games"
date: 2010-11-20
forum: Gaming &amp; Leisure
---

### Post by clear on 2010-11-20
ive downloaded gargoyle, tads, a bunch of interpreters, but there not showing up in the applications menu? how is this done?

---

### Post by pieman711 on 2010-11-21
For the point and click, rather than text based, adventure games have you tried using the SCUMM engine from the software centre? This will install it into the right pace and put in a menu icon in the Games menu. You get two games with it, beneath a steel sky and something else, and it's very easy to get loads of others to work through it. I played the day of the tentacles, monkey island and full throttle with no problems with SCUMM.

---

### Post by Sofox on 2010-11-21
Go to the Ubuntu Software Center, and search for something called Frotz.

Install it, and it should pop up on one of the menus (Software Center should even tell you).

Then run it and open your interactive fiction games.

Let us know if you need anymore help.

---

### Post by clear on 2010-11-21
well, thats the problem, the interpreters arent popping up in the ubuntu applications menu. ive installed like 6 interpreters. and none showed up in the menu.

---

### Post by clear on 2010-11-22
i do need more help. er bump:)btw, following the 24 bump rule. please be very specific when you offer help. what i want to do is play both tads and zcode games. when i dl the interpreter, the interpreter doesnt show up in the application menu. so i need to know why and how specifically does the interpreter work with ubuntu. and how to load games. thanx.

---

### Post by pieman711 on 2010-11-22
Are you using ubuntu or the netbook remix? If you go to the software centre like Sofox said (the one in applications --> Ubuntu Software Centre) and search and download the software there (you'll probably have to put in your password) then it should put the interpreter in your menu under applications --> games most probably. 
If that doesn't work you could try opening the ones you've installed through the run dialogue (alt+F2 probably then type in the name of the programme and it should prompt you with the right command) but that will only work if during the installation process it put the interpreter into your $PATH, again something that happens automatically when you use the software centre. 
The other option is to find it manually (probably where you downloaded it to, or using nautilus's search function) and put in a menu entry yourself. I think you right click the applications menu to be able to add stuff but not sure at teh moment (I'm using the netbook remix right now and it's a different layout here)

---

### Post by Sofox on 2010-11-22
clear, I've figured it out. The answer was staring me in the face, I'm so stupid.

Frotz is a command line tool. It won't show up in the menu because it's run from the terminal.

Here's what you do:

Download Zork and extract it to a directory. For this example, make it "Zork" in your home folder.

Go to Accessories > Terminal.
A black box should pop up

Type this:

cd Zork
cd DATA
frotz ZORK1.DAT

Then the game should play.
Press CTRL+C when you want to quit, or just type "quit"

Let me know if there are any more problems.

---

### Post by farvardin on 2011-05-16
if you can't find a gargoyle launcher in your menu, you should complain to the packager, it seems the .desktop file is not in the filelist: 
[http://packages.ubuntu.com/natty/gargoyle-free](http://packages.ubuntu.com/natty/gargoyle-free)

You can get it there:

[http://garglk.googlecode.com/svn-history/r492/trunk/garglk/gargoyle.desktop](http://garglk.googlecode.com/svn-history/r492/trunk/garglk/gargoyle.desktop)

just copy it on your desktop or into your prefered folder, and click on it. It will present you a menu for loading files.

[EDIT] This version of gargoyle is outdated, and I think it couldn't launch a menu at that time, you have to call the games from the command line, like this:

gargoyle game.z5

frotz can only play zcode games. qtads can play tads games.

---

