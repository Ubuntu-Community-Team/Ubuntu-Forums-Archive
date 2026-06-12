---
title: "How can I remove Beryl in command line?"
date: 2007-06-30
forum: Desktop Effects &amp; Customization
---

### Post by miLl3niUm on 2007-06-30
Sometimes when I install it I can only access command line. Can I remove it from there?

Thank You.

---

### Post by crimesaucer on 2007-06-30
I would do this to remove it in Terminal:

```
sudo apt-get remove beryl
```

```
sudo apt-get remove beryl-manager
```

or to purge...

```
sudo apt-get remove --purge beryl
```


```
sudo apt-get remove --purge beryl-manager
```

---

### Post by miLl3niUm on 2007-06-30
What's purge?

---

### Post by crimesaucer on 2007-06-30
I could be wrong...but I think it is a more thorough way of removing something. It removes marked packages which are scheduled to be purged.

---

### Post by miLl3niUm on 2007-06-30
Anyway, I won't use it (I mean the purge command). Thank you very much for your help and fast reply :D

---

### Post by miLl3niUm on 2007-06-30
Dammit, I open Beryl Manager, I select "Select Window Manager > Beryl" but it changes to Metacity. What do I do now?

EDIT: Should I install Emerald?

---

### Post by crimesaucer on 2007-06-30
As for installing it, you should follow the correct wiki guide for whatever version of ubuntu that you use, also for which graphics card you use.

This is the Beryl wiki (the 2nd one is for Edgy and AiGLX), all though it seems that the site is down right now: 

[http://wiki.beryl-project.org/](http://wiki.beryl-project.org/)
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

---

### Post by miLl3niUm on 2007-06-30
I have Feisty 7.04 with ATI Radeon 9200. Also package "xorg-driver-fglrx" installed.

EDIT: And is the server down? I cannot connect :(

---

### Post by crimesaucer on 2007-06-30
There should be an installation wiki for Feisty and ATI...just Google it, also search the Ubuntu Forums for an installation thread, and check out the installation for Feisty and ATI on this site: [http://wiki.beryl-project.org/](http://wiki.beryl-project.org/)

---

### Post by miLl3niUm on 2007-06-30
I searched but I didn't find any.

And Beryl's website:
[img]http://www.uploadyour.info/uploads/images/asd39502.png[/img]

---

### Post by crimesaucer on 2007-06-30
It's working now: [http://wiki.beryl-project.org/wiki/Support_for_ATI_cards](http://wiki.beryl-project.org/wiki/Support_for_ATI_cards)

---

