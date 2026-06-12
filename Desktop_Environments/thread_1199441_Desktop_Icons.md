---
title: "Desktop Icons"
date: 2009-06-28
forum: Desktop Environments
---

### Post by 1868ccMGB on 2009-06-28
I am sure this topic has been beaten to death. If so please forgive me.

I have installed(decompressed) several programs, the files will launch from the installed directory. How do I put an icon on the desktop to launch the program? I have tried using the right click option to install application launcher and tried both application and application in terminal.

If I setup the application option and then click the icon, nothing happens. The application in terminal option flashes the terminal window before the screen clears again.

Pretty new to Ubuntu, very familiar with Windows.

Suggestions?
Thanks,
Rob
Ubuntu 9.04

---

### Post by Tamlynmac on 2009-06-29
One thought is to check your Gnome Configuration Editor to assure Nautilus is permitted to draw the icons on your desktop.

menu/system tools/configuration editor/apps/nautilus/preferences

Left click and highlight preferences, find "show_desktop" on right side and if unchecked then check the box. Then reboot.

This will permit Nautilus to draw the icons on your desktop when you right click in the menu on a application and select "add this launcher to desktop".

Hope this helps.

---

### Post by 1868ccMGB on 2009-06-29
Thanks for your reply.

I can put an icon on the desktop, it just doesn't do anything when I click it.

I  unfortunately  can not not find the string of commands you gave me either. None of those options exist in any of my pull down menus. A search in the help documentation didn't provide much either. 

Thanks again,
Rob

---

### Post by Tamlynmac on 2009-06-29
I apologize for misunderstanding your request for assistance. I thought you weren't able to display the icons on the desktop. My bad.

Hopefully, someone else will be able to assist you with the desktop application issue of not opening, when double clicked.

---

### Post by 1868ccMGB on 2009-06-29
anybody else have a suggestion on getting a desktop icon to open the program?
Thanks,
Rob
New to Ubuntu

---

### Post by coffeecat on 2009-06-30
Two things.

> **1868ccMGB said:**
> I have tried using the right click option to install application launcher and tried both application and application in terminal.

This is the correct way to do it, but clearly something is wrong. Open a terminal and issue the command that you put in the launcher command field. This way you should get an error message which might give us a clue - the terminal will stay open and will give you a chance to copy and paste the error. Post the error plus details of the application you are trying to launch: where the executable is, where you downloaded it from, how you installed it, etc.

Which leads on to the bit that worries me...
 
> **1868ccMGB said:**
> I have installed(decompressed) several programs

It sounds as though you are making the common error among new Linux users of downloading applications for installation from the internet. That's the Windows way of doing things. Please confirm exactly what you did. What do you mean by decompressed? Did you download tarballs of source code and compile them, or .deb files and double-click on them? You should only need to do this sort of thing for obscure applications and a few other odds and ends. More than 95% of what you might need you'll find in Applications > Add/Remove (the newbie-friendly package manager - a million miles from the same-named Windows abomination) or System > Administration > Synaptic. If you install from a package manager, you'll get menu entries added automatically. With a menu entry, you can simply right-click on it and select "Add this launcher to desktop".

---

### Post by 1868ccMGB on 2009-06-30
The programs are TunerStudio for tuning the Megasquirt fuel injection computer(compressed .jar file which runs under java) and MegaLog Viewer (also a java program). 

Yes, I did a very standard windows thing, decompress the file into a folder and attempt to execute the *.sh file. This WILL load the program, I just can't get the program to run from the launcher.

When I execute the command line from the launcher in a terminal window, I get this:

robert@robert-laptop:~$ /home/robert/apps/TunerStudio/TunerStudio.sh
Unable to access jarfile TunerStudioMS.jar
robert@robert-laptop:~$ 

The TunerStudio.sh file also opens this *.sh file if I double click the *.sh file in the folder and tell it to open in a terminal window.

Thanks again,
Rob

---

### Post by 1868ccMGB on 2009-06-30
Problem solved!

When the program was decompressed a line in the startup .sh file had a # symbol which turned the command line into a comment. The problem wasn't ubuntu at all but rather my misunderstanding of the programming language. 

Thanks to all for your help and support!
Rob

---

