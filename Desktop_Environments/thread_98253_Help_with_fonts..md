---
title: "Help with fonts."
date: 2005-12-02
forum: Desktop Environments
---

### Post by mrmcctt on 2005-12-02
I have been having problems with fonts on a webpage that I go to at times.  I think I have narrowed it down to the msttcorefonts not being 'registered' (if that's the correct word) properly.

I have followed the instructions [here]("http://ubuntuguide.org/#extrafonts").  I have gotten to the ```
sudo fc-cache -f -v
``` which completed successfully.

When I go to the ```
sudo cp /etc/fonts/local.conf /etc/fonts/local.conf_backup
``` command, I get ```
rlodge@ubuntu:~$ sudo cp /etc/fonts/local.conf /etc/fonts/local.conf_backup
cp: cannot stat `/etc/fonts/local.conf': No such file or directory
rlodge@ubuntu:~$

```.

There is no /etc/fonts/local.conf.  How do I get one?  

I think this is why I'm having problems seeing some fonts in some web pages.

As always, any help is appreciated.

---

### Post by dcstar on 2005-12-02
[QUOTE=mrmcctt]I have been having problems with fonts on a webpage that I go to at times.  I think I have narrowed it down to the msttcorefonts not being 'registered' (if that's the correct word) properly.

I have followed the instructions [here]("http://ubuntuguide.org/#extrafonts").  I have gotten to the ```
sudo fc-cache -f -v
``` which completed successfully.
......
As always, any help is appreciated.[/QUOTE]

That is the 5.04 guide, 5.10 is different.

---

### Post by Xian on 2005-12-02
/var/lib/fontconfig/local.conf

---

### Post by mrmcctt on 2005-12-06
Just thought I'd finish this thread out.

I did not find a fix for the fonts on the Road Runner page.  I have two other systems set up with Ubuntu in my house and both of them display the page correctly.  The only thing I can figure is that it's a problem with my laptop and not Firefox or Flash.

Oh well,  I don't really need the page much.  I just like to try to fix things when they don't work right.

Thanks everyone for your help.

---

