---
title: "how to restart X server?"
date: 2009-04-26
forum: General Help
---

### Post by m3alnemer on 2009-04-26
I want to restart the X server (Ctrl+Alt+BkSp) Does not do anything:(

I might missed up the key shortcut somehow. 


is there a way to fix that or at least an lternative for the terminal?

Thanks in advance

---

### Post by VCoolio on 2009-04-26
sudo /etc/init.d/gdm restart

for the keybinding check system > preferences > keyboard shortcuts, maybe it is there. Edit: no it is not.

---

### Post by bdoe on 2009-04-26
Ctrl-Alt-Backspace as a means of restarting X has been disabled in 9.04 Jaunty. I'm not sure yet how to get it back.

---

### Post by fooman on 2009-04-26
it can be re-enabled by installing the "dontzap" package.  open a terminal and run the following command:

```
sudo apt-get install dontzap
```

after it installs,  run this command in a terminal:

```
sudo dontzap --disable
```
you may have to restart the computer after that command....then alt-ctrl-bksp should work again.

---

### Post by jebradley on 2009-12-09
It's even simpler than the above discriptions.

In Ubuntu (gnome)
    * Select “System”->”Preferences”->”Keyboard”
    * Select the “Layouts” tab and click on the “Layout Options” button.
    * Select “Key sequence to kill the X server” and enable “Control + Alt + Backspace”.

This is discribed in
[http://pawan.student.umd.edu/blog/?p=284](http://pawan.student.umd.edu/blog/?p=284)
which also gives the method needed in kubuntu.

---

### Post by walkerk on 2009-12-09
The ugly way...
> sudo pkill X

My alternative to Ctrl-Alt-Backspace in OB.

---

### Post by tenshi-no-shi on 2009-12-15
Thank you, thank you ,thank you... Flash has been freezing my system for whatever reason, hopefully I fixed it, but if not it's nice to beable to kill X with a keycommand.

---

