---
title: "Cannot launch Cave Story"
date: 2012-05-10
forum: Gaming &amp; Leisure
---

### Post by mode7 on 2012-05-10
I was trying out the Commodore Vision Linux distro (Always been a Commodore fan, but too bloated for my tastes.. I'll stick with Ubuntu).
Anyhow, I was playing Cave Story on it for a bit and rather enjoyed the game. Considering it was a live session, I figured I would download it and play it on my Ubuntu 12.04 install.

I downloaded the 1.01 zip and the 1.2 updated executables from the fan site.
Unfortunately, I cannot seem to launch it whatsoever.
All the files, including doukutsu.bin have the executable bit set.

./doukutsu, ./doukutsu_64bits, ./doukutsu.bin.. all return:
```
env: ./doukutsu.bin: No such file or directory
```

I even created a sh script to cd to the directory and launch it.. doesn't seem to work.
Such a simple issue.. it makes me feel like I have some stupid misunderstanding with Bash. 

Anyone know what's up?

---

### Post by thatguruguy on 2012-05-11
> **mode7 said:**
> I was trying out the Commodore Vision Linux distro (Always been a Commodore fan, but too bloated for my tastes.. I'll stick with Ubuntu).
Anyhow, I was playing Cave Story on it for a bit and rather enjoyed the game. Considering it was a live session, I figured I would download it and play it on my Ubuntu 12.04 install.

I downloaded the 1.01 zip and the 1.2 updated executables from the fan site.
Unfortunately, I cannot seem to launch it whatsoever.
All the files, including doukutsu.bin have the executable bit set.

./doukutsu, ./doukutsu_64bits, ./doukutsu.bin.. all return:
```
env: ./doukutsu.bin: No such file or directory
```I even created a sh script to cd to the directory and launch it.. doesn't seem to work.
Such a simple issue.. it makes me feel like I have some stupid misunderstanding with Bash. 

Anyone know what's up?

That is really, really weird. Have you tried re-downloading the game, just in case you got a bad copy?

Personally, I couldn't get doukutsu_64bits to run, but it doesn't really matter due to 12.04's much-improved multiarch support.

---

### Post by mode7 on 2012-05-15
Yes, I have tried it in Kubuntu, then tried it on vanilla Ubuntu after wiping the previous install.
Just can't seem to launch.. 

So I tried it on my other laptop, which happened to be the one I played it on originally (So I KNOW it can work). And it fails to launch again, but with different results.
trying "./doukutsu_32bits(64bits)" and I get a permission denied, so I know bash sees it there. 
When I set the executable bit, 64bits version "cannot be found", and 32bits version says it cannot load the libsdl library (Which is in the directory).
Doing the straight ./doukutsu returns *nothing* to the terminal, but it creates an error.log saying that sdl_init failed, with no indication as to why.

I don't know why this laptop gives more feedback than my other laptop, which simply cannot find the executable in all cases. The other is a macbook, but there should be no environmental differences. I just use the macbook a lot more.

So I'm going to guess it's an issue with SDL, and possibly because of architecture. If so, then I am out of luck, because I use 2 laptops and a desktop, and they are all x86_64 comps :)
For what it's worth, the commodore linux live cd that I tried out was a 32bit build.

---

### Post by thatguruguy on 2012-05-16
That is, again, really weird.  Have you tried other games?

Also, you should know that a commercial version of Cave Story (actually, Cave Story+) has been released, with improved graphics, etc.  You can pick it up [here]("http://www.desura.com/games/cave-story").  That may resolve your problem.

---

### Post by mode7 on 2012-05-17
Thanks for the replies.

I do play a number of other games on this install.. i.e. Minecraft, OpenRA, ASC.
I've also worked on some SDL/C++ development on this laptop, and everything seemed to work fine..

I did indeed see the Cave Story+ release. I am a bit wary to try it, considering I cannot get the free version to run..
I might end up using the Windows or OSX version of the game, although I'd much prefer Ubuntu.

In the morning, I will try downloading the ia32-libs package, which may allow the game to launch. I can't now, since I am at work, and can only tether this laptop off of my data plan :)

I will post results when I can. I'd love to figure this out, or at least learn a little more about Ubuntu's 32/64 bit inter-operation.

---

### Post by mode7 on 2012-05-20
Well, installing ia32-libs fixed it. Launches just fine..
Doesn't reset the resolution when closing, but I can work around that. 
The 1.2 executable (32 bit only) works, but places it in a 640x480 box in the corner of the screen with the rest of desktop visible (Can't interact with the desktop, alt-tab, etc..)

Unfortunately, it would take me forever to narrow down which x86 package is responsible.
I'll look through the packages some more, maybe see some likely culprit.

---

