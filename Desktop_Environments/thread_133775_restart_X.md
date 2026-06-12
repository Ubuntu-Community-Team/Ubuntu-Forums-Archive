---
title: "restart X"
date: 2006-02-20
forum: Desktop Environments
---

### Post by xhie on 2006-02-20
Howdy yall,

This is most likely an incredibly stupid question but...

I'm running ubuntu on a Toshiba R15 tablet, the pen works great, everything works great, the only problem was to get the screen to rotate, I can do that just fine now but I means booting up X with a modified xorg.conf file which I have and it works like a charm.  

I want to do the rotate screen / reboot X thing with a script, the swiching out xorg.conf files I have no problem with, what I dont know how to do is have it reboot X, and if its possable to have it reboot X as the current user without a login screen poping up. 

any help would be great.  :)

---

### Post by Wallakoala on 2006-02-20
rebooting X will log you out of gdm. A shortcut to rebooting X is control+alt+backspace. I forget what the terminal command is to do that.

---

### Post by RAOF on 2006-02-20
From a script you could call "/etc/init.d/gdm restart", which will stop your X server and then start it again.  You'll need root privs to do this, though, so either your script will have to be run with sudo, or you could have it setuid root (which means that the script gets run as root, regardless of who calls it).

---

### Post by xhie on 2006-02-21
/etc/init.d/gdm restart only logs me out of x, it dosent bring it back up, actually It stops at that login screen before X boots up. 

whats command line equivalent of control+alt+backspace?  I'll take that if thats the best I can do with this. 

I thought bash cant setuid, is that not so?

---

### Post by xhie on 2006-02-21
anyone?

---

### Post by dubowski on 2006-02-21
Ctrl+alt+bckspc also stops at the login screen, but thats the way it restarts i think, it starts again from the beginning.

You should automatically be logged in if you wouldnt like it to stop at the login.

---

### Post by xhie on 2006-02-21
be logged in as what? a user? when I do /etc/init.d/gdm restart? 
I am and it stops at the login screen, NOT the normal one, the text one you get after X shuts down. 

I'm fine with it just stoping at the normal login screen. 

adding the above line, and running the whole thing with sudo dosent do it. Ok so how do i setuid in this? If someone could point me somewhere it would be nice. 

:)

---

### Post by dubowski on 2006-02-21
I mean the user should be automatically be logged in at gdm, but i think i misunderstood you :) Sorry.

---

