---
title: "Mini 10v with XP virtualbox"
date: 2009-09-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alienclone on 2009-09-28
first off i dont have my 10v yet so no support needed yet, just some advice and hopefully other's first hand experience. 

[STORY]I will soon be getting a free Mini 10v from comcast for the package i ordered. It should have the usual 1.6 Atom and 1gb mem, not sure whether it will have SSD or HDD. I dont know which operating system it will come with but my plan is to install Ubuntu. I've heard many success stories of Ubuntu running flawlessly on the 10v which made my mouth water because i fell inlove with Ubuntu 5 months ago. I will be using my 10v for work also (mobile locksmith) and need to run a few locksmith programs on it...[/Story]

...BUT, the programs i need to run are, ofcourse, made to run in windows.  I figure my best solution would be virtual windows inside my Ubuntu.

and now for the questions.

anyone have experience with virtualbox on a 10v? will it slow down Ubuntu if i have the VB running all the time that the netbook is running? will that drain the battery quicker? can the 1.6 Atom and 1gb mem handle that? if it comes with an SSD will that affect anything?

i hope my long post didnt put you to sleep and any advice, experience, suggestions will be greatly apreachiated.

---

### Post by Greyed on 2009-09-28
Hmmm, I haven't put VBox on this machine yet.  I'll have to try that one of these days.

One word of caution, if you're going to put UNR 9.04 on a 10v be prepared for some quirks.  It runs and for the most part runs decently.  However it does have some annoyances which haven't been ironed out yet.  S.ome of them you can get PPA packages to fix (or just avoid using) but others are just what they are.  Still, all things told, better than being stuck on XP.  ;)

I might give VBox a whirl on this machine.  It's kind of in flux but if I do I'll let you know how it goes.

---

### Post by mikewhatever on 2009-09-29
I think it's a bad idea, sorry. If you want Ubuntu on it, you'd better dual boot, because you'll probably experience all the problems you mentioned.

I've been running UNR on the mini 10 for the past few weeks and haven't stumbled upon any of the quirks Greyed mentioned vaguely.

---

### Post by Greyed on 2009-09-29
To be fair my signature did have the specifics.  [Nixing UNR 9.04.]("http://greydmiyu.wordpress.com/2009/09/27/nixing-unr-9-04/")

Relevant points:

[LIST]
[*]Video is far slower under UNR 9.04 vs. Dell’s 8.04.
[*]Touchpad was too jerky.  While there are answers for this they are PPA only and not incorporated into mainline yet.
[*]Wireless networking would die after a few hours of usage and not return, even after manually bouncing the interface.
[/LIST]

---

### Post by murderslastcrow on 2009-09-29
I'm getting my Mini 10v in the mail tomorrow. I have basically the same question (just in case I wanna' play some GameGuard MMOs someday like Mabinogi or Maple Story or Gunz in VirtualBox). I think it would be a shame to dual-boot and put an unsafe system like Windows XP on my machine just for the sake of a game or two.

Just for some reference- I'm running a laptop with the same specs as the Mini 10v, just using a different type of processor than the atom (Pentium M).

On this computer, I can run these games fine in VirtualBox, and play a lot of games full speed through Wine. I'm just wondering if I should expect lowered performance due to the wattage of the Atom processor? I mean, if this computer's 1.6 Ghz with 1 GB of RAM as well, shouldn't the performance be nearly identical?

Also, this computer's video processor is probably not as good as the integrated GMA 950 in the Mini 10v. Either way, if you can't answer these questions, I'll be able to do extensive testing with it starting tomorrow. If it can do all this stuff, I don't see any reason why I can't replace it as my main PC.

---

### Post by murderslastcrow on 2009-09-30
Hey there. So, got my Mini 10v today! I have to say, I'm very happy with it. It runs all of my prior development applications. I put it under a lot of stress testing with AWN, VirtualBox, Compiz, Cheese, and some other things open at the same time, just to see how it handled it.

It handles it great! And it's good with hooking up to external displays (like my HDTV! Woot! Yay for VGA). So, it seems like there's not much to worry about with this computer. I'd still say a computer with the same specs and a normal processor might have a tiny, eensy weensy bit more performance, but as far as Ubuntu is concerned, it runs flawlessly on this machine. I'm very happy with my purchase.

However, I'm going to get some MMOs going in VirtualBox with Direct3D support to see how fast they run with the default RAM/VRAM attribution assigned in VirtualBox.

Stay tuned! :3

---

### Post by alienclone on 2009-10-01
> **murderslastcrow said:**
> Hey there. So, got my Mini 10v today! I have to say, I'm very happy with it. It runs all of my prior development applications. I put it under a lot of stress testing with AWN, VirtualBox, Compiz, Cheese, and some other things open at the same time, just to see how it handled it.

