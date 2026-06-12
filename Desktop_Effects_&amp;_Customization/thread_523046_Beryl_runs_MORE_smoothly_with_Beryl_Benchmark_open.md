---
title: "Beryl runs MORE smoothly with Beryl Benchmark open?!"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by CrimsonMemory on 2007-08-11
I'm using Feisty and Beryl.  I've always been quite content with the way everything is working and looking - that is, until I decided today to try Benchmark for the heck of it.  Well, it shows that I'm hovering around 60 FPS, but the weird thing is, I started dragging a terminal window around to see if the wobbly window effect slows it down at all, and I realized that the effect was working SO MUCH MORE SMOOTHLY.  To make sure I wasn't just seeing things, I turned off Benchmark, and dragged the terminal around again.  Sure enough, it just didn't look as nice.  The text would blur a little bit, and it wasn't until now that I realized that the window skips around by just the tiniest iota, which makes a big difference in overall effect.

I'm at a complete loss as to what could possibly cause this.  Does Benchmark limit the FPS to 60, thus capping my refresh rate and making it smoother?  I'm on a laptop with an LCD monitor, which I suppose would make sense, but the idea still seems kind of far-fetched.

Has anyone experienced a similar problem?  Any ideas/suggestions at all would be greatly appreciated - thanks in advance!

---

### Post by EXCiD3 on 2007-08-11
I thought that during Beryl's benchmark feature, wobbly windows and other features were disabled. Are you sure wobbly windows were still enabled during the benchmark?

btw what graphics card are you running it on? And since you are using a laptop, are you using both monitors at the same time? I used both monitors as separate Xservers with Beryl one time, and EVERYTHING was laggy. I disabled my laptop monitor and everything sped back up.

---

### Post by Choad on 2007-08-22
it's because it disables "detect refresh rate" and whacks the refresh rate up to 200

"detect refresh rate" has never worked well for me. i suggest you disable it and set your refresh rate to your monitor;s refrsh rate (probably 60)

---

### Post by CrimsonMemory on 2007-08-26
I know it's a bit late now, but that worked wonders!  Thanks a lot!

---

