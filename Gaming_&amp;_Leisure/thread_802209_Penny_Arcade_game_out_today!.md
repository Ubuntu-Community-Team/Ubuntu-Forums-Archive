---
title: "Penny Arcade game out today!"
date: 2008-05-21
forum: Gaming &amp; Leisure
---

### Post by Vadi on 2008-05-21
All news here: [http://www.playgreenhouse.com/](http://www.playgreenhouse.com/)

They do have a native Linux version, and it works on both 32 and 64bit.

---

### Post by Extreme Coder on 2008-05-21
Great! Thanks for letting me know :)

---

### Post by cogadh on 2008-05-21
Sweet! They even have a demo.

---

### Post by Perfect Storm on 2008-05-21
Diffently a buy. Going try out the demo and see how well it runs on 64-bit system.

EDIT: Works great!

---

### Post by kirsis on 2008-05-21
Downloading the demo. I dig their humor and appreciate the fact that they bothered to create a Linux native version. 

If I like the demo, this will be the first game ever that I'm buying :)

---

### Post by voidmage on 2008-05-21
I can't get full screen to work on 1920x1200. If I pick that resolution, it switches between full screen and windowed mode where it goes offscreen, until the timer runs out and it switches back to 1680x1050 windowed. Did anyone else have this problem and how were they able to fix it?

---

### Post by Vadi on 2008-05-21
I read a report that on a mac on a similar high res that doesn't work. It works for me on 1440x900 though, fullscreen. Try lowering it.

---

### Post by Perfect Storm on 2008-05-21
64-bit:
The only problem (bug) I had was that the game was looking for the fmod files on system wide instead of the game directory, easy to fix by copy the files to /usr/lib32

I'm the only one?
Afterwards I ran ldd on the binary to check the dependency list and it confirm it.


```
[size=1]orion@orion:~/.Games/PAA-Darkness$ ldd RainSlickEp1_bin 	linux-gate.so.1 =>  (0xffffe000)
	libfmodex.so => /usr/lib32/libfmodex.so (0xf7de8000)
	libfmodevent.so => /usr/lib32/libfmodevent.so (0xf7d8a000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7ce4000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf7cde000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7beb000)
	libm.so.6 => /lib32/libm.so.6 (0xf7bc6000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7bbb000)
	libc.so.6 => /lib32/libc.so.6 (0xf7a6c000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7a67000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7a4f000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7a41000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf795a000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf6c1b000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6c18000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6c10000)
	/lib/ld-linux.so.2 (0xf7fd6000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6c0d000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf6c0b000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6bf3000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6bed000)
orion@orion:~/.Games/PAA-Darkness$ 

```[/size]

---

### Post by Het Irv on 2008-05-21
I am getting an error:


```
Could not find a compatible display device! Make sure your display device supports Open GL 1.2 and the following extensions ARB_multitexture ARB_Texture_env_Combine....
``` there are a few others as well.  

LSPCI
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```

---

### Post by Perfect Storm on 2008-05-21
Hmm...it says on the requirement page that they support 950 and up, maybe there something you need to set up in your xorg.conf for running it. But I'm not sure if the support of 950 and up also include Linux, there might be something in the intel linux driver that aren't implanted. Have you tried the latest intel driver release?


OT: Just bought the game :guitar:

---

### Post by EvilOatmeal on 2008-05-21
> **Artificial Intelligence said:**
> Hmm...it says on the requirement page that they support 950 and up, maybe there something you need to set up in your xorg.conf for running it. But I'm not sure if the support of 950 and up also include Linux, there might be something in the intel linux driver that aren't implanted. Have you tried the latest intel driver release?

The system requirements says that the 950 is supported on Linux.
[http://www.playgreenhouse.com/featuredGame](http://www.playgreenhouse.com/featuredGame)

I'm getting the same errors that **Het Irv** does, on my Dell Latitude d830 with Intel in it. :(

---

### Post by Vadi on 2008-05-21
Check the forums, there's a problem that that card and the compression used apparently. Someone put up a solution.

And no, don't get that library error... but what are you using to start the game? I use the bash script they provided.

---

### Post by Perfect Storm on 2008-05-21
Hmm...I run the binary directly...going to check this...


EDIT: Aye, I ran the binary directly. The script fix this.

---

### Post by Swarms on 2008-05-21
I got stuck after defeating the two vulgar robots, I couldn't move like I was still in combat mode, but nothing to click. Had to close, but I see the only way to get there again is to start over again. :(

---

### Post by Perfect Storm on 2008-05-21
Guide Done: [http://gaming.gwos.org/doku.php/guides:64bit:penny_arcade_adventures_on_the_rain-slick_precipice_of_darkness](http://gaming.gwos.org/doku.php/guides:64bit:penny_arcade_adventures_on_the_rain-slick_precipice_of_darkness)

---

### Post by Swarms on 2008-05-21
Ok played the demo through, and nice guide AI. But I had to move the .sh launcher to the directory of the game itself, and edit the menu launcher to direct to that for the game to launch.

By the way, the sound was very choppy, do you use some other settings than those that follow with Hardy?
Played the demo through, and enjoyed it very much. :)

---

### Post by Perfect Storm on 2008-05-21
I didn't understand it what you mean? Is there an error in the guide, just PM me (in danish if you like).


No choppy sound here.

---

### Post by Swarms on 2008-05-21
When I triggered the launcher, nothing happened, and I noticed it was at the /.Games folder, just like the folder containing the game. So I figured if I moved the launcher inside the game containing folder, that means /.Games/PAA-Darkness folder, then it worked instantly. Then I had to edit the string in Alacarte so it directed to the correct folder aswell.

Am I just confusing or does it make sense?

Edit: Btw. how is the full game? :)

---

### Post by Perfect Storm on 2008-05-21
Ah okay, I'll take a look at it...

Started a new game (I didn't saved, hehehe), so I'm still where you can be in the demo.

---

### Post by Vadi on 2008-05-21
The game is worth buying. I do have the choppy-ish sound though, but it's not much of a bother once you get into the action. Or it goes away. Dunno.

---

### Post by jwbaker on 2008-05-22
> **Vadi said:**
> Check the forums, there's a problem that that card and the compression used apparently. Someone put up a solution.

And no, don't get that library error... but what are you using to start the game? I use the bash script they provided.

What forum are you referring to?  This forum?  The Penny Arcade forum?  The forum on the site where you download the game?  Could you kindly post a link?

-Jeff

---

### Post by Vadi on 2008-05-22
[http://forum.playgreenhouse.com/jforum/forums/list.page](http://forum.playgreenhouse.com/jforum/forums/list.page)

---

### Post by Swarms on 2008-05-22
How to tjeck which soundcard you got? Because I think I got a Realtek one and not a SigmaTel.

---

### Post by Perfect Storm on 2008-05-22
Under "Option" there's a box called "Use Hardware Processing". Have you tried if it can help with your problem.

---

### Post by Swarms on 2008-05-22
Yeah, no luck.

---

### Post by arcanistherogue on 2008-05-22
Just jumping in to say I have the exact same audio problem.  I was looking for a solution, just like the above poster said that option does nothing.

---

### Post by voidmage on 2008-05-22
I'm at the final boss and it's segfaulting:
```

