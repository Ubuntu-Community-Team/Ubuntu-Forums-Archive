---
title: "How do I know how much HHD space I have left???"
date: 2005-05-05
forum: Desktop Environments
---

### Post by braveerudite on 2005-05-05
The most important and simple task but then again is not simple to find. Unbelieveble. How do I know how much space I have on my Hard Disk Drive.  This is so stupid... Why Gnome do this?  Why is my secondary HDD or CD drive doesn't show up?  Even Knoppix displays all the drives by default but Gnome just doesn't?  The help options don't even have a search topic box?  Please help. I know theres got to be a way.....But why so hard?

---

### Post by Xian on 2005-05-05
Open a terminal and type the following:

$ df -h

---

### Post by bored2k on 2005-05-05
[QUOTE=Xian]Open a terminal and type the following:

$ df -h[/QUOTE]
 The GUI way: Applications > System > System Monitor > Resources

---

### Post by braveerudite on 2005-05-05
Now I'm getting closer to what I want thx to you guys but is there a way to have an HHD icon (Like in windows C: drive icon) were I can right click it, choose properties and modify???  I know this is Linux but it makes sence to mae it much easier like that.      The way I was trying before was

Places>Computer

Ones I'm in the computer folder I see 2 icons CD-RW/DVD-Drive and another icon that says File System.  Isn't The File System Icon suppose to be the HDD were Ubuntu is installed? I rigth click it choose properties and I don't see the HHD size and remaining space. Please help!!

---

### Post by braveerudite on 2005-05-05
[QUOTE=bored2k]The GUI way: Applications > System > System Monitor > Resources[/QUOTE]
I like the gui way better please read my reply

---

### Post by bored2k on 2005-05-05
[QUOTE=braveerudite]I like the gui way better please read my reply[/QUOTE]
 Linux is not a windows clone.. Your drive is actually mounted inside "file system" like if it was just another directory. What is it that you want to do ?

---

### Post by dolson on 2005-05-06
[QUOTE=bored2k]Linux is not a windows clone.. Your drive is actually mounted inside "file system" like if it was just another directory. What is it that you want to do ?[/QUOTE]
 Exactly. You can have many different partitions, each one mounted wherever you want, so it doesn't make sense to have the drive space listed in Computer... But maybe there should be a more easy to use / more obvious application.than System Monitor - there's really no way someone could just guess that this application would tell them how much free space they have.

I wrote a script a while back that did simply this, but if you aren't really good at scripting it's probably not for you. In any case, it's not pretty, but it gets the job done:

[img]http://icculus.org/~dolson/images/dur2.png[/img]

Perhaps I could whip up a pie-chart type application that automagically detects your partitions and whatnot and then make a .deb out of it. Unless something like this already exists, I don't know.

---

### Post by dragos_avramescu on 2005-05-06
While not a method to know how much space is left, filelight is very useful for finding out where is the used space :)

sudo apt-get install filelight

then
filelight
choose the desired dir for scan, wait for it to reursive search, then it will draw a multi level pie graph... very fine

---

### Post by Xian on 2005-05-06
[QUOTE=dragos_avramescu]While not a method to know how much space is left, filelight is very useful for finding out where is the used space :)[/QUOTE]
I really like that application. The method of presenting directory usage is great.

---

### Post by MaX on 2005-05-06
[QUOTE=braveerudite]The most important and simple task but then again is not simple to find. Unbelieveble. How do I know how much space I have on my Hard Disk Drive.  This is so stupid... Why Gnome do this?  Why is my secondary HDD or CD drive doesn't show up?  Even Knoppix displays all the drives by default but Gnome just doesn't?  The help options don't even have a search topic box?  Please help. I know theres got to be a way.....But why so hard?[/QUOTE]
 You open a directory/folder with nautilus that is on the disk you want to know how much free space you have, and nautilus tells you in the statusbar.

---

### Post by Fab on 2005-05-06
gtkdiskfree also displays partitions and their used/free space

---

### Post by kvidell on 2005-05-06
You could also pinpoint a specific directory and use du...
Example: Say you chose... your home directory..
```
11/kvidell: du -hs /home/kvidell
4.8G    /home/kvidell
```
It's a nice little way of figuring out how much a specific directory is using.
(Options summary: -h is for "human" (just like with df), in otherwords, it lists the size in some sane reading like mb, or gb, respectively, for easier reading. -s is summary, it displays only a total, not the itemized sizes of every file within)

---

### Post by Nu-Buntu on 2005-05-06
One of the great things about Linux. Want to use the CLI? The power is there. Prefer a GUI? Got that too. Custom scripting? No problem.

Yeah, Windows and the DOS box have some of this, but the power of the Linux command line and scripts vs. batch files make it a really powerful tool!

---

### Post by Endolith on 2008-04-29
I noticed that this has been fixed in Hardy.  If you click Properties for a disk, it will show you a pie chart like Windows does.

---

### Post by mikewhatever on 2008-04-29
> **Endolith said:**
> I noticed that this has been fixed in Hardy.  If you click Properties for a disk, it will show you a pie chart like Windows does.

They haven't fixed anything because there was no bug. The feature you are talking about is present in Gusty and Feisty. Take a look at the dates, this thread is almost two years old.

---

### Post by Endolith on 2008-04-29
> **mikewhatever said:**
> They haven't fixed anything because there was no bug.

This thread was started because of a problem; the problem is now fixed.

> The feature you are talking about is present in Gusty and Feisty.

Looks like it was added in GNOME 2.20, which would be Gutsy. [http://arstechnica.com/news.ars/post/20070919-gnome-2-20-officially-released.html](http://arstechnica.com/news.ars/post/20070919-gnome-2-20-officially-released.html)

> Take a look at the dates, this thread is almost two years old.

So now someone finding this thread in a search (like I did) will know up-to-date information.

---

