---
title: "Games Are Very Slow\Laggy"
date: 2011-07-27
forum: Gaming &amp; Leisure
---

### Post by Spirrwell on 2011-07-27
It's not just one particular game so I'll get that out of the way, the issue is with any of the games I've tried. It'll only render a few frames at a time while the sound seems perfectly in sync.

I'm running Ubuntu 11.04, and I've tried with and without Unity, and I've seen no difference. What I've gotten to work is Wine. When I use Wine with Windows games it works fine which were the same games as their Linux counterparts.

Here are my system specs:

CPU: Core 2 Extreme QX9650 3.0 GHz
RAM: 8GB DDR3 2000
GRAPHICS CARDS: 2 NVIDIA GeForce 9600 GT"s" in SLI
NVIDIA DRIVER VERSION: 270.41.06
MONITOR: 22" Sceptre DVI 2ms

----------------------------------------------------

That's all I think that could possibly be relevant other than the fact that I haven't had this problem with older versions of Ubuntu. I am dualbooting with Windows 7, (not using WUBI installer) but no matter how many times I install or reinstall Windows 7 or whatever with different systems and hard drives I keep getting BSODs and crashes beyond belief. So that's kind of why I really want to just completely switch and use VirtualBox or Wine if I really need something for Windows. Anyway, any help is appreciated.

---

### Post by HolgerB on 2011-07-27
Have you tried to disable SLI just for testing purposes ?
Is VSync enabled ?
Which native games have you checked ?
Is your system running nicely ?
What about memchecks / prime in loop-run ?

You should also try out one of the live gaming Linux DVDs out there to verify if the problem is gone.

---

### Post by Legendary_Bibo on 2011-07-27
Install in Windows, problem solved.

---

### Post by HolgerB on 2011-07-27
> **Legendary_Bibo said:**
> Install in Windows, problem solved.
Dear Mister Bibo Sir,

did you read the first post ?
"... What I've gotten to work is Wine. When I use Wine with Windows games it works fine ..."

Sounds more to me that games under WINE run fine while native games have issues.

But agreed: Running Windows games under native OS is much more stressfree than using WINE, :P

---

### Post by Spirrwell on 2011-07-27
> **HolgerB said:**
> Have you tried to disable SLI just for testing purposes ?
Is VSync enabled ?
Which native games have you checked ?
Is your system running nicely ?
What about memchecks / prime in loop-run ?

You should also try out one of the live gaming Linux DVDs out there to verify if the problem is gone.
When I tested the games the first time I had SLI off, but I'll check again to be sure. 

As for VSync, I'll check and edit this post, as I'm in Windows at the moment.

The games, are source ports to older games from 1996 Duke3D and Quake, specifically I was using eduke32 and ezquake as the source ports, but I'll try it with a true Linux game just to be 100% sure even though the games have nothing in common other than the year they were produced.

The system itself runs perfect. Ubuntu is and has always been a great operating system

As for memchecks or whatever, I'm not sure what you mean. What should I use to do that with?

This isn't a very new system and I've had Linux on here before with no problem, Ubuntu 10.10, Linux Mint, Kubuntu, etc. Although I'll check anyway, with a Live CD as systems can deteriorate. 

One more thing I forgot to mention is that I'm using a 64 bit version, of Ubuntu, although I thought that'd be obvious since I have 8GB or RAM.

Also, yes you were correct, I was saying that the games work with WINE perfectly and they are terribly laggy\slow when run natively. As I said I want to give up on Windows because it crashes too often no matter what I do and no matter how many different systems I use it on.

EDIT:

Vsync is enabled, I double checked with SLI, still the same thing. I'm downloading a Live DVD now.

EDIT 2:

I tried Alien Arena, it worked fine, but it crashed when I tried to go fullscreen with my monitor's resolution 1680 x 1050, so I decided to try the other games, but the problem only got worse with the lagging\slowness. So I don't know... I haven't had this problem with these games before.

---

