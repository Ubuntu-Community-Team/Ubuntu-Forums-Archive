---
title: "Ubnutu Minimum Requirments"
date: 2006-09-28
forum: Desktop Environments
---

### Post by heydabop on 2006-09-28
What are the minimum requierments for Unbuntu? If I used alternate install disk, would it work on a computer with 300 mHz, 96 Mb RAM, 8Mb Video Card?

---

### Post by ingo on 2006-09-28
Yes, it would, but you really want more RAM. I'm running Xubuntu on an old ibm tp 600e (333 mHz, 160Mb RAM, no separate video card) and it works a treat even with OpenOffice (and freemind) :)

---

### Post by aysiu on 2006-09-28
You're going to be hurting on Ubuntu with only 96 MB of RAM.

Try [this minimal install guide](http://www.ubuntuforums.org/showthread.php?t=171203).

---

### Post by heydabop on 2006-09-28
I'm using Xubuntu now, but I'd really like Ubuntu, so I'll check out that install guide.

---

### Post by aysiu on 2006-09-28
> **heydabop said:**
> I'm using Xubuntu now, but I'd really like Ubuntu, so I'll check out that install guide.
Oh, you're using Xubuntu already? Forget the minimal install guide, then. The minimal install installs IceWM, not Gnome.

---

### Post by heydabop on 2006-09-28
One of the main things I want from Ubuntu is the gnome-games. I have another thread going on how to put the gnome-games on Xubuntu right now. You'd be suprised how hard it is. I still haven't figured it out and the thread is kind of dead.

---

### Post by aysiu on 2006-09-28
It's not as simple as just ```
sudo aptitude update
sudo aptitude install gnome-games
``` I guess...?

---

### Post by heydabop on 2006-09-28
Yea, I've been told that, but my computer doesn't have internet.

Wait, no one's told me to put aptitude, even when trying to install from the Ubuntu disk.

---

### Post by aysiu on 2006-09-28
I checked out your last thread--you don't have an internet connection--that's the problem.

You can't do it from the Desktop CD (also known as the "live CD"). You have to install it from the Alternate CD. Once you have the Alternate CD, these commands should install it for you: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo nano /etc/apt/sources.list
``` Save the empty file (Control-X, Y, Enter) ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install gnome-games
``` You will need either an internet connection or the Alternate CD, though.

I repeat: you cannot add packages from the Desktop (live) CD.

---

### Post by heydabop on 2006-09-28
OK, I can do that, I do have an internet connection on my family computer, which is the one I'm using to type this. Since it is the family computer I can't do what I want with it (like installing Ubuntu). So I put Xubuntu on my internet lacking computer. I'll download the alternate install and do what you said, hope it works.

---

### Post by aysiu on 2006-09-28
Actually, if the download of the Alternate CD takes too long, you could do this too (a bit more involved, but a **lot** faster):

1. Boot the **Xubuntu** Desktop CD on your family computer.

2. Paste these commands in the terminal: ```
sudo aptitude clean
sudo aptitude update
sudo aptitude install -d gnome-games
```

3. Copy everything out of the /var/cache/apt/archives folder to a USB drive or some other removable media (iPod, floppy disk).

4. Copy all of that stuff to the desktop of your Xubuntu (non-internet-connected) computer.

5. ```
cd ~/Desktop
sudo dpkg -i *.deb
```

Or, better yet, unplug your family computer from the internet temporarily, plug in your Xubuntu computer and install *gnome-games* using *aptitude* and then unplug your Xubuntu computer and plug your family computer back in again.

---

### Post by heydabop on 2006-09-29
Welll, I'm burning the Ubuntu alternate install CD as I type this. Wish I'd read the forum earlier. Could've saved a CD. also, I wouldn't have been able to hook mine up unless I wanted to move it through a few rooms, which my mom wouldn't let me do. Oh well.

---

### Post by heydabop on 2006-09-29
IT WORKED!!! Thank you sooo much. Now that I know I need the alternate CD it has opened up so much more for me. THANKS AGAIN!!

---

