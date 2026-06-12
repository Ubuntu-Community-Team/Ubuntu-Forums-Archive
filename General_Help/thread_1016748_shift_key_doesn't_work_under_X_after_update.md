---
title: "shift key doesn't work under X after update"
date: 2008-12-20
forum: General Help
---

### Post by b16 on 2008-12-20
Hi,

just updated the latest ubuntu height dot ten
and the shift key doesn't work anymore which is why i have trouble inserting numbers (french keyboard)
CAPS LOCK work fine but SHIFT just seems to unselect a selected zone anyway
is useless to get any carater i used to get with it
the xorg.conf is useless
doesn't even contain a keyboard entry
i have just installed this distro on my new LATITUDE E4300 
(at least i copy paste the numbers great !)
it is a X problem since everything works fine in console only mode 
Anybody having an idea
b

---

### Post by b16 on 2008-12-21
I have a Debian Lenny installed on the same computer which works fine.
I have tried to add a device section for the keyboard configuration as in the Lenny xorg.conf but it didn't help...
I really have no clue of what to do.
Is this a setting problem of gnome ?
Would it be a bug introduced by updating some packages (ubuntu 8.10) ?
Anybody having any idea ?
Do I have to manually define the shift key with xmodmap ?

thank you,

b.

---

### Post by b16 on 2009-01-02
I did not really solve the problem but it seems it was due to some appearance choice which i switched to none. I still do not know why it popped up just after an update...
Anyway anyone having the same kind of problem can refer to 
 [http://ubuntuforums.org/showthread.php?t=785029](http://ubuntuforums.org/showthread.php?t=785029)
I did not try fine tuning of normal appearance mode but some solution seems to appear there...

---

### Post by Cracauer on 2009-01-02
Please post xorg.conf

---

### Post by sanso on 2009-01-17
hey there. my shift key is behaving exactly the same way as described above after trying to add support for some keys on my lenovo x60 tablet pc - exactly as described here.. - i cant type a colon right now, please bear with me..

[http://luke.no-ip.org/x60tablet/#keyboard](http://luke.no-ip.org/x60tablet/#keyboard)

not much magic there, putting this file - [http://luke.no-ip.org/x60tablet/examples/.Xmodmaprc](http://luke.no-ip.org/x60tablet/examples/.Xmodmaprc) - into ones home. when i logged out and back in, a dialog - presumably gnome - popped up, telling me about the new xmodmap file and whether it should use and remember it. 
i klicked yes
and ever since, pressing either of the shift keys seems to remove or pause keyboard focus.

i removed the xmodmap file, but that didn't help.

so i looked for the file pointing toward the file in gconf-editor, found it and removed it as well. still not happy.

now i'm slightly nervous. i need this computer to work.

---

