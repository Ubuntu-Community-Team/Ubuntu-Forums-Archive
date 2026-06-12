---
title: "kde-desktop uninstall"
date: 2007-10-26
forum: Desktop Environments
---

### Post by jimmy the saint on 2007-10-26
so I used the method described in the Pshycocats website that is linked to in a few thread on this issue: using aptitude rather than apt-get.  In theory, this means that when I go back and Input
"sudo aptitude remove kubuntu-desktop" everything that it installed should be removed.  Unfortunately this was not the case.  I now have tons of programs that I do not need.  The only thing it removed was 1 package that was 45.1kB.  Has aptitude changed?  
In case anyone is interested, I wanted to try KDE to see if the all the window edge tearing that I am experiencing with my nvidia card would be fixed.  It wasn't.  Oh well, I guess we just need to wait for someone to come up with a way for the new crop of nvidia mobile cards to work nicely with linux.

---

### Post by Tanker Bob on 2007-10-26
What NVidia card are you using? My 8800GTS works perfectly in Linux with NVidia's drivers.

---

### Post by benerivo on 2007-10-26
I don't know if it has changed but you could try```
sudo apt-get autoremove
```to see if it takes the other kde packages away. Failing that, just go in to synaptic and search for kde, then remove all packages other than the ones that will also remove standard ubuntu packages.

---

### Post by TeaSwigger on 2007-10-27
Hello, the psychocats site provides two methods. If you didn't install it with aptitude that first way won't work. Go back to the psychocats website and use the second method.

---

### Post by jimmy the saint on 2007-10-28
I saw the second method right after I posted this.  I ended up also runninght the auto-remove command. Thanks!!

I have the quadro nvs 140, which is supposed to be pretty much the same as an 8600? I believe.  It is mostly just a lot of tearing and garbled animations.  purely cosmetic, but still a little irritating considering its a new laptop with more than enough pure graphics power to run a desktop.  oh well.

---

