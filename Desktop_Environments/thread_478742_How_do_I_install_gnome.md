---
title: "How do I install gnome"
date: 2007-06-19
forum: Desktop Environments
---

### Post by BCPower on 2007-06-19
Is gnome best for ubuntu?  

...or, what ever is best, how do I install and/or load up a desktop?  

It's been a while since I sat at a Linux prompt

---

### Post by llamakc on 2007-06-19
> **BCPower said:**
> Is gnome best for ubuntu?  

...or, what ever is best, how do I install and/or load up a desktop?  

It's been a while since I sat at a Linux prompt

If you used the Desktop iso to install from the LiveCD, you installed Gnome already. Otherwise, if you used the server iso you could install the entire Ubuntu/Gnome stuff with:

sudo apt-get install ubuntu-desktop

---

### Post by BCPower on 2007-06-19
Will that get me GNOME 2.18?

n/m - I see it on the installer.  
Thanks!

---

### Post by BCPower on 2007-06-19
Dang it.  I got an error during install that says, "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 

What should I do?

---

### Post by llamakc on 2007-06-19
Are you installing from the LiveCD or have you already installed Ubuntu's server version?

---

### Post by BCPower on 2007-06-19
I installed the server and then I did sudo apt-get install ubuntu-desktop.  That ran and I chose "No Configuration".  After that, I typed startx and the desktop came up.  

Can I configure all the server stuff from the desktop?

---

### Post by llamakc on 2007-06-19
Sure, if you're more comfortable using the console, start up gnome-terminal @ Applications | Accessories | Terminal.

Or you can still go back to the console with X & Gnome running by entering "ctrl-alt-F2" to get to the TTY2 console. To go back to X, you'd hit "ctrl-alt-F7".

---

### Post by BCPower on 2007-06-19
So, I'm working in X, not gnome?  How do I start gnome?

Sorry, I'm a newbie here.

---

### Post by llamakc on 2007-06-19
Did you install ubuntu-desktop? Do you have a menu and somewhere on that menu is "System". If you click SYSTEM |  ABOUT GNOME does it show up? That's Gnome.

Gnome is a Desktop Environment. It runs on top of Xorg, the windowing server that rests beneath Gnome. 

Why would you install the server version and then want to run something as heavy as Gnome?

You may want to do some reading up on Linux, X-Windows, and the various DE's and Window Managers (WM) to get a better grasp of what's what.

---

### Post by BCPower on 2007-06-19
I won't argue with the fact that I need to read more to get better acquainted.  It's been years since the last time I was a newbie.  

I do understand what you're saying.  Desktops are very taxing on a server.  I would certainly not run that in a production environment but I'm simply exploring everything at this point.  Eventually, I want to have a file/Samba/backup server, mail/DNS server and a couple of windows (and possibly an OS X workstation) to round out my network.  I like the idea of Windows-less servers.

I'm a graphics/multimedia person and I've always been attracted to Linux for performance reasons.  However, Adobe and some others don't seem to like linux as they haven't ported most software apps. over yet.  I'm also attracted to Linux for 3D modeling and rendering machines.

All that being said, I'm a right-brainer and the dang shell is somewhat intimidating.  

Thanks for all of your time and help.

Cheers,
Brian

---

### Post by llamakc on 2007-06-19
In that case, you can certainly find tools to help you config/admin the server stuff, but mostly you'll want to edit the files directly IMHO. Good luck.

---

### Post by bobpaul on 2007-06-19
One thing you might do is use freenx on your server. This will allow you to run your server without a graphical login, but from another machine on the network you could do a remote graphical login. The X server would only be taxing the system when your logged in remotely. There are NX clients for Linux, Windows, and MacOS, so you can do a remote login from just about any machine.

Also, instead of Gnome you might try Xfce4 instead of GNOME. install the xubuntu-desktop package (apt-get install xubuntu-desktop). If you decide to get rid of the gnome environment, follow that with (apt-get purge ubuntu-desktop)

Best of luck to you!

---

