---
title: "gnotify anyone?"
date: 2005-09-17
forum: Desktop Environments
---

### Post by anatole on 2005-09-17
hi,
i was searching for a program that shows a notification when something happens (for example i'm using a script for mp3 conversion, so i could include a line to drop a notification when encoding is done etcetera)

i found gnotify: [http://gnotify.sourceforge.net/](http://gnotify.sourceforge.net/) which looks like exactly what i was looking for, but there are some problems. i realized that it is not in ubuntu so i installed it from an outer .deb from sourceforge, and i can't get it to work, in fact, i do not understand how should it work, and i found no support for it.
are here anyone using gnotify? how did you get it to work? or is there some howto for that?

---

### Post by kwaanens on 2008-03-05
Late,late, late, but 
notify-send (from libnotify-bin package)
or
zenity
might do what you need.

---

### Post by mkarnicki on 2008-03-09
**@kwaanens**

Thanks very much! Late, but very useful piece of information \\:D/. Just what I've been looking for, so good you have answered. I'd like to make use of notify-send, because it's really well gnome standarized, but I can't find any documentation for it (neither googling nor man). Can any one tell me where I can find some tips about notify-send? Zenity's rather not what I need.. Cheers

**EDIT**

I found little more info using notify-send --help , but any more documentation would be also helpful.

---

### Post by kwaanens on 2008-03-09
man notify-send 
in a terminal will give you much info.

---

### Post by mkarnicki on 2008-03-09
Yes, thank you. Like I edited in the last post. But even this:

[http://www.galago-project.org/specs/notification/0.9/index.html](http://www.galago-project.org/specs/notification/0.9/index.html)

is still little. I don't know how to make use of icon nor category.. And I'd really like much to make it work.

**EDIT**

I'm struggling, but making progress to use it's more "advanced" parameters. Thank you.

---

### Post by chewearn on 2008-03-09
Here:
[http://www.galago-project.org/news/index.php](http://www.galago-project.org/news/index.php)

Click on "Specifications" on the right side of the page.  It's a bit cryptic, but some experimentations should help you figure out what works, and what don't.

EDIT:
Opps,a bit late...

For icon, just add -i option, followed by the path of the icon.  E.g.
```
notify-send -u normal -i <path/icon> -t 5000 "Title" "Message"
```

---

### Post by mkarnicki on 2008-03-10
> **AstalaVista said:**
> Here:
[http://www.galago-project.org/news/index.php](http://www.galago-project.org/news/index.php)

Click on "Specifications" on the right side of the page. 

Yup, I found it ^ ^ But still, thanks. And for the tip about icon. Cheers.

---

