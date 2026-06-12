---
title: "Firefox upgrade"
date: 2005-09-23
forum: Desktop Environments
---

### Post by Owdy on 2005-09-23
I wanna upgrade to FF 1.5 beta1. how do i do that?

---

### Post by Dooglus on 2005-09-23
There's no official ubuntu package of it, but you can install the version from mozilla.org.

Go here:

  [http://www.mozilla.org/projects/firefox/](http://www.mozilla.org/projects/firefox/)

Download the linux version and extract it to somewhere in your home directory.  You can use file-roller, or "tar xfz".  Either will do.

Interestingly, the release notes are completely wrong about how to install it.  They're here: [http://www.mozilla.org/products/firefox/releases/1.5beta1.html](http://www.mozilla.org/products/firefox/releases/1.5beta1.html) , and they say that you should "cd firefox-installer" and "./firefox-installer" after extracting it.  Problem is, there's no "firefox-installer" directory or file in the archive.

All you need to do is extract the .tar.gz file into your home directory.  This will make a directory called 'firefox' containing a script called 'firefox', which runs the browser.

You can make an icon in your GNOME panel to start it (right click some empty space in a panel, 'add to panel', 'custom application launcher'.  For the command, put the full path : /home/user/firefox/firefox ; for the icon use /home/user/firefox/icons/mozicon50.xpm .  You'll actually get the proper fox-around-the-world icon instead of the dark blue circle icon that we've been getting used to.

The thing I haven't worked out is how to get other applications to start the right firefox.  So long as you already have 1.50beta1 running, other applications which try to use firefox will use your running 1.50beta1, but if you don't already have it running, they'll start a firefox 1.04, or whatever's the official ubuntu version.

*edit: /home/user should be replaced by the path to YOUR home directory, of course *

---

### Post by Hairy_Palms on 2005-09-23
why? firefox 1.6 is in the repos, and 1.7 is out already

---

### Post by Dooglus on 2005-09-23
You're talking about 1.06 and 1.07.

Owdy is asking about 1.50, which is currently in beta and is still a bit buggy; I've had it crash 6 or 7 times in the last week.  But it feels a lot faster, especially when going backwards and forwards between pages.

---

### Post by Owdy on 2005-09-23
[QUOTE=Hairy_Palms]why? firefox 1.6 is in the repos, and 1.7 is out already[/QUOTE]
I didnt mean 1.0.5, i wrote 1.5 beta1 ;)

Dooglus thanks, i try that! :)

---

### Post by petrol on 2005-09-23
I tried the 1.0.7 update with Synaptic and It broke. It said the .deb package is trying to overwrite the extensions.d/00classic, which is also in package firefox. :???:

---

### Post by Hairy_Palms on 2005-09-23
lol my bad wasnt reading right yea 1.5 is beta and petrol that means one of your extensions isnt compatible with the 1.07 so u gotta remove the problem extension.

---

### Post by treris on 2005-09-23
[QUOTE=petrol]I tried the 1.0.7 update with Synaptic and It broke. It said the .deb package is trying to overwrite the extensions.d/00classic, which is also in package firefox. :???:[/QUOTE]


i had the same problem, but after i used synaptic to uninstall version 1.0.6 of both firefox and mozilla-firefox packages everything went like a charm, as usual

---

