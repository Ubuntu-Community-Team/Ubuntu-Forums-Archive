---
title: "Managing file types in Firefox with Kubuntu 8.10"
date: 2009-01-23
forum: General Help
---

### Post by Dieseler on 2009-01-23
Hello

I have a little dilemma with Firefox and its open with dialog. When I click the open with, it gives me folders rather than installed application choices to open the file with.
Anyone know of a work around for this?

---

### Post by hwttdz on 2009-01-23
Is edit->preferences->applications what you're looking for?

---

### Post by Dieseler on 2009-01-23
> **hwttdz said:**
> Is edit->preferences->applications what you're looking for?

Yes, but this is what I am getting instead of an application list.

[IMG]http://i45.photobucket.com/albums/f99/Dieselerpics/snapshot1.png[/IMG]

There must be a folder to link to that will display the list of applications I think.

---

### Post by Dieseler on 2009-01-23
[[IMG]http://www.threadbombing.com/data/media/2/th_popcorncat.gif[/IMG]](http://www.threadbombing.com/details.php?image_id=3428)

Nobody knows?

---

### Post by hwttdz on 2009-01-23
Yeah, that's the correct behavior.  If you want to use a certain program you only need to know the name of that program.  And then you say:
which programname
and then it will give something like
/path/to/program/programname
and then you just copy and paste that stuff into the box.  

For example deluge would be
/usr/bin/deluge
and transmission would be
/usr/bin/transmission

Let me know if that was confusing.  I'm tired and hungry and not 100% lucid.

---

### Post by Dieseler on 2009-01-23
Thanks hw

I worked it out with that.
You telling me the path /usr/bin was the only way I found it though, Otherwise I would have been searching through system folders for awhile.
Not very intuitive. 
I have been using Firefox with Gnome 8.04 for awhile now and I don't remember ever having to do this.
Open would give a list of Apps and Open containing folder would do just that, open the folder the download was in.
Maybe its just a side effect of using a gnome app with Kde. 
I'm puzzled.

I also noticed that now when I go /Tools/Downloads/Open Containing Folder, it opens the app instead of the location.
Lolz.

---

