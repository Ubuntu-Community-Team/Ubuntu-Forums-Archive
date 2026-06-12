---
title: "Digi Camera, CDrw/dvd drive, and IAUDIO MP3 drive won't mount."
date: 2006-01-31
forum: Desktop Environments
---

### Post by encompass on 2006-01-31
I have installed my USB webcam... and as part of the installation I needed root access not sudo so I created a root password... after this driver install and root password setup... I have lost all connections to devices... even IDE DVD drive is lost... any ideas?  I can't even get into my sudo needed things with out going into root first.  WHAT DID I DO!  I don't like using su I love sudo!  Sudo is my friend... but su is ruining my life... JK  The sooner the better... this is my school computer.

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=encompass]I have installed my USB webcam... and as part of the installation I needed root access not sudo so I created a root password... after this driver install and root password setup... I have lost all connections to devices... even IDE DVD drive is lost... any ideas?  I can't even get into my sudo needed things with out going into root first.  WHAT DID I DO!  I don't like using su I love sudo!  Sudo is my friend... but su is ruining my life... JK  The sooner the better... this is my school computer.[/QUOTE]
Your /etc/sudoers file should look similar to this:
```

# sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets

# User privilege specification
root	ALL=(ALL) ALL

# Added by Ubuntu installer
encompass	ALL=(ALL) ALL

```
If that is OK, I am not sure what you could do except maybe reinstall sudo?

---

### Post by encompass on 2006-01-31
I had this...
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL


I will make the change...

---

### Post by encompass on 2006-01-31
fixed the using sudo part... but still get this...
[[IMG]http://img56.imageshack.us/img56/1388/screenshot3td.th.png[/IMG]](http://img56.imageshack.us/my.php?image=screenshot3td.png)
and as you can see I can manually mount it... just no auto... and that is what I really want.  (that's why I am in a GUI right?) :o

---

### Post by cwaldbieser on 2006-02-01
[QUOTE=encompass]fixed the using sudo part... but still get this...
[[IMG]http://img56.imageshack.us/img56/1388/screenshot3td.th.png[/IMG]](http://img56.imageshack.us/my.php?image=screenshot3td.png)
and as you can see I can manually mount it... just no auto... and that is what I really want.  (that's why I am in a GUI right?) :o[/QUOTE]
Try reinstalling pmount maybe?  It sounds like a permission issue.  Also, if the device you are mounting is in your /etc/fstab, pmount can have a problem with that.

---

### Post by encompass on 2006-02-01
SOLVED!!! For some reason I had lost all the rights... you know... the ones in the user and group settings... and after restoring those right... that would be all but the audio... I was then able to use everything just fine.
Must be a funny bug in some program I was using, but I lost all rights when it happened.
NONE THE LESS... you have helped me, and your willingness is a great thing to see here in the forums.

So now everything seems to be working... thanks...\\:D/ 
For some reason I use those smilies... but they just don't say enough, or the right thing.

---

