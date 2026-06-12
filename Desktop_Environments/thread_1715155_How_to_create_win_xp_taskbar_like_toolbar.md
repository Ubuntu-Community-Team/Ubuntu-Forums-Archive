---
title: "How to create win xp taskbar like toolbar?"
date: 2011-03-26
forum: Desktop Environments
---

### Post by Abhihemu on 2011-03-26
Hi,
I am a new Linux user. I want to know whether there is any way to create a toolbar just like windows taskbar toolbar, in which i can place my music folder and click on it to see the sub-folders-tree. Like this one:-
[IMG]http://www.mytechsupportstore.com/blog/wp-content/uploads/2010/08/desktop-taskbar1.gif[/IMG]

[IMG]http://www.trishtech.com/img_art/win7_deskbar_0.jpg[/IMG]

Kindly help !! Thanks :)

---

### Post by Bucky Ball on 2011-03-26
You could install XP! But seriously, KDE desktop environment might be more to your liking; it is setup more like that. 

You can install Kubuntu (or run it from the disk first to see if you like it) or just install the KDE desktop into your current Ubuntu install and choose that from sessions at the log in screen when you boot. ;)

---

### Post by Abhihemu on 2011-03-26
@Bucky Ball
thanks for reply ! , actually i have placed all my music files according to there moods like - Sad Songs, Bass boost etc. and i used to place a My music toolbar in my win xp taskbar which was good. And i hope Ubuntu should be having such a way. I liked Gnome more than KDE so want to stick with it ;)
One thing more I am Loving Ubuntu Linux and have become a great fan of it's speed and features! :)

---

### Post by Bucky Ball on 2011-03-26
Simple way is to open a file manager window with all the folders in it. In the bottom pane on the left is the same list you have in places. Grab the folder you want to access from your list of folders in the main list window on the right and drag/drop it in that bottom left pane. 

Now your folder will be in the Places drop down menu in the top toolbar. ;)

If it doesn't let you drop your folder in there, open a terminal with Applications>Accessories>Terminal and paste this in:

```
sudo nautilus
```That will give you root permission and allow you to drop the folder there. BE CAREFUL as you will be operating in the file manager as root user so just drop your folder where you want it and close the window again.

This should cover it better:

[http://ubuntuanswers.wordpress.com/2007/12/27/customizing-the-places-menu-in-ubuntu/](http://ubuntuanswers.wordpress.com/2007/12/27/customizing-the-places-menu-in-ubuntu/)

---

### Post by Abhihemu on 2011-03-27
Thanks Bucky,
I tried it but i only got a folder icon in the bottom panel, which opens my music folder :-
[IMG]http://ubuntuforums.org/%3Ca%20href=http://img217.imageshack.us/i/screenshotlsi.png/%20target=_blank%3E[IMG]http://img217.imageshack.us/img217/8448/screenshotlsi.png[/IMG][IMG]http://img217.imageshack.us/i/screenshotlsi.png/[/IMG]
[http://img217.imageshack.us/i/screenshotlsi.png/](http://img217.imageshack.us/i/screenshotlsi.png/)

Actually i want it to show the folder list as in the pics i posted above without opening them.
Thanks :)

---

### Post by Copper Bezel on 2011-03-27
Yeah, I don't know of any alternative Places menu that provides subfolder access directly. The Places menu is, after all, a list of shortcuts, not actually displaying your real directory tree.

---

### Post by ankspo71 on 2011-03-27
Hi,
Hawkscope will allow you to browse your system with a folder tree.
[http://code.google.com/p/hawkscope/](http://code.google.com/p/hawkscope/)
(it requires sun-java5-jre or greater)

Here's another called gnome-menu-file-browser-applet 
[http://code.google.com/p/gnome-menu-file-browser-applet/](http://code.google.com/p/gnome-menu-file-browser-applet/)
Edit: It can be installed by installing "file-browser-applet"

---

### Post by Frogs Hair on 2011-03-27
This may give you a more Windows like taskbar . [http://www.linoob.com/2010/11/dockbarx-0-40-for-ubuntu-10-10/](http://www.linoob.com/2010/11/dockbarx-0-40-for-ubuntu-10-10/)

---

### Post by Abhihemu on 2011-03-28
Hi
@[ankspo71]("http://ubuntuforums.org/member.php?u=734190") hey thanks mate, i have installed hawkscope and it works as i desired, :)  but the second links seems to tough for me because it needs many commands to install it and i am new to Linux. So i'll stick with Hawkscope.

[http://img600.imageshack.us/i/screenshotilu.png/](http://img600.imageshack.us/i/screenshotilu.png/)
[]("http://img197.imageshack.us/i/screenshotubuntuhowtocr.png/")
@[Frogs Hair]("http://ubuntuforums.org/member.php?u=1024576") that dock is really cool !

---

### Post by Krytarik on 2011-03-28
> **Abhihemu said:**
> 
@[ankspo71]("http://ubuntuforums.org/member.php?u=734190") hey thanks mate, i have installed hawkscope and it works as i desired, :)  but the second links seems to tough for me because it needs many commands to install it and i am new to Linux. So i'll stick with Hawkscope.

I personally wouldn't use a java-based applet.

If you want to give "File Browser Applet" a try, it's even in the official repos, no need to compile it by yourself:
```
sudo apt-get install file-browser-applet
```Greetings.

---

### Post by Copper Bezel on 2011-03-28
After about a minute with file-browser-applet:

That's *nice*. I mean, *really* nice. Somebody needs to make an AWN wrapper for that, *stat*. = )

---

### Post by Krytarik on 2011-03-28
> **Copper Bezel said:**
> Somebody needs to make an AWN wrapper for that, *stat*. = )
:P  From now on I'll try to avoid threads about docks, they apparently tend to get really crowded. ;-)

---

### Post by Copper Bezel on 2011-03-28
Not so much crowded, per se. You're just kind of guaranteed to see Rasa, cblnchat, me, and possibly Lucradia. = )

---

### Post by Krytarik on 2011-03-28
> **Copper Bezel said:**
> Not so much crowded, per se. You're just kind of guaranteed to see Rasa, cblnchat, me, and possibly Lucradia. = )
LOL:D Is that the AWN-Club!?

@everyone else: [http://ubuntuforums.org/showthread.php?t=1715935](http://ubuntuforums.org/showthread.php?t=1715935)

---

### Post by Abhihemu on 2011-03-29
@[Krytarik]("http://ubuntuforums.org/member.php?u=1187548") i have removed hawkscope and got the file browser applet in the ubuntu software center! yeah it's very nice light and easy. !!:)

---

### Post by Krytarik on 2011-03-30
> **Abhihemu said:**
> @[Krytarik]("http://ubuntuforums.org/member.php?u=1187548") i have removed hawkscope and got the file browser applet in the ubuntu software center! yeah it's very nice light and easy. !!:)
Cool! Thanks for the feedback! Yeah, I really do think that a Java-based applet is unnecessary heavy for that matter.

---

