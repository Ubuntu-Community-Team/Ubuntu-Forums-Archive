---
title: "display problem: wrong resolution and X11 can't detect display"
date: 2009-03-11
forum: Desktop Environments
---

### Post by davidshere on 2009-03-11
I set my screen resolution to some really high level and the screen went blank.  I forgot that Ubuntu doesn't allow you to confirm that you can see the new screen resolution before it permanently switches to it.

So I've done... probably way too much.

I copied an old version of my xorg.conf file over xorg.conf.  When I boot up it tells me I'm running in low graphics mode.  I say fine, go into screen resolution on the menu to change the screen resolution to the value I want.  It doesn't detect my displays, and says that everything else is fine.  But, when I reboot, same problem.  Low graphics mode.

So I uninstalled gdm and xserver-xorg.  "sudo aptitude purge gdm xserver-xorg"... Then reinstalled them.  Same problem.

Most of the write ups I see about "my screen resolution is screwed up" proudly proclaim to run "sudo dpkg-reconifigure xserver-xorg".  Problem is, when I do that it asks me a bunch of questions about my keyboard, then exits out, and I get no opportunity to do anything about the screen settings.

Any help would be greatly appreciated.  At this point it seems my only option is to wipe the hard drive and start over.  Somehow no matter what I do it seems to remember that I set the screen resolution really high, and uses that when I log in.

Any suggestions would be greatly appreciated.

EDIT: When I log in as a different user, I do not have this problem.  Is that a clue?

---

### Post by davidshere on 2009-03-11
If I could restore either my user account or x/gdm to its original state when it was installed/created, I would be willing to do that.

---

### Post by mhgsys on 2009-03-11
take a look at your xorg.conf 
in console:

```


sudo nano /etc/X11/xorg.conf


```

(or you can use vi / vim) 

and change your resolution back there, 

then restart X

```

sudo /etc/init.d/gdm restart

```

---

### Post by davidshere on 2009-03-12
> **mhgsys said:**
> take a look at your xorg.conf 
in console:

I made modifications there, restored backed up versions of that file, grabbed fresh copies from other machines, pretty much everything you can think of.  I still get blank screen with one user, and fine for everyone else.

Acutally, I removed, purged, and deleted the configuration files for gdm, gnome, ubuntu-desktop, and xserver-xorg... and then reinstalled each.   I copied X11 and gdm configuration files from other machines.  After I recovered from the mess that that created, still same problem.  Blank screen with one user and fine for all the others.

Eventually, after comparing my user files to other users on fresh machines, found the file ~/.config/monitors.xml.  For the user with the blank screen, it looked like this:

```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="default">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1024</width>
          <height>768</height>
          <rate>0</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA">
          <vendor>DEL</vendor>
          <product>0xa00b</product>
          <serial>0x3137574c</serial>
          <width>1600</width>
          <height>1280</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
      </output>
  </configuration>
</monitors>

```

Which, I beleive, sums up my problem.  The default monitor on the top had no specific display information (can't detect display) and the one on the bottom has the wrong resolution.  I removed the first entry and corrected the resolution on the bottom one.  Everything is fine now.

---

### Post by getsha on 2009-03-12
Hi , I have a similar problem .I was trying to use my tv-out and entirely replaced my xorg.conf file with a different one.

When I restarted my computer , the display doesn't come to my screen . The TV-out card too isn't working .

Can anyone please suggest , how am I to see the display.

---

### Post by gjoellee on 2009-03-12
Running xfix should give you back a working xorg. Read how to run xfix here: [http://kshoster.net/index.php?c=tuts/xfix](http://kshoster.net/index.php?c=tuts/xfix)

---

### Post by mhgsys on 2009-03-15
So, the ~/.config/monitors.xml was the problem.
Thnx for clearing that out, valuable information.

---

