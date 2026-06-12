---
title: "Nvidia SLI having trouble turning on - Using Unigine Heaven"
date: 2014-04-23
forum: Gaming &amp; Leisure
---

### Post by nebrethar on 2014-04-23
Hey there, I'm a newish ubuntu user. First post on the forums.

Had a quick question about SLI with a dual 760 system.
I am running 14.04 and figured the best method to turn on SLI would be...

```

sudo nvidia-xconfig --sli=on
```

It seems to do some work, and rewrite the file with the modified parameters.
Afterward, I installed Unigine Heaven 4.0 and ran a benchmark to make sure my SLI was runnign and configured correctly.

On extreme preset, I normally run 35-40 FPS on an SLI-enabled system. I was running around 19.
Looked up in the top right corner and only saw one GPU as well. 
I'd assume i'm doing something wrong, because i normally have two showing up with the SLI mentioned in the OSD.

I already have the newest proprietary Nvidia drivers, and seem to be running great for one card! I'm loving Ubuntu so far.

If anyone has any input at all, please let me know!

Thanks and have a good one!

-Neb

---

### Post by divxclub on 2015-04-05
> **nebrethar said:**
> Hey there, I'm a newish ubuntu user. First post on the forums.

Had a quick question about SLI with a dual 760 system.
I am running 14.04 and figured the best method to turn on SLI would be...

```

sudo nvidia-xconfig --sli=on
```

It seems to do some work, and rewrite the file with the modified parameters.
Afterward, I installed Unigine Heaven 4.0 and ran a benchmark to make sure my SLI was runnign and configured correctly.

On extreme preset, I normally run 35-40 FPS on an SLI-enabled system. I was running around 19.
Looked up in the top right corner and only saw one GPU as well. 
I'd assume i'm doing something wrong, because i normally have two showing up with the SLI mentioned in the OSD.

I already have the newest proprietary Nvidia drivers, and seem to be running great for one card! I'm loving Ubuntu so far.

If anyone has any input at all, please let me know!

Thanks and have a good one!

-Neb


Identical question. In nvidia-settings I do 2 both GPUS yet in Heaven bench I only see one in top right corner, also only one temperature are going up so I know only one is working. Can anyone tell me what to do to get heaven to seee both GPUs ? And in general let's say in Steam how do I enable system wide SLI usage ?

---

### Post by Ranko Kohime on 2015-04-06
Unfortunately, both Crossfire and SLI aren't really a thing in Linux, despite being able to enable them.  SLI specifically is only known to work in IdTech4 games, and in others, produces no effect or a halving of framerates.

[Linux SLI Issues - GeForce Forums]("https://forums.geforce.com/default/topic/767116/sli/linux-sli-issues/")

---

