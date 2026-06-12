---
title: "Make Beryl faster/smoother on your pc"
date: 2007-02-27
forum: Desktop Environments
---

### Post by BBSeXoDuS on 2007-02-27
I just recently came across this tip on the web on some site. And it really does work. 
> 
Open beryl-settings-manager. In the General Options page, under the Main tab, uncheck Sync To VBlank, uncheck Detect Refresh Rate and change Refresh Rate to 200.

Although 200 might be way too much refresh rate to my taste (It must use more cpu) the deal here is making the refresh rate higher than the default 60. This makes the gpu render frames faster than what your monitor shows them, meaning that if there's a cpu bottleneck somewhere the gpu doesnt run out of frames, which shows the non-smooth movement. I really felt the difference, I guess your results may vary, but for me it did a GREAT difference.

---

### Post by BBSeXoDuS on 2007-02-28
I've been doing some investigation, and I found out that the only thing that shows results for me is turning off Vsync to blank. With Vsync enabled I do feel sloppinnes in the windows movement and animations. Turning that off makes it way smoother.

I did also confirm what I mentioned earlier. Using a sync rate of 200 is way too much, and uses a 100% of cpu, compared to the 20-30% used when in normal refresh rate.

My recommendation, disable vsync to blank, and leave Detect refresh rate on (what value you set on the refresh rate doesnt matter if it's set to detect it). If you still want to try with the refresh rate, try a value somewhere between 80 and 100, that's way over your monitors refresh rate and should provide with a smooth experience, and less cpu usage than using 200.

Enjoy!

---

