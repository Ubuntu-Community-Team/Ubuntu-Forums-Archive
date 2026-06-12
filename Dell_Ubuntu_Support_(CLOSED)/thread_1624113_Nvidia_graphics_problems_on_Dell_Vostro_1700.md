---
title: "Nvidia graphics problems on Dell Vostro 1700"
date: 2010-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Godspell on 2010-11-17
Hi all,

I'm using Ubuntu 10.10 32bit on Dell Vostro 1700 with Nvidia GeForce 8600m GT.

There seem to be a problem with graphics; the compiz-config effects aren't very smooth.

Whenever I minimise(using magic lamp) or do the cube, it looks like as if something is slowing them down. Also, a bit choppy with lines when you turn the cube.

I don't have the most updated laptop but I know for a fact that the basic graphics like these should run smoothly.

I think this is the Nvidia GPU problem. I've already unticked the "Powermiser" from "Nvidia Server X Settings" but it doesn't solve anything.

On my other laptop(an acer which is of much lower specs), every thing works just fine.
But it's with ATI which makes me doubt Nvidia even more.

Seriously, Nvidia cards are sometimes just useless. Especially with crap like Powermiser.

I want my machine to output the required performance when I need. 
I mean, don't we all? After all, this is why we're using Ubuntu, right?

So, please tell me how to solve this problem.
Any suggestions are more than welcome :)

Regards,
GS

---

### Post by Godspell on 2010-11-18
LOL

What, nobody has this problem?

I mean am I the only one who thinks Nvidia powermiser or card itself is problematic with performance???

---

### Post by kamohammed on 2010-11-18
AH! I had a similar problem. Mine was when I minimize it goes away ok, but when I restore, it takes a few seconds before the window comes up. At some times it would move like frame...frame...frame... 

Although my problem stemmed from my faulty Hdd, You can try these and hope it works...

Completely remove Compiz
reboot
Re-install back compiz...

When you uninstall compiz see if the computer still moves choppy...
Try re-installing the Graphics drivers...

Some graphics drivers work, but not fully functional. Like my graphics drivers work on my lappy, but if I look to play any games it runs like utter crap... so read up on graphics drivers for your lappy on ubuntu and see if you can get a driver that works for you (Just a suggestion)

edit. PS: I have a Dell Studio 1535 with ATi Radeon HD 3450 256MB...

---

### Post by Godspell on 2010-11-19
Hey, I uninstalled both compiz and Nvidia drivers (along with several reboots, of course).

Then, re-installed both of them.

Results weren't that great, actually.
So far, minimising and restoring windows don't lag BUT the cube still does a bit at the beginning.

I don't know what's wrong with it but Nvidia drivers suck ****, man.
I'm using ATI Radeon HD 4200 (& AMD) on my other laptop and it works flawlessly!

Anyways, I found latest available Nvidia drivers from their website and already downloaded them BUT am hesitating to use'em because whenever the major updates are applied, privately installed graphic drivers get dropped.

I've had this problem before and even made a thread here [http://ubuntuforums.org/showthread.php?t=1520157](http://ubuntuforums.org/showthread.php?t=1520157) Nobody replied though.

So, if you've got any cool awesome ideas, let me know, bruv :D

Or else,I'll just read the detailed notes of Nvidia drivers installation on Linux when I have time.

Cheers for replying, btw.

Regards,
GS

---

### Post by w4r_l0ck on 2011-01-10
Hey, I'm running compiz on my dell XPS M1530 (8600M GT 256mb ddr3), Ubuntu Maverick 10.10 and I'm getting the same problem. 3D cube rotation and simple flipping cube face is choppy as hell. 

I've tried turning off powermizer (setting preferred mode to "prefer max performance" and it still lags. My other rig with a simple Intel graphics accelerator works beautifully though, what a disgrace to such a powerful GPU that could run Modern Warefare 2 at 1680*1050 flawlessly. 

Seriously, ain't there any other linux users who runs on 8600M GT and faces the same problem?

---

### Post by w4r_l0ck on 2011-01-10
Hey, I'm running compiz on my dell XPS M1530 (8600M GT 256mb ddr3), Ubuntu Maverick 10.10 and I'm getting the same problem. 3D cube rotation and simple flipping cube face is choppy as hell. 

I've tried turning off powermizer (setting preferred mode to "prefer max performance" and it still lags. My other rig with a simple Intel graphics accelerator works beautifully though, what a disgrace to such a powerful GPU that could run Modern Warefare 2 at 1680*1050 flawlessly. 

