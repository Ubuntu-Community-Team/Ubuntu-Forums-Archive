---
title: "UNR 9.10 + Compiz = O.K ?"
date: 2009-11-01
forum: Desktop Environments
---

### Post by Oranges10e on 2009-11-01
Hello again,

is the Netbook Remix 9.10 compatible to Compiz? I mean, is it meant to be used with it or would it somehow make problems? I understand, that the UNR is on top of the normal GNOME interface, so it should be no problem, right?

BTW, why was the "desktop" switcher removed?

Third and final question: is it O.K to run the Netbook Remix on "normal" computers or for example a touch-screen computer or should one install the "normal" Ubuntu and then just get (via Synaptic) the UNR interface? I am a big fan of the interface ;)

Oranges

---

### Post by Oranges10e on 2009-11-01
Hello again,

is the Netbook Remix 9.10 compatible to Compiz? I mean, is it meant to be used with it or would it somehow make problems? I understand, that the UNR is on top of the normal GNOME interface, so it should be no problem, right?

BTW, why was the "desktop" switcher removed?

Third and final question: is it O.K to run the Netbook Remix on "normal" computers or for example a touch-screen computer or should one install the "normal" Ubuntu and then just get (via Synaptic) the UNR interface? I am a big fan of the interface :wink:

PS: I apoligize, if this is posted 2x. I couldn't see my other thread, so I made a new one.

Oranges

---

### Post by Glucklich on 2009-11-01
From what was told to me yesterday, UNR is regular Ubuntu with a visual interface makeover, so... it should be compatible with Compiz, as long as you have the hardware to back it up (which most Netbooks, if not all, don't). And it also should run on normal computers since they haven't optimized it for Netbooks yet, due to some bugs on the LPIA, as it appears cataloged as being i386, so... no problem there. But, you can run a LiveCD and test all these things for yourself.

---

### Post by overdrank on 2009-11-01
Threads merged :)

---

### Post by Oranges10e on 2009-11-01
@Glucklich: Hi, thank you for explaining.

I am already using it on a Laptop with a 15" screen and love it. It has been with minimal problems so far, the only thing that is a bit disturbing, is, that the netbook-launcher sometimes takes 90-100% cpu and needs to be restarted in order to get it back to normal. Besides that, it works great. I am not on the machine right now, but I will post my results in 1-2h and tell you how  and if it works with compiz enabled. I tried this a few months ago with UNR 9.04 and the interface got buggy. I assume the same thing though, if it's on "top" of Gnome, it shouldn't be a prob. The hardware to back it up is there :) 

PS: About the Hardware in netbooks: does UNR, or Ubuntu in general, support the new ION netbooks? Does ION hardware work at all?

@overdrank: Thank you :KS

Oranges

---

### Post by Glucklich on 2009-11-01
> **Oranges10e said:**
> 
I am already using it on a Laptop with a 15" screen and love it. It has been with minimal problems so far, the only thing that is a bit disturbing, is, that the netbook-launcher sometimes takes 90-100% cpu and needs to be restarted in order to get it back to normal.

That's no good.
I did some digging and found this: 

