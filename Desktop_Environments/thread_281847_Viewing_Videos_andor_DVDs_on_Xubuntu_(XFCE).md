---
title: "Viewing Videos and/or DVDs on Xubuntu (XFCE)"
date: 2006-10-21
forum: Desktop Environments
---

### Post by TiredBird on 2006-10-21
I was using VLC on Xubuntu for viewing DVDs, files containing similar content and video files. I went 100% xfce, [ ]("http://www.psychocats.net/ubuntu/purexfce") and my VLC disappeared. Is there something I should be using instead or do I need to reload VLC?

---

### Post by john.nicholls on 2006-10-22
Using Xfce 4.4, all I had to do to play a DVD in VLC was to go to File | Open  Disc and enter the Device Name (in my case /cdrom).

John

---

### Post by TiredBird on 2006-10-23
Okay, I reloaded it and all its dependancies, (about 33 MB worth). I haven't tried it with an actual DVD yet but I did try it with a file copy I made of a DVD. A file copy of a DVD, in case you are not aware, consists of a folder containing two other folders, one of which contains around 6 individual files. In Gnome I was able to select the outer folder and it would play the whole DVD. XFCE forced me go down to the raw file level so it will only play about 30 minutes at a time. Then it stops and I have to select the next segment. Do you know anyway I can get it to play the whole movie?

---

### Post by json684 on 2006-10-23
Did you use the option, Open Folder? I use that when I am opening a ripped DVD. Then you just point it at the folder containing the Video_ts and audio_(something) and open. Otherwise, I'm not really sure.

---

### Post by TiredBird on 2006-10-23
It took me a while to find it. On my system I found it as 'open directory' on the VLC menu. It works, thanks much, but now I have another problem. How do I stop the movie. Right now I have two of them running, (the sound at least), and I have teminated VLC. It is not visible, it is not on the task bar or any of my desktops but I am still getting the sound from two movies I started. How do I stop them short of a reboot?

---

### Post by skymt on 2006-10-23
> **TiredBird said:**
> It took me a while to find it. On my system I found it as 'open directory' on the VLC menu. It works, thanks much, but now I have another problem. How do I stop the movie. Right now I have two of them running, (the sound at least), and I have teminated VLC. It is not visible, it is not on the task bar or any of my desktops but I am still getting the sound from two movies I started. How do I stop them short of a reboot?

That's a common bug in VLC. I run into it all the time. Use "killall vlc", or use the XFCE task manager to kill it.

I usually run VLC from a terminal, so I can just hit control-C to kill it if that bug appears.

---

### Post by TiredBird on 2006-10-23
I'm beginning to feel really stupid because I'm having so many troubles. But now I have another one. I'm trying to play a real DVD, (The Hunt for Red October), but I can't get it to start. 

The cd is in my cd-rom drive and it shows up on my desktop so I have to assume the system is recognizing it.

I start the program by clicking on it on the task bar which issues the command, 'vlc'.

The program starts in small form.

On its menu system I use File -> Open disc...

On the open... dialog box I select the tab 'Disc' and choose the disc type as 'DVD (menus)'.

I enter /dev/cdrom in the device box and leave the other boxes as is.

I click on OK but instead of playing the DVD it all disappears.

It works okay on my Ubuntu partition with the Gnome desktop. What is keeping it from working on the XFCE desktop?

---

### Post by TiredBird on 2006-10-23
I just tried running it from the command line to see what kind of messages I was getting. It has a bunch of stuff about region one encoding and a file missing from my home directory. I'm going to look at my other installation, the one that works, and see what I'm missing. Hopefully I will figure it out.

---

### Post by skymt on 2006-10-23
> **TiredBird said:**
> I just tried running it from the command line to see what kind of messages I was getting. It has a bunch of stuff about region one encoding and a file missing from my home directory. I'm going to look at my other installation, the one that works, and see what I'm missing. Hopefully I will figure it out.

What stuff does it print? And do you have libdvdread and libdvdcss?

---

### Post by TiredBird on 2006-10-23
It was 'libdvdcss' that I was missing. Somehow, it did not get installed in my new system or I wiped it out when I tried to reduce to 100% xfce. Anyway, I loaded 'libdvdcss2' from the repository and now it works. Thanks for your help.

---

### Post by TiredBird on 2006-10-23
More along the same vein...

Now that I have it pretty much working I would like to get VLC to start automatically and play the dvd when I insert it. 

