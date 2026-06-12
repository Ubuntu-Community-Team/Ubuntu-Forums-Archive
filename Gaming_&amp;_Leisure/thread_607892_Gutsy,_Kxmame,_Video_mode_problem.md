---
title: "Gutsy, Kxmame, Video mode problem?"
date: 2007-11-09
forum: Gaming &amp; Leisure
---

### Post by Mage921 on 2007-11-09
Hello everybody! Ok, so this is my first post on the forums, and I've gotta admit that I'm pretty useless at the moment when it comes to troubleshooting a linux problem, so I thought that I might ask for some help. :) First a tiny bit of background.

Ended up doing a fresh install of Gutsy after finding out that it can be a little bit of a hassle working with changed packages and stuff after an upgrade from feisty. Anyways, I found out that kxmame and xmame-x don't get along so I installed kxmame manually, and finally got it to work. Yay! Unfortunately, I somehow broke my gl drivers while rotating my cube (heh) and using xmame. Like HARD lock up and such. I don't know if people know if that's a bug or not, but in case you want to have a gl window open, I wouldn't suggest moving the desktop around. :/

Sooooo, I went and reinstalled a whole bunch of drivers, reconfigured xorg.conf, and basically had a hell of a time just to get glxinfo to say I was doing ok. I went back and checked all of the software that uses gl and most of it worked fine. HOWEVER, when running kxmame, it would only work in xvideo  mode is kinda fuzzy and gross. I'm a fan of the normal video, but when I tried to switch  
over to normal video, I got.

"video mode 2 cannot be enabled" 

or something to that effect. I told kxmame to disable mode 2 and hey, I could get a little window looking spiffy in normal video mode. Can't fullscreen, however, which makes me think that it was trying to fullscreen automatically in normal video mode 2 all that time, and  that mode 2 is a funky resolution, but either way... Now I don't get the error, and I just can't get into fullscreen at all on normal video mode. I was thinking maybe I messed up my xorg.conf and the device for my card just doesn't have mode 2 allowed? Unfortunately, I don't know what mode 2 is or exactly how I would specify that I can use it. Oh yeah, and I got rid of that little disable mode 2 option in case you were thinking I might have left it on. :D

Then again, there is the distinct possibility that I'm completely wrong about all of this. Anybody have this problem, or know how to let my computer use video mode 2?

Sorry if that that was a little longwinded! Just not exactly sure how much info to add. haha

---

### Post by disturbedite on 2007-11-09
ummm, as i always recommend now-a-days:
don't use xmame with kxmame.  use sdlmame.  xmame is dead.  sdlmame is still actively developed and far newer.
sdlmame is just basically mame for linux so it does not include a gui/frontend.  if you need one and wanna kxmame (like me) you can grab sdlmame ubuntu/deb packages here:
[http://wallyweek.altervista.org/index.php](http://wallyweek.altervista.org/index.php)
but, the catch is, you can't use the kxmame package from the ubuntu repo.  it is too old and doesn't support using kxmame with sdlmame.
you need to go to sourceforge and grab the newer kxmame svn package with sdlmame support and compile it:
[http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402](http://sourceforge.net/project/showfiles.php?group_id=145736&package_id=174814&release_id=514402)

---

### Post by Mage921 on 2007-11-09
Hey, thanks for the direct links. I'll have to switch packages around when I get home. For some reason, I really don't know if that's gonna fix the problem I'm having with the video mode not working, but it can't hurt to use the most up to date and non dead software, eh?

---

### Post by disturbedite on 2007-11-09
my point exactly.

---

### Post by Mage921 on 2007-11-09
Wow, it totally helped, plus sdlmame is pretty sweet! Unfortunately, I think I'm an idiot cause I can't get that cvs package for kxmame to work at ALL. Of course, I'm not using KDE, so that might be a problem. haha. I don't need it, though, as it appears that sdl mame let's you choose the rom you want without doing a whole bunch of typing, which is all I really wanted. I might work on getting an sdlmame compatible kxmame working, but friday night is not the time for such things. Thanks a bunch!

:)

---

### Post by disturbedite on 2007-11-10
you know you have to compile kxmame right?  i said that above...

btw, this might help, i had to disable the joystick to get it to compile:
./configure --disable-joystick

---

### Post by Mage921 on 2007-11-10
Yeah, I knew I had to compile it, but I was getting a whole bunch of errors. When I came back to it tonight, I re downloaded the source and made the configure file and it worked fine. 

I assume you were getting the __s64 not a type error from the joystick.h file? I just commented out the strict ansi test in /usr/include/asm-i386/types.h of course it might be a different file if you aren't using a computer like mine.

> #if defined(__GNUC__)** /* && !defined(__STRICT_ANSI__) */**
typedef __signed__ long long __s64;
typedef unsigned long long __u64;
#endif


And make worked just fine. Anyways, thank you for the help. It's just what I needed to get on the right track! :D

---

### Post by disturbedite on 2007-11-10
so, to clarify, you commented that line out, but you can still use a joystick?
cuz the only workaround i was told of was to disable joystick support when compiling and i would love to use my xbox controller with mame, but i can't cuz of that.

---

### Post by Mage921 on 2007-11-11
Sorry that I didn't have time to get back. Weekend stuff and all. Anyways, I just got my usb adapter for the ps2 and hooked it up. Works fine with sdlmame, cept the up button is a little glitchy. But no worries. It appears that it works just fine otherwise. So hope that helps. :D

---

