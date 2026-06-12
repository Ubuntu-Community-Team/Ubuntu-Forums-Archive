---
title: "Nautilus, Places, and a Documents folder"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Lorian on 2006-08-22
In my home folder I have a folder named "Documents". I added it to the places bar, but it added it to both the main section with stuff like Desktop and File System, and in the section with my other folders. The problem is, I can't get rid of it, I can remove it from the second section, I can even delete the folder, but it just won't go away. Is there any way to get rid of it?

Here is a picture showing what I am talking about:
[[IMG]http://img241.imageshack.us/img241/536/documentstg5.th.png[/IMG]](http://img241.imageshack.us/my.php?image=documentstg5.png)

Cheers.

---

### Post by meng on 2006-08-22
It's supposed to go away when you (from the Nautilus file browser) go to Bookmarks > Edit Bookmarks.
EDIT: but I can't be sure it will cos that's a weird problem :(

---

### Post by Lorian on 2006-08-23
That only shows the folders in the second section.

---

### Post by wallacetheweasel on 2006-09-01
This has been bothering me to end! I've done alot of research on it, and I'd really like to see it resolved.  From what I've read, it seems that that behaviour is a modification that Ubuntu does to the Nautilus source.  I'd certainly like to see Ubuntu give an option somewhere to change that. Perhaps in gconf-editor? Anyways...

Until such time, I would like to be able to remove that change. I want to have a Documents folder in my home folder but not see it in the Places menu.  Honestly, I don't know why Ubuntu does it in the first place. If people want Documents in their Places menu, they can always add it in as a bookmark.  If someone can figure out how to apply a patch or do something equivalent to the nautilus source that undoes what Ubuntu did to add this "feature", please let me know.

This is what I have found on the topic:
[http://www.ubuntuforums.org/showthread.php?t=69369&highlight=places+documents](http://www.ubuntuforums.org/showthread.php?t=69369&highlight=places+documents)
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/22628](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/22628)

UPDATE: This forum post describes the behavior being implemented (among other things) in the Hoary dev cycle:
[http://www.ubuntuforums.org/showthread.php?t=7015&highlight=places+documents+nautilus](http://www.ubuntuforums.org/showthread.php?t=7015&highlight=places+documents+nautilus)

---

### Post by wallacetheweasel on 2006-09-02
Well, I've been working on this since my last post. I kind of have it half fixed. Note: I'm not an expert, I am just doing what seems to make sense to me.  I could be screwing things up on my computer and if that is the case, don't do as I did and screw things up on your computer.

I decided to "apt-get source nautilus" and check out that patch that was referenced in the bugreport above.  I read more about it and figured "well, maybe it's the culprit of what's bothering us. And...I'm not worried about killing this machine because of my own stupidity." So, I simply removed this "debian/patches/06_documents_place.patch", ran debuild to compile it and create .deb files, and installed the created .deb files over the ones obtained from the repository.

Well, I think it half worked.  I attached a screenshot, in which I have a Documents folder in my home folder (~/Documents) and I have also added it to my Bookmarks (explaining the duplicate in my Places menu.) I do however seem to have eliminated the one in the sidebar.  Not sure why it didn't get rid of the one in panel menu as well, but as I said, I am blindly messing about.  Surely someone who knows more could come in here and shed some light.

---

