---
title: "Nedit Won't Run"
date: 2006-06-24
forum: Desktop Environments
---

### Post by tcoyle on 2006-06-24
Hi,
I installed the packages for NEDIT but it won't run from the xterm. This is what I get:

Color name "black" is not defined
Color name "black" is not defined
NEdit: Color name black not in database
NEdit: Color name LemonChiffon1 not in database
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Serial number of failed request:  314
  Current serial number in output stream:  324

Any idea on how I can get Nedit to work on my system?

Thanks,

Tim

---

### Post by edgardz on 2006-07-05
Same prob here... I have the following message:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Serial number of failed request:  312
  Current serial number in output stream:  322

---

### Post by atoponce on 2006-07-05
[quote=tcoyle]Hi,
I installed the packages for NEDIT but it won't run from the xterm. This is what I get:

Color name "black" is not defined
Color name "black" is not defined
NEdit: Color name black not in database
NEdit: Color name LemonChiffon1 not in database
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Serial number of failed request:  314
  Current serial number in output stream:  324

Any idea on how I can get Nedit to work on my system?

Thanks,

Tim[/quote] Is there a specific reason for running NEdit?  I have used it, but [Cream]("http://cream.sourceforge.net/") (GUI front-end for Vim) is solid and contains more features.  Cream offers everything NEdit offers, and more.

BTW- I haven't tried running NEdit from Xterm.  I installed it just fine with:

```
sudo apt-get install nedit
``` 
and I was able to run it from the 'Alt F2' keyboard shortcut and from the Gnome terminal.

---

### Post by Jean-Daniel Tissot on 2006-10-27
> **edgardz said:**
> Same prob here... I have the following message:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Serial number of failed request:  312
  Current serial number in output stream:  322


As root create the file named NEdit in /etc/X11/app-defaults with that content:
*visualID: default

That's all

:( Bad idea all resources are gone 

A better try :
as root remove /etc/X11/app-defaults/NEdit if you create this file

add in ~/.Xdefaults
NEdit*visualID: default

---

### Post by cvmostert on 2006-10-31
> **Jean-Daniel Tissot said:**
> 
A better try :
as root remove /etc/X11/app-defaults/NEdit if you create this file

add in ~/.Xdefaults
NEdit*visualID: default

And where do i find the .Xdefaults file.. or should i create it?

---

### Post by Jean-Daniel Tissot on 2006-11-04
> **cvmostert said:**
> And where do i find the .Xdefaults file.. or should i create it?

You must create it (if it not exits) in your home directory with you preferred plain ascii text editor.
This file is read when your session is started.
You can test the effect with the command:
xrdb -merge ~/.Xdefaults

---

### Post by ebash on 2006-11-07
Another work around is to set the environment variable XLIB_SKIP_ARGB_VISUALS to 1 before starting nedit.

```
XLIB_SKIP_ARGB_VISUALS=1 nedit
```

The problem with this approaches (adding an environment variable or modifiying ~/.Xdefaults is that it needs to be done for all users).

I have created a custom package of nedit that sets the environment variable from within the nedit executable. This has the advantage that the environment variable will affect only nedit and that all users will be able to benefit from it.

My version of nedit is available here at this repository:

```
deb http://debian.potyl.com/ edgy main
```

---

### Post by ThomasU on 2006-11-07
To start Oslo (otherwise it instantaneously dies):
XLIB_SKIP_ARGB_VISUALS=1 /opt/osloedu/oslo

---

### Post by tallman9 on 2007-02-26
Is there a way to do a symbolic link...? so that when I would enter command "nedit" it would execute "XLIB_SKIP_ARGB_VISUALS=1 nedit"  ???
I'm using icewm and I can't make a shortcut to "XLIB_SKIP_ARGB_VISUALS=1 nedit" =(

---

### Post by gnack on 2007-02-27
> **tallman9 said:**
> Is there a way to do a symbolic link...? so that when I would enter command "nedit" it would execute "XLIB_SKIP_ARGB_VISUALS=1 nedit"  ???
I'm using icewm and I can't make a shortcut to "XLIB_SKIP_ARGB_VISUALS=1 nedit" =(

Yes, in bash:

alias nedit='XLIB_SKIP_ARGB_VISUALS=1 nedit'

Add this to your .basrhc file (in your home directory).

---

### Post by tallman9 on 2007-03-10
thanks :)

---

