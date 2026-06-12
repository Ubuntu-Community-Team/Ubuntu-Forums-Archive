---
title: "How to repair Ubuntu"
date: 2009-04-23
forum: General Help
---

### Post by robbyc on 2009-04-23
How do I repair Ubuntu 9.04. I know I could do a fresh install as I hadn't fully configured not yet but I would like to know for the next time :-).

I had a working installation of Ubuntu 9.04 RC on my USB flash drive. I went to Add/Remove and added the restricted drivers package and the ATI Binary X.org driver. 

When I restarted my system I saw the progress bar which continued all the way to the end but when the system tried to display the login screen it went black. I am guessing the display driver has messed up.

My questions are:
1. Is there a way to boot into a command line instead so I can remove the packages using it?
2. I am sure there use to be a repair option when booting for the ubuntu CD, has this been removed? 
3. Any other suggestions on how I can remove these packages or get my system working again?

Many thanks

---

### Post by oldos2er on 2009-04-23
Boot into recovery mode, choose 'xfix' from the menu.

---

### Post by robbyc on 2009-04-23
How does one boot into recovery mode? Thanks

---

### Post by robbyc on 2009-04-23
Ah I was being silly. Obviously on the Grub boot screen will try it now.

---

### Post by robbyc on 2009-04-23
xfix did not fix the promblem, any other suggestions? Cheers

---

### Post by ubu-for on 2009-04-23
> **robbyc said:**
> xfix did not fix the promblem, any other suggestions? Cheers

Try this.

[http://ubuntuforums.org/showpost.php?p=7128360&postcount=2](http://ubuntuforums.org/showpost.php?p=7128360&postcount=2)

---

### Post by aronk on 2009-04-30
> **robbyc said:**
> How do I repair Ubuntu 9.04. I know I could do a fresh install as I hadn't fully configured not yet but I would like to know for the next time :-).

I had a working installation of Ubuntu 9.04 RC on my USB flash drive. I went to Add/Remove and added the restricted drivers package and the ATI Binary X.org driver. 

When I restarted my system I saw the progress bar which continued all the way to the end but when the system tried to display the login screen it went black. I am guessing the display driver has messed up.

My questions are:
1. Is there a way to boot into a command line instead so I can remove the packages using it?
2. I am sure there use to be a repair option when booting for the ubuntu CD, has this been removed? 
3. Any other suggestions on how I can remove these packages or get my system working again?

Many thanks

I had the same problem and I've just fixed it.. :)
Boot into recovery mode, select the netroot option (root shell with networking enabled) and log in. Then type:
```

apt-get remove fglrx*
```this will remove the ATI packages. When it's finished type:
```

dpkg-reconfigure xserver-xorg
```Finally reboot and X should work :)[/code]

---

### Post by Swindlerz on 2009-12-08
> **aronk said:**
> I had the same problem and I've just fixed it.. :)
Boot into recovery mode, select the netroot option (root shell with networking enabled) and log in. Then type:
```

apt-get remove fglrx*
```this will remove the ATI packages. When it's finished type:
```

dpkg-reconfigure xserver-xorg
```Finally reboot and X should work :)[/code]

LOL thanks v.much it just fixed my ubuntu.
I tried installing the graphics driver but it decided to destroy my ubuntu OS.
I am lucky i bumped into this thread (via ubuntu live CD) 
I was at the point of clicking reformat hdd and install the OS all over again. heh

Ubuntu should make a repair disc or connect to server and repair.

---

