---
title: "[SOLVED] Weird problem with gnome-termimal prompt while scrolling through history"
date: 2008-06-09
forum: Desktop Environments
---

### Post by oc1001 on 2008-06-09
Context: I've just upgraded from edgy, and figured I might as well go all the way to hardy. So I'm running terminal 2.22.1 in a pretty vanilla installation of hardy on an x86-64 machine.

The problem: when I try to cycle through my command history in bash, my prompt, which is usually just a '$ ', has the first 12 characters of the previous command appended to it. Everything works fine, except that the prompt has become significantly harder to read..! 

Any ideas of how I might go about fixing this? Here's the command I use for my PS1 variable in .bashrc - I'm guessing this might be the problem, but I never had this problem in edgy...

PS1='\n${debian_chroot:+($debian_chroot)}\[\033[00;32m\]\u@\h \[\033[00;33m\]\w\[\033[00m\]\n\$ '

So my prompt usually consists of <my user name>@<my machine name> <current directory>, and then on a new line, '$ '. The first line works fine, but the second one does not.

Any help would be most appreciated...!

---

### Post by mannih2001 on 2008-06-09
I tried to replicate your problem and used the same string for PS1, but it works just fine here. So maybe you should look for another reason.

---

### Post by oc1001 on 2008-06-09
Thanks for that mannih, looks like I can forget about the PS1 idea...! Which is good because it rules that out. But I'm a little bit short on other ideas. Would anybody have any suggestions of other areas that I could look into?

---

### Post by mannih2001 on 2008-06-10
Have you tried to use a different shell? Just for testing. I guess the question is who's to blame, bash or gnome terminal.

---

### Post by oc1001 on 2008-06-10
Hey good point, thanks mannih :). Hadn't thought of that. Turns out that it's bash - a quick test with zsh shows that there's no problem with gnome-terminal. Which lead me to thinking about bugs in bash, and I managed to find this [[COLOR="Red"]bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/bash/+bug/118636"). Which is similar, although not the same... A suggestion there was adding a new user account, and seeing whether that made a difference, so I'm just off to try that now...

---

### Post by oc1001 on 2008-06-22
Just a heads up with where I got to with this - I'm having this problem on my work machine and we've been swamped here, so I haven't had any time to get too much further with it - but I can confirm that creating a new user account results in a bash that doesn't have this problem. So it must be some funny config niggle somewhere. Or something. At any rate, that's enough of a lead to get moving on this, thanks again for your help your mannih...!

---

### Post by thedrunkduck on 2008-08-21
I have exactly the same problem with xterm. I'm goggling for hints but haven't found any solution so far.

Did you manage to solve it?

[SOLVED] It was a syntax problem

---

