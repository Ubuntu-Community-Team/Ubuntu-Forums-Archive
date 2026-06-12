---
title: "Gaming in Linux as compared to Windows (XP)"
date: 2009-08-18
forum: Gaming &amp; Leisure
---

### Post by sempronius on 2009-08-18
I am a long time Linux user and use Linux almost exclusively, rarely Windows XP (and I also boot into Windows 7 from time to time).

I experience one issue with playing games in Linux:
- the mouse sometimes misses clicks!

But games (the few I play) run great: smooth, high fps, excellent mouse movement etc.

Does my experience with lost mouse button clicks in Linux games (quake2, but also quake1 and quakeworld) sound familiar to some of you (who also boot into Windows sometimes)?


Some additional remarks:
- MS Intellimouse Optical
(but tested with lots of other mice, too: same result!)
- set at 500 Hertz polling rate (in both Linux and Windows)
- comparing the same games
(e.g. for quake2: AprQ2 both in XP and in Linux)
(e.g. for quakeworld: ezquake in both XP and in Linux)

Always the same result:
- playing in XP gives me about the same fps, the same movement quality, but in contrast to Linux: excellent mouse click reliability. De facto: each mouse click (even when rapidly firing) gets registered, none is being lost.
In Linux: most clicks DO register, but some of them are lost when rapidly clicking the mouse1 (fire) button. This happens every day and in every 10 minutes interval at least 3-5 times, so it IS annoying! 

The consequence is:
I am a much better player when using windows (well: I am not bad in either, but the difference is there!).


I tried:
- mouse driver "mouse" and mouse driver "evdev": no difference
- with and without dga: no difference
- opengl and software mode (ugly) quake2: no difference
- maybe (?) a slight difference when using the sdlgl version of quake2 instead of the glx version: fewer clicks are being lost in the sdl version

No, it is NOT a faulty mouse: it works perfectly in windows XP and in windows 7.

I don't have any important background processes running in Linux while playing a game.

I also played with mouse priority changes and with different schedulers: nothing helps.

I even tried a different Linux distribution: Slax (slackware based): same result!


I am inclined to think this is a real Linux issue (kernel?). Though I must add that I tried so many different 2.6 kernels and with so many options... nothing helps.

And one last note:
Many will not notice the problem, only more ambitious/skilled players, I am sure.

Since I tried so many things, read about thousands of threads in Google and in different forums, I am out of ideas right now.

Perhaps, someone can contribute his own experience with mouse button response time in Linux versus Windows.


Oh, and something should be made clear:
I can force the mouse to accept EVERY SINGLE click but I would have to keep the mouse1 button pressed long enough.

So clearly, this must be an issue with Linux requiring a longer period of time of keeping a mouse button pressed until it gets registered. In very rapid fire clicks are lost if I don't keep the button1 pressed long enough. This virtually never happens in windows, though.


Ideas?

thanks, sempronius



EDIT:
I mostly play quake2 at tastyspleen.net (vanilla quake2 deathmatch). Mouse clicks are being lost occasionally, but not that often.
Strangely: When I play deathmatch (OSP tourney this time) at coolnet (217.8.180.90:27910), a Polish server, I get:
a) a much lower ping
b) many more clicks are being lost

---

### Post by Bölvaður on 2009-08-18
Hmm, if we are to play the blame game, then I'd begin at the top and blame the games you are playing. Try playing on your own computer, localhost vs your self (singleplayer or w/e), I guess LAN can be acceptable but even 5-10 ms might be too high to find out if it is the game or the netcode in it.

Try other games, like quake live and warsow. Does it happen there also?

I am a competitive gamer and have a successful history on clanbase, but I have not played the games you have played. And I have never noticed anything like you are describing. I'll keep my eyes on it though.



check my signiture.. just for the fun of it.

---

### Post by sempronius on 2009-08-18
> **Bölvaður said:**
> Hmm, if we are to play the blame game, then I'd begin at the top and blame the games you are playing. Try playing on your own computer, localhost vs your self (singleplayer or w/e), I guess LAN can be acceptable but even 5-10 ms might be too high to find out if it is the game or the netcode in it.

