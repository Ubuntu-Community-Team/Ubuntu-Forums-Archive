---
title: "Dead entries in menu [lxde]"
date: 2013-07-12
forum: Desktop Environments
---

### Post by momist on 2013-07-12
Hi everyone.

I am running a system with separate /home and /data partitions, and have had a few variations of *buntu on it over a few years.  I have just moved to Lubuntu 13.04 for better speed on my old platform and a somewhat cleaner and snappier lxde interface.

As with previous experience, there are left-over artifacts from previous installs, due to the presence in the /home folder of lots of configuration files etc.  One of the most distracting results of this is the presence of entries in the menu structure which do nothing, as the software is no longer installed.  Lxde does not seem to have any editor built in to amend the menu (or I've been unable to find it), so I searched and found lxmed.  I've installed java, and lxmed, and it runs.  However, lxmed only shows me menu items for things that do exist, the dead entries are not listed there, but still exist in the lxde menu.

Can anyone suggest a cure for this, and perhaps a way to clean out my /home folder without having to manually examine/edit every file in there?

Thanks,

Ian

P.S.  I have found the instructions here:
[https://help.ubuntu.com/community/Lubuntu/Documentation/EditingTheMenu](https://help.ubuntu.com/community/Lubuntu/Documentation/EditingTheMenu)
but they don't seem to apply.  For instance, in my 'Graphics' menu, there is an entry for 'Okular' (software I don't ever remember using) which does nothing now.  That name doesn't feature anywhere in either of the two files referred to.  However, there are hundreds of names in those files which don't appear on the menus anywhere.

---

### Post by vasa1 on 2013-07-12
Why don't you try MenuLibre?
[https://launchpad.net/+search?field.text=menulibre](https://launchpad.net/+search?field.text=menulibre)

---

### Post by momist on 2013-07-12
> **vasa1 said:**
> Why don't you try MenuLibre?


Many thanks for the link.  I had looked in the repositories for MenuLibre, and not found it, so I had falsely assumed it would not be available in Lubuntu.  However, I found the ppa to add and I can confirm that it works.

It does seem slightly flakey at times, it took me a while to realise that I had to save changes before anything happened.  It also seems sometimes to require turning off and on again before it will behave, but in general with a bit of work it has done what I needed it to.  Kudos.

Thanks,

Ian

Hey, I can't find the [SOLVED] button on the thread tools?

---

### Post by vasa1 on 2013-07-12
> **momist said:**
> Many thanks for the link.  I had looked in the repositories for MenuLibre, and not found it, so I had falsely assumed it would not be available in Lubuntu.  However, I found the ppa to add and I can confirm that it works.

It does seem slightly flakey at times, it took me a while to realise that I had to save changes before anything happened.  It also seems sometimes to require turning off and on again before it will behave, but in general with a bit of work it has done what I needed it to.  ...

It was there in 12.04 but somehow didn't retain its place in the repos. I don't know why.

I agree that parts of it need a bit of guesswork but I like it better than alacarte (which tries to pull in a lot of GNOME stuff). I avoid the other one because it requires Java and I don't need Java for anything else.

---

