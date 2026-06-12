---
title: "Unreal Tournament too fast"
date: 2006-07-12
forum: Gaming &amp; Leisure
---

### Post by Bagnaj97 on 2006-07-12
Unreal Tournament (The original) runs too fast on my system (Athlon64 3200+, 32bit dapper, 1 gig RAM, NVidia 6600gt with NVidia drivers).

I've disabled powernowd which causes problems, and I've used the script from somewhere on icculus.org, which slows it down a bit. The problem is that even after I've done these things it still runs faster than it should. Does anyone have any ideas what this could be?

---

### Post by PriceChild on 2006-07-12
There is actually an option in the settings window inside the UT gui to change the game speed. Mine is currently set to 100% with similar hardware.

Maybe try lowering yours?

---

### Post by Bagnaj97 on 2006-07-12
The trouble is when I try to play a network game over lan agains windows users I run faster than them. If I set the game speed lower is slows them and me down and I'm still faster than them.

---

### Post by PriceChild on 2006-07-12
Yeah i saw this problem when i had a mini lan party, really annoyed me.

We didn't find any way to sort it out unfortunately. :( (this happenned with a windows machine.)

Have you tried joining a game, instead of hosting?

---

### Post by admiralawesome on 2006-07-12
We had a similar problem playing UT on the lan awhile back; these were all windows machines.  It turns out it has something to do with the way UT calculates the speed of the CPU at startup.  Executing the game with a "-cpuspeed=#" switch, where # is the speed of your CPU in mhz, fixed the problem.  That was in Windows though.  I'd think there would be a similar switch for the linux executable.

---

### Post by Bagnaj97 on 2006-07-12
The problem occurs whether I'm hosting or joining. It's nothing to do with the CPUspeed because I disabled powernowd which scales my cpu speed. This problem really has me stumped.

---

### Post by nthdegree on 2006-07-13
Assuming you use cedega:

Pixel Shaders as 1.4 with Win98 works best of all!

Also use resolutions like 1024x768 and 800x600 (on dapper) as they work best with cedega, in UT you want to run it windowed to avoid problems, synchronize the resolution with that of dapper and then fix the speed by switching from D3D to Software Rendering (or S3 Savage) and then to D3D again.

After that it should have slowed down slighly.  You can then proceed to tweak the options to run smoothly then quit and restart.

Sometimes it takes a little more but it will work eventually, I have a perfect UT running 100% smoothly at the correct speed on both online games and offline.

WARNING:  I thought I might mention that UT crashes constantly under D3D in cedega and I don't mean it not responding, the entire system locks up!

P.S Changing game speed doesn't work for online so it's best to fiddle with the unrealtournament.ini and do the above to help sort the speed.

---

### Post by leech on 2006-07-13
Why would you use Cedega?  Unreal Tournament has a native linux client, and is supported quite well.  

On my laptop I had the problem of it running at about a million frames per second, but after using the script on icculus.org it worked fine.

