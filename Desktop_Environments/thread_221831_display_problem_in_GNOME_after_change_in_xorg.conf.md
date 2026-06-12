---
title: "display problem in GNOME after change in xorg.conf"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Lievre on 2006-07-24
Hello, 
I have a problem with my Ubuntu installation.

I installed Dapper Drake a few days ago on my laptop Acer TM 8106, and everything worked fine. 
But, as I have a wide screen (1680x1050), I couldn't have that resolution "out of the box". I searched on the web, and I found the tool "915resolution", but I couldn't use it because my graphic card is ATI Radeon X700. So I found instructions to change the file /etc/X11/xorg.conf. 

I made changes in this file and since then, there is no display at all when GNOME starts. The computer starts correctly, and then, after the shell write "Starting GNOME Display Manager", the screen goes black. The jingle is playing, so I know that the login window is working but only the display is gone. If I type (blindly) my login and password, the opening jingle plays, so I'm pretty sure that GNOME is, in fact, working.

I tried:
- to modify again the xorg.conf file. I put back the original version that I had backuped. Nothing changes.
- to reinstall Ubuntu. Nothing changes
- to reinstall Ubuntu and formatting the root partition. Nothing changes.
- to erase the xorg.conf file, and the reinstall Ubuntu while formatting the root partition. Nothing changes.
- to do: **sudo dpkg-reconfigure xserver-xorg** to changes the settings in the xorg.conf file. It doesn't change the display problem
- to do: **sudo apt-get update gdm** to reinstall Gnome Display Manager. The problem is still there. 

I'm completely lost. I cannot get back to the original settings where I had a screen, even though the resolution was not perfect.  The computer keep going with a black screen in GNOME even though I erased the corrupted xorg.conf file.

Can someone help me to figure out what happens? Thank you very much!

---

### Post by master_b on 2006-07-24
had similar problem myself.

Hopefully you've only reconfigured xorg.conf once.

If so just rename /etc/X11/xorg.conf~ ( its an automatically created backup). When you reboot you'll be back where you were before reconfiguring xorg.conf.

If not, run the livecd and save a copy of its xorg.conf to /etc/X11/ on tour hard drive installation.

Make a copy of the working version and place it somewhere safe.

Hope this helped.

Bill

---

### Post by wieman01 on 2006-07-24
Jeee... That sounds odd. So you tried formatting the root partition and yet the problem prevails?

Now, not sure what's going on, but there is a chance that Gnome puts the X-settings somewhere else in the Home partition as well. As I am a KDE user, I am not familiar with Gnome. Could you - if you don't mind wasting another hour or so - format your entire harddisk including the home partition and reinstall Ubuntu?

I know this is not a very conservative approach, but if you have no personal files/settings on your computer, you couldn't care less, right?

---

### Post by wieman01 on 2006-07-24
> **master_b said:**
> had similar problem myself.

Hopefully you've only reconfigured xorg.conf once.

If so just rename /etc/X11/xorg.conf~ ( its an automatically created backup). When you reboot you'll be back where you were before reconfiguring xorg.conf.

If not, run the livecd and save a copy of its xorg.conf to /etc/X11/ on tour hard drive installation.

Make a copy of the working version and place it somewhere safe.

Hope this helped.

Bill

My suggestion only after you have tried Bill's approach! But I understood from your note that you have tried restoring the orginal "xorg.conf" file.

---

### Post by Lievre on 2006-07-24
Thank you for your answers,

Bill: 
OK, I will try to rename the file /etc/X11/xorg.conf~ but as I already restored a previous version several times (a backup that I made before to make changes in this file), I am not very optimistic.

Wieman:
In fact I have lots of personal data stored on another partition (would take me days to backup all), and another OS (Windows) on another one also, so reformatting the whole hard disk would be a really desperate solution... 
Is it a way to find out if Gnome has stored these X-settings elsewhere?

---

### Post by Lievre on 2006-07-24
And again:
the problem is, after reinstalling, changing the xorg.conf file, and so on, I open this file in the terminal, and, as far as I see, it is indeed exactly as it was after the first install, so I do not understand how the same file can produce different results? And it is the only file I edited...

---

### Post by wieman01 on 2006-07-24
> **Lievre said:**
> And again:
the problem is, after reinstalling, changing the xorg.conf file, and so on, I open this file in the terminal, and, as far as I see, it is indeed exactly as it was after the first install, so I do not understand how the same file can produce different results? And it is the only file I edited...

Well, ok, perhaps not the whole harddisk then. But could you format your "home" and "root" partition using Partition Magic or a similar Windows tool? Or simply use the format tool that comes along with the Live CD.

Just format/erase the Linux partitions using Windows... Problem is that you won't see them under Linux because they are EXT3 rather than NTFS/FAT32. So I recommend Partition Magic... That's what I used to use in such cases.

---

### Post by Lievre on 2006-07-24
Well, I did as you said: in Windows, with PartitionMagic, I formatted the root partition.
Then I reinstalled Ubuntu with the CD, and it works!!

Thank you very much. It seems that the Ubuntu installation procedure doesn't really format a partition when you ask to...

Now I'm back at the same place that I started, with my resolution still wrong, but now, I have a new problem, my touchpad is not working anymore:-k ... But that's another story... Thank you anyway!:-D

---

### Post by wieman01 on 2006-07-24
Welcome. :-) I had a similar problem before, so don't ask me why but something is wrong with the format tool when you use the Live CD/DVD. Glad this helped.

---