./RainSlickEp1: line 20: 10957 Floating point exception./RainSlickEp1_bin

```
The 10957 is the PID. I'm running 64bit but the game worked fine up until now.

---

### Post by Naegling23 on 2008-05-23
hey, what kind of game is this?

Is this like the old lucas arts games, or more of an rpg, or an action adventure?

I'll check out the demo, but I do want to see whether or not its something I would even be interested in.

---

### Post by cogadh on 2008-05-23
Point n' Click adventure game with a little RPG, a lot of attitude and a few bad words mixed in.

---

### Post by Vadi on 2008-05-23
And breaking your spacebar

---

### Post by desertboy on 2008-05-23
Ron Gilbert and a linux version has me sold.

---

### Post by sirdilznik on 2008-05-23
This game is great.  After playing the demo I made the purchase.  Tons of fun, great cartoony graphics, a fun mix of humor, action,and some RPG elements. 8)

I haven't had any sound issues myself.  I hope those get resolved for others.

---

### Post by Swarms on 2008-05-23
Waiting for soundfix, then I will aswell. :)

---

### Post by anjilslaire on 2008-05-23
Loving the demo. Got it on Linux as well as xbox 360, to compare. They play equally well, with great graphics and sound on both. I'll probably purchase the LInux version to show my support.

---

### Post by Vadi on 2008-05-23
Same purchase extends on all platforms, so you'll still be able to play on your 360.

Edit: btw, someone posted a solution on their forums that solved the choppy sound. Run the game with "pasuspender ./RainSlickEp1", or if you made a launcher for it somewhere, put "pasuspender " before the command to run it.

---

### Post by arcanistherogue on 2008-05-23
> **Vadi said:**
> Edit: btw, someone posted a solution on their forums that solved the choppy sound. Run the game with "pasuspender ./RainSlickEp1", or if you made a launcher for it somewhere, put "pasuspender " before the command to run it.

That did nothing for me.  

```
john@melchior:~/Games/rspod$ pasuspender ./RainSlickEp1
Connection failure: Connection refused
```

When the game launched it still had crackly sound.

I really want to support this but I don't want to buy it if I can't enjoy it :(

EDIT: Would like to confirm that while the first didn't work, this other fix found on their forums did:

```
sudo apt-get install alsa-oss
aoss ./RainSlickEp1
```

---

### Post by Vadi on 2008-05-23
There's a bunch more solutions on their forums, I recommend you try them out.

At least this is a good experience in why you should *not* include software that was just released and not tested enough, heh.

---

### Post by anjilslaire on 2008-05-23
> **Vadi said:**
> Same purchase extends on all platforms, so you'll still be able to play on your 360.

I'm a bit skeptical of that.
You don't have a 360, do you? It's downloaded/purchased from the Xbox Live Marketplace. They don't have license codes. You spend MS Market points, it unlocks. You have no codes to enter or keep. It stays linked to your live account.

---

### Post by TigerDX on 2008-05-23
> **anjilslaire said:**
> I'm a bit skeptical of that.
You don't have a 360, do you? It's downloaded/purchased from the Xbox Live Marketplace. They don't have license codes. You spend MS Market points, it unlocks. You have no codes to enter or keep. It stays linked to your live account.

There is *potential* for it to work like that, because there are codes you can use to get XBLA games for free. However, I don't think Microsoft would ever let it happen that way, because if you bought the game through playgreenhouse.com, they no longer get a share of the sale. Microsoft want their cut because they're effectively acting as the distributor/retailer in the XBLA space.

---

### Post by Vadi on 2008-05-23
No, sorry, I don't have a 360. I'll be quiet...

---

### Post by missingno on 2008-05-23
I'm getting the same bunch of OpenGL 1.2 errors when I try to run the game.

ldd reveals that I'm missing these two libraries:
```

	libfmodex.so => not found
	libfmodevent.so => not found
