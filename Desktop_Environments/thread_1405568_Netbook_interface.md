---
title: "Netbook interface"
date: 2010-02-12
forum: Desktop Environments
---

### Post by paddy.melon on 2010-02-12
Hey guys,
I have a cool new netbook and, want to get a cool new interface and stuff for it. What is a very fast-booting DE that also looks really nice. I like Moblin but, would like the functionality of Gnome but, I want something more like Moblin over UNR. Perhaps, I could integrate a button on Moblin which loads up the UNR interface so, I can use that as well? I know it sounds weird but, pretty cool. Sorta like switching between UNR and Moblin or something similar. can it be done?

---

### Post by x33a on 2010-02-12
Maybe you want this:

[https://wiki.ubuntu.com/Specs/MobileKarmicMoblinRemix](https://wiki.ubuntu.com/Specs/MobileKarmicMoblinRemix)

Also take a look here:

[http://www.tuxradar.com/content/ubuntu-netbook-remix-vs-moblin](http://www.tuxradar.com/content/ubuntu-netbook-remix-vs-moblin)

---

### Post by paddy.melon on 2010-02-15
> **x33a said:**
> Maybe you want this:

[https://wiki.ubuntu.com/Specs/MobileKarmicMoblinRemix](https://wiki.ubuntu.com/Specs/MobileKarmicMoblinRemix)

Also take a look here:

[http://www.tuxradar.com/content/ubuntu-netbook-remix-vs-moblin](http://www.tuxradar.com/content/ubuntu-netbook-remix-vs-moblin)

Well, the idea is that I don't like Moblin for extended times of computing (just for MSN or Facebook) but, it is much nicer to do these things and, faster and easier to do these things on Moblin then on the full UNR. However, to do proper work and, mostly for the multi-tasking, I'd also like full UNR. My idea was to have moblin normally and, have it load GDM in the background (perhaps in a different tab-thingy [like the different ctrl-alt no. thing]) and, have a button in moblin to switch to UNR and a button to switch to moblin... actually...

OK, is the moblin interface available as a package in Ubuntu or, from another repo somewhere (EG. can I load it as a binary like how I can load gdm from console) and then, would it work if I had Moblin on ay tty6 and, GDM/UNR on tty7? AFAIK, I could get them to share all the resources so, it should be fine, right? Then, I'd make a little panel app on UNR to send the keys ctrl alt and 6 and, make an app in moblin to send the keys ctrl alt and 7. How cool would that be? Is my logic correct?

Thx, as always,
paddy.melon

---

### Post by x33a on 2010-02-15
Running different interfaces on different ttys can surely be done. though, i don't think that moblin is available just as an interface. it is a full blown os and the method you describe, won't work with this. one option would be to dual boot moblin and unr, but that would defeat the purpose in your case.

---

### Post by paddy.melon on 2010-02-16
> **x33a said:**
> Running different interfaces on different ttys can surely be done. though, i don't think that moblin is available just as an interface. it is a full blown os and the method you describe, won't work with this. one option would be to dual boot moblin and unr, but that would defeat the purpose in your case.

moblin may be an OS but, it would be possible to package the interface... it would just require a lot of knowledge of C and, a lot of coffee. I know a bit of C++ and, apparently they are similar but... I'm probs not good enough for this, lol. Would be a really good project though... could  be useful in many ways... promote moblin more for a start. Anyway, anyone in on the project?

---

### Post by paddy.melon on 2010-02-21
So, the question I have for all you guys is this: How can I run a different display manager in a different screen thingy/tty (eg. ctrl+alt+#) and, make them run totally side-by side? I'll sort out all the rest.

---

### Post by x33a on 2010-02-21
Well you can run multiple x servers simultaneously.

try
```
startx -- :1
```

This will start another x server on tty8.

---

### Post by paddy.melon on 2010-02-22
Sweet, is it possible to then launch, say KDM off that? If I'm running GDM on tty7 and, that's my main setting? I know I can go to the login screen of GDM and change it but, depends on how I can get moblin packaged, etc. Just thinking ahead... project will probably never get started... Maybe when I have time, maybe, but, thanks so much for the TTY thing!

---

### Post by x33a on 2010-02-22
> **paddy.melon said:**
> Sweet, is it possible to then launch, say KDM off that? If I'm running GDM on tty7 and, that's my main setting? I know I can go to the login screen of GDM and change it but, depends on how I can get moblin packaged, etc. Just thinking ahead... project will probably never get started... Maybe when I have time, maybe, but, thanks so much for the TTY thing!

yes, you can lauch kdm also. just keep it in your .xinitrc.

---

