---
title: "Opera installation Problems"
date: 2006-01-03
forum: Desktop Environments
---

### Post by mustang on 2006-01-03
Hello everyone,

I am trying to install opera. I downloaded the ubuntu breezy .deb from their site. I made sure to download any dependencies (libqt3c102-mt)

Then I installed the .deb (no problems so far)

When I type "opera" in the terminal, I get:

```

/usr/lib/opera/8.51-20051114.6/opera: Symbol `_ZTI11QDragObject' has different size in shared object, consider re-linking
/usr/lib/opera/8.51-20051114.6/opera: Symbol `_ZTI10QPopupMenu' has different size in shared object, consider re-linking
/usr/lib/opera/8.51-20051114.6/opera: Symbol `_ZTI7QPixmap' has different size in shared object, consider re-linking
/usr/lib/opera/8.51-20051114.6/opera: Symbol `_ZTI7QWidget' has different size in shared object, consider re-linking
Fontconfig error: "local.conf", line 1: no element found
opera: Preference initialization failure. Generic failure (-1)

```

I also tried the alternate method to install opera by editing by sources file and installing via synaptic. Still no deal.

Any help would be appreciated.

---

### Post by Zelut on 2006-01-03
I'd check out details here:
[https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera](https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera)

includes manual installation &/or installation thru apt.  Might be a bit easier.

---

### Post by mustang on 2006-01-03
Hi kuyaedz,

I've tried the both ways explained on the page and the troubleshooting options. Nothing will fix it. Although, I have managed to shorten the error:

```

Fontconfig error: "local.conf", line 1: no element found
opera: Preference initialization failure. Generic failure (-1)

```

Any ideas??

---

### Post by mustang on 2006-01-03
*bump*

Anyone?

---

### Post by mustang on 2006-01-04
last bump. Anyone please? I'd really like to get opera running again. I've tried all three methods of installing opera (.deb from opera website, through synaptic, through the tar.gz). All of them return the same error:

```

opera: Preference initialization failure. Generic failure (-1)

```

Thank you...

---

### Post by dandeguire on 2006-01-05
I just installed Opera 8 on Ubuntu 5.10 using the instructions from the second post.  Opera installed just fine, but none of the plugins work.

Dan

---

### Post by Sef on 2006-01-05
Have you checked the Opera website for help either from forums or FAQs?

---

### Post by mustang on 2006-01-10
[QUOTE=Sef]Have you checked the Opera website for help either from forums or FAQs?[/QUOTE]

Thanks a lot for your suggestion Sef. I ended up taking your advice and it solved my problem.

Here's the link in case other people are suffering from the same problem:

[http://my.opera.com/community/forums/topic.dml?id=119281](http://my.opera.com/community/forums/topic.dml?id=119281)

---

### Post by msfz751 on 2006-04-22
Thans to these forums I could resolve the problem with Opera.
I didn't work the first time after deleting the .opera folder in the user directory. I reinstalled with Automatix and removed it with "apt-ger remove opera", and then deleted the folder ".opera", and finally had my Opera restored.

One thing, I noticed though is that when I do the "cat $HOME/automatix.log" it will show all the failed installation I tried with Opera, like this:

  $ cat $HOME/automatix.log
Open Office|Ripper and Tuner
Open Office
Nautilus Scripts
Ctrl-Alt-Del|Opera Browser
Ctrl-Alt-Del|Nautilus Scripts|Opera Browser|Gdesklets
Ctrl-Alt-Del|Nautilus Scripts|Opera Browser
Opera Browser
Wine
Opera Browser
Opera Browser|SUN JAVA 1.5 JRE
Opera Browser
Opera Browser
Opera Browser

Does this affect the future installations?

---

### Post by msfz751 on 2006-04-22
I am sorry. I forgot to mention that the new succesful installation of Opera will not work from Automatix if has to be done from the command line with:

$ sudo apt-get install opera

I am afraid some plugins will not work. Like Java, for instance.

---

