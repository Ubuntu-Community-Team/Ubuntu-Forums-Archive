---
title: "Dolphin Html file misfire to Amarok in Hardy"
date: 2008-04-30
forum: Desktop Environments
---

### Post by nadrach on 2008-04-30
I've just upgraded 7.10 to 8.04 on an old desktop and dropped 8.04 onto a newer Advent laptop. Both have the same quirk in Dolphin. With dolphin displaying "Detail" format, hovering the mouse pointer over a file with ".html" extension will trigger an error message as follows:

The desktop entry file

/usr/share/apps/d3lphin/servicemenus/amarok_addaspodcast.desktop

has an invalid menu entry

addAsPodcast.

The specified Amarok desktop file appears to be correct. My guess is that Dolphin is incorrectly trying to "preselect" Amarok instead of Konqueror, for the HTML file type. Unfortunately, this makes it nearly impossible to select an ".html" file in Dolphin to do anything with it (although bloodymindedness and a quick mouse can persevere), because the error message keeps appearing within a second of hovering the mouse pointer, disabling file operations until the message is acknowledged.

Is there a fix for this?

---

### Post by Xiong Chiamiov on 2008-05-02
I noticed this the other day when I was right-clicking an xml file (I always have my file manager set to double-click).  Since I don't use podcasts, much less add them to amarok through the file manager, I just renamed that file:
```

cd /usr/share/apps/d3lphin/servicemenus/
sudo mv amarok_addaspodcast.desktop amarok_addaspodcast.desktop_

```
and it's fine.

---

### Post by nadrach on 2008-05-06
Fine ... that gets rid of the problem, but it should not be there in the first place. Checking the file type properties for html/htm and xml shows no attachments to Amarok, so why is it being called at all? What is dolphin doing?

---

### Post by Xiong Chiamiov on 2008-05-06
XML I know at least is for podcasts, but I can only guess that it's there for HTML files for the same reason?  It doesn't make much sense to me either.

---

### Post by dfpd62 on 2008-05-15
Thanks Guys.
That fix worked for me too, but I is it a bug or a feature that can be turned off?

---

### Post by Xiong Chiamiov on 2008-05-17
> **dfpd62 said:**
> Thanks Guys.
That fix worked for me too, but I is it a bug or a feature that can be turned off?
I have no idea.  Once the problem went away, I stopped caring.

---

