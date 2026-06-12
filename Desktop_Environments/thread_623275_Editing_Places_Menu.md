---
title: "Editing Places Menu"
date: 2007-11-25
forum: Desktop Environments
---

### Post by barrack on 2007-11-25
I've just installed 7.04 and I've noticed that in the Places Menu there is a "Documents" folder listed just after my home folder.

I've read a few threads on the forums on this topic, but none really applied.

I can't post a pic here, so I will try to be as descriptive as I can. When I click on Places, I see "Home Folder" "Document" and "Desktop" above the first separator line.

I want there only to be "Home Folder" and "Desktop." I believe that's how it was in 6.06.

Alacart Menu Editor cannot do this. "Places" isn't even an option to change it.

The file browser bookmarks can only change that which is below the separator line.

Does anyone have any ideas or thoughts?

---

### Post by knopper67 on 2007-11-25
I was also wondering how to change this, although I don't really mind how the menu is set up by default. To change it i think you have to edit the source code of gnome-panel in the repositories. 

But still, I really wish I could change this around...

---

### Post by the yawner on 2007-11-26
Open up a Nautilus folder (i.e. just click any folder under Places) and on the menus click Bookmarks>Edit Bookmarks. A bookmark editor will open, and you can delete the unwanted folders from there.

---

### Post by barrack on 2007-11-26
That's the problem. When I edit bookmarks, there's nothing to edit. This isn't a bookmark.

---

### Post by brickbat on 2007-11-26
I had a problem with having Desktop listed twice and it wasn't listed in bookmarks.  I think the solution is the same for us both.  Here is how i solved it.

open up a terminal and type

gedit ~/.gtk-bookmarks

In that list you will find ALL your bookmarks including those that aren't listed in the Edit Bookmarks GUI.

Edit it and save it and you should be good to go.

---

### Post by barrack on 2007-11-26
> **brickbat said:**
> I had a problem with having Desktop listed twice and it wasn't listed in bookmarks.  I think the solution is the same for us both.  Here is how i solved it.

open up a terminal and type

gedit ~/.gtk-bookmarks

In that list you will find ALL your bookmarks including those that aren't listed in the Edit Bookmarks GUI.

Edit it and save it and you should be good to go.

Ooh I got really excited. I thought this might do the trick. But when I opened up that file, it was empty. The file exists, but it was empty. :cry:

---

### Post by barrack on 2007-11-28
bump? i don't often bump, but i'm really perplexed on this one.

---

### Post by jARLAXL on 2007-11-28
Dont know why bookmarks doesnt work for you but for me it works just fine.
In any case under any nautilus window click-->View-->Location bar. you should be able to view your bookmarks as well and edit them this way i guess.

---

### Post by mcduck on 2007-11-28
Just rename the Documents-directory inside your home dir to anything else than 'Documents'. It will disappear from the places-menu.

It's not a bookmark, and therefore cannot be removed like nautilus bookmarks. Instead it's a hard-coded directory name that Nautilus will recognize and add to menu if such directory exists in your home.

---

### Post by barrack on 2007-11-29
This is exactly the information I was looking for. Thank you.

---

### Post by dudy'O on 2008-01-16
I followed what the yawner said at it worked for me. Thanks

---

### Post by &amp;)ky#)^ on 2008-01-21
Thanks for the tip.  I'd been trying to figure that one out for quite a while to no avail.

---

### Post by SanskritFritz on 2008-01-25
How can i rename the menu itself? I mean, I want a different name for the menu "Places", it is not descriptive enough for my family (in hungarian at least, localized: "Helyek", it sounds really stupid for hungarians). Also "Applications" sounds really funny in hungarian. Can I rename that also?

---

### Post by nicholim on 2008-02-24
> **mcduck said:**
> Just rename the Documents-directory inside your home dir to anything else than 'Documents'. It will disappear from the places-menu.

It's not a bookmark, and therefore cannot be removed like nautilus bookmarks. Instead it's a hard-coded directory name that Nautilus will recognize and add to menu if such directory exists in your home.

Actually, it isn't hardcoded, like brickbrak said, it's in a file.  The contents of my file was:
```

file:///home/ian/Documents
file:///home/ian/Music
file:///home/ian/Pictures
file:///home/ian/Videos
```
It was easy to do what I wanted, which was make the directories lowercase, all of 15 seconds of work.

---

