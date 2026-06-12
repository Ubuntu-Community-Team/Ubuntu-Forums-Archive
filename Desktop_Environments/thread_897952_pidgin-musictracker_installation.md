---
title: "pidgin-musictracker installation"
date: 2008-08-22
forum: Desktop Environments
---

### Post by anlag on 2008-08-22
I don't know if I'm missing something very simple here, but I cannot get the pidgin-musictracker plugin to show up in my Pidgin plugins interface.

I've just updated to Pidgin 2.5.0, installing it from source. For the musictracker plugin, I've tried:

1. Installing from repositories with 'sudo apt-get install pidgin-musictracker', which supposedly should simply make it appear in Pidgin. It doesn't, tried restarting, no go.

2. Downloading the 'Linux plugin binary' from the project website:

[http://code.google.com/p/pidgin-musictracker/downloads/list](http://code.google.com/p/pidgin-musictracker/downloads/list)

It's a bz2 archive, containing a .so file which I don't know how to use. Following some research, I've tried placing it in ~/.purple/plugins (which I had to create) and in /usr/local/lib/pidgin - which already contains similar files. No go. Worth noting though, is that in the latter directory, every .so file also has an .la file with the same root filename. Should I get such a file for this plugin? Where?

3. Installing from source. Checked out the code with svn, but it doesn't even contain a configure script. Had a go with autoconf to make one from the configure.ac but it just spat out a line of error messages.


This all really shouldn't be this complicated, so I'm assuming I've missed something obvious. Could someone please enlighten me before I break things?

---

### Post by anlag on 2008-08-23
In the end, after fiddling around for a lengthy time, it seems the method of getting the plugin binary and putting it in ~/.purple/plugins is what worked. Don't ask me how, I doubt I could reproduce whatever I did to get it working, but the latest things I tried was installing xmms2 development packages (latest, from website, not the old stuff in regular repositories.) Don't think that really did it. I simply have no idea. Hope that helps. :D

---

### Post by norbert79 on 2008-09-10
Hello there!

Same goes for me, but now with 2.5.1. Installed using FC7 binaries, alien for Gutsy. Got the Linux binary plugin, did both tries /usr/lib/pidgin and ~/.purple/plugins, no go on both.
I have no idea where I am wrong, but does anyone have an idea what I have missed?

---

### Post by Sarmacid on 2008-10-02
I'm running Hardy Heron and was able to get the plugin working installing it with Synaptic.

Last time I booted, I opened amarok and pidgin at the same time. I got an error with something about dcop in amarok and for some reason musictracker started making pidgin freeze, even if I killed pidgin and tried opening it again or restarted the pc. Had to disable/re-enable the musictracker(Very fast cause pidgin was freezing in just some seconds) it and it's all good now.

---

