---
title: "Question regarding hardware support and Ubuntu versions."
date: 2009-01-21
forum: General Help
---

### Post by Roasted on 2009-01-21
So, I'm working with this HP trying to get 8.10 to run along with DRBL server, which supposedly works over top of Ubuntu just fine. I had a few weird issues with 8.10 and after posting on the forums for DRBL, it was recommended that I use 8.04 cause 2 or 3 HP desktops were having issues with 8.10.

But, this confused me.

8.04 uses kernel A, let's say.
8.10 comes out and is equipped with kernel B. So suddenly it's an assumed fact that 8.10 would support more hardware.

But, isn't kernel B just kernel A + more? Like why would 8.10 lack support yet 8.04 supports it? Is kernel A (8.04) a completely different animal? 

I just always assumed that when building a new kernel, you start with the old kernel and add to it, therefore you won't ever "lose" any hardware support. But that was just my naive assumption - I don't have any hard sources for that.

Secondly, 8.10 came out in Oct. As I said, it's running kernel B. Okay, fine. Would 8.04 ever be "automatically" updated to the latest kernel to benefit from the latest hardware support? Or will it forever remain the kernel it was packaged with unless compiled otherwise?

---

### Post by hyper_ch on 2009-01-21
not really, sometimes really old hardware gets removed from the kernel. Sometimes upgrading of drivers will break old hardware unintentionally...

---

### Post by Roasted on 2009-01-21
Put it this way.

Say kernel B supports hardware on this HP that I need. But 8.10 doesn't run right for whatever reason.

So I put in 8.04, which runs kernel A.

Is it possible I could get 8.04 with kernel B? Would I be able to update it with ease? Or would I have to be a linux guru to figure that side of it out?

---

### Post by Roasted on 2009-01-28
Put it this way. I had a problem with my new computer when I built it back in October. I had some issues getting Hardy to play nice with my motherboard.

Well, Intrepid fixed that issue. However, Intrepid used the new kernel.

Problem is, Intrepid must have a bug with video tearing, cause I get it SO much that it makes me have zero desire to watch anything besides youtube on the computer. I'll reboot to Vista if I want to watch something, like a movie.

My question about the kernels is... Intrepid used newest kernel which supports my new hardware... but the older version of Ubuntu worked better for video cause it had zero tearing... but I need newest kernel... video tearing... see where I'm going with this?

Does Hardy LTS use the latest Linux Kernel that Intrepid uses?

---

### Post by mb_webguy on 2009-01-28
What specific problems are you having with videos.  If Intrepid is otherwise working for you, it's probably better to try to fix the video problems than mess around with kernels.

---

### Post by Roasted on 2009-01-28
I have video tearing. It's that simple.

When I watch a movie from a DVD or from a file on my computer, I get video tearing. Totem, VLC, Movie Player, you name it... I have video tearing in it.

Compiz is turned off. In Hardy, if I turned off compiz it solved my problem 100%. In Intrepid, compiz on/off makes no difference.

I tried many suggestions, including adjusting my video output settings in VLC to x11 as well as others in the list.

Nothing makes a difference. At all.


Well, this might be good and bad... I downloaded 8.04.2 from Ubuntu's web site and booted up to the LiveCD. After a quick "uname -r" in the terminal to see what kernel I'm on, I discovered it was .24.... not .27 like Intrepid has. So that confirms my suspicion that even LTS's kernel doesn't seem to be picked up with the newest short term released distro.

On one hand, I had no issues booting to Hardy, so I assume my hardware will work fine on .24. On the downside, I forgot that the menu system and a lot of changes were made with the interface between Hardy and Intrepid. Gahhh... I dig Intrepid too much to go back. :( I'll stick with Vista for movie watching and pray that the darn bug gets fixed...

---

