---
title: "Spider in ubuntu 12.04?"
date: 2012-09-30
forum: Gaming &amp; Leisure
---

### Post by lunalui on 2012-09-30
Hi everybody,
I've just upgraded from Lucid Lynx to Precise Pangolin and there are several features I'm not totally happy about, so I think I'll start spamming the forum with different questions (probably nothing serious, but still annoying for me). Who knows, in the end I might even end up with the minimal number of posts to become an "active member" here ;)

The first one concerns the amazing spider solitaire which was available on lucid (and even karmic) see here
[https://apps.ubuntu.com/cat/applications/lucid/spider/](https://apps.ubuntu.com/cat/applications/lucid/spider/)
but is nowhere to be seen on precise...
Any chances to have the application available in one way or another (by adding repositories or the like)? Sorry for the silly question, I'm just a user, not a computer whizard. I fear there are more to come.
thanks for your reply,
Luisa

---

### Post by TheFu on 2012-09-30
> **lunalui said:**
> Hi everybody,
I've just upgraded from Lucid Lynx to Precise Pangolin and there are several features I'm not totally happy about, so I think I'll start spamming the forum with different questions (probably nothing serious, but still annoying for me). Who knows, in the end I might even end up with the minimal number of posts to become an "active member" here ;)

The first one concerns the amazing spider solitaire which was available on lucid (and even karmic) see here
[https://apps.ubuntu.com/cat/applications/lucid/spider/](https://apps.ubuntu.com/cat/applications/lucid/spider/)
but is nowere to be seen on precise...
Any chances to have the application available in one way or another (by adding repositories or the like)? Sorry for the silly question, I'm just a user, not a computer whizard. 

I spent about 10 minutes looking and didn't find that game or any of the 2 other "near clones".  

New software releases don't always retain old functions. That's the way of the entire industry. The source was available under 11.04, so you could attempt to build it yourself.

[https://apps.ubuntu.com/cat/department/precise/games/](https://apps.ubuntu.com/cat/department/precise/games/)  I do not know why this happened, but **I can make a guess.**  Between Gnome2 and Gnome3, a few (or many) apps were left behind.  Porting to Unity was never a priority for the Gnome guys, so it wasn't ported.  

Or I could be completely wrong.

Ubuntu/Canonical doesn't control all the software available to Ubuntu/Debian. If the author or team didn't want to update the code to work with 12.04, then we are often SOL. Depending on the code license, you might be able to do the port yourself, if you are so inclined.  Which license was it released under?

You could look inside the old version .deb file and find the game author, then contact that person.

I did a little more searching to see if a current debian distro had Spider included - Ubuntu is based off debian, so you can install .deb files for the compatible Ubuntu version.  Finding a PPA would be better from a maintenance perspective, but installing a .deb file should work too. My search lead to a commercial "Spider" website, so I stopped searching right there.  It could be that the author decided to make the game proprietary and earn a little money from it.  Again, I don't know - I stopped looking. That commercial site might be repackaging it for a nominal fee.

Good luck!

---

### Post by thatguruguy on 2012-09-30
> **TheFu said:**
> (lots of words)

... or, you can install aisleriot from the Ubuntu Software Center, if it's not already installed (I think it's part of the default installation). It includes almost every conceivable solitaire game, including spider solitaire.

---

### Post by lunalui on 2012-10-01
thank you for your replies. I've now solved the problem. Following the suggestion of a friend, I basically followed what's in this thread:
[http://ubuntuforums.org/archive/index.php/t-1066625.html](http://ubuntuforums.org/archive/index.php/t-1066625.html)

first of all I entered the following line in my broweser

> [http://packages.ubuntu.com/search?keywords=spider&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=spider&searchon=names&suite=all&section=all)

and selected the lucid version (the one I had before)
I checked that all needed packages were already installed (which they were), then I downloaded the file following the link on the page. 

Clicking on the file on my desktop it launched the installer, and now the game is up and running! 


@thatguruguy
you are right: there is a spider in aisleriot, but the version is different (closer to the windows one and less fun) and the interface is not as pleasant

---

### Post by TheFu on 2012-10-01
You've gone outside the package manager by doing that.  You've risked the sanity of your APT installation.  I wish you luck and that you don't get into APT-Hell over it.

I think you'll find what you've done was a terrible idea over then next few years. I hope it works out fine, but ...

---

### Post by lunalui on 2012-10-01
to be honest, in the next few days (not years), after testing precise a little bit more, I may be installing back lucid, for there are too many things I'm not happy about precise, so this won't be a big problem for me.

---

### Post by TheFu on 2012-10-01
> **lunalui said:**
> to be honest, in the next few days (not years), after testing precise a little bit more, I may be installing back lucid, for there are too many things I'm not happy about precise, so this won't be a big problem for me.

I get what you are saying.  I'm with you about most of the GUI changes but decided to go with a different solution.  Just install LXDE or XFCE and use that instead of Unity.  Remove unity so it gets out of the way. That should solve most useability issues, though it won't solve the lack of this 1 game.  Is gaming a major purpose for this desktop?

I know that I'd never let a single game get in the way of an entire OS install.

Another alternative is to run 10.04 inside a virtual machine just for this 1 game.  Using KVM, VirtualBox or LXC should make this easy if your system isn't old and weak.  Core2Duo + 2GB of RAM or better. [https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)  LXC has the least overhead, but is probably the hardest for a new-to-Linux person to handle.  

Desktop 10.04 support ends in 6 months, so it is a good idea to move to a well supported desktop release like 12.04. You don't have to use the default DE - there are lots of other choices.  12.04 desktops will get patches for 5 yrs.

Anyway, just a thought for your consideration.

---

### Post by lunalui on 2012-10-01
> **TheFu said:**
>   Is gaming a major purpose for this desktop?


Of course not, but neither do I consider my laptop and its operating system like some kind of shrine deserving religious respect... sorry for the disappointment and I hope you won't be offended by my words.

---

### Post by TheFu on 2012-10-01
No offense taken. It has always been your decision to make.  If you are hoping for things to get better in the next release, I think you will be disappointed.

What will you do when 10.04 isn't patched anymore around 4/2013 for security issues?

I create and blow away OS installs all the time. It isn't a big deal at all, but I wasn't assuming the same for you.

Is running a different, current, Linux an option?  Perhaps one with Gnome2 and Spider still included?

---