Question: is there something already in the udev rules files that is trying to start something I don't have installed, like totem, and can I just modify that to use VLC instead or do I have to write a special rule for VLC. (I'm assuming that 'udev' is where I need to be looking.

---

### Post by TiredBird on 2006-10-23
I have just run 'udevmonitor' to see what it knows about my dvd but I insert the dvd or take it out and 'udevmonitor' doesn't do anything. I must be looking in the wrong place. Any ideas?

---

### Post by skymt on 2006-10-23
udev doesn't do anything about launching applications in response to events. In Gnome, the program responsible for that sort of thing is gnome-volume-manager. I don't have XFCE installed right now, so I don't know what it would use. You may want to just install gnome-volume-manager. It requires some Gnome libs, though.

---

### Post by TiredBird on 2006-10-23
I'm using udev rules to cause the decryption and mounting of certain filesystems when certain conditions are met by USB plugins. I assume there has to be something similar that triggers events when a DVD is inserted. (It puts the name of it on my desktop so something is noticing that I inserted it.)

Do you know how programs like 'totem' get started automatically on insertion of a DVD?

In the meantime, I got VLC to start and automatically play the contents of a video folder I click on. (The folder has to contain video type files or it doesn't work.)

Now if I can just get automatic startup with insertion of a DVD I'll be in hog heaven.

---

### Post by skymt on 2006-10-24
udev isn't designed for this sort of thing. This is the job of [HAL](http://freedesktop.org/wiki/Software_2fhal), along with a daemon watching it for events. The only HAL-watching daemon I know of that meets your needs is unfortunately gnome-volume-manager (or the KDE equivalent).

---

### Post by TiredBird on 2006-10-24
I guess it is HAL I need to be looking at in order to base automatic actions on DVD or CD insertion. 

I have several USB devices, (thumb-drives, external drives, etc.), which through rules I wrote for udev, cause the execution of various scripts, (actually batches of commands), depending on the serial number of USB devices plugged in or found at boot-up. I was hoping I could do something like that with DVDs and/or CDs but if it doesn't exist, it doesn't exist. I guess I need to learn more about HAL.

Can you point me to a document or documents that will explain HAL for me. I know it stands for Hardware Abstraction Layer but I don't know much else. I really need a ground up explanation before I attempt to use it. 

Thanks for all of your help.

---

### Post by skymt on 2006-10-24
I already linked you to the best resource I know of: the official HAL page on freedesktop.org. Read up on it there.

It's not designed to be used directly by the user. It's more of a resource for other programs to use. You can probably come up with something that will do what you want using Python and the dbus module. The script would basically sit in the background waiting for HAL to tell it about a DVD, then it would run VLC. That's basically what gnome-velume-manager does.

I don't think there's a way to access DBUS from the shell, so a shell script won't do the job.

---

### Post by TiredBird on 2006-10-24
Sorry, I didn't notice the link in your earlier post. Thanks for all the time you've spent on this.

---

### Post by skymt on 2006-10-24
> **TiredBird said:**
> Sorry, I didn't notice the link in your earlier post. Thanks for all the time you've spent on this.

No problem, that's why I come here. I like helping people, because I like to be helped. Golden rule, and all that.  ;) 

If you come up with a usable solution using Python, make sure to post it so the community can hack on it. You've found a real need: a cross-desktop volume autodetector. A lot of people are using Gnome or KDE who would use something lighter if they could just keep autoplay functionality.

---

### Post by TiredBird on 2006-10-24
I've never used Python and I have an aversion to programming, (from having done too much of it), so it probably won't happen. 

Everything I've done so far, the udev rules and the scripts that go with them, don't involve any programming and I would like to keep it that way. A lot of what I'm already doing involves encryption and decryption using TrueCrypt, but even with that I'm just using the pre-compiled binary. 

I don't get source for anything and I don't have any development tools. I'd like to keep it that way. However, if I do get something working I'll be sure to post it. 

I too help as much as I can with my limited knowledge because I appreciate the help I get.

Actually, part of the above is a lie. I have done some programming for my personal use. I have a rather extensive application that runs on a personal web server to catalog my dvd's. It's a blend of http, mysql, php and xml but no python. (It also doesn't use cookies or javascript as I consider both an invasion of privacy.)

---

### Post by redcharlie on 2007-07-18
xfce has autoplay ability built in the file manager, thunar.
It's not obvious.

see [http://thunar.xfce.org/documentation/C/using-removable-media.html]("http://thunar.xfce.org/documentation/C/using-removable-media.html")

---

