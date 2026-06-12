---
title: "How to get desktop effects  working."
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by Give_Peace_A_Chance on 2007-04-19
When i click desktop effects the screen is just white....
Is my comp not good enough or do i have to download something?

---

### Post by ryan on 2007-04-20
I had the same thing happen only now I can't get anything except a white screen I even did a reinstall and nada just a white screen. Ctrl,Alt F1, nada Alt F2 nada. I can get a fail safe terminal but not sure what to do from there. Any ideas ? tks

---

### Post by quarkcool on 2007-04-20
Same here; I have an ATI X800 XL video card, is that related? Should I install ATI drivers?

Thanks

---

### Post by jazzman83 on 2007-04-20
I have the exact same problem too and have an ATI Radeon Xpress 200M.  I was wondering if there was a way to turn off desktop effects from the failsafe terminal?

---

### Post by papercuts on 2007-04-20
This might sound silly but in my case when the white screen came up all I had to do to turn it off was hit SPACE again. I don't know if this is anything you guys are going through.

---

### Post by Viruk on 2007-04-20
I had the same problem with my Radeon X1600 card. I just left the effects to turn themselves off after about 40 seconds which they do if you dont accept the changes.

I had the same problem when trying to run Beryl on the beta release of 7.04 but I wasn't able to solve it. 

Maybe its the Radeon drivers, has anyone with a Radeon card managed to get this working? If so, did you have to do anything extra or did it "just work" ?

---

### Post by Toxic-Waste on 2007-04-20
I get a "Composite Extension not available" error...:mad:

---

### Post by h00ligan on 2007-04-20
i get the same result with the ati drivers enabled.. and the same white screen without them.

---

### Post by JuanK on 2007-04-20
Geez, seems to be a problem with ATI cards :( .  I have an Radeon Xpress 200 and the exact same problem.  I enabled dektop effects and the screen went white.

I logged on (via ctrl+alt+f1) on a terminal, tried metacity --replace but it doesn't work.  I says it can't find display "", anybody know how to set metacity to the correct display?

---

### Post by Toxic-Waste on 2007-04-20
I have an ATI card as well... This is the same problem as in Ubuntu 6.10. 
I have tried Sabayon and Open SuSe and this problem doesn't exist. This is annoying... :(
I was expecting this to change with 7.04 but it hasn't by the looks of it.
It's a shame...

---

### Post by bustergonad on 2007-04-20
i have the ATI radeon x200 graphics card.
I have just installed Ubuntu for the first time.
I found this topic [here]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m")

Beryl works fine for me using this guide :)

---

### Post by jaimz on 2007-04-20
I have an ATI radeon x800 using the open source drivers (not the fglrx) working with beryl & aiglx

[PHP]Option "XAANoOffscreenPixmaps" "true"[/PHP]

is the code I added in the"Device" Section of my xorg.conf file

it helped with any errors I had at first with my ATI x800

the open source drivers only work with up to the x850 series, not the x1k from what I've read
so for the x1k they'll have to use the fglrx

Not sure if it might work for others, but it worked for me and it might work for you.

This being on feisty of course

---

### Post by eldragon on 2007-04-20
> **jaimz said:**
> I have an ATI radeon x800 using the open source drivers (not the fglrx) working with beryl & aiglx

[PHP]Option "XAANoOffscreenPixmaps" "true"[/PHP]

is the code I added in the"Device" Section of my xorg.conf file

it helped with any errors I had at first with my ATI x800

the open source drivers only work with up to the x850 series, not the x1k from what I've read
so for the x1k they'll have to use the fglrx

Not sure if it might work for others, but it worked for me and it might work for you.

This being on feisty of course

how did you acomplish that? ive been trying to get the ATI drivers to do some desktop effects on my x600 with no luck.....

---

### Post by jaimz on 2007-04-20
I browsed around for info using the advance search  ;)

well, that was just for the code 

on feisty I noticed the open source drivers worked with my ATI card with direct rendering on
on dapper & edgy, the open source drivers never worked for me
so I always had to use fglrx with xgl & beryl

when I realized I could use the open source drivers, I made it my mission to get it to work with aiglx with beryl
I found that code with in 5 minutes and mission accomplished!

edit - oh and it's best to use the open source drivers without anything installed from fglrx, so if you installed it, you're going to have to use the synamptics package manager to fully remove them
then give open source drivers another try

also keep in mind that the way it worked on my x800 might be different for your x600 (I remember things that worked for other x series cards wouldn't work on mine so yeah...)

---

### Post by eldragon on 2007-04-20
> **jaimz said:**
> I browsed around for info using the advance search  ;)

well, that was just for the code 

on feisty I noticed the open source drivers worked with my ATI card with direct rendering on
on dapper & edgy, the open source drivers never worked for me
so I always had to use fglrx with xgl & beryl

when I realized I could use the open source drivers, I made it my mission to get it to work with aiglx with beryl
I found that code with in 5 minutes and mission accomplished!

edit - oh and it's best to use the open source drivers without anything installed from fglrx, so if you installed it, you're going to have to use the synamptics package manager to fully remove them
then give open source drivers another try

