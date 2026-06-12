---
title: "Can't See Installed packages"
date: 2006-01-10
forum: Desktop Environments
---

### Post by ivanrivest on 2006-01-10
I have downloaded packages using synaptic, they have install properly.  But i dont see them. Im new to ubuntu.  Are they supposed to show up the the menus or is there something i have to do??  Any help would be greatly appreciated.

Thank you

---

### Post by zoiks on 2006-01-10
Depends on the package.  Some should show up in your menu system.  Others will only be available at the command line.  Others won't appear to show up at all (like lib packages, etc.) even though they are installed.

---

### Post by DonQuixote on 2006-01-11
Zoiks,

Is there a way of manually adding these apps to the menu so that they DO show up?

---

### Post by newuser111 on 2006-01-11
do **sudo update-menus** in a terminal

---

### Post by zoiks on 2006-01-11
[QUOTE=DonQuixote]Zoiks,

Is there a way of manually adding these apps to the menu so that they DO show up?[/QUOTE]

Yes.  Go to "Applications|System Tools|Applications Menu Editor".

---

### Post by poiuytr on 2006-01-11
Yes, it's actually pretty easy, I just did this yesterday with the game "Neverball" (one of my favorite games).  Note that there are helpful detailed instructions elsewhere in this ubuntuforums.org so you might want to search for that post, too.

Change your directory to the one where the menu application files are located.  e.g. 
cd /usr/share/applications use the "cat" to look at how those files are set up.  Use the "ls" command to look at a list of the files in that directory.  Choose one of the easier, less detailed files.  (IIRC I modeled my new "neverball" file after the one for Frozen Bubbles).  

For Neverball, all I did was create a new empty file (called neverball.desktop).  You can use "vi" or "gedit" to do this.  Alternatively, you could just copy the Frozen Bubble file to one called neverball.desktop.  Then, use that editing program (gedit or vi or whatever) to replace parts of that file with things that make sense (e.g. change the "Name =" line from "Name = Frozen Bubble" to "Name = Neverball."  Also, make sure you change the Categories line so that your new menu item is placed in the exact sub-menu where you want it.  (For me, it was in the same place as the other game I modeled this file after, so I just kept it reading exactly as it had read for Frozen Bubble.   

Oh, and very important, the "Exec =" line needs to point to the exact command line command that opens the program.  For Neverball, it is simple.  From a command line, typing "neverball" opens the program, so that's why I said here that "Exec = neverball"

Here is what my final product looked like:

$  cat neverball.desktop

[Desktop Entry]
Name=Neverball
Comment=Balancing ball game
Exec=neverball
Icon=/home/xyz/Desktop/extraapplicationicons/neverball.png
Terminal=false
MultipleArgs=false
Type=Application
Categories=Application;Game;ArcadeGame;
 
Wait - you are not done.  See that line, "Icon=/home/xyz/Desktop/extraapplicationicons/neverball.png" ??  That tells neverball.desktop where to find an icon that will be used in the Gnome Menu.  Go download a suitable icon from the Internet, and be sure to ideally save it as a .png grsphics file, and use a graphics editing program such as the wonderfully fantastic "Gimp" to shring down its size.  

You may need to experiment a bit to get the exact size you want.  In the Gimp, just click on "Scale Image" and reduce the number of pixels in the Height and Width of the image.  Note tht the final image has to be really small to fit on the menu!  I can't recall the maximum size (maybe 48 x 48 pixels, IIRC from that other post I read in these Ubuntu forums?)  But to be safe, I started out really small (e.g. 24 x 24) and increased it only gradually so the final image was about the same size as the other menu icons (pictures).

Now, save the icon image someplace sensible I have temporarily saved mine in a folder on my Desktop, but you can probably come up with a better idea.  IIRC I tried to save it in the place where the standard Gnome Menu saves its icons, but that is in a special file which cannot be written to.  But it doesn't matter - just choose a location.  And then note that exact path in the "Icon =" line, as I did in the example above.

It worked like a charm, and was so easy.  Now I have a Neverball menu item under Games.  When I hover my mouse over it, just like all the other Menu items it gives me a brief pop-up description of what it is (a "Balancing Ball game"), it has an icon and looks just like all the other professionally-done-by-Ubuntu developers menu items, and clicking on it opens the program.

Try it!  It's fun to add menu items this way, and for a mere desktop guy as I am, too, it gives you a nice sense of Linux accomplishment.

PS, hey Ubuntu developers, THANK YOU for working so hard and gifting us with such an incredible distro.  Ubuntu rocks.

---

### Post by fleshpile on 2006-02-26
Just for the record,

$ sudo update-menus
sudo: update-menus: command not found

---

### Post by Swiss on 2006-02-26
A quik note, you can tell if it will show up or not, If the Ubuntu icon shows to the right of the Synaptic entry, it should (?) show in the menu.

---

### Post by PsTJsT on 2006-02-28
[QUOTE=Swiss]A quik note, you can tell if it will show up or not, If the Ubuntu icon shows to the right of the Synaptic entry, it should (?) show in the menu.[/QUOTE]
Although I haven't been able to figure out which package it was, I installed something a few weeks ago that surprised me because it had the Ubuntu icon in Synaptic but didn't automatically show up on a menu (at the time, I also thought that icon was a safe indicator of whether it would appear in a menu).  I'll try to figure out exactly what package it was when I have a little more time...

Also, the converse (i.e., if it doesn't have an Ubuntu icon in Synaptic it won't automatically show up in a menu) doesn't appear to be reliable either.  For example, "burgerspace," "toppler," "solarwolf," and "frozen-bubble" automatically show up in my kids' games menu but none of them have the Ubuntu icon in Synaptic.

---

### Post by PsTJsT on 2006-02-28
[QUOTE=poiuytr]Yes, it's actually pretty easy, I just did this yesterday with the game "Neverball" (one of my favorite games).  Note that there are helpful detailed instructions elsewhere in this ubuntuforums.org so you might want to search for that post, too.
<snip>
Try it!  It's fun to add menu items this way, and for a mere desktop guy as I am, too, it gives you a nice sense of Linux accomplishment.[/QUOTE]
Although it likely won't provide much of a sense of accomplishment, there seems to be a slightly easier method...

In a SMEG window ("smeg" from a terminal window, or System Tools > Application Menu Editor), select the "category" (in the left half of the window) in which you want the menu item to appear (or create a new "category" via the "new menu" button on the bottom left), and then click the "new entry" button on the bottom right.  Name the entry whatever you want (e.g., Penguin Racer), enter any description you want (e.g., The new and improved Tux Racer.), and enter the name of the executable (which often, but not always, is the same as the Synaptic package name) on the comand line (e.g., ppracer).  Also, you can browse around for a suitable icon by clicking on the Icon button/square.  Many icons can be found in the /usr/share folders (/pixmaps, /games, /applications, etc.).

---

### Post by poiuytr on 2006-03-01
Ah well, I guess there is something to be said for learning things the hard way the first time around.  :-)  It sure was fun that way, anyway...

Thanks for the pointers re: smeg, which I wasn't familiar with.

Cheers, Poiuytr

---

