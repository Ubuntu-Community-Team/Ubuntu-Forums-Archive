---
title: "Facebook  poker"
date: 2009-07-01
forum: Desktop Environments
---

### Post by edward2536 on 2009-07-01
Hi
running Ubuntu 9.04 and think its great. now have new printer and that works brilliant . what is my problem then you may ask! There seems to be a problem in facebook on TEXAS HOLDEM POKER. Now, i can see my money , my friends, everything "except the playing tables"!  This is just a hindrance, but if this does not work what else may not work in the future? I have all the plugins etc ,etc and still it does not work. Even thought Firefox 3.5 might help but, alas no. Tried in other broswers still no luck . Worst of all it works in WINDOWS, which is what iam am getting away from.
Please help sort the problem 
Thanks

---

### Post by pytheas22 on 2009-07-01
Does the poker application run in flash (if you don't know, please provide a link to the application's site or something so I can look up how it works)?  If so, I would suspect a problem with your flash plugin.

Do you know which flash player you have installed?  If you don't know (and it's alright if you don't), please open a terminal from the Applications>Accessories menu, run the following two commands and post the output here:
```

dpkg --get-selections | grep -e flash -e gnash -e swf
uname -rm
```

That will tell me which flash player you're using.

Also, as a workaround, you could install wine, which will allow you to run most Windows applications on Ubuntu, and run the Windows version of Firefox in it.  You can install wine using the Add/Remove Programs utility or by typing:
```

sudo apt-get install wine
```

