---
title: "X refuses to load"
date: 2007-07-30
forum: Desktop Environments
---

### Post by thexaspect on 2007-07-30
Ok, I'm running Fiesty (64 bit) with dual monitors, no Compiz/Beryl/etc. I just got it installed and was changing my ui around, and when I rebooted, it loaded up gdm, put it my uname and p/w, and up comes a dialog box:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of these failsafe sessions to see if you can fix this problem. "
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "valdos"
/etc/gdm/Xsession: Beginning session setup...
bind: Permission denied
```

Any ideas? I can get into x via the recovery mode as root, but where do I go from there? Total noob problem, I know, but really I just need to know where to start from, and I can figure it out from there. I'm assuming I borked something with the new gdm config that I was playing with, so I'm thinking it's either gdm or x that's having the problem. So how do I fix the problem without reinstalling?

---

### Post by phidia on 2007-07-30
Sometimes that error is a permissions problem. I have some notes on fixing it but it may not work depending what exactly caused your specific problem.
What worked for me is to "cd /home"  
"sudo chmod 700 <yourusername>"
"sudo chown <yourusername yourusername>"
"sudo chgrp   <yourusername yourusername>"

after doing the above you may also need to "cd <yourusername>"
"chmod -R  777*"

Where I've entered <yourusername> you, of course, will just enter the user name for the account you're trying to repair.

Try that and see if it gets you into your home.

---

### Post by thexaspect on 2007-07-30
ok, so you're saying if my username's "x", something to the effect of:

"sudo chmod 700 <x>"
"sudo chown <x x>"
"sudo chgrp <x x>"

?

---

### Post by thexaspect on 2007-07-30
tried it, and it didn't work. but now my user might as well be root. any other ideas anyone?

edit: I'm 100% positive that I'm not out of diskspace, unless a 500gb / can be filled up by only installing fiesty.

---

### Post by phidia on 2007-07-31
Don't add the "<" and ">" symbols i just used those as delineators.

the command would look like this e.g.
> sudo chmod 700 x

---

### Post by thexaspect on 2007-07-31
i figured it out, but it didn't do me any good. i finally just said screw it and rooted in to backup my files and reinstalled over the top of it. unfortunately i forgot my xorg.conf, LAME

---

