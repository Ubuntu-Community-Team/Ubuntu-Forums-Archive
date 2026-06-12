---
title: "New Unity 13.04 file manager is terrible"
date: 2013-04-30
forum: Desktop Environments
---

### Post by aceprry on 2013-04-30
The filemanager in 12.04 allowed me to open a folder while the other files and folders remained in view.  I found that to be really useful.  The new filemanager works more like windows where the only way you can see the files in a folder is to click on the folder, replacing the view of the current directory with the contents of the clicked folder.  I liked it much better when I could see the current directory as well as the contents of the folder at the same time.  This is a seriously backward move.  I was able to easily move files between a folder's directory and its parent directory easily.  I wonder if it's possible to get the older file manager back, or improve the "new" version with features from the older version.

---

### Post by grahammechanical on 2013-04-30
For the record, the utility that you are referring to is not the Unity 13.04 File Manager but the Gnome.org Nautilus File Manager version 3.6.3. Don't like it? Tell Gnome.org.

By the way it is possible to open more that one instance (window) of File Manager. Right click the File Manager icon in the Unity 13.04 launcher and select Open a New Window. That will let you do what you want. I should think.

Regards.

---

### Post by aceprry on 2013-04-30
Thanks for the info [COLOR=#000000]grahammechanical,

I'll look around for the correct place to send my feedback.  I was trying to get the name of the program, but couldn't find an 'about' button or option.

I know I can open another instance of the file manager, and even open that within the same window as the first instance.  BUT, the point is that it was so much easier, quicker, and convenient to do it the old way.  Does anyone else feel that's a problem?
[/COLOR]

---

### Post by tonywhelan on 2013-04-30
Gnome' new version of Nautilus lacks a lot of things. No more F3 split-window facility, and with the removal of the Preferences menu there is no way to set the default view to list-view rather than icon-view, no way to change which columns are visible (eg owner, permissions), and so on. There is no toolbar button for Reload/Refresh (you have to click a menu item), and the location bar is "block mode" rather than textual (so you can't copy it to clipboard).

Some of those things can be changed under the hood using the "gsettings" command but that is not an easy tool to use and you can break stuff rather badly. The new Nautilus is essentially castrated as far as I'm concerned.

I had already looked at using the Linux Mint fork of Nautilus ("nemo") and liked it. Nemo's right-click menu in nemo has everything Nautilus used to have, plus standard options to 'open as root' and 'open terminal here' which are things I make use of regularly. 