Seriously, ain't there any other linux users who runs on 8600M GT and faces the same problem?

---

### Post by Godspell on 2011-01-10
> **w4r_l0ck said:**
> 
Seriously, ain't there any other linux users who runs on 8600M GT and faces the same problem?

You're in for the treat mate (at least I think lol) because I found some good info on ever-annoying Nvidia issues.

To being off with, I was quite upset that nobody replied me.
Like you said, I really don't think we're the only ones with this issue, yet there was no reply. However, I don't blame Ubuntu at all but Nvidia.
Regardless of the fact if they support opensource drivers or not, I HATE powermiser.
It's even more annoying that this issue was exactly the same on Windows since last 3 years or so. Thought I'd escaped that and all cause I rarely use Windows these days but hell....was I wrong heh

Anyway, I found couple of guides (which seem fairly updated) and here they are.

HOWTO: Latest NVIDIA Driver
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

HOWTO: Improve NVIDIA laptop graphic performance
[http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)

For me, this one is purely for educational purpose but nevertheless, it is always useful to understand how Graphic drivers work on Ubuntu, and how to use opensource drivers.
[http://ubuntuforums.org/showthread.php?t=1046504](http://ubuntuforums.org/showthread.php?t=1046504)

I haven't tried following any of these guides myself but they look decent.
Personally, I'd like to suggest you to read them carefully before trying out (regardless of which one you're following).
If you're not sure of something, make sure you post it on their threads.

Hope this is all useful.

Cheers and regards,
GS

P.S Let me know how you get on if you have a chance :)

---

### Post by w4r_l0ck on 2011-01-10
haha well, Good news, I've found a solution!

My full specs are : Ubuntu 10.10 Maverick
GPU : 8600M GT (Nvidia driver version : 260.19.06) - I'm using proprietary drivers directly available from the repository)

And the simple fix that worked for me: - Enabling "Loose Bindings" and "Indirect Rendering"
If you have already installed compiz-fusion I'm pretty sure that "compiz fusion icon" is automatically installed together with the package.

Just load the app from > Applications > System Tools > Compiz Fusion Icon
and you should see the icon on your top panel - somewhere near the wireless icon for me.

Right click on it > Compiz Options >  
enable loose bindings and/or Indirect Rendering and see whether if it works for you.

GodSpeed ;)

---

### Post by Godspell on 2011-01-10
> **w4r_l0ck said:**
> haha well, Good news, I've found a solution!

My full specs are : Ubuntu 10.10 Maverick
GPU : 8600M GT (Nvidia driver version : 260.19.06) - I'm using proprietary drivers directly available from the repository)

And the simple fix that worked for me: - Enabling "Loose Bindings" and "Indirect Rendering"
If you have already installed compiz-fusion I'm pretty sure that "compiz fusion icon" is automatically installed together with the package.

Just load the app from > Applications > System Tools > Compiz Fusion Icon
and you should see the icon on your top panel - somewhere near the wireless icon for me.

Right click on it > Compiz Options >  
enable loose bindings and/or Indirect Rendering and see whether if it works for you.

GodSpeed ;)

You also installed the Nvidia drivers via **System -> Administration > Hardware Drivers** right? That's what I did in the first place. Can't remember the version though.

Hmm...I really don't understand what you mean, bruv.
The way I load compiz is **System -> Preferences -> CompizComfig Settings Manager** and I've never seen Compiz icon on any of my panel.
So, can you be specific please?

Thanks for the speedy reply though :)

GS

---

### Post by kimberlite on 2011-01-10
> **Godspell said:**
> 

Hmm...I really don't understand what you mean, bruv.
The way I load compiz is **System -> Preferences -> CompizComfig Settings Manager** and I've never seen Compiz icon on any of my panel.
So, can you be specific please?

Hi,

Compiz Fusion Icon is an application that you can install either via Synaptic or by typing: ```
sudo apt-get install fusion-icon
``` After that you can start it from application menu.
Good luck!

---

### Post by Godspell on 2011-01-10
> **kimberlite said:**
> Hi,

Compiz Fusion Icon is an application that you can install either via Synaptic or by typing: ```
sudo apt-get install fusion-icon
``` After that you can start it from application menu.
Good luck!

I've just installed it :) Thanks for explaining me about it.

w4r_l0ck, it worked!

Thank you very much for sharing such a valuable piece of information :D

Regards,
GS

---

### Post by w4r_l0ck on 2011-01-11
Cheers! Problemo solved.

---

