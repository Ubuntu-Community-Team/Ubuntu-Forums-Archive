---
title: "Resolution too high for login screen?"
date: 2005-12-21
forum: Desktop Environments
---

### Post by Maelgwyn on 2005-12-21
When I get to the login screen when I've turned my Ubuntu box on, I have all these really ugly lines, and it's because the resolution is too high. 

I know that's the reason because the lines went away when I changed my desktop's resolution to 1024x768... How do I change the resolution for the login screen, or is there another way to fix this? :rolleyes:

---

### Post by schilcha on 2005-12-21
Had a similar problem when I entered 1600x1200, which can't be handled by my monitor. What I did was:
*)Press CTRL+ALT+F1 to get to a text-terminal
*)BACKUP /etc/X11/xorg.conf (i.e. cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup)
*)edit /etc/X11/xorg.conf
--> locate lines containing your resultion
--> substitute with a proper one or delete it, if more resulutions have been entered
*) restart X (/etc/init.d/gdm restart)

Here is a part of my xorg.conf, to which I applied the changes:
> 
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 Go]"
        Monitor         "Acer Travelmate 630C"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x1024" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x1024" "1024x768"
        EndSubSection
        *[...]*
EndSection


In case things are screwed up even more, just fall back to the original xorg.conf...

Good Luck!

---

### Post by Maelgwyn on 2005-12-23
I don't have an xorg.conf...

I tried to 
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

and was told it didn't exist...

So I tried to
```

find xorg.conf

```


and again it didn't find a thing... :S

---

### Post by The Warlock on 2005-12-23
[QUOTE=Maelgwyn]I don't have an xorg.conf...

I tried to 
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

and was told it didn't exist...

So I tried to
```

find xorg.conf

```


and again it didn't find a thing... :S[/QUOTE]
First off, that's not the way to use find, but that's not the important thing here. 

It seems impossible that you don't have an xorg.conf. Type ```
ls /etc/X11/
``` and tell us what it says. Don't forget that ext3fs is case-sensitive!

---

### Post by Maelgwyn on 2005-12-24
heh sorry, there's the problem:

x11 rather than X11

:oops:

---

### Post by Maelgwyn on 2005-12-24
ok, I've tried to **kate** /etc/X11/xorg.conf but I get the following error:

```

Error: "/var/tmp/kdecache-nik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
nik@quark:~$

```

is there a way to kill kate :???:  and then revive her so I can edit this file?

---

### Post by Maelgwyn on 2005-12-24
I've figured out what that error message means..

It's an ownership thing right? Kubuntu doesn't like me running Kate as root, does it?

if I just run it normally:

kate /etc/X11/xorg.conf

then I can't save the file once I've edited it... :confused:

---

### Post by dcstar on 2005-12-24
[QUOTE=Maelgwyn]I've figured out what that error message means..

It's an ownership thing right? Kubuntu doesn't like me running Kate as root, does it?

if I just run it normally:

kate /etc/X11/xorg.conf

then I can't save the file once I've edited it... :confused:[/QUOTE]
Save the file to your home directory, then as root move it to where you want it.

---

### Post by infoseeker on 2005-12-24
Do------>

sudo gedit /etc/X11/xorg.conf

---

### Post by Maelgwyn on 2005-12-24
Fixed - I used nano :D

---

