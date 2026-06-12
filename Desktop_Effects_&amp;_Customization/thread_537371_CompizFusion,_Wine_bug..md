---
title: "CompizFusion, Wine bug."
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by umanzor on 2007-08-28
Since a lot happened since the disastrous CF update, I'm not sure if this a CF or Wine bug. Anyways, while using CF some wine decorations don't appear. But it looks like it only happens to some windows. 

[[IMG]http://img440.imageshack.us/img440/6097/untitledpt3.jpg[/IMG]](http://imageshack.us)

Is there any fix?

(he, btw, I'm using IE because I need to use some site that only works with IE)

---

### Post by michael37 on 2007-08-30
Wine is nearly incompatible with Internet Explorer and is nearly incompatible with Xgl/Compiz.  Congratulations with running this combination at all :)

If you want to run IE in Wine, I recommend [ies4linux](http://www.tatanka.com.br/ies4linux/page/Main_Page).  If you want to run Wine, I recommend not using Compiz -- [Wine FAQ](http://wiki.winehq.org/FAQ#head-f1ef104fbe61a4f294662f26e09f325c9271e671).  But I like Compiz, so I don't run Wine.

My personal solution is running a virtual machine for IE (yes, I also need to access some websites using IE).  My personal favourite is [ VirtualBox](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html), although, if you CPU is brand new, you may be better off with KVM (kernel virtual machine).

---

### Post by umanzor on 2007-08-30
ies4linux uses Wine actually. It's a rather strange problem, after a while, the decorations appear. But it's really annoying since the window perse is not being handled by compiz, so it can't be move, resized, and appears in every viewport and on top of everything. As I said, after some minutes, the decorations appear and it begins to work as it should...

Weird.

---

### Post by michael37 on 2007-08-31
> **umanzor said:**
> ies4linux uses Wine actually. 
I am aware of that, but ies4linux configures Wine in a very funky way to make it work with IE.  

> **umanzor said:**
> It's a rather strange problem, after a while, the decorations appear. But it's really annoying since the window perse is not being handled by compiz, so it can't be move, resized, and appears in every viewport and on top of everything. As I said, after some minutes, the decorations appear and it begins to work as it should...

Weird.

Which version of compiz you are running?  Please run  ```
sudo dpkg -l | egrep "decor|compiz"
```

---

### Post by Rupertronco on 2007-08-31
It's a problem with the newest version of Wine and how it ineracts with compiz. If you use any other window manager it operates just fine. i'm using compiz core .55 with the newest wine, and i just end up running wine apps on desktop environments where i dont use compiz.

---

