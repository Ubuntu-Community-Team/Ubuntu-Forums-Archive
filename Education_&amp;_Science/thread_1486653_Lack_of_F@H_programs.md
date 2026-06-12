---
title: "Lack of F@H programs"
date: 2010-05-18
forum: Education &amp; Science
---

### Post by 311005901 on 2010-05-18
I got excited about [Folding at Home]("http://en.wikipedia.org/wiki/Folding@home") and I wanted to help out!

After some research, I used origami to install F@H on 2 computers with completely different specs. I don't know if I did it right... :(

I wanted to get a monitoring program for my computer so I installed FahMon from source (but can't get it to work and the PPA looks [stagnant]("https://launchpad.net/~tsunetomo/+archive/ppa/+packages")) and I couldn't get Protein Think to work because [it's too confusing]("http://ubuntuforums.org/showthread.php?t=101817"). By [this page]("http://prothink.sourceforge.net/"), Protein Think was built on Ubuntu, but there are no debs... :confused:

Can someone with programming skills make a good F@H program for personal use? :confused: Why hasn't this been done? Why hasn't the [Ubuntu Team]("https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu") developed a simple program?

Suggestion:
[LIST]
[*]Installs origami easily from a .deb
[*]Automatically configures origami with CPU architecture, RAM, and GPU settings from startup
[*]Installs a graphical monitoring program like FAHmon or Protein Think
[*]Simplifies joining the [Ubuntu Team]("https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu") for F@H
[*]Lets the user select idle/time settings and sets cronjobs accordingly
[*]Lets the user select laptop or notebook power settings and update to acpi
[*]Lets the user scale down CPU usage by a graphical slider
[*]Doesn't require a terminal, compiling, documentation, configuring, or manuals for regular use
[*]Offline folding support
[*]Easy stop and start daemon
[*]Proxy and firewall management
[*]Lookup of current totals worldwide, team, and personal
[/LIST]

Can Ubuntu be a pioneer in Folding? :confused:
I can't program, but it seems so easy...

/rant
I dunno...
Maybe not...

---

### Post by Chronon on 2010-05-19
[https://help.ubuntu.com/community/FoldingAtHome/origami](https://help.ubuntu.com/community/FoldingAtHome/origami)

Origami is already in the repositories.  It tells you how many packets you have completed. I think it's fine as a F@H client.  I wouldn't want or need most of the stuff you mentioned.

---

### Post by 311005901 on 2010-05-20
I'm glad someone else is interested in Folding!

Origami works nicely, but I would like something that doesn't use the command-line extensively.

---

### Post by hrsetrdr on 2010-05-22
Sounds like you're looking for a program like InCrease, that's for Apple machines, the closest app for such _was_ fininstall, but appears to be depreciated now.

I wrote an article a while back on f@h installation using the GUI and CLI; a dead-bang easy method, I must say.  ;)
[http://www.overclockers.com/linux-folding-setup-guide-gui-method/](http://www.overclockers.com/linux-folding-setup-guide-gui-method/)

For monitoring there's HFM.net, which can be installed on Ubuntu:
[http://groups.google.com/group/hfm-net/web/hfm-in-ubuntu](http://groups.google.com/group/hfm-net/web/hfm-in-ubuntu)

---

