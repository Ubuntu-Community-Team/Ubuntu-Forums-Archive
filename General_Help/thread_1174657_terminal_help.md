---
title: "terminal help"
date: 2009-05-31
forum: General Help
---

### Post by noelc on 2009-05-31
Hi, Trying to learn linux and doing ok so far I think.


Anyway when playing with start up processes today I turned something off which took me straigth to a full screen terminal. I tried rebooting and same thing full screen terminal. cant reboot into Ubuntun 8.10. I,m presented with a full screen terminal. I can log in and navigate directories but I,m new to this so very much stuck in terminal screen. I,m presuming theirs a script I need to type in the terminal which will graphicaly load ubuntu but my manuals dont help..

Would appreciate any help here thanks

---

### Post by ActiveFrost on 2009-05-31
Try this : 
```
exec gnome-session
```

---

### Post by mcduck on 2009-05-31
This should take you into the graphical login screen:
```
sudo /etc/init.d/gdm start
```

---

### Post by noelc on 2009-06-01
> **mcduck said:**
> This should take you into the graphical login screen:
```
sudo /etc/init.d/gdm start
```

Thanks that work great.

I,m not sure why but I cant turn this booting into terminal off so Ubuntu automatically boots into graphical.

I get a message saying no resume image?

Can you assist?

---

### Post by sanemanmad on 2009-06-01
> I get a message saying no resume image?

this is normal, look at this post for the explanation. [No Resume Image]("http://ubuntuforums.org/showthread.php?t=422875")

As far as the boot into terminal... I think you accidently changed the init levels in the "Process menu" and your pc is now simply booting into say init level 1. Take a look at this link for more explanation [Init levels for Ubuntu]("http://en.wikipedia.org/wiki/Runlevel#Ubuntu"). You will probably need to install chkconfig ```
sudo apt-get install chkconfig
```

---

