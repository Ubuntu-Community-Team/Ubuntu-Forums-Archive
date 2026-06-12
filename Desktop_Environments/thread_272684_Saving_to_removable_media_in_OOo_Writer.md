---
title: "Saving to removable media in OOo Writer"
date: 2006-10-06
forum: Desktop Environments
---

### Post by srunni on 2006-10-06
Hi,

I save documents that I type in OpenOffice.org Writer to a flash drive very often. I run Kubuntu 6.06, and when I open the "Save As" dialog to choose the save location the first time I save a new document, I click on the "Storage Media" button located on the left side of the "Save As" window. This allows me to easily select the flash drive without having to navigate to the /media folder. However, when I go to the folder on the flash drive that I want to save the document to and click "OK," I get the error ```
Saving using protocol "media" is not supported
``` I noticed that  the address bar in the "Save As" window says "media:/sdg1", not "/media/sdg1" (the flash drive is mounted to /media/sdg1). However, using "/media/sdg1" works just fine. But this means that every time, I have to change "media:" to "/media". Is there any way to get around this? It gets really annoying when you're creating a lot of new documents.

Thanks in advance for the help!!

---

### Post by kidders on 2006-10-06
The media protocol is a made-up notion that doesn't really exist. Some UIs like KDE & Gnome like to use it. OpenOffice (which is pretty platform-independent) doesn't understand it.

I imagine opening things by navigating to their mount point will avoid any confusion.

Hope that helps.

---

### Post by srunni on 2006-10-07
Well, is there any way to get around this? Can I modify KDE so it goes to "/media" instead of "media:" when I click on the "Storage Media" button? Also, this ONLY happens when I'm saving. For example, I can open files from "media:" just fine.

---

### Post by kidders on 2006-10-07
> Can I modify KDE so it goes to "/media" instead of "media:"
No, not really. KDE will go wherever you send it. If you access your filesystems in a more "conventional" manner, your applications won't get upset with you.

---

### Post by srunni on 2006-10-09
Then can I modify OOo so it doesn't do this?

---

### Post by kidders on 2006-10-09
OpenOffice isn't really *doing* anything other than dutifully obeying instructions given to it by KDE, so there's nothing to modify, I'm afraid.

Just to reiterate, there's no reason why you _have_ to open OpenOffice documents (or anything else, for that matter) using the fake "media" protocol abstraction. It's just as easily done the "normal" way, by navigating to the actual location of your files, rather than a pretend location that doesn't even exist.

The same principle applies equally to any other application not written by the KDE developers. There is no reason to expect any of them to be able to access URLs that start with fish:/ media:/ bluetooth:/ etc, etc, OpenOffice included.

---

### Post by srunni on 2006-10-11
Well, there's a reason that button is there - so you can use it to easily navigate to your media devices. And if KDE applications have no problem with the "media:" protocol, wouldn't it be possible to make OOo compatible? Or otherwise, add the option to KDE to let the user select which folder the "Storage Media" button opens? Maybe I can suggest it to the devs or something. There might already be an OOo plugin as well.

---

### Post by kidders on 2006-10-11
Hey again,

Unfortunately, I doubt the OOo devs will be too interested in implementing a linux-only feature like that, but maybe there *is* a plugin, like you suggested. (It'd be handy!) OpenOffice, just like other apps, support most major URI protocols (such as http), but they probably won't know about ones that some KDE dev drempt up on a rainy day, hehe.

After all, you wouldn't expect Gimp to load an image off your phone when you try to open "bluetooth:/00:11:22:33:44/sdcard/filename.jpg", just because that's what KDE does.

I suppose it's one of those things you have to get used to in the world of free software, where developers wander off in their own directions sometimes :-(

---