```
And a quick search of synaptic for libfmodex, fmodex, modex, libfmodevent, fmodevent, modevent, dammitwherethehellarethesepackages, etc, yields nothing. Halp?

---

### Post by cogadh on 2008-05-24
Those are two of the libs that come with the game (found in the linux_libs directory), you aren't going to find them in Synaptic. As long as you extracted the game to its own directory, then all you should need to do is run the launch script (RainSlickEp1 *not* RainSlickEp1_bin) and the game will find them on its own.

---

### Post by MaximB on 2008-05-24
Played the Demo , cute game, good and unusual style of graphics, a bit cranky sound for me,  but am I missing something ?
I mean all I did in the demo is to collect some items and 2 buddies (and a cat) and fight, always fight...

Is there something else to that ? like solve things or...something else besides fighting ?
(not that I'm complaining, the fighting part is cool by itself but it could get boring after awhile).

---

### Post by quadomatic on 2008-05-24
Cool a demo!

---

### Post by missingno on 2008-05-24
> **cogadh said:**
> Those are two of the libs that come with the game (found in the linux_libs directory), you aren't going to find them in Synaptic. As long as you extracted the game to its own directory, then all you should need to do is run the launch script (RainSlickEp1 *not* RainSlickEp1_bin) and the game will find them on its own.

```
david@david-laptop:~/Desktop/rainslick$ ./RainSlickEp1
*Error message popup about OpenGL*
./RainSlickEp1: line 20:  5685 Segmentation fault      ./RainSlickEp1_bin
```
I even tried copying the two libraries over to /usr/lib in case it was just having problems trying to find the libraries in linux_libs, no dice.
[size=-6]This game better be good once I get it to run...[/size]

EDIT: Oh, wait, ldd RainSlickEp1_bin now shows those two dependencies as satisfied, so I guess whatever's causing the OpenGL errors was something else.

---

### Post by cogadh on 2008-05-24
What do you have for video hardware? It sounds like you are having the same issues that some Intel chipset users are reporting. If so, Vadi said there is a fix posted on the game's forums.

---

### Post by missingno on 2008-05-24
I've got an ATI Radeon X1200, but I'll check on the forums to see if the fix will work anyway.

EDIT: Seems the distributor's website has an announcement posted today about an update to the game to fix things for certain graphics cards. Yay, hope this works!

EDIT EDIT: No dice. >_<

---

### Post by acoustibop on 2008-05-24
> Easily amused by the shinies in Compiz-Fusion
Try starting the game with Compiz disabled, missingno.

---

### Post by bg11 on 2008-05-25
> **MaximB said:**
> Played the Demo , cute game, good and unusual style of graphics, a bit cranky sound for me,  but am I missing something ?
I mean all I did in the demo is to collect some items and 2 buddies (and a cat) and fight, always fight...

Is there something else to that ? like solve things or...something else besides fighting ?
(not that I'm complaining, the fighting part is cool by itself but it could get boring after awhile).

I know what you mean, but the humour is the highlight of this game.  That's what penny arcade is known for.

---

### Post by sirdilznik on 2008-05-25
> **MaximB said:**
> Played the Demo , cute game, good and unusual style of graphics, a bit cranky sound for me,  but am I missing something ?
I mean all I did in the demo is to collect some items and 2 buddies (and a cat) and fight, always fight...
[B]
Is there something else to that ? like solve things or...something else besides fighting ?[/B]
(not that I'm complaining, the fighting part is cool by itself but it could get boring after awhile).

Yes.  You collect items to solve cases and move the story along (Think Monkey Island or old Sierra games like King's Quest, Space Quest, etc...).  Interact with a bunch of NPCs.  Get support characters.  Advance in level.  Get new attacks.  Upgrade weapons.  Play mini-games.

---

### Post by MaximB on 2008-05-25
> **sirdilznik said:**
> Yes.  You collect items to solve cases and move the story along (Think Monkey Island or old Sierra games like King's Quest, Space Quest, etc...).  Interact with a bunch of NPCs.  Get support characters.  Advance in level.  Get new attacks.  Upgrade weapons.  Play mini-games.

I know it's not an RPG but do you have several ways to solve a quest ? are there multiply endings ?

---

