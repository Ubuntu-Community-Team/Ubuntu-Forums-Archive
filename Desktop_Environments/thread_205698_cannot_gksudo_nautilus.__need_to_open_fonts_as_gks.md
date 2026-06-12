---
title: "cannot gksudo nautilus.  need to open fonts:/// as gksudo install global ttf otf font"
date: 2006-06-28
forum: Desktop Environments
---

### Post by TOPPEL on 2006-06-28
Originally Posted by TOPPEL
i'm trying to install otf and ttf for global system and can't ever gksudo nautilus

i cannot gksudo nautilus so i can open fonts:///

i dont know any other way to globally install ttf and otf fonts.

thanks

~# nautilus

(nautilus:12516): Gtk-WARNING **: cannot open display:

---

### Post by henriquemaia on 2006-07-06
[quote=TOPPEL]Originally Posted by TOPPEL
i'm trying to install otf and ttf for global system and can't ever gksudo nautilus

i cannot gksudo nautilus so i can open fonts:///

i dont know any other way to globally install ttf and otf fonts.

thanks

~# nautilus

(nautilus:12516): Gtk-WARNING **: cannot open display:[/quote]

Try this:

Open a terminal and type

```
sudo nautilus /usr/share/fonts
```

Hope this helps.

---

### Post by mannheim on 2006-07-06
... or you could do (in a terminal)

```
sudo nautilus fonts:///
```

The error that you quote suggest that you were doing something like:

```
[COLOR="Blue"]user@host:~$[/COLOR] sudo -i
Password:
[COLOR="Blue"]root@host:~#[/COLOR] nautilus fonts:///          [COLOR="Red"]Wrong![/COLOR]
```

You can't run a gui app as root this way, because after "sudo -i" the necessary environment variables are not set.

---

### Post by TOPPEL on 2006-07-07
that makes sense then.  could you kindly tell me how to launch a Gnome app from console as root then ?  

this is what i tried and failed

root@MAIN:~# nautilus /usr/share/fonts

(nautilus:16799): Gtk-WARNING **: cannot open display:

---

### Post by bhuvan72 on 2006-10-28
Hi folks,

I am a complete newbie here.

I need to read a native language website (Tamil) and it supplied a .ttf font file.

How do I install this.

I tried to copy it in /usr/share/fonts/truetype/ttf-tamil-fonts
and restarted firefox, but i still see only special chars...

Thanks,
Bhuvan.

---