It handles it great! And it's good with hooking up to external displays (like my HDTV! Woot! Yay for VGA). So, it seems like there's not much to worry about with this computer. I'd still say a computer with the same specs and a normal processor might have a tiny, eensy weensy bit more performance, but as far as Ubuntu is concerned, it runs flawlessly on this machine. I'm very happy with my purchase.

However, I'm going to get some MMOs going in VirtualBox with Direct3D support to see how fast they run with the default RAM/VRAM attribution assigned in VirtualBox.

Stay tuned! :3

thankyou for sharing your experience, im exited to hear good things about its performance. just curious did you get the HDD or the SSD?

---

### Post by murderslastcrow on 2009-10-01
HDD. And, surprisingly, it doesn't get the computer very hot! And I suspect the SSD wouldn't heat up at all.

Of course, I am using ext4 since I'm gonna' try dist-upgrade when Karmic comes out (trying to keep from my fresh install fetish since I have a lot of friends who aren't very partition-friendly and I need to give them confidence that they can just upgrade).

It's wonderful. To put this into perspective, even when you're running this thing with Windows, you can run The Sims 2 full speed. So take that into account with extra speed and stability in Linux, and that's about what you can expect performance-wise.

I'm going to try as many 1 GB requirement games as I can over the next month just to see how it handles them. I wouldn't expect The Sims 3 to run with any higher than 5 FPS, which should also put it into perspective.

---

### Post by murderslastcrow on 2009-10-01
Just a few notes about the Dell Mini 10v that I think everyone should be aware of.

1. Unless it's the first time you've used Linux, the DELL version of Ubuntu is retarded. Mutated and a bit useless. Compiz in 8.04 seems to have blacklisted the graphics card in the mini10v, so none of that. Wine is greyed out in Add/Remove (I'm guessing for copyright reasons), but for a newcomer it makes things pretty simple to understand. I wasn't really bought by the desktop widget interface. Might as well upgrade to Jaunty/Karmic before you even open it.

2. The touchpad really DOES suck as much as the reviews say. Like, I thought it was an overexaggeration. It really does take some getting used to, and I don't plan to use it for any gaming/work. You need to get your fingers on the VERY VERY bottom to click without moving something.

3. Why does my pure and unfettered Ubuntu Mini have a Windows logo on the super key?? WAAAAAAAII!!?!?

Those are the only bad things about this computer. All but one can be fixed (the touchpad). Everything else is glorious, wonderful, and more than I expected. It really is worth the money, and you get to support Linux! What could be better?

Converting all of your mp3s to oggs through Audacity? Yes, yes that would make it better *guilty as charged by himself*. I love this thing too much, I swear. XD

---

### Post by donmor on 2009-10-01
I have a Dell Mini 10V and run dual boot with Win XP and Ubuntu 9.04 "Notebook Remix" and has been 100%  Booted from a 1 GB key and everything went perfect. I recommend this install to anyone that wants to dual boot using a smaller screen.
Tried wubi install and when windows updated, it destroyed the boot.  Had to install Ubuntu to get my win xp back or would have meant a restore.

---

### Post by Greyed on 2009-10-02
> **murderslastcrow said:**
> 1. Unless it's the first time you've used Linux, the DELL version of Ubuntu is retarded.

Uuhhh....  no.

> Mutated and a bit useless. Compiz in 8.04 seems to have blacklisted the graphics card in the mini10v, so none of that.And yet it works fine on my Dell 8.04 10v.

> Wine is greyed out in Add/Remove (I'm guessing for copyright reasons),It is?  *goes to check*  Odd, the only color difference here is the one denoting that it is **installed**.  

> 2. The touchpad really DOES suck as much as the reviews say.In 9.04 it is.  Dell's 8.04 it is usable.  Not the best but it works when netbooking away from a surface where one can employ a mouse (like browsing in bed).  That's coming from a person who loathes the whole concept of the touchpad.  :P

> 3. Why does my pure and unfettered Ubuntu Mini have a Windows logo on the super key?? WAAAAAAAII!!?!?Pft, why is the key there at all.  It was added by Microsoft as the "Windows" key.  It is what it is.  Frankly I wish I could find keyboards without it.  I had to rip it off my game machine's keyboard yesterday because it kept dumping me out of Aion to the desktop.  Worst idea for a key ever.  But it is what it is, the Windows key.  So it is appropriately labelled.  Big whoop.

---

### Post by murderslastcrow on 2009-10-02
Odd. I did use the DELL version for a good 2 hours before reinstalling, and the touchpad seemed to be the same as it is now. :\ Really troublesome, but I've gotten used to using it.

I guess maybe they changed something about it between when you and I got it? Not sure, but I'm hoping that these problems won't happen for everyone, and glad that you didn't face them.

I guess I really should give DELL some credit for trying to integrate their services and make it a complete package with an easier interface. I definitely think it could use some improvement in the future, though.

I apologize if I used strong or offensive language back there. XD I guess I'm a slave to my own pickiness.

---

