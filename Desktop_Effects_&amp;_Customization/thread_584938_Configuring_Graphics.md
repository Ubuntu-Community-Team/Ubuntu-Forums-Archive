---
title: "Configuring Graphics"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by shanepardue on 2007-10-21
This may come across vague, but it seems there are a few issues I encounter on each of my machines running Ubuntu and I've put up with them for a very long time, but I wanted to see if there were any tips on how to fix them.

My laptop is running an 945GM video card and I get vertical window tearing despite setting compiz to "enable vsync". Is there a way around this tearing or is that a product of my poor quality monitor or video card?

On my desktop (running an Nvidia fx5500), the moving of windows is very smooth, but animations such as magic lamp tend to get a little choppy. Is this something that can be fixed or is this a product of a poor Nvidia driver? My friend's does the same thing with a 8800 I believe. His card by no means should have any such problems.

I appreciate any advice you can provide..even if they aren't fixes, I'd like to know what the cause of the problems are. Thank you very much for your time!

---

### Post by shanepardue on 2007-10-22
Any tips are accepted :)

---

### Post by shanepardue on 2007-10-25
Not all at once!

---

### Post by cdekter on 2007-10-25
I can't help with your vsync problem - I find that enabling it has the desired effect. However, with the choppy animations...

I found that turning off 'detect refresh rate' in the Compiz settings smooths things a lot. However some animations still are choppy. It can depend a lot on what the system load is like at the time. My theory is that the underlying cause is unfavourable thread scheduling. Linux gives higher priority to background services such as network etc etc. Further evidence for this: few weeks ago I took a shot at compiling a custom kernel with CFS patches applied, and it did make the Compiz animations a lot smoother.

So, besides compiling your own kernel with those patches applied, the only other thing I did was increase the length of the animation. That gives the system time to draw more frames, and tends to make it seem smoother.

Having said all that, I'm not using Compiz on Gutsy at the moment due to the infernal nVidia driver bug that makes all videos display as globby green messes.

---

### Post by shanepardue on 2007-10-26
That's very interesting! That's exactly the kind of advice I was looking for. Do you believe it was worth compiling your custom kernel? Did you see a big difference?

---

### Post by TNakos on 2007-10-26
hmmm.

---

### Post by cdekter on 2007-10-28
Compiling the kernel wasn't actually such a huge effort as it may sound. The actual compilation did take a while tho... 

It's definitely worth it if you're interested in that sort of thing, however the Completely Fair Scheduler is in the next version of the Linux kernel that will probably form part of the next Ubuntu release. You may be better off waiting until then. Also note that I did this on Feisty - I haven't searched around to see if anyone's done a CFS patchset for the Gutsy kernel version. Personally I haven't bothered to do it on Gutsy as yet.

---

### Post by shanepardue on 2007-10-28
Awesome..I'll have to look into that.

The window tearing on the intel video driver is the hot topic now. It's killing me!

---

### Post by Cresho on 2007-11-19
thanks for this information.  I am running gutsy 32bit.  I have a hp w2408 monitor with a 6400 black edition amd along with a 8800gt.  I was wondering why i had such poor performance until i removed the "detect refresh rate" and bumped the refresh rate to 200.  It is smooth silk.  And finally the anti liasing at boot up fix with the load nvidia driver setting command by adding startup file to system->preference->sessions "nvidia-settings --load-config-only".  This looks way way better than a mac.  seriously! antiliasing is at 16q override application and anisotrophic filer at 16x

---

### Post by Cresho on 2007-11-21
> **Cresho said:**
> thanks for this information.  I am running gutsy 32bit.  I have a hp w2408 monitor with a 6400 black edition amd along with a 8800gt.  I was wondering why i had such poor performance until i removed the "detect refresh rate" and bumped the refresh rate to 200.  It is smooth silk.  And finally the anti liasing at boot up fix with the load nvidia driver setting command by adding startup file to system->preference->sessions "nvidia-settings --load-config-only".  This looks way way better than a mac.  seriously! antiliasing is at 16q override application and anisotrophic filer at 16x

Had to disable antiliasing and anisotrophic filter because of refresh problems after a script disabled and re-enabled compiz.  if i boot up, wine is fine but if I disable it during ....hmm.  Ill see if its my commands.

---

