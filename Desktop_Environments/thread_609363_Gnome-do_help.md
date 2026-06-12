---
title: "Gnome-do help"
date: 2007-11-10
forum: Desktop Environments
---

### Post by trash on 2007-11-10
I can't get the addins working and there is some strange behaviour with Opera and Gnome-do icons in AWN... for example the opera icon will disappear and gnome-do will minimize and refocus opera.. it's bizar!

EDIT: it just happened again, the opera notification icon in AWN just disappeared, opera is still running and the gnome-do icon now does what the opera notification icon used to do, it has completely taken over what the opera icon did. If i close opera, the gnome-do icon reverts back to being gnome-do.

Gnome-do can be found here [https://launchpad.net/gc](https://launchpad.net/gc)
very cool little app!

---

### Post by davidsiegel on 2007-11-12
I think this is an AWN issue - the strange icon weirdness.

To get addins to work, you need to have a directory called ~/.do/addins. If it doesn't exist, create it. Place your addins in that directory (Pidgin.dll, Rhythmbox.dll, etc.) Now, quit GNOME Do if it's running because Do loads addins on startup right now. If none of this works, your version of Do might just be too old. Use Do from this PPA archive:

> Packages
=========
Do packages are currently available through a Launchpad PPA. These packages are from the still-in-development codebase and, like the project, are potentially unstable. Please make sure to provide feedback on packages to the mailing list.
 To use the packages from the PPA, add the following lines to your /etc/apt/sources.list file:
 deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
 and install GNOME Do with the command: sudo apt-get update && sudo apt-get install gnome-do.


---

### Post by trash on 2007-11-12
it was an older package I had so I upgraded but it's not working either:(.
I'm also getting more Opera weirdness but this time it seems unrelated to Gnome-do. Opera is either stuck in maximized mode or completely mininized... so i'l get back to gnome-do after i get Opera under control again lol.
Thanks!

---

### Post by trash on 2007-11-14
k everything seems to be back to 'normal'... I installed the newer packages an created the ~/.do/addins folder, downloaded the plugins and restarted Gnome-do but no joy.

The plugin properties say to open with Wine(I guess because thay are .dll's).... what else can I try?

---

### Post by davidsiegel on 2007-11-14
Please start gnome-do from the command line and paste the output here. Also paste the output of `ls ~/.do/addins'

---

### Post by trash on 2007-11-14
seems ok... EDIT: when i type in a contact name i don't get any options for pidgin

kenji@kenji-laptop:~$ gnome-do
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Applications" Item Source.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Define" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Directory Scanner" Item Source.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Firefox Bookmarks" Item Source.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Open" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Open URL" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Recent Files" Item Source.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Run" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Run in Shell" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "GNOME Special Locations" Item Source.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Email" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Open Terminal Here" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Chat" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Pidgin Buddies" Item Source.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Rhythmbox Music Jukebox Actions" Item Source.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Play" Command.
14/11/2007 2:25:52 PM [Info]: Successfully loaded "Rhythmbox Music" Item Source.
14/11/2007 2:25:52 PM [Info]: Binding key '<Super>space' for '/apps/gnome-do/preferences/key_binding'

(Do:9074): Gtk-CRITICAL **: gtk_label_set_label: assertion `str != NULL' failed
kenji@kenji-laptop:~$ ls ~/.do/addins
Pidgin.dll  Rhythmbox.dll

---

### Post by davidsiegel on 2007-11-14
Everything is as it should be - do you have AIM and Jabber screen names in your buddy list? Do you have music in rhythmbox? What happens if you type "play"?

---

### Post by trash on 2007-11-14
it doesn't find any yahoo contacts, nope i don't have any aim or jabber contacts.

it doesn't find any music however play will open rhythmbox and play.

---

### Post by davidsiegel on 2007-11-14
Well, the Pidgin plugin only supports AIM and Jabber right now because that's all I use :) Rhythmbox should work well, though. Make sure you have music imported, I guess.

---

### Post by trash on 2007-11-14
OH hahaha, I guess it works just fine then:lolflag:

Really great work so far David, I will be looking forward to the next release!
Cheers

---

### Post by thecapuchin on 2007-12-12
I've just found Gnome-do this evening and it looks like a great little application.

However I have not been able to get it to do a couple things which seem like it should be able to:

A)  While I can get it to bring up Pidgin in the window I am unable to use it to send messages to my Jabber/AIM contacts when I hit the down arrow I'm prompted with a list of what looks like all of the shell scripts and bookmarks I have but no option for IM.

B)  Is there a way to be able to execute shell scripts through the Gnome-Do interface?  So far all that has happened any time I try one is that the file is opened in Gedit for viewing rather than actually executing the file.

C) When I type "Run" two things show in the Gnome-Do window - Run Application and Shared Folders of all things.  Pressing enter on either of these presents me with the Shared Folders dialog box rather than the Run Application dialog.

That should be it for me for now but I look forward to further developments.

---

### Post by ScdGigi on 2008-01-10
Hi all! I can't make Rhythmbox plugin work.. this is my output when running Gnome-do from command line:
```

** (Do:7917): WARNING **: The class Do.Universe.AbstractCommand could not be loaded,
used in Do.Addins, Version=1.0.2923.17372, Culture=neutral
10/01/2008 8.10.22 [Error]: Do encountered and error while trying to load addin
/home/gigi/.do/addins/Rhythmbox.dll: Could not load type 'Do.Universe.AbstractCommand' from
assembly 'Do.Addins, Version=1.0.2923.17372, Culture=neutral'.

```

What can I do?

Thanks

---

### Post by davidsiegel on 2008-01-10
You're using an older version of Do. Follow the instructions here [https://wiki.ubuntu.com/GnomeDo/Plugins](https://wiki.ubuntu.com/GnomeDo/Plugins) to find the appropriate Rhythmbox plugin for your version.

---

### Post by ScdGigi on 2008-01-10
> **davidsiegel said:**
> You're using an older version of Do. Follow the instructions here [https://wiki.ubuntu.com/GnomeDo/Plugins](https://wiki.ubuntu.com/GnomeDo/Plugins) to find the appropriate Rhythmbox plugin for your version.

Right! But.. how can I update Gnome-do? I've added this repo:
```

#Gnome-do
deb http://ppa.launchpad.net/rharding/ubuntu gutsy main
deb-src http://ppa.launchpad.net/rharding/ubuntu gutsy main

```

Thank you fo quick answering!

---

### Post by davidsiegel on 2008-01-10
The package in the PPA is outdated. Wait a couple weeks.

---

