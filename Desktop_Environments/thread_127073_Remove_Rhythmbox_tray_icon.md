---
title: "Remove Rhythmbox tray icon?"
date: 2006-02-08
forum: Desktop Environments
---

### Post by Garyu on 2006-02-08
I really like Rhythmbox, it's definitely my favourite music player in Ubuntu. BUT I have two issues with it that I would like to change, if you can tell me how...

1) That system tray icon sure is annoying. The popup with song/artist always shows its ugly face at the wrong time. How do I remove it? I have the player on my task bar, I don't need a tray icon as well.

2) The "Play count" starts from scratch every time I close Rhythmbox. It would be neat if the play count would be saved in a file and if you want to reset it you could do it manually. I'm guessing this is a bit more difficult to implement...

---

### Post by kaamos on 2006-02-08
At least rhythmbox 0.9.3 has the option to not to use the song/artist popup. Also the (total) play count seems to work.

Look here: [http://ubuntuforums.org/showthread.php?p=714980#post714980](http://ubuntuforums.org/showthread.php?p=714980#post714980)

---

### Post by Garyu on 2006-02-08
really? well, I will have to try to install that then. thanx. :)

EDIT:

Well, I tried to download the Rhythmbox 0.9.3 deb file, but it depends on libgpod0. So I downloaded libgpod0, but that depends on libdbus-1-2. So I downloaded the deb for libdbus-1-2 and what do I get? "libdbus is in conflict with dbus", and I can't uninstall dbus because other packages depend on that. So it seems I'm stuck with old Rhythmbox until the new one hits the repositories.

It's times like these that make me appreciate apt-get and synaptic soooo much.

---

### Post by kaamos on 2006-02-08
Funny, I got it installed just by installing rhythmbox, libgpod and libgpod-common from mightmos. Where did you try to get libgpod0?

---

### Post by Garyu on 2006-02-08
I went to mightmos homepage and downloaded his deb-files... oh, but only rhythmbox though... the libgpod0 wasn't linked from his pages, so I found it here on some ubuntu-page with deb-files... don't remember the adress...

EDIT: uh, I'm stupid. the libgpod was right there on mightmos page. :P I was just too blind to see it, and that worked a whole lot better to install than the ubuntu one. :D

thanx for your heads up =)

---

### Post by Herd on 2006-02-23
Downgrading to 9.0 gets rid of the annoying track popup things.  Find the package in synaptic then click package > force version and pick 9.0.  Way less effort than upgrading to 9.3.

---

### Post by MighMoS on 2006-02-24
No t.  Just MighMoS :-).  Also, glad I could be of help.

---

