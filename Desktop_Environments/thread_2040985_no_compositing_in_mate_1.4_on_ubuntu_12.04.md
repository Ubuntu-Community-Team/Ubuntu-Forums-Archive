---
title: "no compositing in mate 1.4 on ubuntu 12.04?"
date: 2012-08-11
forum: Desktop Environments
---

### Post by LLCoolJeff on 2012-08-11
Hello I recently installed mate 1.4 on my 12.04 ubuntu system and two things happened that puzzled me:

1. A lot of system apps are double installed (screensaver, system monitor, calculator, etc) is this normal for this install?

2. Mate has no composting for desktop effects for things like docky. Is there a way to enable this?

I don't know if I botched the install somehow, or if this is how it is supposed to be but I would like to know how to fix it. Should I completely uninstall mate and then reinstall from scratch? if so, how do I do this?

Thanks for your help...

---

### Post by vexorian on 2012-08-11
1. Yes. Because Mate has forked all of GNOME's apps. But if you installed ubuntu through normal means, all of GNOME's apps are still there. If it is a hidrance you might have to uninstall either the gnome or mate versions

2. Accordign to this: [http://www.dedoimedo.com/computers/linux-mint-mate.html](http://www.dedoimedo.com/computers/linux-mint-mate.html) there should be a customization menu that allows you to enable compositing.

---

### Post by LLCoolJeff on 2012-08-11
I do not have the desktop settings in my MATE, maybe because I do not have mint installed like on the picture?

also in the windows manager (system>preferences>windows) there is no composting option....Why would this be?

EDIT: I have compiz FYI, and I cannot find anything in compizconfig either that would let me enable composting, where could it have gone?

---

### Post by lisati on 2012-08-12
I've edited the thread title. :D

---

### Post by orange2k on 2012-08-12
I think this might help:

[http://www.tuxgarage.com/2012/05/run-mate-with-compiz-in-ubuntu.html](http://www.tuxgarage.com/2012/05/run-mate-with-compiz-in-ubuntu.html)

---

### Post by flyingfisch on 2012-09-26
Here is another option, if you do not want to use compiz:

```

sudo apt-get install mate-conf-editor
mateconf-editor

```

Now in the mateconf-editor, go to Apps>Marco>General. Click the checkmark next to "compositing_manager".

Hope that helps ;)

---

