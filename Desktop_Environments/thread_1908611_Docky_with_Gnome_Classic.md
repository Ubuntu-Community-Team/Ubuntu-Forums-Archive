---
title: "Docky with Gnome Classic"
date: 2012-01-13
forum: Desktop Environments
---

### Post by tava0002 on 2012-01-13
I have 64-bit Ubuntu 11.10 installed and I'm using Gnome Classic desktop.  I have Docky installed and it's working fine but I can't set it to autohide.

The hiding option is greyed out in the docky settings even after selecting a dock.

Any ideas to make it autohide?

---

### Post by cortman on 2012-01-13
You need to enable compositing in your DE. You can do this with Compiz Config Settings Manager

```
sudo apt-get install compiz
sudo apt-get install compizconfig-settings-manager
```

You'll find "compositing" as one of the options.

---

### Post by tava0002 on 2012-01-13
Thanks for replying, I already have those installed and the compiz settings manager has a check mark next to composite.

Is there a way to enable autohide in the config files?

```

$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.

$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
```

---

### Post by cortman on 2012-01-14
Hm... That's very odd.

Try opening a terminal and typing

```
gconf-editor
```

and go to apps> metacity> general. Make sure the compositing_manager checkbox is checked. Just in case compiz isn't working for whatever reason.

---

### Post by jarmore on 2012-01-17
> **cortman said:**
> Hm... That's very odd.

Try opening a terminal and typing

```
gconf-editor
```

and go to apps> metacity> general. Make sure the compositing_manager checkbox is checked. Just in case compiz isn't working for whatever reason.

I had same problem only with 32 bit Ubuntu 11.10 ... composting error message and 'autohide' was greyed out. The above quote fixed it all for me. Perfect!! Thank you!

---

### Post by afrendeiro on 2012-11-04
I have the same problem, using ubuntu 12.10 and gnome classic.
I just can't make compositing to work with docky.

Also, in gconf-editor and in metacity->general there's no compositing option.
I've added that manually with no effect.

Any ideas? Thanks

---

### Post by VideoRoy on 2012-11-06
> **afrendeiro said:**
> I have the same problem, using ubuntu 12.10 and gnome classic.
I just can't make compositing to work with docky.

Also, in gconf-editor and in metacity->general there's no compositing option.
I've added that manually with no effect.

Any ideas? Thanks

+1 I am having exactly the same problem.

Anyone have experience with this?  I am new to Docky.

Thanks.

---

### Post by VideoRoy on 2012-11-06
> **VideoRoy said:**
> +1 I am having exactly the same problem.

Anyone have experience with this?  I am new to Docky.

Thanks.

Solved my situation.  I had chosen "Gnome Classic No Effects"at login.  Choosing regular Gnome Classic solved.

---

### Post by wildmanne39 on 2012-11-06
Old thread closed.

---