In Ubuntu 13.04 you can install the Cinnamon desktop and the Nemo file Manager from the Ubuntu repositories, but the drawback is that although you can tell Ubuntu to use nemo for files and folders, the management of the deskop stays with Nautilus, so right-click on desktop produces a nautilus submenu rather than a nemo sub-menu*. If you don't mind that limitation, then that's your solution. If you are using an earlier version of Ubuntu (eg 12.04, 12.10) you will probably have to install an extra repository to get the option of installing nemo - take a look at [http://www.noobslab.com/2013/01/install-nemo-file-manager-in-ubuntu.html]("http://www.noobslab.com/2013/01/install-nemo-file-manager-in-ubuntu.html") to see how. 

(* It is possible to use gsettings to tell Ubuntu not to use nautilus as desktop manager but despite a bit of web searching I couldn't see a (successful) way to make Ubuntu use nemo as desktop file manager.)

Since I also prefer the menu-based Cinnamon desktop to the Unity desktop, I went one step further and have just done a test build on my "mucking around" spare PC; built standard Ubuntu 13.04, then uninstalled nautilus, _after which_ I installed Cinnamon and nemo. (NB Order is important; seems you must install cinnamon and nemo AFTER you remove nautilus, or else they'll be removed too).

This gave me the Cinnamon desktop at session login (Unity disappeared off the session options list), and nemo became the file and desktop manager automatically.  I'm liking what I see. Cinnamon does need to make a few improvements yet (integration of the separate gnome settings and cinnamon settings menus is in the pipeline) but I'm comfortable with it. I have added a few panel indicator applets (eg weather) and figured out how to make the panel height larger and the icons bigger (my eyes aren't young any more). Just in case there are any applications that have calls to nautilus hardcoded, I added a file /usr/bin/nautilus which contains the text below and made it executable, so anything that calls nautilus will be redirected to nemo.

#!/bin/bash
nemo $1 $2 $3 $4
exit 0

So it seems to me that you can have Unity with Nemo provided you don't mind Nautilus running the desktop, OR you can ditch Unity by removing Nautilus and installing the Cinnamon desktop and Nemo.

---

### Post by kevinmchapman on 2013-04-30
> **tonywhelan said:**
> Gnome' new version of Nautilus lacks a lot of things. No more F3 split-window facility, and with the removal of the Preferences menu there is no way to set the default view to list-view rather than icon-view, no way to change which columns are visible (eg owner, permissions), and so on. There is no toolbar button for Reload/Refresh (you have to click a menu item), and the location bar is "block mode" rather than textual (so you can't copy it to clipboard).


Are you sure about all those?

I'm on 3.8, but I think 3.6 was the same. F3 split pane is gone, definitely, and Reload is indeed under a menu. Preferences is under whatever you call the menu for Files next to Activities. This has default view and column selection. I just tried a cut-and-paste from the location bar into Gedit, and that worked too.

Edit: isn't Ubuntu on Nautilus from 3.4? If so, were those features missing and have been added back since? Upshot is that they are there now, anyway

---

### Post by JonPaul on 2013-04-30
If you look in the Software Centre there are several alternative file managers. At least you don't have to install all the Cinnamon stuff (if you don't want it that is:P)

JP

---

### Post by The Cog on 2013-04-30
It might be worth trying thunar. It's the file manager with XFCE. It uses mainly gnome libraries, so won't pull in too many extra libraries (I think).

---

### Post by tonywhelan on 2013-04-30
Thanks kevinmchapman

I used the F3 split-screen umpteen times a day so losing it is a PITA. It took Gnome/Nautilus years to add the F3 split-screen option, then they just took it away again. People have different ways of working, and I appreciate it can be difficult for a software team to build in all the options that users might like, without complicating the system excessively, but I just don't understand the mentality behind removing the split-screen option. The alternative they provide (right-click, choose Copy To) is a clumsier procedure in my view.

I'm looking at a clean install of Ubuntu 13.04 now ... and yes I see that if you right-click on the "blocky" location bar you can indeed Copy. Not obvious unless you know. So know we do!

You're also right about preferences. I now see that if you open Files (nautilus) then move the cursor to the Unity "menu bar" (if that's what its called) the word 'Files' appears and if clicked there are options for setting preferences. I guess this would be obvious to someone who is accustomed to using Unity. After years happily using standard Ubuntu I switched to Linux Mint when Unity arrived. But I also find Ubuntu with Cinnamon/Nemo added in lieu of Unity is equally friendly.

---

### Post by aceprry on 2013-05-01
Ok, I found a real nice solution.  Someone patched the 13.04 file manager so that it looks and feels like the old one, even includes the F3 split screen.  Very simple to install, from his own PPA.  Check out: [http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html](http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html)

I'm not sure if I should mark the thread as solved, maybe I should leave it as is and consider it a complaint thread about 13.04.  Enjoy everyone.

---

### Post by tonywhelan on 2013-05-01
good work. Looks like that patch was only just announced on webupd8 over the last 24 hours, which explains why I didn't see it earlier this week when I went looking.

---

### Post by Mike80 on 2013-05-01
> **tonywhelan said:**
>  There is no toolbar button for Reload/Refresh (you have to click a menu item), and the location bar is "block mode" rather than textual (so you can't copy it to clipboard).

I don't like those very much too but I alternate with other file managers. 

The one I liked the options most was Konkeror and/or Dolphin but I don't have it know as I feel it kinda "heavy" and I don't know how to explain but I prefer those programs that come with KDE to be used in "kde session"s. But it allows us to customize the navigation bar better than others, I mean, thru point and click and drag - that's how I prefer, editing thru a gui rather than config files. For instance PCManFM has the navbar buttons too small and in Konkeror one can resize the navbar buttons/icons.
Sorry if I wasn't very clear.

---

### Post by anejo on 2013-05-01
> **aceprry said:**
> Someone patched the 13.04 file manager...
+1 on that!
I'm sure we'll see a Nautilus update that'll return some normailty to that awesome app
But in the meantime, @The Cog's suggestion to use THUNAR is awesome!
I tried it and found a real gem... mass file renames are a real breeze with Thunar
Geez Nautilus... get your act together!

---

### Post by Pkunk on 2013-05-28
I tried every "tweak" in and out of the book but couldn't get the latest nautilus to play nice.
Now i enjoy using the file manager "pcmanfm" which is the default file manager for lubuntu. v0.9.10 is very stable and i don't miss nautilus at all since switching ever. And best of all the compact view actually works very well.

---

