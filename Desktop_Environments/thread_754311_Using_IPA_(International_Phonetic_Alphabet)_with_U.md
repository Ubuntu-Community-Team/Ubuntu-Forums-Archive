---
title: "Using IPA (International Phonetic Alphabet) with Ubuntu"
date: 2008-04-13
forum: Desktop Environments
---

### Post by mdbookworm on 2008-04-13
Hey all,
Is anyone out there using Ubuntu for extensive work with the IPA? I have read up on kmfl and scim, but can't seem to get my keyboards working... I tried installing manually, and I cannot get them to show up in the scim startup thingy. I also cannot get scim to do anything with the shortcut ctl+space...

I know there are some posts on kmfl and some on IPA (esp. [here]("http://ubuntuforums.org/showthread.php?t=198788")) but all the info I can find on these topics is rather old (1-3 years). This is why I started a new post.

Is kmfl still used by anyone? I cannot tell if it is abandoned or just the install info that is out of date... It does not bolster my confidence in it that no one seems to have talked about it in a few years.

I know you can specify an IPA input method in gutsy (which I am using), but it doesn't handle some issues that I need (such as superscripts for aspiration, etc.).

Are there better/different ways of handling keyboards, keyboard mapping out there?

I would like to be able to search the data and pull out words that matched certain criteria (maybe through sql, php/ruby?) - any ideas there? will using a keyboard map hinder that or will it not matter?

Thanks for anyone out there who can help...

---

### Post by Winge on 2008-04-16
There sure are people using KMFL, and there are packages available for all the latest Ubuntu releases, including the 8.04 beta. However, the critical package which connects SCIM and KMFL is not available in the standard repositories. To install it:

$ echo "deb [http://packages.sil.org/ubuntu](http://packages.sil.org/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list > /dev/null

(Change "hardy" to correspond to your distribution, i.e. "feisty","gutsy", etc.)
Then:

$ sudo apt-get update
$ sudo apt-get install scim-kmfl-imengine

That's it. You should now be able to configure KMFL and add .kmn keyboards in your SCIM Input Method Setup (in Gnome it's under System, Preferences).

What might be added, and which I didn't find very obvious when I experimented with this, is how to actually enable SCIM (and in effect KMFL) as your input method. In Gedit, you can always right click and select SCIM in the menu, but this is not available in all programs. What you can do instead is to select SCIM as your standard input method:

$ im-switch -c

That should give you a menu where you see your current setting, and be able to change it to something else. SCIM should be an option in that menu. Log out and in again to let your change have effect.

Please let me know how this works out for you.

---

### Post by mdbookworm on 2008-04-17
Excellent! Works very well. That was definitely the missing piece in the puzzle!
Thanks a ton!

---

