---
title: "Where is desktop background directory ?"
date: 2011-03-25
forum: Desktop Environments
---

### Post by mrpenguin on 2011-03-25
I want to add and remove pictures to use as a background ... I know I can do this by right clicking on the desktop but I am looking for the actual file where the backgrounds are stored.

Is there a way to access this and not use the terminal ??

i am using Ubuntu 10.10 64bit

---

### Post by Krytarik on 2011-03-25
They are in "/usr/share/backgrounds".

If you are looking for the users desktop background "choice" file instead, it is "~/.gnome2/backgrounds.xml".

Greetings.

---

### Post by ChipOManiac on 2011-03-25
Do you mean the ones supplied with the os? In that case it's
/usr/share/backgrounds

---

### Post by mrpenguin on 2011-03-26
Great Thanks, found it .... now how do I delete the pictures already in there ? I need to be root but I know nothing about the terminal, is there a way to do it without the terminal ?

---

### Post by PCNetSpec on 2011-03-26
Easiest way is open nautillus as root...

open a terminal and enter:

```
gksudo nautilus
```

Now use the nautilus window that just opened to delete them
(be aware right clicking and selecting "Move to Wastebasket" will only send them to the root trash bin... if you want to fully delete them, highlight them and hit the **Shift+Delete **keys)

or delete them from the command line:

```
sudo rm /usr/share/backgrounds/<filename>
```

---

### Post by Krytarik on 2011-03-26
> **mrpenguin said:**
> Great Thanks, found it .... now how do I delete the pictures already in there ? I need to be root but I know nothing about the terminal, is there a way to do it without the terminal ?
- press Alt+F2
- enter
```
gksudo nautilus
```Also see this earlier thread:
[http://ubuntuforums.org/showthread.php?t=1712297](http://ubuntuforums.org/showthread.php?t=1712297)

Running 'sudo' graphically:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Viper92Z on 2011-03-26
Lunch Terminal and type:

```
gksudo nautilus
```

Then a window will show up, you can use it to explore folders, just delete whatever you want with that.

---

### Post by mrpenguin on 2011-03-26
Awesome ! Got it .......... thanks guys

---

### Post by jonbwilson on 2011-03-31
Follow up question to this. When I pull up the Appearance app to set themes, backgrounds, etc., I notice that any background I've previously added that wasn't originally included with the OS is gone, and I have to add it again. Is there any way to make those backgrounds "stick" in that selection window? I've tried copying the pictures into the usr/share/backgrounds, as well as the /.backgrounds folders, but that didn't work. Any ideas?

---

### Post by Krytarik on 2011-03-31
I know, I used to experience the same behaviour, until just now!!
That's really weird, maybe a recent update, or it returns just tomorrow. ;-)

I used to switch between the backgrounds located in my home directory, and they were always gone when I chose another one of them. And I believe to remember that I also tried it once in "/usr/share/backgrounds", out of annoyance about the repeated disappearence of my added backgrounds. And it also didn't work!

But if it stays like it is now, I'd be really glad!

Since I can't reproduce that behaviour at my system currently/anymore, I can only suggest to fiddle with manually editing "~/.gnome2/backgrounds.xml", right the same like I did, before I surprisingly noticed that it changed its behaviour.

---

### Post by jonbwilson on 2011-03-31
> **Krytarik said:**
> I know, I used to experience the same behaviour, until just now!!
That's really weird, maybe a recent update, or it returns just tomorrow. ;-)

I used to switch between the backgrounds located in my home directory, and they were always gone when I chose another one of them. And I believe to remember that I also tried it once in "/usr/share/backgrounds", out of annoyance about the repeated disappearence of my added backgrounds. And it also didn't work!

But if it stays like it is now, I'd be really glad!

Since I can't reproduce that behaviour at my system currently/anymore, I can only suggest to fiddle with manually editing "~/.gnome2/backgrounds.xml", right the same like I did, before I surprisingly noticed that it changed its behaviour.

This looks like it might be the ticket. Crossing fingers.

---

### Post by jonbwilson on 2011-03-31
> **jonbwilson said:**
> This looks like it might be the ticket. Crossing fingers.

Nope. I added one of the images to the .xml file and no cigar. I even rebooted to try to make it show up and it didn't work. It's not really that big of a deal. Just one of those annoying quirks. Oh well.

---

### Post by hictio on 2011-03-31
Check this [Karmic: System wide wallpaper for regular joes ](http://oesediez.blogspot.com/2010/02/karmic-system-wide-wallpaper-for.html), I've done that on Karmic, but perhaps it'll work for you.

---

### Post by jonbwilson on 2011-03-31
> **hictio said:**
> Check this [Karmic: System wide wallpaper for regular joes ](http://oesediez.blogspot.com/2010/02/karmic-system-wide-wallpaper-for.html), I've done that on Karmic, but perhaps it'll work for you.

Worked like a charm. Thanks for the link. Of course, I don't know that I'll ever change my background/theme away from the Elegant Gnome Pack (it's so damn sexy), so it might be moot at this point.

For those of you having this issue that are too lazy to click on a link and tinker on your own, just type this into a terminal:

```
gksu gedit /usr/share/gnome-background-properties/ubuntu-wallpapers.xml
```

That'll bring up the required xml file in your text editor with root privileges (you'll have to enter your password first). Then just mimic the tags for the other images and add your own. Make sure you know where the image you want to add is located e.g. /home/jon/.backgrounds or something similar.

---

### Post by Krytarik on 2011-03-31
Thanks for the feedback! However, my user's "backgrounds.xml" still works fine! :)

---

