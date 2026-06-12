---
title: "Beryl packages in repos act weird?"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by sloggerkhan on 2007-04-20
I am using the beryl from Feisty repos and have a question about it.

Right clicking on the top bar of a window no longer has the option to move the window to workspace left or right. Why is this? I am pretty sure when I used beryl before I still had that option. The always on top and other grouped options are gone too. Is there a way to get them back? Or are they now gone forever with beryl in use?

Thanks.

---

### Post by rich.bradshaw on 2007-04-20
You can try the newest new new new beryl snapshots if you add this to your sofware sources list

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

and type:

wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

in order to get the pubkey.

Then just do 

sudo apt-get update
sudo apt-get install beryl emerald

---

### Post by sloggerkhan on 2007-04-21
Hmm. Taking a look. Will see if svn version is different. I was thinking maybe I'd been overlooking an option somewhere, but guess I'll see. Thanks.

---

### Post by celticbhoy on 2007-04-21
SVN version better, but I had probs with feisty please post a reply if it goes ok for you.

---

### Post by sloggerkhan on 2007-04-21
Well, beryl works with SVN version and repo version fine.
Still interferes a bit with most 3-D apps.
And the choices such as move workspace right and always on top disapear from the window title bar menu.

---

