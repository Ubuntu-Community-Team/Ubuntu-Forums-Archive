---
title: "skype: log in problem"
date: 2005-12-15
forum: Desktop Environments
---

### Post by rheology_boy on 2005-12-15
hi, 
i have installed a variety of skype versions, which all seem to run fine until the point where you have to create an account or log in as an existing user. 

however, for every version, i'm unable to enter more than three letters for the password, i.e. make more than three characters appear as stars in the box.  therefore i can't log in ( - skype requires at least four letters; the next arrow at the bottom is not active, and i assume that this is why.)

 any suggestions?
-Chris

---

### Post by anil_robo on 2005-12-16
Make sure you downloaded skype from [www.skype.com](www.skype.com). If you downloaded from somewhere else, it's credibility might be questionable. It may even be a hack!

Redownload skype from [www.skype.com](www.skype.com), check md5 checksums if possible and match those. Delete the .skype directory from your home directory. Make a fresh install of skype. Then try logging in. Even if you see only three letters and no "next" sign, try entering the full password with keyboard and press ENTER... it may just be a display problem ;)

---

### Post by veehell on 2005-12-20
I have similar problem, at home without "proxy" it is ok. But at work with proxies and lotta fw it is impossible for 5mins to succesfully login to skype. (installed, run-able, just only connect or create new just stuck in "connecting ... " without any error :(

I read some stuff here related to skype vs proxies and also on skype.com. They just point me to set the proxy via gnome and fireforx has own settings (but without password or any auth.)

For me it seem to be problem to provide user/pass to proxy to let me go thru. /just imho/. (i had problems with synaptic too(but it is solved already via the gnome proxy setting > Preferencies > Network Proxy, there is also user/pass to provide to. So i did it. But skype still on "connecting..." 

Also i check the files for skype, if there is some kind of config (yep it is) but no any info related to proxy :( Anyone know how to ?

---

### Post by lorenzo on 2006-05-30
Any solution to this proxy problem? I have just installed Skype and I cannot access the options menu and I cannot log in behind a proxy...

---

### Post by nematocyst on 2006-05-30
[QUOTE=rheology_boy]hi, 
i have installed a variety of skype versions, which all seem to run fine until the point where you have to create an account or log in as an existing user. 

however, for every version, i'm unable to enter more than three letters for the password, i.e. make more than three characters appear as stars in the box.  therefore i can't log in ( - skype requires at least four letters; the next arrow at the bottom is not active, and i assume that this is why.)

 any suggestions?
-Chris[/QUOTE]

I have this exact problem (not the proxy problem described later).  I believe it's related to heavily garbled passwords that I use, including shifted numbers and all the stuff in the bottom right area of a qwerty keyboard.

My "fix" to this problem was to click "forgot password" or whatever, and just use the password they sent me.  It wasn't as garbled, and I got past 3 chars just fine that way.

---

### Post by lorenzo on 2006-05-31
Regarding the proxy: here it is the solution...

In terminal type:

> export http_proxy=http://username:password@proxyserver:proxyport
> export https_proxy=http://username:password@proxyserver:proxyport
> skype

ciao,
Lo

---

### Post by Dafydd on 2006-07-11
> **lorenzo said:**
> Regarding the proxy: here it is the solution...

In terminal type:

> export http_proxy=http://username:password@proxyserver:proxyport
> export https_proxy=http://username:password@proxyserver:proxyport
> skype

ciao,
Lo

Nothing happens for me. Same problems... Can't get skype to connect behind university proxy which needs a password and username. Skype works on Windows on the same network...

Anyone have any other ideas?

Dafydd

---

