---
title: "Folder Icons won't change"
date: 2007-06-03
forum: Desktop Environments
---

### Post by chrisrx on 2007-06-03
I changed my icon theme a while ago to a white theme, (Can't remember exactly what it was called)  but now whenever I try to change my icon theme, all the icons change except for the folders.
So all the folders on all drives and external drives are all white which doesn't fit in with the rest of the themes.
Has anyone got any idea why the folder icons are not updating and the rest of them are?

---

### Post by chrisrx on 2007-06-03
Well I tried updating the icon cache and now my folder icons are gone completely and only showing the paper icon. 

I think I deleted the icon set I was using a couple weeks ago in an effort to get rid of the white folder icons so that might explain why it's showing the paper now that i've updated the cache.

But I still don't know why its constantly trying to use that one icon for the folders no matter what i change the icon set to.

---

### Post by oldsmobile_mike on 2008-03-04
> **chrisrx said:**
> Well I tried updating the icon cache and now my folder icons are gone completely and only showing the paper icon. 

I think I deleted the icon set I was using a couple weeks ago in an effort to get rid of the white folder icons so that might explain why it's showing the paper now that i've updated the cache.

But I still don't know why its constantly trying to use that one icon for the folders no matter what i change the icon set to.


Ever find a solution to this?

---

### Post by dulbirakan on 2008-04-26
I have a similar problem in Hardy, my folder icons are fixed to default icon set...

---

### Post by adohall on 2008-04-27
I think this may have something to do with the fact that Hardy is looking for a the folder icon in a folder 'Places' while some icon sets (like the glass icons for example) put them in a 'Filesystems' folder.

I don't know how to fix this though. Any ideas?

---

### Post by dimbulb1024 on 2008-04-27
I had problems with Glass Icons. Check out the [comments section]("http://www.gnome-look.org/content/show.php") under Glass Icons on GNOME-Look.org.

---

### Post by adohall on 2008-04-28
A couple of very helpful Ubuntu users gave me the solution over at gnome-look.org:

1. Open Nautilus with root permission (terminal - sudo nautilus)
2. Extract the theme tar.gz file (e.g. Glass Icons) into /usr/share/icons folder.
3. Go to /usr/share/icons/glass-icons/scalable/filesystems/ and right click the gnome-fs-directory.svg file and select the Make Link option. This will create a link and you rename that link folder.svg.
4. Do the same with these other files:
- gnome-fs-trash-full.svg -> user-trash-full.svg
- gnome-fs-trash-empty.svg -> user-trash.svg
- gnome-fs-home.svg -> user-home.svg
- gnome-fs-client.svg -> computer.svg
- gnome-fs-web.svg -> applications-internet.svg
- gnome-fs-desktop.svg -> user-desktop.svg
- gnome-fs-server.svg -> network-workgroup.svg
- devices/gnome-dev-harddisk.svg -> drive-harddisk.svg
- devices/gnome-dev-dvdrw.svg -> drive-optical.svg
- devices/gnome-dev-removable.svg -> drive-removable-media.svg
5. Customize a theme by choosing Glass Icons;
6. Reboot (or change icon theme and then change back)

---

