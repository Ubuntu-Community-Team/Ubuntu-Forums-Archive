---
title: "Kompozer Crashes with a Segmentation Fault"
date: 2009-03-12
forum: General Help
---

### Post by beastrace91 on 2009-03-12
When I am using Kompozer and I select the "view" option at the top of the screen when I move my cursor over the first option in the list it crashes with a segmentation fault. Anyone have any idea if there is a way I can correct this?

~Jeff

---

### Post by Sand &amp; Mercury on 2009-03-12
If you're using Intrepid, this is a known problem. The version in the repositories is a bit of a dud unfortunately (the software in the repos has a problem with an inconsistency with a library or other that is causing the crash, iirc). Go to the Kompozer website and download it from there, they don't have up-to-date .debs last I checked, but they do have tarballs that you can extract and run without compiling, and they should work ok for you. :)

---

### Post by dragos240 on 2009-03-12
Yes i got a tarball of of a german website and it work great and the program is in english :D. I'm going to try to find it for ya.

---

### Post by smartboyathome on 2009-03-12
Get the development release, it is built against the latest GTK+ (the stable release is built against an older version of GTK).

---

### Post by Derevko on 2009-04-02
Hi,

I prepared a KompoZer package for Debian. I Uploaded my preliminary work in my PPA for Ubuntu users:

Jaunty:

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) jaunty main


Intrepid:

deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) intrepid main


Hardy: 
deb [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu) hardy main


Feedbacks are welcome :smile:

Cheers,
Giuseppe.

---

### Post by beastrace91 on 2009-04-02
Awesome! I just updated to Jaunty, I'll take a look at downloading it from here over the weekend :)

~Jeff

---

### Post by jj_norris on 2009-06-11
To let everyone know. This works for the Jaunty version. That is what I currently have. Thank you so much for this Derevko! As for other versions of Ubuntu, I do not know. But this is a fix for me.

Many many thanks.

Junious Norris

---

### Post by Francewhoa on 2009-06-23
KompoZer 0.7.10 is unstable with Ubuntu. Try the latest version 0.8 alpha it's more stable. The new version has views/tabs built in and spit window like Dreamweaver. Find this post: [http://ubuntuforums.org/showpost.php?p=7501868&postcount=6](http://ubuntuforums.org/showpost.php?p=7501868&postcount=6)

---

### Post by beastrace91 on 2009-06-23
Cool, thanks for the tip.

~Jeff

---

### Post by dcstar on 2009-06-24
> **Onopoc said:**
> KompoZer 0.7.10 is unstable with Ubuntu. Try the latest version 0.8 alpha it's more stable. The new version has views/tabs built in and spit window like Dreamweaver. Find this post: [http://ubuntuforums.org/showpost.php?p=7501868&postcount=6](http://ubuntuforums.org/showpost.php?p=7501868&postcount=6)

You can use the current Kompozer version by installing the older GTK package and modifying the Kompozer startup script to use it.

There is a post already in the forums with all the details on how to do this.

---

