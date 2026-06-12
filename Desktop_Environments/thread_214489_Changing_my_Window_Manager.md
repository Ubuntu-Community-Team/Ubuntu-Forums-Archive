---
title: "Changing my Window Manager?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by MikeMLP on 2006-07-12
I installed KDE from Ubuntu using apt-get install kubuntu-desktop.  I am now playing around with KDE, and enjoying it.  

I've noticed that I can enable transparancy effects or shadows, but there is no real effect (the buttons are pushed, but the actual shadow and transparency effects don't show up).  The tooltips say that these settings only work if using the Kwin Window manager.  

I have a funny suspicion that metacity is still being used, since I installed kubuntu over Ubuntu.  I would like to see what kind of eye candy KDE and its Kwin has to offer.  

Can anyone give me any information about how to find out for sure what window manager I'm using, and is it possible to change window managers as it is Desktop Environments (Could I use Kwin with my Kubuntu session and Metacity with my Ubuntu session?  If so, How?

Thanks!

---

### Post by Ctrl+Alt+Del on 2006-07-12
you should be using kwin if you selected kde as your session in gdm.
You can check if metacity is running by typing ps aux | grep metacity in a terminal

---

### Post by Jucato on 2006-07-12
You are using KWin by default when you log into a KDE session. The possible reasons you are probably not seeing any window transparencies/shadows could be:

1. you are not using 3d hardware acceleration, which means you are not using the latest driver for your video card

or

2. your Xorg is not configured to handle composites/translucencies/shadows. I forgot how to do this one. But I'm sure there's a guide here somewhere...

---

### Post by MikeMLP on 2006-07-12
I ran that from the terminal and got this:

```
 mike@Ubuntu:~$ ps aux | grep metacity
mike     15784  1.0  0.1   2876   796 pts/1    R+   18:48   0:00 grep metacity
 
```

Does this mean that metacity is in fact running (I am still very much a newbie ;) )?

---

### Post by jonrkc on 2006-07-12
> **MikeMLP said:**
> I ran that from the terminal and got this:

```
 mike@Ubuntu:~$ ps aux | grep metacity
mike     15784  1.0  0.1   2876   796 pts/1    R+   18:48   0:00 grep metacity
 
```

Does this mean that metacity is in fact running (I am still very much a newbie ;) )?
Nope, that means it isn't running.  What was returned was the line created by your request to find metacity.  It just means grep (the finding mechanism) looked for metacity--that was the last process that took place.

You can get the KDE "whole works" by swapping your gdm manager for the kdm one.  Since you've indicated you're not very familiar yet with getting around in files, etc., I'm not going to outline a way to do that here; but I suspect the Gnome control panel provides a way to change login managers.  Have a look there.  (I don't use Gnome, so I can't help you in the search.)

To enable transparency you have to see that your xorg.conf file has a section like this:

```

Section "Extensions"
   Option "Enable" "Composite"
EndSection

```

You also need to "comment out" the line that says "Load DRI" near the beginning of the file, if it's there.  That just means placing a "#" sign (without the quotes) in front of it.  In many languages the "#" sign is used to mean a comment that the program or script will ignore when it runs.

If you know how to back up your xorg.conf file (found in /etc/X11), you can do those things and if something goes wrong you can always restore the original file.

---

### Post by MikeMLP on 2006-07-12
jonrkc:

Thanks for the reply.  I changed the xorg config file per your instructions and then tried enabling the translucency and shadow effects, but a message came up explaining that the compositor crashed twice within a minute and that compositing would be disabled for the session.

I do have my restricted ATi driver (I was running XGL / Compiz for fun, on my Gnome session, but I found resizing windows on both vanilla Gnome and XGL Gnome very slow (moving them did seem faster using XGL though)  I am very pleased so far with the speed at which KDE runs, and I'm hoping to enable as much eye candy as possible while avoiding the sluggishness of Gnome)).

-As a side note, does anyone know why XGL / Compiz changes the Xorg configuration?  There are documented cases of it (myself included) changing the user's keyboard settings and, for me, it also messed up my custom mouse settings, killing X. (I thought it was what I added to the xorg.conf file to get the KDE effects working, but later found out that it was my messed up mouse configuration that was the cause).

Ok, end of OT tirade...
Any ideas to solve the crashing of composite effects? I suppose the easiest explaination is that it is "experimental" But why would it be included if it didn't work at all?  I'm sure some people have been able to get it working.

---

### Post by jonrkc on 2006-07-12
Compositing works for me with a cheap ASUS Nvidia GeForce2 MX4000 card on a cheap Gigabyte 2004 RZ motherboard.  I got the same crash message as you after I DISABLED compositing because I don't care for it.  So that suggests that you didn't get it enabled after all, OR your hardware doesn't support it OR your kernel doesn't support it.  

Did you make sure to comment out "Load   DRI" in xorg.conf?  

It's true that compositing is still experimental, but to my surprise it didn't crash, whereas it had under Hoary 5.04.  

There are many, many posts here and on LinuxQuestions.org concerning compositing and maybe one or more of them will give you the clue you need.

I didn't have any reconfiguring/messing up of mouse or keyboard from compositing enabling.

A side note, yes, KDE is much faster and works much better than even a year ago.  I believe the KDE people really do want to put out a useful and efficient product.  I used to sneer at it, but not now.

---

### Post by Jucato on 2006-07-12
I hope this HOWTO would help you. I'm just not sure how up-to-date it is.
[http://www.ubuntuforums.org/showthread.php?t=75527](http://www.ubuntuforums.org/showthread.php?t=75527)

---

### Post by RAOF on 2006-07-12
> **MikeMLP said:**
> ...
I do have my restricted ATi driver (I was running XGL / Compiz for fun, on my Gnome session, but I found resizing windows on both vanilla Gnome and XGL Gnome very slow (moving them did seem faster using XGL though)  I am very pleased so far with the speed at which KDE runs, and I'm hoping to enable as much eye candy as possible while avoiding the sluggishness of Gnome)).
...
Ba-baw!  The proprietry ATI driver is rubbish, from what I can tell (thankfully, I've got an nVidia card).  By enabling Composite (above), you've entirely disabled 3D acceleration - the driver only supports using exactly one of {Composite, 3D}.  It's probable that your crashes are due to the ATI driver.

The work around would be to use XGL in your KDE session - it provides Composite support **using** the 3D support, so you can have both :).  You'd do this using the same sort of tricks to get a Gnome XGL session (just without loading Compiz).

The reason why Composite is an option is that for many drivers it actually works.  The latest couple of proprietry nVidia drivers have run it very stably indeed, and open-source drivers can also handle it.  It just sucks that ATI produce rubbish linux drivers.

---

