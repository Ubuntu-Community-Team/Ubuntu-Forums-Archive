---
title: "Administration applications not accessible"
date: 2006-03-16
forum: Desktop Environments
---

### Post by walrex on 2006-03-16
HI I just recently installed Ubuntu 5.10. Everything went fine. except I can't use any of application under * [COLOR="DarkOrange"]System &#8594; Administration &#8594;[/COLOR]* it ask for the password I type it in the it loads the application then it escapes:cry: .  I used[COLOR="Red"] ( sudo apt-get update )
(sudo apt-get upgrade)[/COLOR] to update my system because I can't use the _Synaptic Package Manager _[COLOR="Red"].
(apt-get update /upgrade) [/COLOR] worked like a charm:KS . it updated my system But still I couldn't use any of thee application underneath the * [COLOR="DarkOrange"]System &#8594; Administration &#8594;[/COLOR]* ?????!!!!!!
all my user & root password are OK
Can anyone help?

system: P3 800,128 ram,6 GB HD,ATI card,LAN 10/100,

---

### Post by bitonw on 2006-03-22
hi,

i have the same problem on my new install.

os ubuntu 5.10 on dell latitude d610 with 1gb ram, 60gb disc

and indeed if i use sudo it works but not via the system / administration

regards,
bt

---

### Post by bitonw on 2006-03-22
new update,

when i su root i can start synaptic... and than it's working normal but i can't start it under the normal user...

bt

---

### Post by bitonw on 2006-03-23
got it working again.

under user root changed the shadow file and removed the passwd of root and changed it in *
disabled root user according the docs found on ubuntu web site.
booted the box with an rescue disc and edited the /etc/sudoers file. added my userid under the root entry.
booted ubuntu and yes i could now use sudo again.
added the group admin and made my self a member of it
used sudo visudo -f /etc/sudoes and added this new group %admin  ALL=(ALL) ALL and removed my userid

the only thing i don't understand is why the group admin wasn't on this box...


bt

---

### Post by soliac on 2006-05-12
Hi, I've got the same problem.
I've just installed Ubuntu and now can't configure anything advanced :( .
I'm a real newbie here, can someone help with this problem?

---

