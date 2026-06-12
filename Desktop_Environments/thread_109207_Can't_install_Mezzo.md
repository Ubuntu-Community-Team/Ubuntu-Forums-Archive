---
title: "Can't install Mezzo?"
date: 2005-12-28
forum: Desktop Environments
---

### Post by Maelgwyn on 2005-12-28
I've just installed mezzo, and trying to follow the instructions on the synphonyos website...

> 
[FONT=Arial, Helvetica, sans-serif][SIZE=2]Then copy the settings to your home directory (as regular user,               not root do)[/SIZE][/FONT]
                                             [FONT=Arial, Helvetica, sans-serif][SIZE=2]cp                     -Rvf .mezzo ~/.
                    cp -Rvf .orchestra ~/.[/SIZE][/FONT]


but when I try cp -Rvf .mezzo ~/. , I get told:
> 
cp: cannot stat `.mezzo': No such file or directory


help?

---

### Post by Iandefor on 2005-12-28
I had the same issue; just tagging on my own help request. Although this is probably more appropriate in a Mezzo support forum.

---

### Post by Maelgwyn on 2005-12-28
excellent :) I've posted on the Mezzo forum

[http://www.symphonyos.com/forum/index.php?showforum=4](http://www.symphonyos.com/forum/index.php?showforum=4)

---

### Post by fak3r on 2006-01-31
[QUOTE=Maelgwyn]I've just installed mezzo, and trying to follow the instructions on the synphonyos website...

but when I try cp -Rvf .mezzo ~/. , I get told:

help?[/QUOTE]

Bad docs on their part, the needed directories are in /etc/skel:

```
cp -Rvf /etc/skel/.mezzo ~/.
cp -Rvf /etc/skel/.orchestra ~/.
```

Also I have a quick howto here: [http://fak3r.com/articles/2006/01/31/howto-mezzo-desktop-on-ubuntu](http://fak3r.com/articles/2006/01/31/howto-mezzo-desktop-on-ubuntu)

---

### Post by Maelgwyn on 2006-02-01
Awesome thanks for that - I'm working my way through your How-To right now :)

*crosses fingers*

---

### Post by fak3r on 2006-02-01
[QUOTE=Maelgwyn]Awesome thanks for that - I'm working my way through your How-To right now :)

*crosses fingers*[/QUOTE]

Please let me know what works or doesn't work and I'll follow up.  I've got a sister thread for this going over on Symphony's forums here:
 [http://www.symphonyos.com/forum/index.php?showtopic=662&st=0&](http://www.symphonyos.com/forum/index.php?showtopic=662&st=0&) 

I've already updated the HOWTO once thanks to Ryan's (Symphony Lead dev) feedback and will pass any feedback I get here over there.

---

