---
title: "generic vs server - funny problem?"
date: 2009-05-04
forum: General Help
---

### Post by abjt on 2009-05-04
I have two options (not including recovery options) in my grub list i.e. 9.04 server and 9.04 generic.

since the last few days I have encountered some odd behaviour on the "server" option.

when I select the server option to boot, it goes through and seems to boot up all the drivers etc but then ends up with a blank screen. The funny thing is 
- i can use the mouse (very entertaining to see the mouse cursor moving on a black screen:)
- i can connect to the mail server
- i can connect to the web page from other pc
- i can connect to the samba status page from other pc
- but i cannot connect via vnc

However when i select the generic option from the grub menu all works fine.

the only major activity i remember doing is setting up postfix and dovecot - i followed the instructions on ubuntu.com.

my hardware config is
- Intel DG45FC mother board with integrated graphics
- CD/DVD via USB
- Hauppauge TV card via USB
- nothing else.....

what do i need to do to get my server option back to what it was ?

---

### Post by abjt on 2009-05-04
bump... anyone? Normally i get pretty quick responses.

---

### Post by ptn107 on 2009-05-04
The 'server' option loads Ubuntu using the server kernel.  The 'generic' option loads Ubuntu using the desktop kernel of the same version.  If your using Ubuntu's graphical environment (GNOME, KDE, XFCE, etc...) you should be using the 'generic' option as each kernel is optimized for that particular type of system[1].  It is not recommended that you use a server kernel on a desktop system for various reasons, but one of the big ones is that some of your desktop hardware may not work.  Most of your server applications will work fine from a desktop kernel but not necessarily the other way around.  In fact, I would boot to your desktop using the 'generic' kernel and remove the server kernel entirely.  From a terminal...

1. Make sure generic packages are installed properly first:
```
sudo aptitude install linux-firmware linux-generic linux-headers-generic linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic linux-image-generic linux-image-2.6.28-11-generic linux-restricted-modules-common linux-restricted-modules-generic linux-restricted-modules-2.6.28-11-generic
```

2. Remove the server packages:
```
sudo aptitude remove linux-image-server linux-image-2.6.28-11-server linux-headers-server linux-headers-2.6.28-11-server linux-restricted-modules-server linux-restricted-modules-2.6.28-11-server
```

[1]_[Information about the server kernel]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel")_

---

### Post by abjt on 2009-05-04
Thanks.... but I'd like to retain the server option as I do intend to use it as a server. I am only planning to log on to it occasionally.
How do I repair it? I can't even log from a terminal.

i should have clarified... the ubuntu machine is not my desktop.

---

### Post by ptn107 on 2009-05-04
You may need to download an Ubuntu Desktop live CD in order to access your server system via terminal and make sure all appropriate packages are installed.  I know this doesn't quite answer your question but I would suspect a recent update broke something.

---

### Post by abjt on 2009-05-04
ptn107,

apologies, I am not sure I have understood it (look at my only 5 cups of ubuntu)
I had originally installed 8.10 from liveCD and it was working fine. The upgrade to 9.04 was also working fine until last week. also, my samba and mail servers are accessible from myy desktop but I cannot boot into the UI or connect via terminal. How do i repair it so that i can do both for the server option?

---

