---
title: "KeePass under WINE Autotype problem"
date: 2008-12-26
forum: Desktop Environments
---

### Post by bedachtm on 2008-12-26
I am relatively new to Ubuntu and I seem to have hit a brick wall on this one. I am a KeePass user on Windows (which I am trying to flee ASAP).

I installed KeePassx (from the Ubuntu library) and started using it with a copy of my Windows .kdb file. Everything seemed fine, except that the autotype (both from the drop down menu within KeePassx and the Ctl-Alt-A) did not work.

Thinking that this was a problem with the port to linux, I installed WINE and then the current (1.14) Windows KeePass version.

Result: Same Thing. From KeePass, using CTL-U I open the right page, but the CTL-ALT-A AND the menu option Autotype do nothing,

I went back to an older verion of KeePass (1.11) but same result.

Am I missing something? Is there some mystery to the Global Hot Key in Ubuntu that I haven't run across?

Can anybody help?

---

### Post by staticsage on 2009-01-07
I ran into an issue with auto-type in KeePassX. It appears that the 'Title' of the password entry has to be a partial match of the window title that you want to auto type into.

For example if you have an entry for google.com with yahoo as the title of the entry, it will not autotype (even if you have google.com in the URL field). If you change the title of the entry to google it works.

I don't run KeePass in wine so I'm not sure sure what to do with that, but I hope this helps.

---

### Post by bohemier on 2010-05-25
I know this is an old thread, but you have to install xdotool to make autotype work

---

### Post by DiagonalArg on 2011-02-23
Details at the bottom of this page:

[http://keepass.info/help/v2/setup.html](http://keepass.info/help/v2/setup.html)

At this moment, the Ubuntu repository's version of xdotool is too old.  The only debs availalbe at the xdotool website are 64-bit.

---

