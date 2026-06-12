---
title: "xfce and themes"
date: 2006-01-17
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-17
I have installed xubuntu and use
xfce. If I go into synaptic and choose to install xfce themes I have to remove
a whole lot of files among xubuntu etc.

Why?

and another thing. If I get a error sound or anything while playing music trough xmms the
music dissapears for a long time.... is it a way to get around this?

A way to make it possible to play both music and listen to movies with sound at the same time is also
desired...

and last thing.
Howto make a screendump in xfce?

---

### Post by Joeb on 2006-01-17
I can answer your first question about the themes, but somebody else will need to tackle the others (or post them seperately).

I am assuming you added some repositories to install xubuntu.  As such, you have the xubuntu people's version of packages and Ubunutu's version of XFCE (you don't need xubuntu to install XFCE).

What is happening is that there are conflicts between the two different packages.  I believe that xubuntu has already installed the XFCE themes, but when you try and install the xfce-themes package from Ubuntu, it complains and says that it has to uninstall the other version, first.  Since, other xubuntu packages may depend on these, then, they too, are uninstalled, and so on and so on.

If you choose to use the xubuntu XFCE packages, then you should only use the xubuntu ones.  If you choose to use the Ubunutu XFCE packages, then likewise, you should only use those.  Otherwise, mixing packages from two different sources for the same application (even worse for the same desktop!) is problematic at best.

Hope that helps,

Joeb

ps.  for your sound question, you might post that under the Video and Sound hardware forum.  I don't believe it is specific to XFCE.

---

### Post by grumpymole on 2006-01-17
For screen capture, use an application called scrot (SCReen shOT).  It is a commandline app, but is easy to use.

> sudo apt-get install scrot

Then look at the man page for scrot.  If I remember, you run it from cmd line using a delay of a few seconds.  This gives you enough time to get the desktop to where you want it to be, and then it captures it to a jpg file.

Regards

Warren

---

### Post by j_monty10 on 2006-01-17
[QUOTE=syklitengutt]

and another thing. If I get a error sound or anything while playing music trough xmms the
music dissapears for a long time.... is it a way to get around this?

[/QUOTE]

Which sound system are you using?  ALSA, OSS or ARTS

---

### Post by Galoot on 2006-01-17
For screencaps I use GKrellShoot, a plugin for GKrellM. You can capture the desktop or any window, with or without the window frame, and also set a delay as with Scrot. I haven't tried it with video caps, though.

---

### Post by syklitengutt on 2006-01-18
tnx for replies... so if I boot up using gnome session,
remove all packages that came with xubuntu and then install
only xfce4 and its themes and extras I should be fine?

As for the sound and mixer in xfce I got the options to use mixer or mixer 1.
Im pretty shure im running alsa,
but entering the volume control it sais Device: /dev/mixer

---

### Post by Joeb on 2006-01-18
[QUOTE=syklitengutt]tnx for replies... so if I boot up using gnome session,
remove all packages that came with xubuntu and then install
only xfce4 and its themes and extras I should be fine?

As for the sound and mixer in xfce I got the options to use mixer or mixer 1.
Im pretty shure im running alsa,
but entering the volume control it sais Device: /dev/mixer[/QUOTE]


In a nutshell, almost.  Go into the Synaptic Package manager and tell it to search for everything XFCE related (in titles and description).  Then click on the installed ones and tell it to do a "complete" uninstall.  Then remove the source list you added for Xubuntu and then tell Synaptic to reload the package lists.  After that, you can search again for XFCE and then install any of the XFCE stuff you want.

That said, there is nothing wrong with the xubuntu version.  However, their goal is to make a system that uses XFCE and doesn't have any dependencies to gnome packages.  So as they go further along with their work, their is the potential of having more conflicts (unless the Ubuntu programmers agree to remove the dependencies from their builds).

As for your sound problem, I'm not a sound expert, but as long as you are booting back into gnome, check and see if the problem still exists.  If it does then it's not a XFCE problem, but a configuration or driver problem (sounds like you have to programs trying to hit the sound card at the same time and it's choking on it).

Anyway, enjoy XFCE.  It's a great lightweight window manager!

---

