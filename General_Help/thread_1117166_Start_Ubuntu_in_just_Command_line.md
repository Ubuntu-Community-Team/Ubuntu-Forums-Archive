---
title: "Start Ubuntu in just Command line"
date: 2009-04-05
forum: General Help
---

### Post by helstreak on 2009-04-05
I would like to start Ubuntu in just the command line with no windowing stuff such as Xorg.  I have a computation that needs all the computer it can get so nothing unnecessary should be started.  How can I do that?

Thank you very much :) :) :)

---

### Post by Cybie257 on 2009-04-05
see this link. It might be what you are looking for:

[https://lists.ubuntu.com/archives/ubuntu-users/2005-July/044261.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-July/044261.html)

-Cybie

---

### Post by night_fox on 2009-04-05
[http://ubuntuforums.org/archive/index.php/t-250566.html](http://ubuntuforums.org/archive/index.php/t-250566.html)

3 ways,
1st one is bad as it gives you full on root access,
3rd one requires internet.

Personally, I would start it normally, do Ctrl+Alt+F1, maybe have to do it twice on my Intrepid, then kill all processes using too much memory, cpu that are clearly associated with the graphical interface, anything to do with compiz, x, metacity, gnome, etc.

Wireless is hard to do from the command line though.

---

### Post by Cybie257 on 2009-04-05
Better yet, use this method. 

[http://www.nvnews.net/vbulletin/showthread.php?t=79966](http://www.nvnews.net/vbulletin/showthread.php?t=79966)

It doesn't require killing anything and just shuts down Xserver and easily lets you start it up again.

-Cybie

---

### Post by helstreak on 2009-04-05
> **night_fox said:**
> [http://ubuntuforums.org/archive/index.php/t-250566.html](http://ubuntuforums.org/archive/index.php/t-250566.html)

3 ways,
1st one is bad as it gives you full on root access,
3rd one requires internet.

Personally, I would start it normally, do Ctrl+Alt+F1, maybe have to do it twice on my Intrepid, then kill all processes using too much memory, cpu that are clearly associated with the graphical interface, anything to do with compiz, x, metacity, gnome, etc.

Wireless is hard to do from the command line though.

How can i kill a process from the terminal?

---

### Post by mb_webguy on 2009-04-06
IMO, the best way is to simply [add a console login entry to the GRUB menu]("http://ubuntuforums.org/showthread.php?p=6782289&highlight=console+grub#post6782289").

---

### Post by Hospadar on 2009-04-06
> **helstreak said:**
> How can i kill a process from the terminal?

If you go to a terminal with Ctrl-Alt-F1, you can kill your entire X session and everything running in it with ```
sudo /etc/init.d/gdm stop
``` if you are running vanilla ubuntu
for kubuntu and xubuntu run kdm and xdm (respectively) instead of gdm.

Also I believe you can remove the gdm init script using "update-rc.d" This'll mean when you boot up you'll just get a terminal, then if you want a graphical session, you login and```
sudo /etc/init.d/gdm start
```You might want to read up on that.

You might also just want to install ubuntu server if you don't need X on the machine, or install server then build up a fluxbox desktop or something else light like that.

---

