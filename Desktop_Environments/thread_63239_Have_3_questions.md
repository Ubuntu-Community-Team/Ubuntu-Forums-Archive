---
title: "Have 3 questions"
date: 2005-09-07
forum: Desktop Environments
---

### Post by D3k on 2005-09-07
I have some problems

1)Why it says that I have no X when compiling some app?
2)Why I can't become root in KDE Control Center?
3)How can I share my dial-up connection using samba?

I'm using Kbuntu 5.04 with KDE 3.4.0 and some parts of GNOME 2.10.

---

### Post by frodon on 2005-09-07
3) I don't know with samba but you can share your connection with [firestarter](http://www.fs-security.com/docs/connection-sharing.php) (it's a firewall with a really nice GUI).

---

### Post by GeneralZod on 2005-09-07
[QUOTE=D3k]I have some problems

1)Why it says that I have no X when compiling some app?
2)Why I can't become root in KDE Control Center?
3)How can I share my dial-up connection using samba?

I'm using Kbuntu 5.04 with KDE 3.4.0 and some parts of GNOME 2.10.[/QUOTE]

1)

You need to install the x11 development headers; search synaptic for 

x11 dev

and install.  I *think* the exact package is called libx11-dev, but I'd search just in case.

2) It's a well-known and highly annoying bug in Kubuntu that has never been fixed.  A workaround is to invoke kcontrol via

```

sudo kcontrol

```

I'm hoping it will be fixed for the next release.

---

### Post by yhotg on 2005-09-07
[QUOTE=GeneralZod]1)

You need to install the x11 development headers; search synaptic for 

x11 dev

and install.  I *think* the exact package is called libx11-dev, but I'd search just in case.

2) It's a well-known and highly annoying bug in Kubuntu that has never been fixed.  A workaround is to invoke kcontrol via

```

sudo kcontrol

```

I'm hoping it will be fixed for the next release.[/QUOTE]

general, do u use synaptic in KDE? or kynaptic?

---

### Post by GeneralZod on 2005-09-07
[QUOTE=yhotg]general, do u use synaptic in KDE? or kynaptic?[/QUOTE]

I use synaptic personally, as it is far superior - hopefully, I'll be able to use Adept, soon, though :).  You may need to install some additional libraries (as obviously, synaptic is not a Qt/KDE app), but I have absolutely no objection to doing this.  Some people like to keep their systems 100% GNOME or 100% KDE, though.

---

### Post by yhotg on 2005-09-07
[QUOTE=GeneralZod]I use synaptic personally, as it is far superior - hopefully, I'll be able to use Adept, soon, though :).  You may need to install some additional libraries (as obviously, synaptic is not a Qt/KDE app), but I have absolutely no objection to doing this.  Some people like to keep their systems 100% GNOME or 100% KDE, though.[/QUOTE]

yes, i am waiting for adept too. 
so u just did apt-get install synaptic  ?? and that takes care of the libraries right?

and about the x11-dev, which one is the one to apt-get?

libx11-dev - X Window System protocol client library development files
libxi-dev - X Window System Input extension library development files
x-dev - X protocol development files
xlibs-dev - X Window System client library development files transitional package

i just had for the first time the same problem while trying to compile Ktranslator with kinstaller....

checking for X... 
configure: error: Can't find X includes. Please check your installation and add the correct paths!


er... is Kinstaller alright, no? or it has problems too?

---

### Post by GeneralZod on 2005-09-07
[QUOTE=yhotg]yes, i am waiting for adept too. 
so u just did apt-get install synaptic  ?? and that takes care of the libraries right?
[/QUOTE]

Yes, and yes :)

[QUOTE=yhotg]
and about the x11-dev, which one is the one to apt-get?

libx11-dev - X Window System protocol client library development files
libxi-dev - X Window System Input extension library development files
x-dev - X protocol development files
xlibs-dev - X Window System client library development files transitional package
[/QUOTE]

I'm not sure - try libx11-dev, and if that doesn't work, add in xlibs-dev.

---

### Post by yhotg on 2005-09-07
[QUOTE=GeneralZod]Yes, and yes :)



I'm not sure - try libx11-dev, and if that doesn't work, add in xlibs-dev.[/QUOTE]


didn't work  :|

---

### Post by D3k on 2005-09-08
Thank you, but here are some more questions (oh, i deeped in questions! :)).

Why Firefox does not start?
Why i can't edit K Menu?

---

### Post by D3k on 2005-09-27
Err, can anyone help me???

---

### Post by Paperjam on 2005-09-27
[QUOTE=D3k]Why Firefox does not start?
Why i can't edit K Menu?[/QUOTE]

Open a Konsole-Window and execute *kmenuedit* and *firefox*. If you receive error-messages, post them here.

---