Try other games, like quake live and warsow. Does it happen there also?


Not sure about single player mode (because I am not motivated enough to play it for an extended period of time) but you are right, I should check this...

You made me curious about quake live - I will definitely go and download that thing now. ;-) Though I am not that much of a quake3 player.

More experiences very welcome! :-)

sempronius

---

### Post by CharmyBee on 2009-08-18
> **Bölvaður said:**
> Hmm, if we are to play the blame game, then I'd begin at the top and blame the games you are playing. 
I blame the latency of the kernel. It's a failure for twitch gaming. I also do notice the difference of input responsiveness between Windows and Linux and it's definitely responsive on Windows.

Another problem is SDL_input. Both platforms can suffer equally because of that library.

---

### Post by SolarOnline on 2009-08-19
I've had very little issues with gaming on both my Ubuntu and my Vista Box.

I must say that configuring games is much easier on Vista, but it that was taken away and I had to choose purley based on OS I'd choose Ubuntu every time.

---

### Post by sempronius on 2009-08-19
> **CharmyBee said:**
> I blame the latency of the kernel. It's a failure for twitch gaming. I also do notice the difference of input responsiveness between Windows and Linux and it's definitely responsive on Windows.

Another problem is SDL_input. Both platforms can suffer equally because of that library.

So I am not alone with my problem?

I just tested quake live and I also used a different quake2 client (r1q2), but the problem remains: _some_ of my mouse button presses are lost!

This does not happen when a mouse button is pressed down and kept down (like continous fire with the machine gun, for instance). The mouse doesn't interrupt the fire.

But the issue happens when one has to rapidly press and release the mouse1 button, like with repeated railgun shots or the shotgun.

If the time between two successive mouse button presses is VERY brief, the problem becomes obvious!

This is NOT so in windows (XP, 2000 and 7). Obviously Linux requires the user to keep the mouse button pressed down a wee bit longer (but enough to make a world of a difference).

I am really frustrated by this problem. So I would like to hear from other users who play both in windows and in Linux and who play games like quake2 above average!


One remark considering sdl:
I am not sure sdl is to blame.
I compiled quake2 both for sdl input and without sdl input. The sdl input version loses fewer mouse button clicks than the other (non-sdl) version!


EDIT:
Perhaps, the whole issue is related to the fact that the mouse in Linux is less independent of high CPU usage. I mean, if one causes high CPU load by launching a specific program, the mouse cursor in Linux becomes jerky or the mouse even freezes for a few seconds.
This never (except in the most extreme cases) happens when I load a CPU intensive application in windows; the mouse keeps moving in a normal, non-jerky, way.

But raising the priority of the mouse events in Linux, does not really help. :-(


sempronius

---

### Post by juancarlospaco on 2009-08-19
Try an USB mouse, if its not.
:)

---

### Post by CharmyBee on 2009-08-19
> **sempronius said:**
> So I am not alone with my problem?

Not at all! Some don't even want to admit this shortcoming.

> **juancarlospaco said:**
> Try an USB mouse, if its not.
:)

That won't do a thing. Even a $50 gamer mouse won't help this situation.

---

### Post by juancarlospaco on 2009-08-19
I dont know i got one and dont miss anything...

---

### Post by sempronius on 2009-08-19
> **CharmyBee said:**
> Not at all! Some don't even want to admit this shortcoming.

Yes, I fear, you are so right! 
A big problem in every fan community (or what you would like to call it) is ideologically motivated blindness... sigh... Not to say that I found this in this forum, but via google searches it is hard to find simple honest statements without any kind of ideology behind them. Many fans of <insert whatever> react as if they were personally attacked if someone utters a legitimate criticism or points at a weak spot...

Okay, this intermezzo should be enough. ;-)

I could also go on and mention another "design flaw"(?) in Linux or rather xorg which is the lack of a setting for true "mouse speed" (speed! not acceleration!) xset m only sets acceleration and thresholds, there is nothing to set a true multiplier for _speed_. But this is another topic and not my original question here.

> 
That won't do a thing. Even a $50 gamer mouse won't help this situation.

Yes. As I already said, I used a lot of different mice, the problem is omnipresent in Linux, but not in Windows.

