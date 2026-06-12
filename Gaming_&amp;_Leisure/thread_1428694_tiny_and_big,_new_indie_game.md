---
title: "tiny and big, new indie game"
date: 2010-03-13
forum: Gaming &amp; Leisure
---

### Post by portets on 2010-03-13
just wanted to tell people there's a new game out for linux. it's pretty cool.

just a beta right now. the beta's free, but i'm pretty sure the full game will cost. it's called "Tiny and Big".

they have 32-bit and 64-bit builds. the 64-bit build is running perfect on my machine.

check it out: [tinyandbig]("http://www.tinyandbig.com/download/")

ps, sorry if it's been posted. i never saw it posted though

edit: also, in order to play it, you need these dependencies if you  don't have them

```
sudo apt-get install libsdl1.2-all libsdl-mixer1.2  libopenal1
```

---

### Post by Naiki Muliaina on 2010-03-13
Ty for posting, demos workin here on 64 bit karmic too. :popcorn:

---

### Post by Dayofswords on 2010-03-13
after seeing the video
there is no way that is going to play on my computers

---

### Post by dyltman on 2010-03-13
that actually looks pretty cool.

---

### Post by portets on 2010-03-13
yeah, it actually runs a little slow on my core2duo and 9600m gs.

but only at native resolution, and mostly when i get to the top of the mountain. (1366x768.)
it runs smooth at 800x600. i think i might tell them something.

it's just a beta though, it might get faster. i'm going to send them an e-mail thanking them for linux support though. you guys should too.
we need to let more indie developers know how happy we are for the attention.

oh, and it looks like they use a few open source development tools. in the readme it says:

> Libraries we use 
--------------- 
 
Bullet Continuous Collision Detection and Physics Library 
-- 
Cal3D Character Animation Library 
-- 
Cg Toolkit 
-- 
Lua 
-- 
libogg & libvorbis 
-- 
OpenAL cross platform audio library 
-- 
SDL Simple DirectMedia Layer 
-- 
stb_truetype 
-- 
TinyXml

---

### Post by Chesnut on 2010-03-13
Ohh! That is awesome! Gonna try that game fo' sho'!

---

### Post by DoktorSeven on 2010-03-13
Looks nice, great concept, but the controls are way too floaty and buggy.  Fell through the world several times and jumping is very difficult to stick.

They really need to work on a solid control scheme before going forward.  It'd really be a great game if they could fix that.

---

### Post by Chemical Imbalance on 2010-03-13
Thanks for letting us know about this game.

Super fast download (10 megs a second!).

Looks really interesting, and super awesome that they include linux builds.

---

### Post by portets on 2010-03-13
> **DoktorSeven said:**
> Looks nice, great concept, but the controls are way too floaty and buggy.  Fell through the world several times and jumping is very difficult to stick.

They really need to work on a solid control scheme before going forward.  It'd really be a great game if they could fix that.

yeah, i've noticed the controls feel floaty. and the character floats a lot when jumping. (you can move left and right while still in the air).

i've never fallen through the ground though. but one time i cut down a pillar and it fell through the ground.

remember guy's, they said it's a beta. next to download it says **"BETA v0.1".**

---

### Post by hikaricore on 2010-03-13
Saw the demo friday at work, looks awesome!
I'll probably test it out tomorrow.

---

### Post by juancarlospaco on 2010-03-14
/home/juan/Descargas/tinyandbig/tinyandbig: error while loading shared libraries: libCg.so: cannot open shared object file: No such file or directory

