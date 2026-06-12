---
title: "No GUI file explorer (Thunar) in 9.04"
date: 2009-06-02
forum: General Help
---

### Post by chipppy on 2009-06-02
**(SOLVED) big thanks to those that assisted me**I have bit of a silly one.

I did the 8.10-9.04 upgrade and I cannot find Thunar (the GUI file exploer thingy.

I use it heaps for moving files around and it just seems to have disappeared.

Anyone know how to get it back.  I have looked in the noraml add/remove programs and cannot find it.

Cheers
chipppy

---

### Post by chngr on 2009-06-02
I am not a profesional, but i recommend you to open a terminal.
Issue the followings.

```

apt-cache search thunar

```

You should see "thunar" or something similer to that. Then
type this command, which installs the software. 
```

sudo apt-get install thunar

```

I hope it works.

---

### Post by benj1 on 2009-06-02
are you using ubuntu or xubuntu ?
thunar is default for xubuntu, nautilus is default for ubuntu.

is it opening up files from the places menu that the problem?
are files displaying on the desktop?

---

### Post by merlinus on 2009-06-02
You can use Synaptic to get and install thunar.

---

### Post by chipppy on 2009-06-03
Good Afternoon

Thanks for the assistance, some answers to a few questions

I use both Mythbunut and Ubuntu on 2 seperate compluter, at home.  And XP and Vista computer at work and I regularly get mixed up.

So looking at an Ubuntu 9.04 machine only
Looked in Synaptic package manager, and found that Nautilis is installed.  Had a look around and couldnt find it anywhere.

It is being used as the access to home, videos, pictures, etc so it is there and working fine.

**So what I am trying to do it setup launchers on the desktop for the Video and Music folders. ** 
I opened the folders OK but I cannot figure out how to send a launcher for the folders to the desktop.  
Can anyone help me out please.
**How do I create launchers for the Video and Music folders on the desktop?**

Any and all assistance in getting this right is greatly appreciated

Cheers
chipppy

---

### Post by benj1 on 2009-06-03
if on the desktop
right click and 'create launcher'
if on the panel 
right click, add to panel, then custom application launcher.

then for the command add
'nautilus /path/to/file/to/open'

---

