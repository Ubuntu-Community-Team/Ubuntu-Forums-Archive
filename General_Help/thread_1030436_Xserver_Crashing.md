---
title: "Xserver Crashing"
date: 2009-01-04
forum: General Help
---

### Post by Ewald on 2009-01-04
I am having problems with Xserver crashing and kicking me out to the login screen.

The latest Xorg.0.log.old is attached.

Thanks

---

### Post by cactusgal on 2009-01-05
Well, since nobody else has responded yet, I'll jump in. I'm very new to Ubuntu and Linux but this is the first problem I've had to deal with. Mine didn't just crash but wouldn't start at all. I Googled the problem (which led me to this forum and the Linux forum) and tried a few suggestions I found. None of them worked for me so I decided to try uninstalling it (sudo apt-get remove xserver-xorg) and then reinstalling it (sudo apt-get install xserver-xorg). This worked for me and I'm happy to say everything is working fine now. Hope this helps.

Regards,
cactusgal

---

### Post by ymenager on 2009-01-05
I'm having the same problem, as well as another person here in the office.

I tried to look in the logs but i can't see anything that indicates what went wrong (maybe that bogus lenght comment? but it doesn't even has a datestamp so who knows *sigh*), the last lines of xorg.0.old are: 

(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
AUDIT: Tue Jan  6 09:31:36 2009: 6217 X: client 4 rejected from local host ( uid=0 gid=0 pid=6414 )
AUDIT: Tue Jan  6 09:31:49 2009: 6217 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6456 )
AUDIT: Tue Jan  6 09:31:49 2009: 6217 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6457 )
AUDIT: Tue Jan  6 09:31:49 2009: 6217 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6458 )
BOGUS LENGTH in write keyboard desc, expected 5720, got 5736

---

### Post by vikrant82 on 2009-01-06
I am encountering same problem when I did an upgrade to Jaunty. Similar fate, cant login, X crashes and thrown back to login screen

---

