---
title: "Ubuntuforums notifications via  notify-osd"
date: 2012-06-01
forum: Forum Feedback &amp; Help
---

### Post by krustenBrot on 2012-06-01
Hey,

i was wondering if it is possible to integrate for example ubuntuforums.org into my "Messages" tab in the upper panel and enable notifications on e.g. answers to a opened thread.
maybe something similar to [*FBuntu*]("http://www.webupd8.org/2011/07/fbuntu-facebook-notifier-with-ubuntu.html")..

):P

---

### Post by sffvba[e0rt on 2012-06-01
*Thread moved to **Forum Feedback & Help**.*


404

---

### Post by 700 on 2012-06-28
That's a good idea. I've been thinking about it, but I need to get familiar with notify osd first. Do you know any places to get sample python scripts with notify osd implemented, or pdf's with good tutorials about that?

---

### Post by MG&amp;TL on 2012-06-28
I had been thinking about doing something this for the Ubuntu App Showdown, but it seems Vbulletin doesn't have an API reference to speak of, so I was a bit stuck.

I also tried implementing my own web scraper. That worked, but it was a pain in the rear to do, and still had problems.

@ 700:
[PHP]import pynotify
pynotify.init("My app")
n = pynotify.Notification("Title", "Content here", "applications-games") #Title, Content, Icon name
n.show()[/PHP]

---

