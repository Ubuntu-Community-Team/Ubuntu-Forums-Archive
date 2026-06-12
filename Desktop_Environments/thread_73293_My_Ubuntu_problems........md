---
title: "My Ubuntu problems......."
date: 2005-10-08
forum: Desktop Environments
---

### Post by floyd27 on 2005-10-08
well I'm having quite the time trying to solve these problems ubuntu is giving me....
It was interesting at first but it's fast becoming a headach. Im finding myself logging into windows to do things i shoud be able to do here...

1-No ATI overclocking...
2-Cant mount a image (iso,bin/cue)
3-No decent monitor (cpu,temp,fan speeds,volts etc.)

Im wondering what to do...? Continue with these headacks.. or just give in to the biggest headach of all (win#@$%) but at least it works....

---

### Post by madjo on 2005-10-08
1) As far as I know, ATI's drivers aren't up to standard for Linux. So yeah, it might indeed be impossible to overclock your ATI.

2) what command did you try to mount the ISOs? (might help some of the people here, I haven't tried to do it yet)

3) What kind of monitor do you need? If you are in Gnome, there are GDesklets that are capable of doing this. Check this site for more details:
[http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

---

### Post by Zwack on 2005-10-08
Never tried ATI overclocking... What benefit does it give you?

It may be that something else can help...

I've found for some things I have to compromise between X and Y.  I always choose the one I think I'll use rather than the one that might be cool...

Can't mount an image is an interesting one... is the image corrupt?  Perhaps that is the problem?  Is it that the filesystem is unknown?  Do you have the modules you need installed?

If you don't have a decent monitor then why bother overclocking your graphics card?

Or do you mean that you don't have a "decent" system monitor.


My experience is that there are a plethora of system monitors.  Generally speaking though, I don't care about my fan speeds, the temperature, how many volts are running through the processor...   I care about system resources...
do I have enough CPU?  Is the load too high?  Am I swapping?  Do I have disk space?  Do I have I/O contention?

Applications -> System Tools -> System Monitor gives a graphical interface to that...  But if you look in Synaptic you will find many (many) more.  GKrellm has a ton of addons...  lmsensors probably provides the information you are looking for...

I hope that this helps

Z.

---

### Post by floyd27 on 2005-10-08
..
As for the overclocking. it increases the core amd mem speeds. Same as overclocking a cpu say..
It is a great card but it can do more so why not do it.. my whole system is massivly overclocked.. (and it is a good one)

Iv tried everywhich way to mount a bin/cue file with cdemu (had alots of help too) and after a week i gave up. Decided to convert it to iso,, Lots of help and still no go...

Its not currupt b/c i burnt it and watched it in windows....(works everytime)

im looking for a cpu-z or everest style system monitor.. Something that gives you EVERYTHING you could ever want about your sys.(with overclocking this is very important)

these are things i cant live without. which is why im typing this in win#@$% now..

---

### Post by Zwack on 2005-10-08
sounds like you should be looking around in /proc and look at packages like 
mbmon, lmsensors, xmbmon, sensord and xsensors....

These are all used for monitoring hardware...

Yes, it's possible to push a system harder than it was intended... but if some components are marginal (within tolerance, but at the wrong end) then you could push too hard and cause problems...

Overclocking always seems to me like Ricers (if you don't mind a car analogy)... For the amount spent on making sure it all works pushed to the limits you could have bought a car that could do the same without the work.  Some people like the work... others prefer to have it done for them, and others prefer to start with a better machine...

Staying on cars, we have a 1964 1/2 V-8 Mustang, that cost less than a Ricer to buy, and doesn't need expensive mods to become a reasonable car.  

I hope the sensor info helps.  I rarely need to mount images so I can't help... but if you burnt it to disk, can you watch it in Linux?  If you can't then it sounds like it's not a problem mounting it, but perhaps a missing codec...

BTW, if it's got less than four CPUs, Four GB of Memory, and redundant SCSI drives, it's not a good system.... :-P  I wouldn't mind upgrading to an IBM p570 myself...

Z.

---

### Post by floyd27 on 2005-10-09
wow..
that was quit the opinion there....
to bad i didnt ask for it..
Just because you dont wish to extend your knowledge of computers/cars doesnt mean the rest of us dont want to.
BTW I wouldnt brag about owning a ford...(I happen to know cars aswell)

---

### Post by flyingbrass on 2005-10-09
I overclock too.  Even if a person doesn't, it's nice to keep an eye on temps, voltages and fan speeds.  You'll need to install lm-sensors.  Then you can use your choice of interfaces (gkrellm, one of the gdesklets, etc.) to display the numbers.  Check out the [lm-sensors howto](http://www.ubuntuforums.org/showthread.php?t=2780).

I've never played with ISOs in Linux.  Pretty sure you need to mount as loopback:

[http://www.ubuntuforums.org/showthread.php?t=35460](http://www.ubuntuforums.org/showthread.php?t=35460)
[http://www.ubuntuforums.org/showthread.php?t=21332](http://www.ubuntuforums.org/showthread.php?t=21332)

---

### Post by Zwack on 2005-10-09
[QUOTE=floyd27]wow..
that was quite the opinion there....
too bad i didnt ask for it..
Just because you dont wish to extend your knowledge of computers/cars doesnt mean the rest of us dont want to.
BTW I wouldnt brag about owning a Ford...(I happen to know cars aswell)[/QUOTE]

Sorry if I upset you... that wasn't the intention... If you read the top it specifically mentions some things that you might want to look at to help you in your quest for monitoring.  The rest states that "some people like the work" while pointing out that the economic benefit is not always there.

To try to summarise the rest of it (in a way that I hope doesn't offend you)...

Overclocking involves pushing the components beyond their designed tolerances.  If you overclock it is possible to damage your hardware.  In some cases overclocking can achieve performance increases for little to no cost.  In some cases it can achieve minor increases for more than the cost of purchasing the components rated for the higher level.  

Given that you are doing things that were not intended with the hardware, you can't expect it to be supported.

Thanks for ripping on owning a Ford, my point was that buying a Honda, sticking stickers and lights all over it, and an exhaust tip on it doesn't make it any better a car.  A V-8 engine is usually going to be a higher performance engine without the "effort" and is not usually any higher cost.  Yes, Ford had build issues, even back in 1964, but any car that has survived over 40 years already must have been one of the better built ones...  

Still, it looks like mbmod/xmbmod might give you what you want, if not, lmsensors/sensord/xsensors/gkrelm will give you some of the information.

Of your "three issues" it looks like searching through the available packages would have resolved one.  The answer to one is "it can't be done" and the third is an interesting issue...  

So, have you tried that image that you wrote to disk under Linux yet?  Did it work?  Did it fail?  

Oh, and by the way, I don't consider that most of what ricers/overclockers do would extend my knowledge about either Cars or Computers.  In fact in most cases I don't think that it extends their knowledge either.  

Z.

---

### Post by 11hjpphty76lkjj on 2005-10-09
The command sequence for mounting an ISO image is something like:

```
mount -t iso9660 -o ro,loop the_cd_image.iso /mount/point
```

Although I haven't given it a try *yet*.  Will sometime today.  Have several things I'm trying to accomplish and that's one of them.

Aaron

---

### Post by floyd27 on 2005-10-09
I am able to get the image mounted but no player will open it.. Iv tried every file every player.. nothing works..This is my problem,sorry if i wasnt clear on that
But the image is wounted...?

btw . today overclocking is a common practice..In fact the cards with the most support in linux nvidia, now sells cards Overclocked out of the box....It has became one of their selling features.. 
another ex. The ati 9500 and 9700 both have the exact same core.. One is just set lower from the factory.. So in a sence your no "overclocking" you just getting to where it was origionally designed to be in the first place.....Its cheaper to make the same core and lower the speed than to make 2 different cores....

---

### Post by Zwack on 2005-10-09
Well, to be frank, my PCs all work "well enough" and the machines I use for most of my work (which is where I do most of my computing) are much larger, more expensive and are not intended to be "overclocked"...

Sometimes chip sets are sold in two flavours due to differences in which test passed.  If it pases test A but not B then it is sold as a cheaper card to run at a lower speed...  The original 486SX was a 486DX sold with the math co processor "disabled"...

I would check the ubuntu guide for additional codecs as I think that that may be your problem.  I haven't found anything I can't play on my machine right now...

I hope that this helps.

Z.

---

### Post by floyd27 on 2005-10-09
Well im not gona bother wasting time trying to mount it anymore..
i have all the codecs// I can watch anything but its the mounting thats horrible..
Windows comes to the rescue again... Its to bad too, as i hate windows, but i dont have to look at it when the movie is playing..

---

### Post by dusanyu on 2005-10-10
you may want to look at gkrellm
[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)
you can get it from apt

---

