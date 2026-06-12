---
title: "Can't set background after Natty upgrade"
date: 2011-04-19
forum: Desktop Environments
---

### Post by distobj on 2011-04-19
Hey everyone,

Since upgrading my former Karmic/Lucid/Maverick laptop to the Natty beta recently, I've been unable to change anything about my desktop background.  Each time I reboot, the background is a different solid color, but I can't change the color nor set a wallpaper image.  Here's what I've tried;

- "Appearance Preferences" -> "Background"
- the compiz wallpaper plugin
- gconftool-2/gconf-editor
- xsetroot

Any ideas?

Thanks.

---

### Post by freakengine on 2011-04-30
+1.  

Mine doesn't change colors but is stuck on the default desktop wallpaper.  In the appearance settings my wallpaper of choice is highlighted but it doesn't appear on the desktop.  This happens whether or not Unity is in use.

---

### Post by ankspo71 on 2011-04-30
Hi,
Have you checked to see if this is because of a permissions problem? It sounds like what it could be. Go to your home directory and make sure everything in your hidden ".gconf" directory is owned by you (not root). Also check the files and folders within that directory too.

**The graphical way:**
You can see the permissions by right clicking on any file or folder and select properties then go to the permissions tab.

However, to change the ownership permissions of those files you will have to run your file browser as root.
```
gksudo nautilus
```
then browse to 'filesystem' on the left, then /home/yourusername

You can change the permissions by right clicking on any file or folder and select properties then go to the permissions tab. Remember that if you are changing permissions to an entire directory, that you need to select "apply permissions to enclosed files".

**The command way:**
To check all files and folders in that directory, paste this command in the terminal:
```
ls -alR ~/.gconf | more
```
Use the enter button to see more results.

If anything aren't owned by you then you can use the chown command to gain ownership of the files and directories:
```
sudo chown -R yourusername:yourusername ~/.gconf
```

---

### Post by freakengine on 2011-04-30
Well, I was going to try your generous suggestions but now I can't get any file folders to open in either Unity or classic.  I think I have my own solution.  It's called going back to Maverick.  If I'd wanted a beta I'd have DL the beta.  Seriously.  I need my laptop to work.  I think I just jumped in too soon to see what Unity was all about.

BTW, my desktop wallpaper problem didn't exist for the first day of my upgrade.  It was a day or so later when it reared it's head.

---

### Post by ludovicc on 2011-04-30
Do you have an NVidia card? It's very likely that you have a bug with the proprietary driver - it happened to me. If so, try to open 'Additional drivers' and select NVidia accelerated driver (version 173), then reboot. This old version is a bit more stable and Unity works (but video with VLC fails for me). There is a bug opened for that issue, I hope that it will be solved soon enough.

Ludovic

---

### Post by zebrattt on 2011-04-30
> **ankspo71 said:**
> Hi,
Have you checked to see if this is because of a permissions problem? It sounds like what it could be. Go to your home directory and make sure everything in your hidden ".gconf" directory is owned by you (not root). Also check the files and folders within that directory too.

**The graphical way:**
You can see the permissions by right clicking on any file or folder and select properties then go to the permissions tab.

However, to change the ownership permissions of those files you will have to run your file browser as root.
```
gksudo nautilus
```
then browse to 'filesystem' on the left, then /home/yourusername

You can change the permissions by right clicking on any file or folder and select properties then go to the permissions tab. Remember that if you are changing permissions to an entire directory, that you need to select "apply permissions to enclosed files".

**The command way:**
To check all files and folders in that directory, paste this command in the terminal:
```
ls -alR ~/.gconf | more
```
Use the enter button to see more results.

If anything aren't owned by you then you can use the chown command to gain ownership of the files and directories:
```
sudo chown -R yourusername:yourusername ~/.gconf
```

I have the same problem.  I did this, and all the files are owned by myself (rather than root).

---

### Post by distobj on 2011-05-01
I have an ATI card, and just switched to fglrx to resolve another problem... but alas, still have the background issue.

One thing I noticed is that after using xsetroot (xsetroot -solid red), and then rebooting, for a brief moment during the shutdown process I do see a wall of red.  Also, the changing color I mentioned in my initial post was apparently attributable to my frequent attempts to change the background image. Now that I've stopped doing that, I'm stuck on green.

---

### Post by zebrattt on 2011-05-01
> **distobj said:**
> I have an ATI card, and just switched to fglrx to resolve another problem... but alas, still have the background issue.

One thing I noticed is that after using xsetroot (xsetroot -solid red), and then rebooting, for a brief moment during the shutdown process I do see a wall of red.  Also, the changing color I mentioned in my initial post was apparently attributable to my frequent attempts to change the background image. Now that I've stopped doing that, I'm stuck on green.


i also noticed a similar thing.  when I logout or shutdown, the background image I select does appear for a moment, which means I can "select" a background, but it can not be displayed.

---

### Post by harm82 on 2012-09-27
> **ankspo71 said:**
> Hi,
Have you checked to see if this is because of a permissions problem? It sounds like what it could be. Go to your home directory and make sure everything in your hidden ".gconf" directory is owned by you (not root). Also check the files and folders within that directory too.

**The graphical way:**
You can see the permissions by right clicking on any file or folder and select properties then go to the permissions tab.

However, to change the ownership permissions of those files you will have to run your file browser as root.
```
gksudo nautilus
```
then browse to 'filesystem' on the left, then /home/yourusername

You can change the permissions by right clicking on any file or folder and select properties then go to the permissions tab. Remember that if you are changing permissions to an entire directory, that you need to select "apply permissions to enclosed files".

**The command way:**
To check all files and folders in that directory, paste this command in the terminal:
```
ls -alR ~/.gconf | more
```
Use the enter button to see more results.

If anything aren't owned by you then you can use the chown command to gain ownership of the files and directories:
```
sudo chown -R yourusername:yourusername ~/.gconf
```

THANK YOU ankspo71! You solved my 6 months irritation today. Please buy yourself some cookies in my name!

---

