---
title: "Windows vs. Native Linux performance?"
date: 2006-03-01
forum: Gaming &amp; Leisure
---

### Post by Donshyoku on 2006-03-01
Hey all, my desktop serves as a media center (TV tuner for watching/recording, I have not TV) and a gaming center.  It is on Windows right now, but I am trying to make the transition into MythTV or maybe Freevo very soon.

I have a question... most of the games I play (UT2004 and Quake 4 are all that I play right now) will run natively in Linux.  Which is good, but I am unsure about performance?

With the proprietary Nvidia drivers in Ubuntu... should I expect more or less performance as compared to Windows?  Quake 4 is already pushing my system, and if I am going to lost 10FPS in Linux, that will just about kill it.

Any comments?  Thanks!

---

### Post by polpak on 2006-03-01
Native games running under linux will tend to perform better (not worse) than the same game running natively under windows.

Non-native games running in wine under linux are a bit more likely to see performance loss, but it varies from game to game.

---

### Post by Donshyoku on 2006-03-01
Good to know!  

The memory usage in Linux is much lesser than that of Windows.  The game only has access to about 800MB of my 1GB of RAM.  Ubuntu doesn't use nearly as much!

Now, if I could figure out my TV tuner issue (psssst... check out the Sound and Video forum!).

Thanks, again!

---

### Post by xequence on 2006-03-01
Ive heard of UT running much better in linux. (But not with ATI).

---

### Post by deathbyswiftwind on 2006-03-01
I myself have experienced ut04 in linux run awsome but the quake 4 runs better in windows for me

---

### Post by leech on 2006-03-02
Quake4 runs quite well in linux, and I think they just released a beta patch for it.  UT2004 easily runs as well, if not a bit better than windows.

I have MythTV running here and it's sweet.  I have TV Tuner issues of my own... but that's because it's a crappy tuner...

Leech

---

### Post by glaze on 2006-03-02
[QUOTE=Donshyoku]Good to know!  

The memory usage in Linux is much lesser than that of Windows.  The game only has access to about 800MB of my 1GB of RAM.  Ubuntu doesn't use nearly as much!

Thanks, again![/QUOTE]

If You don't have a special kernel patch set, the kernel can only utilize about 896 MiB  RAM even if You have more.

---

### Post by Eazy© on 2006-03-02
For me UT2004 have just about the same fps, perhaps better than in Windows, but fps is not every thing. You can read about my problems here:
[http://ubuntuforums.org/showthread.php?t=136630](http://ubuntuforums.org/showthread.php?t=136630)

Maybe I'm just picky, but as I see it, it's unplayible. Noone seems to have a solution to this problem, and neither do I. So for me, I'm stuck with Windows.

---

### Post by dickohead on 2006-03-02
I'm pretty sure that Quake is developed for Linux first... read that somewhere once....

---

### Post by AndersAA on 2006-03-03
all of the games mentioned so far (including quake) is optimized for windows, and a lot of them has stuff like all assembly optimizations available for windows.  This brings a huge performance boost, which in my experience means it runs pretty much same speed on linux/windows until the first few performance patches shows up for linux ;)

---

### Post by frodon on 2006-03-03
I ran steam under windows and linux and was really surprised to see better performances under linux especially because it's a windows games.
By the way, i use cedega to run steam.

---

### Post by leech on 2006-03-03
[QUOTE=AndersAA]all of the games mentioned so far (including quake) is optimized for windows, and a lot of them has stuff like all assembly optimizations available for windows.  This brings a huge performance boost, which in my experience means it runs pretty much same speed on linux/windows until the first few performance patches shows up for linux ;)[/QUOTE]

I don't know if that's entirely true.  I would think that it's more like the games are optimized for the API (in the case of Native games like the iD games, it's OpenGL), so it theoretically should all be up to how good are your OpenGL drivers.  The rest of the difference would be just in overhead, like the OS, services, etc.

Leech

---

### Post by AndersAA on 2006-03-03
[QUOTE=leech]I don't know if that's entirely true.  I would think that it's more like the games are optimized for the API (in the case of Native games like the iD games, it's OpenGL), so it theoretically should all be up to how good are your OpenGL drivers.  The rest of the difference would be just in overhead, like the OS, services, etc.

Leech[/QUOTE]

if I remember correctly, both the UT and quake engines had masm assembly optimizations, and those could not be compiled in linux, so the windows code was FAR more optimized in the beginning.

---

### Post by Talikar on 2006-03-03
[QUOTE=AndersAA]if I remember correctly, both the UT and quake engines had masm assembly optimizations, and those could not be compiled in linux, so the windows code was FAR more optimized in the beginning.[/QUOTE]

And the unfair comparison between windows running windows games and linux running windows game continues!

Well duh things made mainly on windows gear and for windows software will most certain run better on windows! Unless the linux box is tweaked in a certain way, but then again, if you think about it Linux CAN run Windows games and its own games. Can windows run linux games? I have no idea, my best guess is no, not unless it's source is compiled using windows software.

My point is, things made for linux will run generally better on linux; things made with windows.... well... hit and miss scenario here, but that's fine. Windows games with a frontend allowing them to run on linux (like Doom3 for example)... Well, I can't see any reason why the same hardware can't produce the same or better quality of gameplay. So I honestly don't see how a game like that would suffer a performance loss.:-k 

The point of the matter is, if you want both windows and linux games working at 100% , dual boot both Operating Systems.:twisted:

---

### Post by handy on 2006-03-04
I have run ut2k4 on my machine in a dual boot senario.  

(I barely boot xp these days, & it's about to be cloned onto a small drive I have kicking about & only put in it's draw if I have to help somebody else with those tools.)

Anyway, I have found ut2k4 to be atleast as fast on Ubuntu as on xp.  I run it with everything turned on to the max re: graphics, & @ 1600 x 1200 res'.

It runs faultlesly under all conditions, I could not think of anyway to improve ut2k4 under either OS.

I also play Guild Wars under Cedega 4.4.3 on Ubuntu, @ 1600 x 1200 res', not quite as good as under xp, but fantastic anyway! :KS 

No need for xp for me...

---

### Post by AndersAA on 2006-03-04
[QUOTE=Talikar]And the unfair comparison between windows running windows games and linux running windows game continues!

Well duh things made mainly on windows gear and for windows software will most certain run better on windows! Unless the linux box is tweaked in a certain way, but then again, if you think about it Linux CAN run Windows games and its own games. Can windows run linux games? I have no idea, my best guess is no, not unless it's source is compiled using windows software.[/QUOTE]

thats my point, native stuff if highly optimized for windows will generally run as fast on linux, and as soon as performance patches shows up for linux (which they generally do fairly soon) it's linux rules all ;)

I remember UT ran faster on linux when it was brand new if your cpu wasn't the bottleneck, but after optimizations linux won it basically every time even with a slightly slower cpu ;)

---

### Post by leech on 2006-03-04
[QUOTE=AndersAA]if I remember correctly, both the UT and quake engines had masm assembly optimizations, and those could not be compiled in linux, so the windows code was FAR more optimized in the beginning.[/QUOTE]

I could be wrong, but if I recall, the original Quake was actually coded on a Linux machine, or it was a *nix machine of some other type.

Either way, it's apples to oranges.  Most games in Windows use DirectX, whereas all the games in linux use OpenGL.  This of course is one of the reasons why ATIs suck in Linux, they're OpenGL drivers aren't fantastic under Windows either.  

Leech

---

