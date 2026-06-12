---
title: "Which Konqueror to link to desktop?"
date: 2008-08-21
forum: Desktop Environments
---

### Post by Silversleeves on 2008-08-21
Hi,

I found creating an application link to the GiMP a lot easier than this.

Basically what I am looking to do is create an application link to Konqueror on my Kubuntu desktop, not for Web browsing but more to navigate the filsystem (alongside Dolphin, not in place of it). I've browsed /usr/share/applications/kde in Dolphin and I see quite a few components of Konqueror there, the greater number of which seem to handle URLs from the Web. I'd like to know if linking to one of these would launch the application, so that all I'd have to do right away would be to "show the navigation pane" and proceed as usual.

Hope someone has an idea.

Silversleeves

---

### Post by Ubuntiac on 2008-08-21
From memory I think it's:

```
/usr/lib/kde/bin/kfmclient openProfile filemanagement
```

---

### Post by maybeway36 on 2008-08-21
Close:
```
/usr/bin/kfmclient openProfile filemanagement
```

---

