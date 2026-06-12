---
title: "about locales"
date: 2005-07-02
forum: Desktop Environments
---

### Post by kimes on 2005-07-02
What I wanna do is to change gnome menu to use english
I'm using locale ko_KR.UTF-8
I heard that if I change LC_MESSAGES variable to en_US.UTF-8 or something..
I can see english menu..

So i changed ~/.gnomerc file and /etc/environment..
but

locales command still show that my LC_MESSAGES variable is ko_KR.UTF-8..
How can I change that?

en_US.UTF-8 is already set up by dpkg-reconfigure locales..
any idea?

---

### Post by Stemp on 2005-07-02
Why aren't you changing the language in gdm ?

---

### Post by kimes on 2005-07-02
[QUOTE=Stemp]Why aren't you changing the language in gdm ?[/QUOTE]
 Is there any other way to change locale except setting in gdm?
like edit some conf file...

---

### Post by argux on 2005-07-03
Maybe if you make an alias for gnome-panel like this:

alias='LC_MESSAGES="en_US.UTF-8" gnome-panel'

in your .bashrc and then restart gnome? I don't even know if gnome-panel is what you need to specify, but it's the closest thing that I found. You might give it a try, anyway.

---

### Post by t2kburl on 2005-07-03
I keep getting messages (when I use dpkg) that my locales are broken or not properly installed, yet synaptic shows no problems.

any ideas?

---