And yes, of course, I used USB mice (and also PS/2). With PS/2 the issue is even worse for me.

I hate using windows exclusively or switching between the systems, so I am still interested in more experiences and (if possible) work-arounds or real solutions. (Not that I am too positive about getting one, though).


sempronius

---

### Post by CharmyBee on 2009-08-19
Using linux-rt kernel (usually seen in audio enthusiast distros) will help, but video driver support isn't guaranteed.

---

### Post by oldrocker99 on 2009-08-19
I have been using Ubuntu for gaming and for other things for 16 months and have never noticed this situation before. Then again, I'm so bad at FPS games that I tend not to play them...

:guitar:

---

### Post by Bölvaður on 2009-08-19
[clickTest_32bit]("http://dl.getdropbox.com/u/955154/clickTest/clickTest_32bit")
[clickTest_64bit]("http://dl.getdropbox.com/u/955154/clickTest/clickTest_64bit")
ATTENTION: run in terminal for the output, there is no use running this without it.


I wrote a simple program to test mouse clicks. There probably is a better way to measure hits other than just count the ones that are detected and look at a graph of audio recording of the mouse clicking and see if it is all have been registered.

I have only used 1 mouse and one main computer past years so I can not say if I'd get a different results with another mouse or lower frequency cpu.

But what I do know is that all of the clicks in this test program I wrote are being registered. The reason for that might be because I do not put it into sleep state.


What I am thinking is that maxfps ingame might cause this to happen if the part of the code that handles inputs is done as many times as drawing of frames.
So perhaps if you have it capped you may click 2 times at a time when the game is in sleep state and may not detect either one of them or only one.

---

### Post by sempronius on 2009-08-20
> **Bölvaður said:**
> 
I wrote a simple program to test mouse clicks. There probably is a better way to measure hits other than just count the ones that are detected and look at a graph of audio recording of the mouse clicking and see if it is all have been registered.


Would you mind posting the source code?


> 
What I am thinking is that maxfps ingame might cause this to happen if the part of the code that handles inputs is done as many times as drawing of frames.
So perhaps if you have it capped you may click 2 times at a time when the game is in sleep state and may not detect either one of them or only one.

I normally play quake2 with what is called "independent physics", like cl_async "1", like cl_maxfps "90", r_maxfps "1000".
But of course I also checked the issue with "indep. physics" disabled (cl_async "0"); in this case, my aiming is worse, so this would not be a solution.

And not to forget:
I use these exact same settings in windows, too.


Do you or anyone else have an explanation why the "lost clicks" issue seems to be worse on low ping servers than on high ping servers?? When I play on the Polish server or some other European server, the issue is worse than when I play on American servers. Any possible explanation?


I would also like to describe the "lost mouse clicks" problem a little bit more:

Imagine a quake2 game, use the rail gun.
If you fire the rail gun successively very fast, you will notice that about every second mouse click does not trigger a shot! This appears to be normal behaviour because the rail gun is a slow gun.

So if you fire a first shot and don't wait until the rail gun is ready again and try to click a second time, this shot does not happen.
If, however, you fire a first shot and (still the same as before) you don't wait long enough to click a second time - BUT THIS TIME instead of just clicking a second time, you click a second time AND ALSO keep the button pressed down a little bit longer, then this second shot will be successful - obviously because it is not the very fast clicking itself that is important, but the interval between two successive shots! So if you keep your finger pressed down a bit longer, you will be able to fire another time.

This is the same in Linux as it is in Windows!

BUT:
I am under the impression that in Linux the finger needs to be pressed down a little bit (a wee bit!) longer than in Windows.

And that appears to be all the magic behind the problem!

Linux does not "lose" the second click, I would conclude...
But it needs a longer time interval between successive mouse events - but this depends on the weapon used!
I never notice the "lost clicks" issue with the machine gun or the simple blaster, but I do notice it with the rocket launcher, the rail gun and the super shot gun, for instance.


If I knew how to tweak the timing in the source code, I might be able to improve that issue.
Provided that it is not a fundamental latency problem of the Linux kernel (though I use a real-time kernel anyway).


sempronius

---

