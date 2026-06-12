---
title: "Make a launcher go through terminal?"
date: 2009-03-15
forum: General Help
---

### Post by cereal killer on 2009-03-15
To make a long story short, I have to launch Skype as root through terminal with a specific command. I'm trying to add it as an icon to my AWN dock, but it won't work as a simple launcher icon (I'm guessing because of root).

Is there a way to add it to AWN, or at least make a proper script and place it on the desktop so I don't have to go through the terminal every time?

---

### Post by Altay_H on 2009-03-15
If you look at the Properties of the launcher in the dock it should show the command that it uses to launch. It's probably something like "skype". You should be able to change that to the special command you need to use from the terminal and it should work. For example, to launch it with super-user privileges you could change it to "gksudo skype".

I hope this answers your question.

---

### Post by cereal killer on 2009-03-15
> **Altay_H said:**
> If you look at the Properties of the launcher in the dock it should show the command that it uses to launch. It's probably something like "skype". You should be able to change that to the special command you need to use from the terminal and it should work. For example, to launch it with super-user privileges you could change it to "gksudo skype".

I hope this answers your question.

This was actually my attempt to fix it, but it doesn't launch. 

I think that when you run it as root and you're required to enter a password, AWN is helpless.

---

### Post by Altay_H on 2009-03-15
> **cereal killer said:**
> This was actually my attempt to fix it, but it doesn't launch.
Are you sure you have gksudo installed? Try running gksudo from the terminal to ensure that that's not the problem.

If that's not the problem I doubt I can help you. Perhaps there's someone else here who knows more about AWN...

---

### Post by SuperSonic4 on 2009-03-15
I always thought %u at the end opened it in a terminal

---

### Post by sisco311 on 2009-03-15
Running skype as root is a very bad idea.

Please share the full story with as, maybe 
we can help to fix your problem in a proper way. :)

---

### Post by cereal killer on 2009-03-15
> **sisco311 said:**
> Running skype as root is a very bad idea.

Please share the full story with as, maybe 
we can help to fix your problem in a proper way. :)

Well, I finally decided to switch over to the bugfest known as Intrepid. My webcam doesn't work with Skype anymore (worked in every previous version), so I found a command that somehow gets it to work.

sudo LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

When I put this line in the command line of any launcher, it doesn't work. 

So I wonder what the deal is...
.

---

### Post by cereal killer on 2009-03-16
Anyone have any ideas?

---

### Post by sisco311 on 2009-03-17
> **cereal killer said:**
> Anyone have any ideas?

try, the command without sudo:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

if it works create a script in /usr/bin
```
gksu gedit /usr/bin/skype2
```
> #!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and make it executable:
```
sudo chmod +x /usr/bin/skype2
```

use the skype2 command in the launcher.

---

### Post by cereal killer on 2009-03-17
This is the error I get when I put that command in without "sudo"

**ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.**

Skype then proceeds to open, but when I try to log in, it tells me, "Another Skype instance may exist." I definitely have no other Skype window open, I tried it seconds after turning on my PC.

With sudo it works fine.

Why is it a bad idea to open Skype with sudo? Security risk?

Thank you for your help!

---

### Post by cereal killer on 2009-03-25
Ok, I'm having a new problem. 

I can't even launch Skype without root. It keeps saying "Another Skype Instance May Exist"

---

### Post by gregbzh on 2009-04-13
> **sisco311 said:**
> try, the command without sudo:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

if it works create a script in /usr/bin
```
gksu gedit /usr/bin/skype2
```


and make it executable:
```
sudo chmod +x /usr/bin/skype2
```

use the skype2 command in the launcher.

Cheers.  This works for me.

---

### Post by ThomasU on 2009-04-29
Another way:
How to launch Skype + V4L2 directly from Gnome / Ubuntu Jaunty menus so that the webcam works:
Menu System --> Preferences --> Main Menu
In the window select Internet, then Skype
Click on [Properties] button
In Command enter:
bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'

---

### Post by benditoelqueviene on 2009-10-21
It doesn't work to me.  I have an Eye 110 Genius webcam and none of the scripts above work with Skype.  All of the give this answer:
```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: clase ELF errónea: ELFCLASS64
```
I guess it is because i don't have the right permissions but i don't know how to make it executable or usable for any user different to root.

Thanks if you can help...  Thanks any way.

---

### Post by siquad on 2010-02-07
The message:
object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

shows up when you try to load the 64bit version of the library with skype, as someone already mentioned, skype will only work with 32bit.
If your system is 64bit, then the library version under /usr/lib will be 64bit, if it's 32bit...
So to use the 32bit on 64bit system you'll have to specify /usr/lib32/.

---

### Post by realgt on 2011-05-19
> **ThomasU said:**
> Another way:
How to launch Skype + V4L2 directly from Gnome / Ubuntu Jaunty menus so that the webcam works:
Menu System --> Preferences --> Main Menu
In the window select Internet, then Skype
Click on [Properties] button
In Command enter:
bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'

THX this worked for me!

---

