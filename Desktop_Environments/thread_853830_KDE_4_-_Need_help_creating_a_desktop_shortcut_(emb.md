---
title: "KDE 4 - Need help creating a desktop shortcut (embarrasing I know)"
date: 2008-07-08
forum: Desktop Environments
---

### Post by jmc1 on 2008-07-08
Until I discovered KDE 4.1 I had gotten sick of trying Linux - it was less flashy than the free copy of Vista I had (Compiz was nice, but GTK's style easily wears on you), less compatible with the programs and hardware on my system, and Ubuntu releases seemed to be going backwards on those issues. But once I learned about KDE 4.1's cool stuff (the widgets, the better-than-Aero Oxygen theme, etc) I was compelled to give it another try. Once I managed to get World of Warcraft working on it, I was compelled to leave it on the drive for good.

Alas, not everything can go so perfectly. Although I've been having performance superior to Vista playing WoW, I have to start it each time by hitting Alt+F2 and typing:

wine "c:\program files\world of warcraft\wow.exe"

Obviously, this is a huge pain in the rear end (more so in the wrist). But when I created a shortcut using the instructions I found on WoWWiki and the Ubuntu Documentation, clicking it did nothing. I have yet to find any solution to this. Maybe I'm doing the wrong searches, maybe the beta version of the system is just frigged up, but whatever the case, I can't make a shortcut.

So I beseech the Ubuntu community: whats the i'm-gonna-kick-myself solution to this confounding issue?

Thank you for your help!

---

### Post by wilbbe01 on 2008-07-08
Not sure how your instructions said to do things, but here is an idea that I know has worked for me with wine stuff or any stuff for that matter in the past.

Create a script like the following.

#!/bin/bash
wine /path/to/your/programs/exe

save that file and open up a terminal.  Go to your terminal, change into the directory with your text file and type "chmod a+x [name of text file]"  Just to make sure things worked try typing the following from the directory containing your script.

./myscript

Your program should open.  Once it does that you should in theory be able to click it on the desktop and whatnot as well and just choose run if it prompts you, not sure what kde does in that situation.  Does that solve your issue at all?

---

### Post by jmc1 on 2008-07-09
Yep, that works :)

It would be nice if scripts could have custom icons, but its no big deal. Using World of Warcraft is dead simple now, and thats all I need. Thanks!

---

### Post by wilbbe01 on 2008-07-09
Glad that works for you.  I know in gnome you are able to change the icons of the script file.  I'm not sure if it changes the icon for all scripts or just the one you change it on though.  The way you would go about it in gnome is simple and in properties.  The icon is then a thing you can click on and it will give you a window to choose the path.  You would think KDE would have that ability as well as KDE seems to be more towards the fancy side of things where gnome seems to be more small, reliable, yet still feature filled.  Anyway, glad it worked for you, good luck playing.

---

### Post by brimlar on 2008-07-10
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

I think it details how to set up a shortcut, etc as well.

---

### Post by eightmillion@gmail.com on 2008-07-26
There is a way to get it to have an icon. You need to create a .desktop file. Here's an example...

[INDENT][Desktop Entry]
Encoding=UTF-8
Name=World of Warcraft
Comment=World of Warcraft
Exec=wine "c:\program files\world of warcraft\wow.exe"
Icon=/home/username/wowicon.png
Terminal=false
Type=Application
StartupNotify=false
[/INDENT]

You should just have to change the path to the icon that you want to use. Then save the file as warcraft.desktop and drop it on your desktop and you should be good to go.

---

### Post by _ryan on 2008-10-11
I realize I'm probably way too late to help the original poster but hopefully I can help other people looking for the same thing. 

After you create the shell script you could create a Desktop Shortcut by right clicking in an empty area, Create New-> Link to Application -> Application <Tab>. Browse for your script. You can also customize the icon by clicking the icon in the General Tab.

---

### Post by |{urse on 2009-03-11
Just wanted to say, neither of the above solutions work in kde4. I have LOTS of scripted shortcuts that i would love to have on my desktop (with the appropriate icons). the .desktop shortcuts only work in gnome and the other solution is using nautiluses right click menu. How do you make a simple launcher (with custom icons) for kde4?

O well, back to openbox.

---

### Post by |{urse on 2009-03-11
Okay, I'm sure this not the proper way to do this but if i drag any old icon off the k menu and drop it on the desktop then edit everything uder icon settings (in the right click menu) i can do it. Why are the .desktop files im making and placing in ~/user/Desktop not showing up here (this is the first time i've tried KDE4)? Im sure this is total pebkac but the desktop is a little counterintuitive.

Edit: Even if i edit the name of the shortcut im "using" it doesn't appear to change the original name under the icon Gaaahhh

---

### Post by |{urse on 2009-03-11
Okay, i give up, KDE4 just isn't usable yet.  ^^ certainly someone out there can make a "generic shortcut" plasmoid, maybe ill mess with that tomorrow, maybe not. I am *VERY* impressed with the aesthetics, though it needs more work under the hood.

---

