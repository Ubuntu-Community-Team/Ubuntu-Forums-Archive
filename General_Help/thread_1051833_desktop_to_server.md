---
title: "desktop to server?"
date: 2009-01-27
forum: General Help
---

### Post by dxlwebs on 2009-01-27
hey all,

currently im running a ubuntu desktop pc as my server which is working great apart from everytime i go to bed 99% of the time whilst im a sleep it will freeze and im sure its an overload error

so i thought that maybe the server version would work better! is that right!

also would it be possible toupgrade from desktop to server with out losing anything!

and how much harder is it to install everything on a server version than a desktop version?

thanks for your help!

---

### Post by mb_webguy on 2009-01-27
Actually, I believe that going from desktop to server would be more accurately a downgrade, since the server version doesn't use a desktop environment, and is entirely command-line.  And you would likewise obviously not have any of the GUI applications that require X.

If it's simply a matter of not having enough resources, you can always go to the Options at the login window and select a terminal session.  That's close to what you would get with a server install, anyway, but you'd have the option to log into Gnome.

EDIT:  As far as installing things on the server...  You're still using the same repositories.  Anything you can install on a server you can install on a desktop.  I personally have my laptop set up as a LAMP server for web development on the go.  I also have a UPnP mediaserver set up on the same laptop, so I can transfer files to my PS3.  With a server, you'd be doing the same, just from the command line.

---

### Post by dxlwebs on 2009-01-29
so realy i would have to do a new install if i wanted the server edition because i run a lot of sites of this server and i really believe it doesnt have enough resorces 

my pc is 1 gb ram 32 mb graphics card pentium 3 proccesor and i run about 6 sites and 3 or 4 of them are forums!

---

### Post by hyper_ch on 2009-01-29
> **mb_webguy said:**
> Actually, I believe that going from desktop to server would be more accurately a downgrade, since the server version doesn't use a desktop environment, and is entirely command-line.

and why would that be a downgrade?

> **dxlwebs said:**
> so realy i would have to do a new install if i wanted the server edition because i run a lot of sites of this server and i really believe it doesnt have enough resorces
Not really, disable X from starting and install the server kernel and use that to boot from by default.

---

### Post by dxlwebs on 2009-01-29
howwouldi disable X from starting and install the server kernals i already have apache2 and everything installed for the server side!

---

### Post by hyper_ch on 2009-01-29
remove gdm/kdm/xdm from the runlevels and well, install the server kernel instead... you can install it like any other software.

---

### Post by jerome1232 on 2009-01-29
I'm just re-enforcing what hyper-ch said.

I would definitely install the server kernel and if not switch to running in a command line only, at least go for a much lighter window manager, like icewm, fluxbox, openbox etc...

as for getting x to not run at startup I think this will do it [http://ubuntuforums.org/showthread.php?t=141071](http://ubuntuforums.org/showthread.php?t=141071)

after you log in and you wanted to start x up for whatever reason just issue the command
```
startx
```

xorg is a resource hog :) And the server kernel is optimized for it's job.

---

### Post by dxlwebs on 2009-01-29
thanks for the link ill use that tonnight and see what happens 

erm where do i find the server kernals? and what do they do that i haven already installed?

---

### Post by geirha on 2009-01-29
I don't think the server kernel will give much of a performance boost. You'll probably be fine with just using the kernel you are using now, just without running X, but it doesn't hurt to try. Install the package [linux-image-server](apt:linux-image-server), which will install the latest server kernel.

The kernel you are currently using will still be available from the boot menu, so you can easily switch back if it doesn't work properly.

---

### Post by dxlwebs on 2009-01-29
ok thank you

---

