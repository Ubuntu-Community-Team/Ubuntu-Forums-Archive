---
title: "login &quot;su -&quot; ,not able to open apps"
date: 2006-03-07
forum: Desktop Environments
---

### Post by deepclutch on 2006-03-07
Hello,
I use Ubuntu Breezy 5.10 and GNOME.i tried to su as this:
```
prakash@sputnik:~$ su -
Password:
root@sputnik:~# gedit

(gedit:13377): Gtk-WARNING **: cannot open display:
root@sputnik:~#
```
what should i do to able to open guis from terminal.is it to do something with "xhost +"
EDIT:I forgot to tell that if i simply try "su" without hyphen and login i can run any gui apps for eg;gedit etc
Thanks

---

### Post by jpkotta on 2006-03-07
Try
```

echo $DISPLAY
su -
export DISPLAY=:0
```
:0 is the most common but may be different.  Use whatever is returned by the echo command.  Also, sudo should have no trouble starting GUI apps.

---

### Post by deepclutch on 2006-03-08
Thanks.i tried that and for me display is ":0.0".i tried opening gedit and below is the result:
```
prakash@sarge:~$ echo $DISPLAY
:0.0
prakash@sarge:~$ su -
Password:
sarge:~# export DISPLAY=:0.0
sarge:~# gedit
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gedit:9926): Gtk-WARNING **: cannot open display:
```
what will be wrong..

---

### Post by RAOF on 2006-03-08
You should, in general, use **sudo** or **gksudo** rather than **su**.  See the wiki:
[wiki.ubuntu.com/RootSudo](wiki.ubuntu.com/RootSudo).  Note particularly that graphical apps should be run using **gksudo**!

---

### Post by akiro.yamamoto on 2006-03-09
Try this:
[ALT]+[F2] (Run dialog)
type: 
gksudo gedit
You will be asked for YOUR password, enter it then click OK and gedit shout start. ;)

---

### Post by kennethb on 2006-03-09
[QUOTE=deepclutch]Hello,
I use Ubuntu Breezy 5.10 and GNOME.i tried to su as this:
```
prakash@sputnik:~$ su -
Password:
root@sputnik:~# gedit

(gedit:13377): Gtk-WARNING **: cannot open display:
root@sputnik:~#
```
what should i do to able to open guis from terminal.is it to do something with "xhost +"
EDIT:I forgot to tell that if i simply try "su" without hyphen and login i can run any gui apps for eg;gedit etc
Thanks[/QUOTE]

If you are trying to open a file in gedit from a terminal screen (e.g., command prompt), then type:

sudo gedit sample_file.txt

where sample_file.txt is the name of the file you want to open/view/edit with the gedit text edior.

---

### Post by deepclutch on 2006-03-19
Solution seems for me is to install "sux" which exports all ur X credentials when u use " sux  -".now that works for me,Thanks every body

---

