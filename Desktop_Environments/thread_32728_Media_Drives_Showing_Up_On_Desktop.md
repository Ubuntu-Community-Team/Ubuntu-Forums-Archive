---
title: "Media Drives Showing Up On Desktop"
date: 2005-05-09
forum: Desktop Environments
---

### Post by AndyAWS on 2005-05-09
I've been running Ubuntu (Hoary) for about a month now, and using the UbuntuGuide I have my Windows system partition mounted read-only under /media/ and another partition (FAT32) which I use mainly for storage (mp3's, downloads...etc) also mounted under /media/. Yesterday when I started Ubuntu both of these partitions showed up on the Desktop (for the first time) and in the Menu under "Places", so I didn't have to navigate to 'Computer -> filesystem -> /media/' to access them.

What I would like to know is how do I get this to happen all of the time. I have no idea what caused them to show up yesterday, but they're gone again now, and it was very convenient to have the storage drive more easily accessable.

---

### Post by RadioImp on 2005-05-09
I don't use Gnome myself, so going to take a guess at this one from what I've heard and read with other people.

Is the gnome-volume-manager running? try 'ps aux | grep volume' in a console window to see.

I believe this is the program responsible for auto mounting of drives and desktop icons, though I may be wrong. If it's not running, try 'gnome-volume-manager&' to start it and then see what happens.

Hope this helps.

---

### Post by Sam on 2005-05-09
[QUOTE=AndyAWS]I've been running Ubuntu (Hoary) for about a month now, and using the UbuntuGuide I have my Windows system partition mounted read-only under /media/ and another partition (FAT32) which I use mainly for storage (mp3's, downloads...etc) also mounted under /media/. Yesterday when I started Ubuntu both of these partitions showed up on the Desktop (for the first time) and in the Menu under "Places", so I didn't have to navigate to 'Computer -> filesystem -> /media/' to access them.

What I would like to know is how do I get this to happen all of the time. I have no idea what caused them to show up yesterday, but they're gone again now, and it was very convenient to have the storage drive more easily accessable.[/QUOTE]
Just open gedit, then open the open dialog. You can drag 'n drop folders from the right to the left part of the window, then these folders will be available from the Places menu.

---

### Post by AndyAWS on 2005-05-09
Thanks for the help, I'll give it a try when I get home tonight.

Though I still have no idea why they spontaneously showed up on the desktop yesterday, then went away after the next reboot...

---

### Post by Alexander Kirillov on 2005-05-09
[QUOTE=AndyAWS]Thanks for the help, I'll give it a try when I get home tonight.

Though I still have no idea why they spontaneously showed up on the desktop yesterday, then went away after the next reboot...[/QUOTE]
They are supposed to show on the desktop all the time. What you see is likely a bug - a frequently reported one (you can search these forums for hal/dbus). It is known to developers, but, AFAIK, no solution yet exists. 

Just a quick check: type on command line 
sudo /etc/init.d/dbus-1 restart

Do the icons reappear?

---

### Post by AndyAWS on 2005-05-09
[QUOTE=Alexander Kirillov] Just a quick check: type on command line 
sudo /etc/init.d/dbus-1 restart

Do the icons reappear?[/QUOTE]

Yes they do. 

Thanks for the info,  that solves the 'appearing drives' mystery. 
As long as it doesn't cause any problems (and it doesn't appear to), I can live with it until it gets fixed.

---

### Post by titus1950 on 2005-05-09
Hi,I did this the newbie way,because I am,
1-I follow the Guide to mount my vfat partition.
2-I follow the guide to log in as root.
3-As root go to media and find your windows mounted partition,then right clic on it 
....Make Link, make one, Give all Permissions to it and leave it there.
4-Log in as user,as you normaly do,and go to Media,find the Link you just made and copy it to your Desktop,and now you can rename it or change the folder for an Icon...Etc,Etc .And when you boot ! IT WILL BE THERE FOR YOU.
That was my newbie Solution...hope will help somebody.
Good Luck.

---

### Post by stoneguy on 2005-05-09
As Alexander Kirillov pointed out, there are problems around gnome-volume-manager. See
[http://ubuntuforums.org/showthread.php?t=27087](http://ubuntuforums.org/showthread.php?t=27087)

---

### Post by titus1950 on 2005-05-09
Thanks for the link but it doesn't give a solution,I really hope the developers can find one soon,for now whoever wants Windows on his Desktop can have it,as I did. It just Works.......¡

---

