---
title: "GEDITing root owned files?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by kkimmell on 2006-05-08
This must be simple but I can't find a thread covering it. I use joe for bash editing but I'm trying to figure out how to edit files using gedit.

If I open a root owned file from the file browser it's read only in gedit. So I figured launching via a terminal window with:

```
sudo gedit /etc/postfix/master.cf
```

would work but I get a "cannot open display" error. Is there a way to route that command to my gnome session? perhaps the problem here is that I'm on an NX session so I need to send it to whichever destop that is. How do I find out?

Thanks for any pointers.

-Kevin

---

### Post by exosyst on 2006-05-08
have you tried:
```

export DISPLAY=:0
sudo gedit /location/to/file

```
?

---

### Post by kkimmell on 2006-05-08
[QUOTE=exosyst]have you tried:
```

export DISPLAY=:0
sudo gedit /location/to/file

```
?[/QUOTE]

Yes and I get the cannot open display error.

Let me reiterate that I am freeNX'ing into the machine so my GNOME session probably isn't the 0th display. Is there a simple way to find out what display my freeNx'ed session is considered?

-K

---

### Post by MaX on 2006-05-08
```
gksu gedit /location/file/
```

---

### Post by tennvols_69 on 2006-05-08
or you can go to system tools run as differant user   then tyoe gedit in  that will allow you to use gedit as root.

---

### Post by kkimmell on 2006-05-08
[QUOTE=tennvols_69]or you can go to system tools run as differant user   then tyoe gedit in  that will allow you to use gedit as root.[/QUOTE]

That's great and it works. Now I don't suppose there's a way to make shortcuts or links that will launch an app with that permission? I'd basically like to be able to open a Gedit session with multiple tabs open with all of my key config files loaded.

In redhat I could open GEDIT and setup all of the tabs and then upon logout have Gnome save the settings. Then at next login it would open GEDIT with all of the tabs loaded...

I tried it here and I got a message saying that GEDIT doesn't support this so I'm thinking it's particular to UBUNTU, Debian, or this version of gnome? Anyhow, a shortcut to launch it would be even better.

Thanks,
Kevin

---

### Post by tennvols_69 on 2006-05-10
tbh im not sure if thats possible...new user but i will look into it for you.

---