With wine installed, go to the Firefox website and download the *Windows* version (the website may auto-detect that you're running Ubuntu and try to give you the Linux version of Firefox; in this case, look for a link that says something like "Download Firefox for other operating systems" and click it).  Save the .exe installer to your desktop, right-click on it and select "Open with Wine Program Loader" to run it.  Once the installation finishes, launch Firefox from the Applications>Wine>Programs menu (not from the shortcut icon in your task bar or from the Applications>Internet menu--both of these will start the Linux version of Firefox, which is not what you want).

There's a good chance that your poker game will work properly in the Windows version of Firefox.  And yes, you can have both the Windows and Linux versions of Firefox installed (and even running) at the same time.  You can use the Windows version just for playing poker, and the Linux one for everything else.

---

### Post by edward2536 on 2009-07-02
> **pytheas22 said:**
> Does the poker application run in flash (if you don't know, please provide a link to the application's site or something so I can look up how it works)?  If so, I would suspect a problem with your flash plugin.

Do you know which flash player you have installed?  If you don't know (and it's alright if you don't), please open a terminal from the Applications>Accessories menu, run the following two commands and post the output here:
```

dpkg --get-selections | grep -e flash -e gnash -e swf
uname -rm
```That will tell me which flash player you're using.

Also, as a workaround, you could install wine, which will allow you to run most Windows applications on Ubuntu, and run the Windows version of Firefox in it.  You can install wine using the Add/Remove Programs utility or by typing:
```

sudo apt-get install wine
```With wine installed, go to the Firefox website and download the *Windows* version (the website may auto-detect that you're running Ubuntu and try to give you the Linux version of Firefox; in this case, look for a link that says something like "Download Firefox for other operating systems" and click it).  Save the .exe installer to your desktop, right-click on it and select "Open with Wine Program Loader" to run it.  Once the installation finishes, launch Firefox from the Applications>Wine>Programs menu (not from the shortcut icon in your task bar or from the Applications>Internet menu--both of these will start the Linux version of Firefox, which is not what you want).

There's a good chance that your poker game will work properly in the Windows version of Firefox.  And yes, you can have both the Windows and Linux versions of Firefox installed (and even running) at the same time.  You can use the Windows version just for playing poker, and the Linux one for everything else.


Thanks for the info  Flash results

andrew@andrew-desktop:~$ dpkg --get-selections | grep -e flash -e gnash -e swf
adobe-flashplugin                install
flashplugin-installer                install
flashplugin-nonfree                install
libswfdec-0.8-0                    install
swfdec-gnome                    install
andrew@andrew-desktop:~$ uname -rm
2.6.28-13-generic i686
andrew@andrew-desktop:

I have Wine and did what you suggest (very easy the way you stated) and it works!!
So do you think the problem is with Ubuntu or because a "plugin some how is not working. I have even tried sending a email to Facebook but have had no reply yet.
[http://www.facebook.com/login.php](http://www.facebook.com/login.php) this is  facebook login.
unable to send link to the poker with out sending all my log in details, but it  TEXAS HOLDEM POKER by zynga.com
Thanks again 
andy

---

### Post by pytheas22 on 2009-07-02
According to zynga.com, the application does use flash, so I do suspect that your issue results from a bug in the plugin that allows Firefox to display flash content.

There are several different flash plugins available for Ubuntu, but only one of them--the one from Adobe--really works.  It looks like you have both Adobe's plugin and a different one called Shockwave installed, and I'm not sure which one is enabled.  If you're using Shockwave, there's a good chance that it doesn't know how to display the poker game correctly.

So I'd recommend uninstalling the Shockwave plugin to see if that helps things.  To remove Shockwave, type:
```

sudo apt-get remove libswfdec-0.8-0 swfdec-gnome
```

After you type this, the system will display some information that looks similar to this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following packages will be REMOVED:
  libswfdec-0.8-0 swfdec-gnome
[/B]0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 127kB disk space will be freed.
Do you want to continue [Y/n]?
```

Pay attention to which packages it says it's going to remove.  If it wants to remove any packages besides the two mentioned in the example above, don't agree to do it, and tell me the names of the packages it wants to remove.

This is important because there's a small chance that removing the Shockwave packages will also cause other applications not to work.

If the system doesn't say it's going to remove any packages besides libswfdec-0.8-0 swfdec-gnome, you can safely agree to do it.

You will need to restart Firefox for changes to take effect after removing Shockwave.

Another thing you can consider (if you have a lot of time to spend on this) is installing Firefox 3.5, which was released a few days ago and may work better than the older version of Firefox that Ubuntu currently uses by default.  You can install it by typing:
```

sudo apt-get update
sudo apt-get install firefox-3.5
```

or searching for it in the graphical Add/Remove Programs utility.

After you install it, run it by typing "firefox-3.5" in a terminal (if you try to open it by using the shortcut in the taskbar or the Applications>Internet menu, you'll be opening the older version instead).  It might do a better job of displaying the poker game.

---

### Post by KrisInfinity on 2009-07-09
I happened to accidentally find the solution :lolflag:

Click in the empty place where the tables should be displayed and press tab. There should appear now a yellow square that highlights the different buttons. Move it with the arrows until you reach the part where the tables should be displayed and press space.

Now the tables will be displayed but you can only navigate them with the arrow key.

Enjoy

---

### Post by ogromano on 2009-08-13
Hello....

Thanks for finding that solution... now I can at least view the tables....

Now if I can figure out how to Raise it would be great.

When it's my turn, I can push any of the buttons to Call, Check, Raise (the default amount), etc, but I can't write the amount to raise nor can I use the slider to increase the amount and I can't push the + or - buttons either.

With TAB I can navigate the buttons, but the field for the raise amount doesn't seem to have a tab stop and in any case it would drive me crazy to play a while using tab so much!!!

Anyone have any solutions??

Thanks!

---

### Post by pytheas22 on 2009-08-13
ogromano: the easiest solution would be just to use the Windows version of Firefox to play the game.  Instructions for setting that up are in post #2.

Otherwise, I've never played this game so I'm not sure how you might work around your problem using the Ubuntu version of Firefox, but maybe someone else will have a suggestion.

---

### Post by jandara on 2009-08-20
So, no formal/logical solution for this yet? I will try removing the Shockwave plugin (if any)...

---

### Post by silvestros on 2009-08-20
I had the same problem with facebook poker and other flash games, try giving the command:
```
sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
```
It worked for me. Also, the flash was not working very well with youtube and other videos, now it works perfectly.

---

### Post by nichpakaich on 2010-01-19
I've tried to uninstall all flash plugins, except the adobe release, but to no avail.

I don't know, but it seems Flash just don't do well in Ubuntu (neither Firefox, or Opera could do the job as well as in XP).

---

### Post by nichpakaich on 2010-01-20
I've tried the wine approach, the result is worse. The screen is flickering, and everything is running very slow.

Gosh, is there no way I can play Zynga Poker on Ubuntu?

---

### Post by pytheas22 on 2010-01-20
nichpakaich: yes, unfortunately flash in Ubuntu doesn't always work well.  Adobe doesn't give much attention to the Linux version of flash player.

The only other thing I would suggest is trying the plugin installed directly from [Adobe's site]("http://get.adobe.com/flashplayer/"), instead of the one that Ubuntu provides in its repositories.

---

### Post by steindor2 on 2010-01-20
> **nichpakaich said:**
> 
Gosh, is there no way I can play Zynga Poker on Ubuntu?

nope, but you can always play poker palace on facebook

---

### Post by nichpakaich on 2010-01-20
> **pytheas22 said:**
> nichpakaich: yes, unfortunately flash in Ubuntu doesn't always work well.  Adobe doesn't give much attention to the Linux version of flash player.

The only other thing I would suggest is trying the plugin installed directly from [Adobe's site]("http://get.adobe.com/flashplayer/"), instead of the one that Ubuntu provides in its repositories.

done that before, and since the result is far from "good" I took your suggestion with the wine approach.

I can tell you, before I upgraded to 8.10 (I was using 7.10 with FireFox 2) the thing was doing just fine. So, I doubt it's about Linux-Flash compatibility, I think it has something to do with FireFox3 doing bad on Linux.

---

