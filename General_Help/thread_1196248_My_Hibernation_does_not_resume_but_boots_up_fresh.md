---
title: "My Hibernation does not resume but boots up fresh"
date: 2009-06-24
forum: General Help
---

### Post by Lockheed on 2009-06-24
I can put my computer into hibernation mode and it writes down its data for around a minute. But then when I try to resume it just boots up clean session of Ubuntu with none of the data I left open during hibernation.

I rely heavily on hibernation so that is a huge turn off.

I have 3.8GB RAM and here is my cat /proc/swaps
```
Filename				Type		Size	Used	Priority
/dev/sda7                               partition	4096532	0	-1

```

---

### Post by microsome on 2009-06-30
I have the same problem. I my case I had to create a new swap file since I gave my machine more ram.

---

### Post by Lockheed on 2009-06-30
I am trying to compile my kernel with TuxOnIce but so far it's all errors. I think it's because I'm using the newest kernel and the patch for this version is still in beta.

---

### Post by renkinjutsu on 2009-06-30
compile the latest stable 2.6.30
that's what i'm using, and hibernation works like a charm

i took an extra step in configuring it, that is besides letting the old kernel config taking care of everything, I went under the hibernation option and was able to choose a partition for the kernel read the saved hibernation data from.. i set it to /dev/sda7 which is my swap.. i don't know if it's due to the newer kernel, or the addition of that option, but my hibernation works now.

---

### Post by Lockheed on 2009-07-01
Yeah, that's what I did, too. No luck.

Which TusOnIce version did you use?

---

### Post by renkinjutsu on 2009-07-01
tuxonice? .. i don't think i'm using that.
is that supposed to be enabled in the kernel? i don't think i've compiled such a thing, and synaptic doesn't say tuxonice is installed either.

---

