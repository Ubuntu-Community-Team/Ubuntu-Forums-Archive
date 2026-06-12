---
title: "Strange BUG!Upgraded to 8.10 Intrepid - Gnome - &quot;Places in Menu&quot; acting very strange!"
date: 2008-11-04
forum: Desktop Environments
---

### Post by MozartlovesUbun2 on 2008-11-04
Hi

I just upgraded from Hardy to Intrepid on 2 different laptops, all works well, just one of them is acting up!

Top left Menu corner - Applications - Places - System

in Places when I click my Home folder or any other location (pictures, documents, etc), it does not open but instead Rhythmbox application opens up!

So I uninstalled Rhythmbox and tried again,

and then Movie player opens!!!!!!!

I just wanna access my Home folder of Pictures folder

Please help, how to fix this mess?

---

### Post by Halow on 2008-11-04
I didn't have this problem, but it sounds a little like a [thread]("http://ubuntuforums.org/showthread.php?t=969586&highlight=picture+cd") I checked earlier. Maybe it'll help?

---

### Post by MozartlovesUbun2 on 2008-11-04
> **Halow said:**
> I didn't have this problem, but it sounds a little like a [thread]("http://ubuntuforums.org/showthread.php?t=969586&highlight=picture+cd") I checked earlier. Maybe it'll help?

Thanks

Checking it out now

---

### Post by tastyllama on 2008-11-05
I have the same problem.  When I click on Home Folder, Desktop, Documents, Music, Pictures, Videos, and even 33.5GB Media, Rhythmbox opens.  Frustrating problem, especially since I can't find where to edit the Places menu.  The Computer, CD/DVD Creator, and other entries seem to work.

  It doesn't seem to be linked to the other thread posted.  That one looked like an autorun problem when a CD or other media inserted.

  BTW, I am having this problem on more than one computer, although the other computer is giving the error "Failed to execute child process wxvlc (no such file or directory)".  I suppose it is trying to start vlc?

---

### Post by tastyllama on 2008-11-05
OK, found the solution (worked for me).

[Long Thread]("http://tennessee.ubuntuforums.com/showthread.php?p=6038154")
[Short Thread]("http://ph.ubuntuforums.com/showthread.php?t=960545")

Solution: open Nautilus (like from Places -> Computer), then right click in any folder, properties, select the Open With tab, and from the list select Open Folder.

Apparently, the default action for folders gets changed to some other program.

Good Luck!

---

### Post by SpetsnazC4 on 2008-11-05
Thanks, your solution worked. I was going nuts.

---

### Post by stephanecharette on 2008-11-06
In my case, it kept trying to open with "gedit", which would complain with "/whatever/some/path is a directory.  Please check that you typed the location correctly and try again."

> Solution: open Nautilus (like from Places -> Computer), then right click in any folder, properties, select the Open With tab, and from the list select Open Folder.

Apparently, the default action for folders gets changed to some other program.

This solution worked perfectly for me as well.  Thanks.

Stéphane Charette

---

### Post by wavesound on 2008-11-12
Hi Guys
Thanks for this,  was driving me insane!!!
So simple to fix!!! :guitar:


Cheers
Bob

---