### Post by HolgerB on 2011-07-28
When I talked about memory checks I mentioned using memtest on your system to check out if there are any memory issues. Mersenne prime (Mprime) is also a good option to check System stability. Beside certain tools to test the graphic adapter they are the best tools to verify system stability. 

As for crashes under Windows I never experienced them. Since I administer a medium sized virtualized test environment I often install Windows (2k8, Vista, Win7) and never run into issues. Honestly I think Windows and its relation to bluescreens / crashes are really nonsens (unless you have some other hidden issue like buggy hardware, buggy drivers and so on). In other words: If your system is running as stable as you think I would expect that you are able to install any recent Windows version from an original installation medium (important !) really smoothly.

Also check closely the output of dmesg for any issues. 

I was going nuts on my system (hardware see in footer) to get my graphic adapter working unless I found out that a "simple" hardware error was causing problems. My mobo has issues in adressing more than 3GB. I removed one memory stick and everything is now running smooth as silk.  
:lolflag:

Edit: 
In order to test the stability of physical systems I usually boot up any Ubuntu flavor in livemode, grab mprime ([http://www.mersenne.org/freesoft/](http://www.mersenne.org/freesoft/)) and leave it running in mixed mode (using both CPU and RAM) at least over night. For stress testing graphic adapters I have had good success using furmark under Windows (don't know if it runs under WINE).

---

### Post by Spirrwell on 2011-07-28
Well... I spent the past few hours working on my system, it was failing memory checks, and I've got it down to it's either a bad RAM socket or a bad piece of RAM, so for now I'm running 4 GB which is good, because now I can run my RAM at the full 2000 MHz speed. So all that is now fixed, Windows seems to be working fine. The games are still laggy though, but I suppose it doesn't matter anymore. Thanks for the help. I always thought it was the processor.

---

### Post by Spirrwell on 2011-07-29
> **ken_ham said:**
> Perhaps your magic donkeys may be of assistance?

Don't waste your breath, I've dealt with a lot more idiotic than that. I can't even tell you how many times I've bashed people for not reading my entire posts because it's right there in plain site. I'm not intentionally calling anybody an idiot here, but without reading a post all the way through how do you know you didn't miss something important, like I don't know... a debug log. (Yes that's happened to me already, some guy suggested, "Be sure to also post your debug log." when it was there with code tags, how could you miss it?)

Anyway, it's just not worth it anymore.

---

### Post by HolgerB on 2011-07-29
> **Spirrwell said:**
> Well... I spent the past few hours working on my system, it was failing memory checks, and I've got it down to it's either a bad RAM socket or a bad piece of RAM, so for now I'm running 4 GB which is good, because now I can run my RAM at the full 2000 MHz speed. So all that is now fixed, Windows seems to be working fine. The games are still laggy though, but I suppose it doesn't matter anymore. Thanks for the help. I always thought it was the processor.
Well, sorry to hear about your hardware issue. I share your pain. Esp. for the time wasted already.

You could find out if the RAM has an issue by putting it into a RAM socket which is currently running. Esp. Dual channel configurations are often sensitive when using bleeding edge timings / FSB clocks.

By "I supose it doesn't matter anymore" I guess you mean that you will use Windows then again. Not the worst option IMO. Please mark the thread as "solved" in the first topic subject.

Glad I could somewhat help.

---

### Post by Spirrwell on 2011-07-29
> **HolgerB said:**
> Well, sorry to hear about your hardware issue. I share your pain. Esp. for the time wasted already.

You could find out if the RAM has an issue by putting it into a RAM socket which is currently running. Esp. Dual channel configurations are often sensitive when using bleeding edge timings / FSB clocks.

By "I supose it doesn't matter anymore" I guess you mean that you will use Windows then again. Not the worst option IMO. Please mark the thread as "solved" in the first topic subject.

Glad I could somewhat help.
Yeah I know. Thanks for the help, but it's not too bad of a disappointment, I've got a lot of DDR3 RAM I saved for when I build an i5, so I really couldn't care too much that I had this problem anyway.

Again, thanks, I'll mark this as solved.

---