[http://www.linuxforums.org/forum/linux-desktop-x-windows/147750-netbook-launcher-using-100-cpu.html]("http://www.linuxforums.org/forum/linux-desktop-x-windows/147750-netbook-launcher-using-100-cpu.html")

Here's a quick explanation of what the command in the end does:

[http://ubuntuforums.org/showthread.php?t=759309]("http://ubuntuforums.org/showthread.php?t=759309")

Basically, it will reset your xserver.xorg. Now, it's your choice.

> **Oranges10e said:**
>  About the Hardware in netbooks: does UNR, or Ubuntu in general, support the new ION netbooks? Does ION hardware work at all?

nVidia has been taking Linux into consideration, so... if it is not supported yet, I believe it will be soon. It's about time... decent graphics on netbooks and nettops!

---

### Post by Oranges10e on 2009-11-01
Hi, thank you. I will try this right away and see how it goes, this isn't dang. or anything, right? It won't impact system stability etc. right?

Yeah, I hear ya, I really, really hope they give us ION support asap. I was planning on buying two ION netbooks and installing Ubuntu on them. Any way to make a wish? :P :KS

Oranges

---

### Post by Glucklich on 2009-11-01
> **Oranges10e said:**
> I will try this right away and see how it goes, this isn't dang. or anything, right? It won't impact system stability etc. right?

Since so many people replied on that thread and all of them said the same thing, I think it can't hurt. The worst case scenario might be reinstalling UNR... but this is the an absolutely pessimistic exaggeration, since A LOT would have to go wrong for that to happen ;)

In my opinion, that's one of those problems that shouldn't be underestimated and needs a solution. Let me know how that works.

---

### Post by Oranges10e on 2009-11-01
Hi, I just typed in that command. It just "ate" it up and didn't give me any sort of information if and what it actually did. Nothing happend yet, I'll have to wait and see if cpu usage goes up again or not. 

Oranges

---

### Post by Glucklich on 2009-11-01
> **Oranges10e said:**
> Hi, I just typed in that command. It just "ate" it up and didn't give me any sort of information if and what it actually did. Nothing happend yet, I'll have to wait and see if cpu usage goes up again or not. 

OK. Just out of curiosity, what was the frequency of that event? Was it task related?

If you remember these things, use them to see if this was successful or not. I'll be waiting for your feedback.

---

### Post by Oranges10e on 2009-11-01
Hm, I would say it happend every few minutes at random. Mostly after starting my browser (Firefox). The scrolling became slow and other things launched or reacted with a delay. The interface itself remained O.K and was doing fine. I asked a friend to upgrade to Jaunty on her netbook. She doesn't seem to have this problem. Maybe it's because I am using a Laptop? Would be strange though, since it's "just" on top of Gnome (I love it :P). 

Right now it seems to be doing fine. Maybe that command did do something after all? I'll try out a few things and see how far I can get and report back to you asap.

BTW, I installed the new 190 Nvidia drivers a few days ago, because I was getting this annoying screen "flickering" every few min. after I hooked up my fullhd LCD and used it as my primary screen (the drivers didn't help). Anyway, I noticed there wasn't a xorg file to save my nvidia-settings, have they taken it out on purpose or is something wrong?

Thanks for your support Glucklich.  :KS

---

### Post by Glucklich on 2009-11-02
LOL. You entered it, it had to do something ;)

No problem, glad I could help.

---

### Post by Oranges10e on 2009-11-02
Ok, after some testing, I can say: it works :) I ran a few tests and it seems to be doing good, even with a bunch of tasks open or while playing a game.

Awesome.

PS: About the ION question: [http://www.nvidia.de/Download/index.aspx?lang=de](http://www.nvidia.de/Download/index.aspx?lang=de)  There are those ION drivers, at least for the Desktop. So, maybe you're right, maybe Nvidia will support this faster then I thought.

Oranges

---

### Post by Glucklich on 2009-11-02
> **Oranges10e said:**
> Ok, after some testing, I can say: it works :) I ran a few tests and it seems to be doing good, even with a bunch of tasks open or while playing a game.

Ah! The final confirmation.
Now, my only doubt is... is this only valid for laptops or for some netbooks as well? Since I saw one person's post with a netbook that had the symptoms of 100% used CPU.

Anyway, glad to know your problem is fixed ;)

---

### Post by Oranges10e on 2009-11-02
Okay, it just started again >,> It's strange though, it happend right after I searched for some updates. It was working fine before that the whole night. I had to force quite the netbook-launcher. It had, together with compiz and the gnome-system-monitor, a waiting channel of "0" listed. I really wonder what's causing this.

Oranges

---

### Post by Glucklich on 2009-11-02
> **Oranges10e said:**
> Okay, it just started again >,> It's strange though, it happend right after I searched for some updates. It was working fine before that the whole night. I had to force quite the netbook-launcher. It had, together with compiz and the gnome-system-monitor, a waiting channel of "0" listed. I really wonder what's causing this.

Making the assumption that you restarted after entering the command... and that you entered "sudo" before the command...
While we're waiting for someone else to enter the discussion, can you test it without Compiz for a while and do whatever you were doing when that happened?

---

### Post by Oranges10e on 2009-11-03
Hi, sorry for the late response, had work to do :)

Anyway, yes, I typed in sudo and I did restart after typing it all in. I tested it without Compiz, the same result. I didn't even have Compiz activated when I first started getting this problem. Maybe I should file a bug-report? I could go back to Jaunty, but I like the new interface on UNR Karmic and most of it's new features. I'll give it 2-3 more days, if we don't find a solution, then I will just do a downgrade. Jaunty looks nice too :)

Oranges

---

