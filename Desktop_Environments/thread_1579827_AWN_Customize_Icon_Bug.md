---
title: "AWN Customize Icon Bug?"
date: 2010-09-22
forum: Desktop Environments
---

### Post by walkerpett on 2010-09-22
Hi everyone,

I have Ubuntu 10.04 with AWN 0.4
I have two applications that I have given custom icons because they have no default icon.  I have both icons' .png files stored in an icons directory in my home folder. At first everything seemed to work fine, but then I noticed one day that one of the apps icons had changed to the same icon as the other app...  So I tried switching it back, but when I changed the icon of one app, the other one changed also!  Now I can't seem to assign more than one custom icon to multiple AWN launchers.  What is the deal?

---

### Post by beyondwithinitself on 2010-10-26
I am having this same problem.  With two or more custom launchers, the "customize icon" function stores only the last icon chosen and applies it to all of the launchers.

---

### Post by kerry_s on 2010-10-26
pic please, i don't understand.
did you try restting back to default & customize again?
are you using the latest version from ppa?

---

### Post by beyondwithinitself on 2010-10-26
I have two custom launchers in the applet bar.  Whenever I set the icon for one, it changes both to that icon.

Update: I just found a way around this by first adding an Opera link to the desktop (since AWN doesn't allow drag n drop from its own Cairo menu to the applets bar) and then dragging that link onto the AWN applet bar.  This saves the program icon correctly, and allows me to keep my custom game icon.

So for Opera (or any recognized program in the Menu), instead of using the AWN Preferences to add a custom applet and icon, one needs only to drag the program (from somewhere other than the Cairo menu) to the applet bar.  

The game, however, is not in the main menu (sits unzipped in a /downloads/ folder) and has a .i386 extension.  So, Preferences is the only way to add a launcher and icon.  This will work as a temporary solution for me until I have another unrecognized program (in which case I'll be back :)

---

### Post by Majgeek on 2010-11-09
I think I found a solution.  I also ran into the same problem when trying to customize the icon on a "unrecognized" app.  It seems to happen when the system has no custom icon assigned to the app.  So what has worked for me is to  create a custom launcher on the desktop for the application I want to add.  Then right click the generic launcher icon and under the basic tab, click the "image of the icon" button and change it to the custom icon.  Then drag the launcher into AWN task manager launchers panel.  You can also change the icon for the app on AWN's panel to something else later without it conflicting with any other custom icons.

I originally thought that I could delete the launcher from the desktop after dragging it into the launchers panel. But after a restart the icons disappeared from AWN. So I found you have to put the launchers into a folder somewhere, then drag the launcher into the launchers panel.

---

### Post by ChrisOfBristol on 2012-11-22
Works for me on Ubuntu 12.10 -Unity +Gnome-session-fallback.

---

