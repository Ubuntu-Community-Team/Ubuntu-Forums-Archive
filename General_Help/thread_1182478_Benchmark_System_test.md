---
title: "Benchmark? System test?"
date: 2009-06-09
forum: General Help
---

### Post by bilijoe on 2009-06-09
I'm looking for an objective way to evaluate the overall performance of my installation. One good solution would be a test suite that performed meaningful tests on all critical systems, and then displayed the results in a way that would tend to make obvious, any area where the physical devices involved (CPU, Memory cards, Hard disks, Optical drives, etc.) were not performing correctly, or at the speed they should. I'd also like it to be easy to spot bottlenecks, such as memory slow enough that processes have to wait for it. I know there are programs and utilities available that give relatively raw readouts of some of the critical systems, but only one or a few, and usually completely without any way to put the [usually raw mathematical] output in context. The few benchmark type programs I have seen give me, anyway, results that don't seem to match reality, that is, the reality of using the computer, and experiencing things that take much longer than a computer that benchmarked where mine does, should take--they should happen in an instant.

I have been using Ubuntu-Linux exclusively, for about three years now (and I'm a big fan). I have, what I consider to be a rather fast machine (for what I do--I'm sure it wouldn't suit a gamer). I have a DELL Optiplex 270, with a 2.8GHz, Intel, Hyperthreading Pentium IV, 2.0Gb Memory that I don't remember the details on, but I do remember when I bought it, I didn't buy the cheapest available, I bought [at least close to] the fastest memory I could find (this system only supports DDR memory though). I've got an Nvidia GeForce 550 - 256 video card, my primary HDD and optical drive are both SATA drives (second and third HDDs and second optical drive are EIDE). LAN is a hardwire connection, Monitor is an HP w2408. Isn't this a relative fast system? Or am I just too far out of it to know when I've got antiquated equipment? 

The reason this is important is that I'm getting all too Window$-like performance from this system (Ubuntu version 9.04), and I don't know why. Do I have a failing piece of hardware? Is my memory too slow? Do I just have too much eye-candy turned on, or too many FireFox add-ons installed? I do have "Visual Effects" turned on, at "Normal", but with a seperate Video card I thought that would be safe.

I did see an article (or it may have been a post in one of these forums) that FireFox's state files can become corrupted and cause all kinds of various, non-specific, problematic behavior, so I hammered mine and let the system rebuild them (then I had to go put back all that FireFox eye-candy). That actually did make a lot of difference (and reminded me all too much of the Window$ Registry), but only moving my perception of the system's performance from "Rediculous and totally unacceptable" to "Shouldn't a 2.8Ghz machine be faster than this? Should I ever have to wait for the computer?"

I use FireFox more than anything else, but I also use the Movie Viewer, the Open Office Word Processor and Spreadsheet, and some webpage and Blog authoring stuff, Gimp, and some Image Capture software quite a lot too. Two examples of particularly frustrating behavior I have to put up with are: 1) When I load a page that's more than one screen long, response to the scroll wheel is, more often than not, very, very sluggish--to the point where the host program (usually either FireFox, or Open Office) freezes up (with Compiz turning the window to B&W, to indicate an "unresponsive program") for as much as 2 or 3 seconds--then the page leaps a screen or two. After this initial lag, the response to the scroll wheel is better, but, at best, I'd never call it "responsive"; 2) When cursoring through a line of text, the cursor either freezes, or disappears--when you let the key up, the cursor appears right where you'd have expected it to be, if you could see it, but, not being able to see its movement, well, it's hit and miss--quite frustrating.

So, what I'm really asking is, if somebody out there can give me an idea of how my system should be performing, and whether what I'm experiencing is normal or not. Everybody talks about how fast Linux is, and I remember, right after I started using it, being impressed with how fast it was. Now, I feel way too much like I'm running at "Window$ speed". Any suggestions, recommendations, or criticism will be welcome.

---

### Post by Wiebelhaus on 2009-06-09
Watching thread.

Something is a miss , we'll need more information as what programs are running if there's anything consuming to much resources unnecessarily , Like playonlinux constantly keeping the wine engine running or if your having a hardware failure such as a failing disk , You need to download [UBCD]("http://www.ultimatebootcd.com/") and run HDD diagnostics and memory diagnostics as well as mainboard diags , we will get to the bottom of this , start with those hardware diagnostics first and then if they all pass we will trouble shoot software.

---

