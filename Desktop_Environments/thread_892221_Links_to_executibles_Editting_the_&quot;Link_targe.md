---
title: "Links to executibles: Editting the &quot;Link target:&quot; line?"
date: 2008-08-16
forum: Desktop Environments
---

### Post by Hitorijime on 2008-08-16
As the title suggests, I need the ability to edit the link target line of a link within Ubuntu. I've had little success looking around for a solution to my problem, so I thought I'd try asking you guys.

Sorry if this ended up in the wrong forum, first post/thread. :)

---

### Post by ad_267 on 2008-08-17
I don't think there's a simple way to do this in the file browser. One option would be to delete the link and then create a new link (You can drag files or folders with the middle mouse button to create a link).

You can also do this from the command line using "ln -sf /path/to/target link_name"

the f option means force, so it overwrites existing links.

---

### Post by Hitorijime on 2008-08-20
I don't think that would do it, if I'm understanding you correctly. Perhaps I should be more specific. Specifically, what I need to do is add an IP to the link target line.

---

### Post by wgarn on 2010-07-29
> **ad_267 said:**
> I don't think there's a simple way to do this in the file browser. One option would be to delete the link and then create a new link (You can drag files or folders with the middle mouse button to create a link).

You can also do this from the command line using "ln -sf /path/to/target link_name"

the f option means force, so it overwrites existing links.

A more detailed description of the above - in context of broken target links, through changing the mounting point from '/media/sda1' to '/media/data'.
1. Open terminal (Applications >> Accessories >>Terminal)
2. go to the folder that contains the link (e.g. your desktop: cd /home/your-user-name/Desktop)
3. get the previous path (e.g. use file browser [Places >> Desktop] and copy from Properties)
4. use the above command and allow whitespaces in path and link name,e.g.

ln -sf '/media/data/Virtual Folder/file that is my actual link target.txt' 'My long original existing link name'
(Note: paste previous path and change the modified "mounting point")

---

### Post by Robert05 on 2010-07-29
Ubuntu forums is a community it is a complete Linux-based operating system**.**

---

