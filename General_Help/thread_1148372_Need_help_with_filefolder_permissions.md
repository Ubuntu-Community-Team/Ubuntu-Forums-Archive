---
title: "Need help with file/folder permissions"
date: 2009-05-04
forum: General Help
---

### Post by Alienwarek on 2009-05-04
Ok heres whats going on. I've been having some trouble with my GRUB loader and I can only get in via the LiveCD. what I want to do is back up all my file/folder but every time I try I get an error saying that I can't cause of permissions. can anyone help me? (I'm still very new to Ubuntu)

[http://ubuntuforums.org/showthread.php?t=1137578](http://ubuntuforums.org/showthread.php?t=1137578) <--(this link has to do with my GRUB trouble)

---

### Post by mike555 on 2009-05-04
When running the live cd, go to terminal and type;   gksudo nautilus     ... and that should open nautilus with root permissions , then you should be able to change the files permissions and copy them .... I guess I don't need to tell you to backup to a thumbdrive next time ,before something like this happens again ......... or if you are going to reinstall you might make a partition just for backups ...

---

### Post by Bindsa on 2009-05-04
Try the tip mike555 gave you:

Press [COLOR="Red"]ALT + F2[/COLOR] and enter:
```
gksudo nautilus
```

You could also try this to restore your GRUB:

Open up a terminal and type this:
```

sudo [COLOR="Red"]grub[/COLOR]
[COLOR="Red"]grub[/COLOR]> find /boot/grub/stage1
```

This should return something like: (hd1,1) 
Write that sentence down. Now type into the terminal:
```
[COLOR="Red"]grub[/COLOR]> root (hdA,B)
[COLOR="Red"]grub[/COLOR]> setup (hdA,B)
[COLOR="Red"]grub[/COLOR]> quit

```
Where A and B are the values you wrote down earlier.
Now try to reboot into Ubuntu.

---

### Post by Alienwarek on 2009-05-04
mike555 thx that worked... and Bindsa I've tried reinstalling GRUB and i still get

```
[ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename. ]

grub>
```

---

