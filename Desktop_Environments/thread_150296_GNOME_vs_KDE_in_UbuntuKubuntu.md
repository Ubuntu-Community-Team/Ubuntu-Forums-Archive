---
title: "GNOME vs KDE in Ubuntu/Kubuntu"
date: 2006-03-25
forum: Desktop Environments
---

### Post by Bloodrule on 2006-03-25
I'm confused.  I have Ubuntu installed but I want to check out the KDE desktop.  I don't want to have to install Kubuntu from scratch.  How can I install KDE in Ubuntu and how can I revert to Gnome once I've finished playing with KDE?  Seems like taking a sledgehammer to a peanut to have to install all of Kubuntu when all I need is the desktop environment.  Hope I've posted in the right section!

BR

---

### Post by Leif on 2006-03-25
open up synaptic, search for kde and install it. alternatively, search & install kubuntu instead, which will get you the whole shebang. logout, and you will be able to select between kde & gnome at the login screen.

---

### Post by dan828 on 2006-03-25
From the console you can just do

sudo apt-get install kubuntu-desktop

Let it do its stuff and restart, then you can pick either KDE or Gnome as a session type when you log in.

---

### Post by Bloodrule on 2006-03-25
When I do

sudo apt-get install kubuntu-desktop

I get the following messages:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

Do I have to have a live internet connection to install the package or is it already on my system somewhere waiting to be unpacked?

---

### Post by n8bounds on 2006-03-26
I believe that whenever you "apt-get" something it looks at your repositories to find whatever you asked it for.  Hardly anyone (and definitely not by default) has a local repository configured...so, to answer your question, yes, connection to the interweb required.

---

### Post by nealklomp on 2006-03-26
For Ubuntu: sudo apt-get install kde.
It takes awhile, KDE is a little rickety on Ubuntu with Gnome and I found that there are some issues with cd player.
Beware I am a novice, a very rookie programmer-ish and only a month or so into being full time exclusive linux. But I have also tried a half dozen distros.
I installed KDE, but never use it. I find it to be a bit to Windblowsy.

---

### Post by Bloodrule on 2006-03-26
Thanks for those helpful comments.  Even with a live broadband connection, everytime I try "sudo apt-get install kubuntu-desktop" I get a "couldn't find package" message.  Same if I try kde instead of kubuntu-desktop.  Have I got the name of the package right?

---

### Post by dan828 on 2006-03-27
Well, it worked for me.  Perhaps it has something to do with what you have your repositories set to.  I don't know that for sure and I'd think that the kubuntu-desktop packages would be available in the default settings but I'm just guessing.  You can set what repositories your system checks from synaptics or you can edit the sources.list yourself.

Perhaps some other helpful person can give you more info.  :)

---

### Post by Bloodrule on 2006-03-27
Thanks for the suggestion.  I'll try synaptics and see if that is the problem.

---

### Post by Sef on 2006-03-27
Also before you download kubuntu, do an update:

sudo apt-get update

---

