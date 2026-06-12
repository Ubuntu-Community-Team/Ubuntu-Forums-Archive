---
title: "WINE and Panels"
date: 2009-05-27
forum: General Help
---

### Post by oddeyed on 2009-05-27
Hello. 
I use Spotify (an online streaming music program [legal]) in WINE because there is currently no Linux port. The problem is that WINE doesn't seem to see my Gnome Panels. What I mean is that when I click 'Maximise' it just covers the entire screen. 

For what its worth, I am on a 16:9 display.

Hope someone can help :).

---

### Post by hyperdude111 on 2009-05-27
I also use spotify in wine but never had this problem. Try a newer version of wine maybe?

---

### Post by lovinglinux on 2009-05-27
Open Wine configuration tool, select the "Graphics" tab and select the option "Emulate a virtual Desktop", then set the "Desktop size" option to smaller than your resolution.

---

### Post by XCan on 2009-05-27
> **oddeyed said:**
> Hello. 
I use Spotify (an online streaming music program [legal]) in WINE because there is currently no Linux port. The problem is that WINE doesn't seem to see my Gnome Panels. What I mean is that when I click 'Maximise' it just covers the entire screen. 

For what its worth, I am on a 16:9 display.

Hope someone can help :).

This sounds like you've disabled one of the options "Allow the window manager to..." in Wine. Have a look in Configure Wine -> Graphics. Also, if that doesn't work, you may want to add spotify in the Applications tab of Wine and give it a virtual desktop.

---

### Post by oddeyed on 2009-05-27
> **hyperdude111 said:**
> I also use spotify in wine but never had this problem. Try a newer version of wine maybe?

I have the latest version from the repos.

[quote=XCan]This sounds like you've disabled one of the options "Allow the window manager to..." in Wine. Have a look in Configure Wine -> Graphics.[/quote]
Nope, they're all enabled.

I guess I'll just do the virtual desktop thing. :-|

EDIT: I just realised that there isn't much point in doing the virtual desktop really, because rather that do that I can just have it not maximised. Still, its a shame though.

---

### Post by XCan on 2009-05-27
> **oddeyed said:**
> I have the latest version from the repos.

EDIT: I just realised that there isn't much point in doing the virtual desktop really, because rather that do that I can just have it not maximised. Still, its a shame though.

Hehe true that. :D 

Anyway, the latest version from the repos is often not the most up to date one, despite that it's labeled as a stable version. Wine is developing extremely fast, and I think it would definitely be worth it for you to check out one of the newer versions.

It's quite easy [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) .

---

