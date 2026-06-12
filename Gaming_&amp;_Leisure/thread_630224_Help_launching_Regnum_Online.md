---
title: "Help launching Regnum Online"
date: 2007-12-03
forum: Gaming &amp; Leisure
---

### Post by Fonon on 2007-12-03
OK, I have heard good things about Regnum Online, and decided to reinstall it on this box.  So, I downloaded the rolauncher.tar.gz from the site, and extracted the file.

I double clicked the application, nothing happened.

I right-clicked, hit open, and nothing happened.

I uninstalled WINE, in case WINE was trying to execute it, and tried the above.  No change.

I went into the terminal, and went to my desktop, and typed 

```
rolauncher
sh rolauncher
```

Neither of them worked.

Please help?

---

### Post by AoWhijun on 2007-12-03
Does the file you're trying to run have executable permissions?

---

### Post by LinuxGamer on 2007-12-03
Try opening a terminal, changing dir to where you have the rolauncher and want it to download all the resources and typing:
MALLOC_CHECK_=0 ./rolauncher 
Just Copy and paste the above command if you want.
(This is because of a change in the GNU libc in Gutsy)

---

### Post by Fonon on 2007-12-03
Thanks, LinuxGamer.

I'll log in later, I just wanted to launch is currently so I can see if it works.

---

### Post by s_spiff on 2007-12-05
ok, I was facing the same issue, and i used the above suggested command and I got this :
```

spiff@spiffed:~/.Games/regnum$ MALLOC_CHECK_=0 ./rolauncher

(rolauncher:6159): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64


```
With this, a small blank window opened up, but with no contents. 
What is going on?

---

### Post by Vadi on 2007-12-06
Clearly you don't have the right elves!

Where did you guys get the linux installer? I only found a torrent for now, but it's not working at all.

---

### Post by belio on 2007-12-06
This one worked  for me, with the command above:

[http://www.regnumonline.com.ar/downloads/files/rolauncher.tar.gz](http://www.regnumonline.com.ar/downloads/files/rolauncher.tar.gz)

---

### Post by Vadi on 2007-12-06
Ah I got the .torrent file working.

And yay, my card is exactly an ATI Radeon 7500.

Edit: Okay, skip that. The installer never finishes, and when I exit it, it deletes the entries it made. I'll try the file above.

---

### Post by s_spiff on 2007-12-06
I got the same as the link provided.. but still doesnt work... 
elves? huh?

---

