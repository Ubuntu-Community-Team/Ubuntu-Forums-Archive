---
title: "AWN Dock installation failes/Mac OS X look-alike"
date: 2009-06-30
forum: Desktop Environments
---

### Post by SPARTAN-118 on 2009-06-30
Hi there, not sure if I'm posting in the right forum, but anyway, here's my problem.

I am trying to transform my Ubuntu to look like Mac OS X by following the tutorial here: [http://linuxondesktop.blogspot.com/2008/05/transforming-your-ubuntu-804-desktop-to.html#comment-form ]("http://linuxondesktop.blogspot.com/2008/05/transforming-your-ubuntu-804-desktop-to.html#comment-form")

I get to the part where it says to install the AWN dock. Then I start to have trouble.
After I add the repositories, (by using 'echo "deb[FONT=monospace]  [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main[/FONT][COLOR=#6C7AA1][FONT=Verdana][/FONT][/COLOR]" | sudo tee -a /etc/apt/sources.list' and 'echo "[FONT=monospace]deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main[/FONT][COLOR=#6C7AA1][FONT=Verdana][/FONT][/COLOR]" | sudo tee -a /etc/apt/sources.list') I run sudo apt-get update, and this is what happens:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems
(funny, since I'm running apt-get update...)
This happens whether I add the repositories through the Terminal or via System->Administration->Software Sources .
I must also add that I tried changing "ubuntu hardy main" to "ubuntu jaunty main", since I have 9.04 Jaunty Jackalope.

Also, when I try applying the theme in Emerald, I'm not sure how to apply it (double-click it?), since when I "select" the theme and click refresh, the close/minimize/maximize buttons are still on the right, not the left, while the screenshot in Emerald shows them on the left, like in Leopard.

Any help on either of these matters would be greatly appreciated (should I try [http://ppa.launchpad.net/awn-core/ubuntu](http://ppa.launchpad.net/awn-core/ubuntu) jaunty main instead of [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main?). :p

SPARTAN-118

---

### Post by SPARTAN-118 on 2009-07-04
You know what, never mind, turns out after I followed the directions on AWN's site (not using the awn-testing package, but awn-core) it installed perfectly.

Question though: 
If I were to right click on "remove panel" for Ubuntu's taskbar (since it gets in the way and doesn't look good if I always have a button on the side to restore it when I click "hide" or "autohide"), would I be able to get it back? I don't want to permanently mess up my computer, but I want it to look as Mac-like as possible. (If you haven't noticed, I'm tired of the Human/Human-Clearlooks coffee themes, and the other built-in ones don't attract me in the same way as a Mac.)

---

