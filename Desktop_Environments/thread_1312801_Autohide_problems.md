---
title: "Autohide problems"
date: 2009-11-03
forum: Desktop Environments
---

### Post by Daniel Zi on 2009-11-03
Hi everone, first I moved the top task bar to the bottom so that the two task bars are right next to each other.

I right clicked to auto hide and now both bars merged to one and look empty - meaning they are blank: applications, places... are not there anymore.

Right clicking does'nt do anything, and neither does restart the computer.

Any one have any ideas?

thanks very much

---

### Post by xxsa on 2009-11-07
I'm having similar kind of problem.

Moved  top panel to bottom and set autohide on. After that I couldn't do anything.

I was able to move the mouse cursor but couldn't select anything, and keyboard didn't work. Restart didn't solve the problem.

So I started in recovery mode and manually edited file:
~/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml 

Removing options from following line:
<entry name="auto_hide" mtime="1257599460" schema="/schemas/apps/panel/toplevels/auto_hide" type="bool" value="true"/>

like this:
<entry name="auto_hide" mtime="1257599460" schema="/schemas/apps/panel/toplevels/auto_hide"/>

solved the problem.

This is just to recover from the situation. Doesn't solve the original problem.

I think there's a bug in panels implementation. Hope they get  it fixed, I'd also like to merge two panels together and use autohide to that merged panel.

---

### Post by xxsa on 2009-11-09
It seems like others are having the same problem (I got a private message asking more information on solving this).

Maybe somebody with more experience should comment on this. I'm also a noobie and my solution is just a dirty workaround.


Private messager asked about gtk error when changing the value. I don't know about that. 

Here's what I did in more detail:

Booted to recovery mode, opened the file with pico editor, removed unnecessary attributes and saved the file. Then I restarted and everything worked fine.

It could also be the case that you have  set both  bottom and top panel to autohide and you should change properties for both. Bottom panel properties are here:
~/.gconf/apps/panel/toplevels/bottom_panel_screen0/%gconf.xml

---

### Post by lapdog on 2009-11-12
> **xxsa said:**
> I'm having similar kind of problem.

Moved  top panel to bottom and set autohide on. After that I couldn't do anything.

I was able to move the mouse cursor but couldn't select anything, and keyboard didn't work. Restart didn't solve the problem.

So I started in recovery mode and manually edited file:
~/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml 

Removing options from following line:
<entry name="auto_hide" mtime="1257599460" schema="/schemas/apps/panel/toplevels/auto_hide" type="bool" value="true"/>

like this:
<entry name="auto_hide" mtime="1257599460" schema="/schemas/apps/panel/toplevels/auto_hide"/>

solved the problem.

This is just to recover from the situation. Doesn't solve the original problem.

I think there's a bug in panels implementation. Hope they get  it fixed, I'd also like to merge two panels together and use autohide to that merged panel.

Thanks for the recovery solution, xxsa!  That did it for me.  I was quite surprised as I was just going through basic Ubuntu documentation (of the Gnome desktop) and trying stuff out.  When I turned on Autohide, I found that the standard Gnome panels where not working at all.  (It's hard to get around X when your window manager breaks.)

xxsa, would you point me in the right direction as far as where to get detailed info on gnome config files, please?  I did a cursory look around, but, based on the number of directory levels to dig into to find the right XML file, I would have never found it without help or a detailed manual.

Daniel, xxsa:  Did either of you post this bug to Launchpad?  I did not see it.  I was going to if no one else is/had.  Such an environment crash seems important to note and fix.  (Logging in with Failsafe Gnome did not work either.)

Should this thread be in the Desktop Environments Forum?

---

### Post by xxsa on 2009-11-13
Hi lapdgog! I'm glad that my solution helped you :)

I don't know about any documentation describing gnome config file structure. I just searched manually and found that particular .xml file.

I didn't post this to Launchpad, I'm new to Linux and didn't know should I. If that's the case, it would be good if you could post it there.

And yes, Desktop Environments Forum could be better place to this thread.

---

### Post by lapdog on 2009-11-13
Ok, I'll make a bug report to Launchpad.

What Ubuntu version and video driver are you guys using?  (I suspect it might have to do with the video driver, but I could be wrong.)

I'm on Ubuntu 9.10 with nvidia 190.42.

I tried it on an old IBM with Ubuntu 9.04 and no proprietary drivers and Autohide seemed to work fine.

---

### Post by lapdog on 2009-11-13
Looks like someone else had this issue and reported it to Launchpad 21 hours ago:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/481643](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/481643)


Thanks for moving this to Desktop Environments forum.

---

### Post by lapdog on 2009-11-13
Forgot to mention:
Both of the standard Gnome panels on my desktop were at the *top* of the screen.

---

### Post by cmittle on 2009-11-15
> **xxsa said:**
> 

So I started in recovery mode and manually edited file:
~/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml 

Removing options from following line:
<entry name="auto_hide" mtime="1257599460" schema="/schemas/apps/panel/toplevels/auto_hide" type="bool" value="true"/>

like this:
<entry name="auto_hide" mtime="1257599460" schema="/schemas/apps/panel/toplevels/auto_hide"/>

solved the problem.


Thank you so much for this help. 

I moved my panel from the left side to the bottom and that broke it.  When I'd restart it was still broken I could see the panel was trying to show up on the bottom of the page, but I could not click on places/applications/system or anything, and when I right clicked I couldn't get any options that would allow me to put my panel back on the left side.  

I did exactly what you showed above and restarted gdm (sudo /etc/init.d/gdm restart) my panel showed up no problem.  Then I chose to move it back to the left side, and replaced the original options just like they were restarted gdm again and now it's back to its old self.

That's a silly way to break my desktop.  Also while this was happening logging into gnome I couldn't click on the desktop or anything.  Logging into failsafe gnome however I managed to create a launcher from which i could get into firefox and find this thread.  Then I created a launcher for the terminal to use to do the above steps.  This needs to be repaired!

---

### Post by bmuluu on 2009-11-25
> **xxsa said:**
> 

So I started in recovery mode and manually edited file:
~/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml 

Removing options from following line:
<entry name="auto_hide" mtime="1257599460" schema="/schemas/apps/panel/toplevels/auto_hide" type="bool" value="true"/>

like this:
<entry name="auto_hide" mtime="1257599460" schema="/schemas/apps/panel/toplevels/auto_hide"/>

solved the problem.


Thank you!

---