The problem I had was with Rune, which has the same speed problem UT does, though the script worked for Rune to slow it down, the sound is pretty much crap on my laptop (I still need to try it out on my desktop to see if that's the case there too.)

I don't know if shutting off PowernowD will do anything.  I just know that the script in essence just adds some heavy math computations to start up before the game, so that your CPU will go to it's max speed before starting UT or Rune.  So in essence you shouldn't need to shut off powernowd.

Leech

---

### Post by nthdegree on 2006-07-13
"This installation doesn't support glibc-2.0 on Linux / x86_64"

That is the message the installer gives and I (and i'm sure any other x86_64 user will think the same and) am not prepared to downgrade to i386!

Maybe someone could tell me how to specify the older glibc version as that may work :)

I want to ditch cedega badly but need it for UT and Q3A due to these problems.

---

### Post by Bagnaj97 on 2006-07-13
> **nthdegree said:**
> "This installation doesn't support glibc-2.0 on Linux / x86_64"

That is the message the installer gives and I (and i'm sure any other x86_64 user will think the same and) am not prepared to downgrade to i386!

Maybe someone could tell me how to specify the older glibc version as that may work :)

I want to ditch cedega badly but need it for UT and Q3A due to these problems.

I'm using the 32bit version of ubuntu so that problem doesn't affect me. I guess you could use a chroot environment to avoid cedega, I dont know how to do that though. If you dont need punkbuster grab the version of quake3 from icculus.org, there is a native x86_64 build.

---

### Post by Bagnaj97 on 2006-07-13
Under windows UT runs fine without the extra -cpuspeed=2000 under wine it works with -cpuspeed=2000 but is too fast otherwise, and the native version is too fast. I dont know what the problem can be because gkrellm and the CPU frequency scaling monitor panel applet both report my cpu as running at 2000MHz.

---

### Post by DemonTPx on 2006-11-10
Hi.

I am having this same problem, but found out that if I disable audio in UT, the game will run correctly (even with powernowd on). But when I turn audio on (both the generic and the openal drivers), it starts to run at 200~300% speed.

I also tried the icculus.org script, which floods the cpu for 4 seconds while starting UT. But this makes the audio really shocky!

---

### Post by hardsteel on 2006-11-10
I have almost the same problem. My cpu is athlon 64 X2 3800+. The game runs normally for some time and then runs very fast. Also had this problem with 64 bit windows xp. I thought installing 32 bit ubuntu would solve this, but no. Tried some icculus script, booting with acpi=off and noapic. The causer of the problem seems to be 2 cores. Any way to fix this problem? Other games (ET, Q3) seem to work fine. Please help me fix this problem, otherwise I am forced to downgrade to Athlon 64 :(

No ideas?
up

---

### Post by smack on 2006-11-12
Turning on vsync is a workaround for this problem.

---

### Post by BLTicklemonster on 2006-11-12
Run at high resolution, surround sound, download bittorrents, and watch a movie while you play.

lol j/k Hope you get it working with the vsynch thing.

---

### Post by Polygon on 2006-11-12
do you have a dual core processor? i know with games like half life they run at like hyper-speed with dual cores unless you specifically tell it to use one core.

---

### Post by DemonTPx on 2006-11-13
Could anyone confirm my thought on this? By turning off the sound?
By setting this in the ~/.openalrc file:
(define devices '(null))
Or something like that...?

---

### Post by hardsteel on 2006-11-14
> **smack said:**
> Turning on vsync is a workaround for this problem.

U mean turning it off? Because by deafult, it is turned on and to disable it it must be turned to 'true' :) That's a wierd thing but it's true.
Now, in windows i type 'preferences' in the console and it opens a windows where i can change the setting. This command doesn't work in linux and i didn't find the appropriate setting neither in unrealtournament.ini or user.ini.

Now what? :-k 

> **Polygon said:**
> do you have a dual core processor? i know with games like half life they run at like hyper-speed with dual cores unless you specifically tell it to use one core.
I am running dual core cpu but how am I supposed to tell the computer to use only 1 of them :(

up, up, up, another up :P
ffs, seems I gotta downgrade :|

---

### Post by iamdead on 2006-11-17
try to go to nvidia settings and set the antialiasing on 4x.I got a speed problem whit  UT GOTY AND TACTICAL OPS, this worked for me :) before i did that i tried many things ..optimice prossesors new drivers and a lot of things i find on the  net.i hope this will work for som of you

---

### Post by DemonTPx on 2006-11-30
..And what if I do not have a nVidia card, but an intel?
..And what about the sound issue i am having? can anyone who has this problem, PLEASE check if unreal tournament is working properly if the sound is disabled? (see my previous post #17 how to do that)

Thanks.

[edit]
Again: when sound IS enabled, the video is way too fast, and the audio is too slow, and shocks...
[/edit]

---

### Post by steve.horsley on 2006-12-15
> **smack said:**
> Turning on vsync is a workaround for this problem.

I'd like to try that fix - how do I turn on vsync?

---

### Post by szantaii on 2007-03-20
Maybe I have a solution for those who have Beryl.

The story:
I've faced the same problem, when UT was running too fast...
I recently intalled Beryl, and I've played UT on it (and its speed was ok), but when I mde some changes in the Beryl Manager. And from that UT was too fast... (I have a Lenovo 3000 n100 with a Core2Duo 1.66GHz and Intel GMA950).

The Solution:
Open the Beryl Manager, go to the Extras 'tab' and chechk blank the Disable limiter function under Bechmark menu.
My problem was that I've forgot to set it blank (not chechked), so thats it. My UT is running fine now.

---

### Post by Fingel on 2008-03-15
Over the last fews days I've been trying to solve this issue, I have UT running smooth now in Linux.
I wrote a howto you can find here: [http://www.fingel.com/ut/howtos/utonlinux.html]("http://www.fingel.com/ut/howtos/utonlinux.html")
It also addresses some of the sound problems some have been having.
Happy Fragging!:guitar:

---

### Post by BLTicklemonster on 2008-06-13
I'd thank you if I could, Fingel.

[IMG]http://img262.imageshack.us/img262/4155/shot0088jj3.png[/IMG]
(That's in a room full of really good shooters)

I dropped a new 64 bit athlon 3200+ into my tower and hooked my ubuntu drive up to it just hoping it would work, and it did, remarkably! But UT was skanky til I found your launcher. Thanks a ton!

---

