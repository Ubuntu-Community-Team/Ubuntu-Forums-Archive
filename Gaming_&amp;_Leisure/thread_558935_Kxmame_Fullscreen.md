---
title: "Kxmame Fullscreen?"
date: 2007-09-24
forum: Gaming &amp; Leisure
---

### Post by MonkeyBoy on 2007-09-24
I have been tinkering with Kxmame and am pretty happy with it but I can't get it to run with a proper full screen.  If I put full screen mode on the game is still in a smaller frame on the screen.

Anyone know how to fix this?

---

### Post by motoperpetuo on 2007-09-30
i'll do you one better...i can't even figure out how to set full screen mode. please let me know how, anyone.

it's weird, because i installed kxmame yesterday, and it was working great, all my games were full screen, but today they're itsy-bitsy. i'm not aware that i changed anything. any advice would be awesome.

---

### Post by meldroc on 2007-10-24
It helps to be running the X11 version of xmame, in package xmame-x.

The problem is that there's a bug in the kxmame package that causes it to incorrectly conflict with the xmame-x package.

See [https://bugs.launchpad.net/ubuntu/+source/kxmame/+bug/113699](https://bugs.launchpad.net/ubuntu/+source/kxmame/+bug/113699) for details.

I did manage to fix this bug for myself by changing the debian/control file as seen in the bug page, but that involves rebuliding the package from source, which is a more complicated than just installing the package using apt-get or adept.

Once you do get kxmame and xmame-x coexisting on your system, then all you have to do is go to the configuration dialog and enable the Xv or Xvideo extension, then it should Just Work.

---

### Post by motoperpetuo on 2008-04-03
so, i finally figured this out, or at least for my system, a dell inspiron 530n, ubuntu preinstalled (although i'm currently running linux mint on it) with an Nvidia GeForce 8300 GS 128mb video card.

note that, for some reason, when i was saying "fullscreen" in my earlier post, i didn't actually mean "fullscreen." i meant that i wanted my games to play in a window, but not an itsy-bitsy one. here's how i accomplished this:

1)Start up kxmame. In the game list, right-click on the game and choose properties.
2)Click on Display from the icons on the left.
3)Choose scan3 from the Effects drop-down menu. 
4)Click on Rendering (on the left). Deselect Fullscreen, if it's selected. Click OK to close the dialog.
5)Double-click on the game to start it.
6)Graphics will probably come up looking a little grainy. Hold down left-ctrl and press Page Up to fill the color in a little.

Note that you may have to change the Effects setting to “scan2” or something else for some games to get them to work right.

---

### Post by disturbedite on 2008-04-03
> **meldroc said:**
> It helps to be running the X11 version of xmame, in package xmame-x.
sorry, thats bad advice.  xmame has been dead for a long, long time.  kxmame has supported sdlmame for a while, but unfortunately the kxmame package in the ubuntu repo is too old.  (doesn't support sdlmame).

sdlmame is in the hardy repo & if one isn't running hardy, there are ubuntu packages here:
[http://wallyweek.altervista.org/](http://wallyweek.altervista.org/)

an updated kxmame ubuntu package (x86) was made by DoktorSeven of this forum, it is here:
[http://sdcofer.googlepages.com/home](http://sdcofer.googlepages.com/home)

---

### Post by motoperpetuo on 2008-04-04
i was running sdlmame on my old computer before getting a new computer two weeks ago. i chose sdlmame mainly because i could get the games to play in a window at a decent size, but aside from the window-size problem (which, as i mentioned above, i just figured out), kxmame felt a lot more solid. sdlmame would get a little jerky every minute or two, and sound was crackly. plus, sdlmame didn't have the "real arcade feel" that kxmame did (don't know how to describe that better).

the kxmame that i got from the ubuntu repositories is running great now, but i'm curious what the advantages of the newer version are, or of sdlmame, for that matter.

---

### Post by disturbedite on 2008-04-04
i don't think you understand motoperpetuo.
sdlmame i*s *the mame binary (emulator).  kxmame is a frontend.  kxmame is not an emulator, simply a frontend.
*don't* install the kxmame package from the ubuntu repo.  the kxmame package from the ubuntu repo is old.  it does not support sdlmame.
you should completely uninstall kxmame & the xmame packages you have installed.  then grab the sdlmame & kxmame packages i mentioned in my previous posts & install them.

---

### Post by motoperpetuo on 2008-04-04
that's likely. i often don't understand.

to be honest, i installed kxmame from the repositories in linux mint this time around, but i think they're the same ones ubuntu uses. everything is working great, better than i've ever gotten mame to work in linux. large windows, no jerkiness when playing, sound is perfect. would i gain extra functionality from installing the more-up-to-date kxmame you pointed out?

---

### Post by disturbedite on 2008-04-05
yes, i believe linux mint does use the ubuntu repos.

---

### Post by clancymf on 2008-10-10
> **disturbedite said:**
> yes, i believe linux mint does use the ubuntu repos.

Its been quite some time since you posted this but I wanted to say thanks!  I am just getting into mame and these posts helped alot.

---

