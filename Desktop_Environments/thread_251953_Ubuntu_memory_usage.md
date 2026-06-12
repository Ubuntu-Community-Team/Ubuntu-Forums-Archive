---
title: "Ubuntu memory usage"
date: 2006-09-06
forum: Desktop Environments
---

### Post by moose6589 on 2006-09-06
I'd like to start out by saying that I love Ubuntu, and it just keeps getting better. With things like XGL, Windows looks more and more antiquated/annoying everyday. 

However, I am wondering about the memory usage of Ubuntu (on my system at least). Granted, I am running XGL/Compiz full-time, along with Firefox, Thunderbird, and sometimes Azureus, but still, I think the memory usage has gotten a little out of hand. Yesterday, after turning my computer on and using it for only one afternoon, I typed in 'top,' which claimed that I was using up 510 MB of memory and 490 MB of swap. I only have 512 MB of RAM. The system was still responsive (because of my 1 GB swap), but 1 GB memory usage is a bit scary, even for a modern operating system. If this were Vista, then I wouldn't be complaining, but this is Ubuntu! 

I know asking OSS to be both amazing in functionality and super-efficient is a tall order, but then again, I have much faith in all the wonderful developers. Does anyone have any thoughts on this matter? I hope memory usage doesn't become a taboo topic here in the future (like in the Firefox forums) because it is definitely something important to consider for everyone.

---

### Post by _mrv on 2006-09-06
Seems to be java (Azureus?) and XGL eating large portion of your memory.

Can you sort that process list by memory usage? (press M when running 'top').

 _mrv

---

### Post by moose6589 on 2006-09-06
Actually, this shot was taken yesterday, so I don't have the same system running right now. I sorted it by VM usage, which somewhat correlates to resident memory usage. I also noticed that XGL and Java (Azureus) take up massive amounts of memory, although I doubt anything can be done about this.

---

### Post by tribaal on 2006-09-06
Also don't forget linux will always try to fill up your RAM to a maximum with buffers and disk cache.

To have more accurate readings of your available memory, type "free -m" in a terminal (figures are in MB).

For further info, check out the link in my sig.

- trib'

---

### Post by orb9220 on 2006-09-06
Well stop complaining. You have only 512mb so add more ram.
You want to blame things then blame
1)Java it is a resource hog on any system especially when using another resource hog Azureus.

2)xgl is basically eye candy. You want candy then you have to pay for it. That again is not linux's fault.

3) Firefox uses java and runs a little better but still is a bit slow.

4)Between xgl and java that alone is eating up 35% of your ram. Get more ram. But don't expect a decent car to be made to look like a ferrai to perform like one. And don't expect it to be able to behave like a pickup  truck hauling all that extra stuff without paying a mechanic to modify  your car to haul larger loads and the engine to match.

---

