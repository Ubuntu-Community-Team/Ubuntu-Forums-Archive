---
title: "KDE Desktop Installation - Help Needed"
date: 2006-09-27
forum: Desktop Environments
---

### Post by DannyG on 2006-09-27
Hi,

I've been using Linux off and on for a while now for programming and other similair activities, but I've only just started using Ubuntu. When I installed Ubuntu I didn't get the option to install the KDE Desktop, so I need some help installing it.

I've searched all over and found some solution but none seem to work at all. When I try the command:

"sudo apt-get install kubuntu-desktop"

I get landed with:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

I also tried following the instructions found at [http://www.psychostats.net/ubuntu/kde/html](http://www.psychostats.net/ubuntu/kde/html) and I get:

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

When I go into my Synaptic Package Manager I have the KDE Deskptop area, but in here are just applications like kalarm, knotes, kontact etc. There is a package called kdebase-bin but I don't think this is what I need.

Oh, and I've checked the Logon screen to see if KDE is already installed and it isn't.

If anyone could help me with this it would greatly appreciated.

Many thanks.

---

### Post by nathanbriggs on 2006-09-27
sudo apt-get install kubuntu-desktop

is what you want

---

### Post by DannyG on 2006-09-27
Sorry I need to correct my previous post, it should say

When I try:

"sudo apt-get install kubuntu-desktop"

I get:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop


That command doesn't work for me.

Any help on this please?

---

### Post by DannyG on 2006-09-27
**[COLOR="Red"]_PROBLEM FIXED_[/COLOR]**

After reading some more, I did the following to fix this problem:

Open up the sources.list file, to do this:

[B]"cd /etc/apt/"
"sudo gedit sources.list"[/B]

Now I just uncommented everything in this list (note: uncommenting *everything* might not have been necessary, but I did it anyway).

Save and exit. Now do:

**"sudo aptitude update"**

Once this has done updating your packages, do:

**"sudo aptitude install kubuntu-desktop"**

*(Note: I read somewhere to use the aptitude command because it made it easier to uninstall KDE if you want to, whether or not this is true I do not know).*

From here it pretty much installs itself, when I was installing it asked for my Ubuntu CD, so have this handy.

Hope this helps other people who have this problem.

DannyG

---

