---
title: "Move font from fedora to ubuntu"
date: 2008-12-19
forum: General Help
---

### Post by ftornell on 2008-12-19
Hi, have another computer that runs fedora 10 that has a font called qub.

A neat 6px font that I would like to have on my other ubuntu installations.

I think it is part of the mplus-font package but after installing the package it wont show up.

The file is not a ttf file so i can't copy it over!

mplus-qub: 6px

any tips?

---

### Post by Elfy on 2008-12-19
Hi install xfonts-mplus, qub is in there.

```
sudo apt-get install xfonts-mplus
```

---

### Post by ftornell on 2008-12-20
Hi, i have installed that one but the font does'nt appear in the fontlist when opening the appearance tool...

Any hints?

---

### Post by ftornell on 2008-12-20
any suggestions?

---

### Post by Elfy on 2008-12-20
I hadn't forgotten - I've managed to find the font after it installs it's called

mplus_q06r.pcf.gz in /usr/share/fonts/X11/misc

Although I haven't as yet been able to use it anywhere - I also tried to extract it from the source and have, but that is unusable anywhere too.

I'm still digging though.

I checked whether there was a bug reported for the package - there isn't as yet - might be worth you doing so, if you do link here and I will confirm it.

If you've never done so then this should help - [http://ubuntuforums.org/showpost.php?p=6367705&postcount=1](http://ubuntuforums.org/showpost.php?p=6367705&postcount=1)

This is wher eit would need to be reported I think
[https://bugs.launchpad.net/ubuntu/intrepid/+source/xfonts-mplus](https://bugs.launchpad.net/ubuntu/intrepid/+source/xfonts-mplus)

---

### Post by ftornell on 2008-12-20
> **forestpixie said:**
> I hadn't forgotten - I've managed to find the font after it installs it's called

mplus_q06r.pcf.gz in /usr/share/fonts/X11/misc

Although I haven't as yet been able to use it anywhere - I also tried to extract it from the source and have, but that is unusable anywhere too.

I'm still digging though.

I checked whether there was a bug reported for the package - there isn't as yet - might be worth you doing so, if you do link here and I will confirm it.

If you've never done so then this should help - [http://ubuntuforums.org/showpost.php?p=6367705&postcount=1](http://ubuntuforums.org/showpost.php?p=6367705&postcount=1)

This is wher eit would need to be reported I think
[https://bugs.launchpad.net/ubuntu/intrepid/+source/xfonts-mplus](https://bugs.launchpad.net/ubuntu/intrepid/+source/xfonts-mplus)

It's reported!

---

### Post by Elfy on 2008-12-21
Do you have a link for it?

---

### Post by Elfy on 2008-12-23
I'll add here the link to the answer

[https://bugs.edge.launchpad.net/ubuntu/+source/xfonts-mplus/+bug/310091](https://bugs.edge.launchpad.net/ubuntu/+source/xfonts-mplus/+bug/310091)
[http://ubuntuforums.org/showpost.php?p=3899496&postcount=4](http://ubuntuforums.org/showpost.php?p=3899496&postcount=4)

---

