---
title: "Installed apps don't show on the menu"
date: 2005-05-05
forum: Desktop Environments
---

### Post by Malkosha on 2005-05-05
So far Ubuntu has been pretty great. I got all the little extras installed like I wanted to and everything is smooth.

Except .....

When I install programs from synaptic the most icons never show up on the menu. For instance, I installed Tuxkart and while I can run it from the term, the icon isn't on the menu anywhere. I've rebooted, killed the panel and restarted it, etc but still not there.

I've been trying a few distros lately, and Ubuntu is the only one with this problem. In fact, this is really a "game breaker" esp for a noob. Anyone have an idea why this is happening? It works in Mepis, Fedora Core 3, Libranet, etc. I can't believe that this most simple of functions won't work in Ubuntu. I imagine I could create the menu icon myself, but what a hassle when there are distros where this works to a tee. Any ideas? Is it just me or am I'm whining for nothing?

---

### Post by Joeb on 2005-05-05
This is a problem with Gnome, not Ubuntu.  The latest/current version of Gnome is changing how menues work to be compatable with the freedesktop specs (I think that's what they're called).  Anyway, most applications still are packaged assuming the old menu structure of Gnome.  As such, they don't create the menu entries when installed.  To make it worse, The latest/current version of Gnome doesn't ship with a menu editor, thereby making it more difficult to create menu entries yourself.

There are two options.  One, you can manually create the .desktop entries in ~/.local/share/applications (hopefully there are a few there so you can just edit one and save it with the new name) or two, if you search on the Ubuntu forums, someone has created a little app/script to create menu entries for you.  The link to the script is: [http://www.ubuntuforums.org/showthread.php?t=21390&highlight=menu+update](http://www.ubuntuforums.org/showthread.php?t=21390&highlight=menu+update)

Again, this is really a Gnome problem and pretty much any distro using the latest version of Gnome will have it.  It's just that most others don't use it yet.

Joeb

---

### Post by Malkosha on 2005-05-05
Thanks for the reply!

I have the menu editor and it seems to work great. However, I installed quite a few things and it would take a ton of work to get them all in. I thought it was a gnome problem ... which is one of the reasons I really don't care for gnome. I've been working with KDE for so long I guess I'm spoiled. Oh well, it was great while it lasted.

Again, thanks for the help!

---

### Post by DutchLau on 2005-05-05
When will this "bug" be fixed? It's damned annoying. For the time being I have to run many many apps from terminal or by making launchers, which is a pain in the butt!

Greets,

DutchLau

---