also keep in mind that the way it worked on my x800 might be different for your x600 (I remember things that worked for other x series cards wouldn't work on mine so yeah...)

yes, since i realized my x600 should work with ati + aiglx, i made it a mision too.... plus fglrx is being kind of buggy resolution wise......

anyway, that code isnt cutting it for me.....ive removed everything fglrx already....not working.. damn

EDIT:

i had one last nasty fglrx driver installed......once its gone....everything's back.....ati drivers are not that good, yet they work, i bet they will get better in time.....

btw; how stable is compiz for you? ive found it highly unstable, killling not only gdm, but the whole machine to a full freeze.....twice.....
im keeping effects on hold for now........


EOEDIT

---

### Post by derrekito on 2007-04-21
> **Toxic-Waste said:**
> I get a "Composite Extension not available" error...:mad:

There doesn't seem to be a viable work around for that pertaining to ATI drivers.  It needs Composite Extension, so you would have to enable it in /etc/X11/xorg.cof , HOWEVER doing so breaks the driver and when typing fglrxinfo in the command prompt MESA drivers show up.

---

### Post by fotzlapen on 2007-04-21
I managed to get compiz and Xgl working on my graphics card.  Its an ATI Radeon X2300.  It took a lot of stuffing around with compiling my own fglrx drivers but its working and very stably with compiz  Beryl works as well, but is nowhere near as stable.  I got most of my info for it from this post:

[http://ubuntuforums.org/showthread.php?t=409012&highlight=ati+beryl+installation](http://ubuntuforums.org/showthread.php?t=409012&highlight=ati+beryl+installation)

The formatting in the post is pretty nasty, but when it comes good its great.

Anyone know what is the deal with Xgl and its memory usage?  Is it supposed to go up 2MB everytime you swap desktops.  Seems a bit excessive!  Is this a well known issue?  Does aiglx have the same problem?

---

### Post by Talon2 on 2007-04-21
> **Viruk said:**
> 
Maybe its the Radeon drivers, has anyone with a Radeon card managed to get this working? If so, did you have to do anything extra or did it "just work" ?

Radeon 9600 here.  Worked out of the box (fresh install of 7.04).  Didn't even have to tweek xorg.conf.

It sounds to me like a lot of the problems mentioned in this thread and with more modern radeon cards than I have.  The open source radeon driver is not quite there yet with recent ATI hardware unfortunately.  For the future I'd recommend video cards in this order:

1) Intel (fully open source and Just Work (tm))

2) nVidia (closed source but at least provided driver works well)

3) ATI (older cards that are fully supported by the open source driver work well.  ATI's closed source driver is poor.  There are simply far better choices than ATI if a person is looking for modern graphics cards.)

---

### Post by gashcr on 2007-04-21
Well, maybe I was just lucky... I had to do nothing to make it work, and it runs like silk with my radeon 9250

---

### Post by derrekito on 2007-04-21
> **gashcr said:**
> Well, maybe I was just lucky... I had to do nothing to make it work, and it runs like silk with my radeon 9250

are you running the open source "ati" drivers or the "fglrx" proprietary drivers?

---

### Post by eldragon on 2007-04-21
well, compiz didnt work that well....and effects are nowhere to be seen.....only wobly and cube.... and some transparency....

beryl, works great, not one single freeze.

AIGLX is great if you ask me.

too bad you dont get the same performance with the open ati drivers than what you get with fglrx...

lets hope the next gen of drivers come with better linux support

---

### Post by kbzona on 2007-04-21
> **eldragon said:**
> well, compiz didnt work that well....and effects are nowhere to be seen.....only wobly and cube.... and some transparency....


You can see  Compiz configuration through :

gconf-editor --> apps --> compiz.... bla bla bla....

Is the SVN Beryl  working well on Feisty?!?!?!?! cause i tried it but it gives me a white screen :(

---

### Post by eldragon on 2007-04-24
> **kbzona said:**
> You can see  Compiz configuration through :

gconf-editor --> apps --> compiz.... bla bla bla....

Is the SVN Beryl  working well on Feisty?!?!?!?! cause i tried it but it gives me a white screen :(

i didnt try it...just the 'stable' one

im still having troubles with Xorg or the ATI drivers (Open Source), where computer will completely lock up randomly if compiz or beryl are enabled.....so, fancy looking desktop goes disabled by now...unless someone has a solution

---

### Post by MarkyMac on 2007-04-27
I have a sneaky suspicion that you still are using a resolution of 1024 x 768.
I have a Radeon 9600 128MB M10 in my Dell 8600 & "out of the box" I can only use 1024 x 768 resolution.
Am I correct?
I did use the Desktop Effects but then wanted better resolution & installed the closed ATI drivers.
Bam, dead Effects.
Now I think I'm going to uninstall the ATI drivers & run with the wobbly winders so I impress the kids looking at my screen.
:-D

---

### Post by eldragon on 2007-06-07
i actually got tired of trying....... like a saying goes: 'useless to push if the dick is short'

so, back to fglrx. the bling goes off. and stick with descent 3drender on games (to the extent of ati's shortcomings), and wait for them to make their crapware work.

xgl never worked for me (for some reason i cant explain). so no bling through there either. right now i couldnt give a rats *** about it. im tired of hoping.

what really bugs me is everytime i do some zooming on video that will put some part of it offscreen. garbled pieces of offcreen video appears as a static image somewhere. which is a problem, since ive got a 16:9 screen and tv is still 4:3 analogue. :( (this happens on mythtv)

amd/ati: fix your **** (or open your drivers / specs, so that someone can do it for you)

enough rant

---

### Post by Ki11ah on 2007-06-07
I am quite a noob but managed to get Beryl up and running 
with my Radeon 9600 gfx card. I was well impressed as
it only took a couple of attempts taking roughly an hour.

If I can provide any of my configs to help anyone
let me know on here and I will see what I can do.

A short video of my system running here...
[http://www.youtube.com/watch?v=5Uk4cPR8TuE](http://www.youtube.com/watch?v=5Uk4cPR8TuE)

---

