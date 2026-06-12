---
title: "XCursor theme causing keyboard to crash any application running"
date: 2007-08-01
forum: Desktop Effects &amp; Customization
---

### Post by Shadow ZERO on 2007-08-01
Hi,

I installed a new XCursor theme from gnome-look.org.

[http://gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533]("http://gnome-look.org/content/show.php/Silver+XCursors+3D?content=5533")

Here's the installation steps:
__________________________________________________ ____________________________
Installation:

Copy the two folders 'Silver' and 'default' to your ~/.icons directory and
restart your X-Server.
__________________________________________________ ____________________________

I had to do something different to make it work though. I had to put the main folder "Silver" in my usr/share/icons directory. I also had to take the index.theme file from the "default" folder in the archive and put it in in the main "Silver" folder(along with the cursors subdirectory).

After that i was able to select the Silver theme from my Preferences/Mouse/Pointers. It looks fine at first, but then almost any keyboard activity crashes whatever application i'm using. In nautilus selecting a file in a directory and pressing a key to skip to the first file starting with that letter will cause nautilus to crash and restart. Even the search feature from the Linux Mint main menu crashes the entire thing. The main terminal won't even start, i have to use xterm.

If i switch back to one of my default pointer styles everything goes back to normal. How can i get this to stop so i can use the new cursor theme?

---

