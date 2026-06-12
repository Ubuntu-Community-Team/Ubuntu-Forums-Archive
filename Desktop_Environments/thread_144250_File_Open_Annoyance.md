---
title: "File Open Annoyance"
date: 2006-03-13
forum: Desktop Environments
---

### Post by John Jason Jordan on 2006-03-13
Ubuntu-64 Breezy, Gnome desktop

In most applications when I go to open a file the dialog box that pops up is hopeless.   It shows just a few folders:

Home
Desktop
File System
iPod
CD-ROM 1
cdrom0

Usually I need to click on File System in order to navigate to the folder I am looking for. (Like right now I have started gedit with sudo because I need to edit the fstab file.) But there is no easy way to navigate -- no "tree," no "forward" or "back" buttons. And you can't tell if what you're looking at is a folder or a file or what, because there are no icons or color schemes or anything to tell them apart.

I'm assuming this behavior is built into Gnome somehow, since most applications pop up an identical File Open dialog box. I don't even know where it's getting what it displays -- my iPod is almost never mounted, and even if I did I don't want to open a file on it because that would probably screw up the iTunes database. And there is no device "CD-ROM 1." At the same time I do have an external pocket drive that I sometimes plug in, but that never appears.

Is there a way to change what the File Open dialog box looks like? Can I stop it from displaying anything but the File System, and have that appear in a tree? Can I make it show all devices that are mounted? Can I somehow refresh the view, like after I plug in the pocket drive?

---

### Post by aysiu on 2006-03-13
Can you post a small screenshot of this annoyance?

---

### Post by John Jason Jordan on 2006-03-14
[QUOTE=aysiu]Can you post a small screenshot of this annoyance?[/QUOTE]
Here it is:[ATTACH]7041[/ATTACH]

---

### Post by Madpilot on 2006-03-14
The buttons along the top - that have a left arrow, "Home" and "Documents" on them in your screenshot - are directory links as well. Click on them to move to the directory on the button; it can be faster in some cases than using the tree.

As for the 'always starts in Documents' irritation - I wish you could cure Ubuntu of this, but I haven't found a way to. I want it to open the Gnome File Manger thing in my home directory, not /$USER/Documents...

---

### Post by aysiu on 2006-03-14
It's a Gnome thing, but I definitely see a difference between folders and files. Maybe you need a different icon theme?

Consider using KDE perhaps...

---

### Post by John Jason Jordan on 2006-03-14
[QUOTE=aysiu]It's a Gnome thing, but I definitely see a difference between folders and files. Maybe you need a different icon theme?[/QUOTE]
What theme are you using?
[QUOTE=aysiu]Consider using KDE perhaps...[/QUOTE]
Ugh.

---

### Post by John Jason Jordan on 2006-03-14
[QUOTE=John Jason Jordan]What theme are you using?[/QUOTE]

Never mind. I found that I can get icons in the File Open window like you have by fiddling with the themes.

As for the slider things along the top, they are pretty useless. Problem is that looking at them you have no idea what folder is the next one up. It only shows three levels. A tree is much faster to negotiate and easier to use. And the File Open dialog box does have two panes. It seems only natural that the one on the left would be a tree with the files displayed in the panel on the right. 

I have a strong suspicion is that the slider idea was because the Linux person who designed the Open File dialog box wanted to make sure it looked as little like Windows as possible. Never mind the fact that Gates spent gazillions on user research to find out what people find convenient and easy. Sometimes a bit of imitation is a good idea. :)

Also I haven't been able to figure out how to get it to stop displaying locations that don't exist in the left pane.

But at least I now have icons so I can tell a file from a folder. Making progress. :)

---

### Post by htinn on 2006-03-14
It might help you to use Bookmarks of locations using the "+Add" button in the lower left corner. That'll save you lots of searching in the future.

---