LibC* is installed :(

---

### Post by Chemical Imbalance on 2010-03-15
> **juancarlospaco said:**
> /home/juan/Descargas/tinyandbig/tinyandbig: error while loading shared libraries: libCg.so: cannot open shared object file: No such file or directory

LibC* is installed :(

Same happens here too.

I've had tons of other games have problems with shared libraries on Ubuntu.

---

### Post by DoktorSeven on 2010-03-15
Install libCg manually from nvidia, then run **sudo ldconfig**.

Make sure the libs copy over, too (in /usr/lib or /usr/lib64); I had an odd problem where I copied the whole thing over to /usr but the .so files didn't.  They might have been symlinks or something, I don't remember.

---

### Post by hikaricore on 2010-03-15
Runs super smooth and sweet on my nvidia 8600.  ^_^
Fun little game.  Am I the only one who's tried to see how many ways you can kill the guy?
Thus far he refuses to cut himself in half with the lazer.  :(

---

### Post by Chemical Imbalance on 2010-03-15
> **DoktorSeven said:**
> Install libCg manually from nvidia, then run **sudo ldconfig**.

Make sure the libs copy over, too (in /usr/lib or /usr/lib64); I had an odd problem where I copied the whole thing over to /usr but the .so files didn't.  They might have been symlinks or something, I don't remember.

Did this, but now I get "error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory".

---

### Post by portets on 2010-03-15
did you do the "apt get" instruction in my first post?

---

### Post by Chemical Imbalance on 2010-03-15
> **portets said:**
> did you do the "apt get" instruction in my first post?

Ah, I didn't see that you edited your post.  
Thanks.  I'll try it.

---

### Post by portets on 2010-03-15
> **hikaricore said:**
> Runs super smooth and sweet on my nvidia 8600

really? it runs pretty slow on my 512mb 9600. about 12 fps.

what resolution are you running at?

---

### Post by hikaricore on 2010-03-15
> **portets said:**
> really? it runs pretty slow on my 512mb 9600. about 12 fps.

what resolution are you running at?

1600x1200.  You don't have deskop effects or anything silly like that running in the background do ya?

---

### Post by portets on 2010-03-15
nope. turned them all off, rebooted. even running at 800x600 in full screen gives me about 25 fps.

---

### Post by hikaricore on 2010-03-15
What version of the nvidia driver are you using?

> glxinfo | grep "OpenGL version string"

---

### Post by portets on 2010-03-16
195.36.03

but other games work just fine.


could it be a 64-bit issue?

---

### Post by hikaricore on 2010-03-16
Could be, I'm on 32bit.

---

### Post by portets on 2010-03-16
hmm..   anyone else using 64-bit?

---

### Post by MaximB on 2010-03-16
I run Ubuntu 64-bit and after "installing" the libCg (64-bit) from Nvidia it runs without any problems (using Nvidia GTX 275 Videocard).

---

### Post by Chemical Imbalance on 2010-03-16
I'm running an onboard 8300 and it works great. 
I'm using 64 bit and the nvidia libraries already mentioned.

I like the look of the game, but I agree that the controls are a little iffy at the moment.

---

### Post by portets on 2010-03-17
> **Chemical Imbalance said:**
> I'm running an onboard 8300 and it works great. 
I'm using 64 bit and the nvidia libraries already mentioned.

I like the look of the game, but I agree that the controls are a little iffy at the moment.

weird...
i just updated to the latest cg toolkit with no improvement.
 
and the latest nvidia drivers (195.36.15) which gave me a few fps. but it's still unplayable when i get halfway up the mountain.

---

### Post by bruno9779 on 2010-04-14
with licg from repos I have had a prompt about upgrading from licg 2.1 to 2.2 with a download link :

 [http://developer.nvidia.com/object/cg_download.html](http://developer.nvidia.com/object/cg_download.html)  -

I have installed libcg 2.2.tgz from there with alien, but I keep getting the prompt about being on 2.1 and the app freezes up and i can't kill it even from tty

thanks

---

### Post by bruno9779 on 2010-04-14
it is working now, but the prompt stays

---

### Post by efikkan on 2010-04-14
Looks interesting, I'm going to try it out.

---

### Post by kind_bud on 2010-04-14
I tried it out, I like the cartoony graphics and the fun of it. But the puzzles are kind of hard, it took me 10 minuts to figure out how to jump up the first opsticle on the moutain, and I can't figure out how to get up to the main statue, where you are stopped with pillars. I wish they would make a "walk through" for it on gamefaqs.com. I also like the story to it of the guy with the bolt cutter, and the line. I don't know if the full version is going to be free, but I hope it will be. But if its like the game lugaru where they just give out the demo for free, I will still be happy with it. Has anyone here tried the game X3, I was thinking of getting that for linux, but was unsure of how good it works on it. Anyway, if anyone else had problems with the puzzle in tiny and big, please tell me.

---

### Post by myromance123 on 2010-04-15
I like the demo very much, had no problems running it.

 Although I did have issues with the sound. After about 10 minutes into the game it starts to crackle up and then just  buzzes... Sometimes being in a certain position returns the sound but moving loses it again. Happens every time :/

 Yeah I cant kill the underpants stealer. Tried though hehe
Slice and dice~

---

### Post by bruno9779 on 2010-04-18
Kool game. I f they price it reasonably (under 20$) i will probably buy it

---

