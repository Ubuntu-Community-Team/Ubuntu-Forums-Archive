---
title: "kde dev for 3.4.1?"
date: 2005-07-30
forum: Desktop Environments
---

### Post by kLy on 2005-07-30
Grabbed kde 3.4.1 off [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341)

It's great but there isn't any dev packages (eg. kdebase-dev)

So I can't compile for KDE unless I downgrade. Are these going to be available?

or only when breezy gets released? :(

Thanks

---

### Post by SGC on 2005-07-30
Have you tried running this command:
sudo apt-get install kdebase-dev

---

### Post by kLy on 2005-07-30
yes. that points to the 3.4.0 package in main since [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) doesn't have that package. If I install that, I have to downgrade to 3.4.0 :(

---

### Post by SGC on 2005-07-30
[QUOTE=kLy]yes. that points to the 3.4.0 package in main since [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) doesn't have that package. If I install that, I have to downgrade to 3.4.0 :([/QUOTE]
 Can you post the what the mesage the you got when you type the above command

Becuse kdebase-dev is in the repository:
[http://kubuntu.org/hoary-kde341/pool/kdebase/kdebase-dev_3.4.1-0ubuntu0hoary1_i386.deb](http://kubuntu.org/hoary-kde341/pool/kdebase/kdebase-dev_3.4.1-0ubuntu0hoary1_i386.deb)

---

### Post by kLy on 2005-07-30
oh... hmm... ok, my bad. Figured it out now. I had set up my prefs file so with hoary pinned with a very high priority (I was trying some breezy packages). I think that's why it wanted to install the 3.4.0 packages. I've killed that and now it's great. Thanks!

---

