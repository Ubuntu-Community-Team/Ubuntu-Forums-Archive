---
title: "Ubuntu Freezes Momentarily"
date: 2011-06-09
forum: Desktop Environments
---

### Post by MacinViLLe on 2011-06-09
I'm in a very annoying state.

My computer stops briefly (about 2-5) seconds. I have been using Ubuntu since 8.04, and this Natty is the first release that gave me this headache! It's like my computer is doing something at the background that eats lots of memory, thus it stops responding momentarily.

How should I go about troubleshooting this? I am not using Unity, it causes longer time freeze. Attached is the screen shot of my computer activity. Though you can see that I have opened lot of applications, but let me inform you that the behavior does not change even if there's not a single program running.

---

### Post by coffeecat on 2011-06-09
You are using most of your memory and swap is being used. I'm wondering if the brief "freezes" are due to chunks of RAM being swapped in and out of swap. This can be noticeable. There are spikes of CPU activity every 10 or 20 seconds. Do these coincide with the freezes?

Check your hard disk activity light when the freezes occur. If it flickers, then this could be to do with swapping. The fact that you didn't see this in earlier releases could simply be down to the fact that Unity will be a little more memory hungry than vanilla gnome. You've probably passed a tipping point.

---

### Post by MacinViLLe on 2011-06-09
Hi coffeecat,

Thanks for the reply. Yes you are correct: the moment my Ubuntu freezes is the same time the spikes appear in CPU graph.

But I am not using Unity anymore, I logged in using Ubuntu (Classic).

I'll try to log in using other options aside from Ubuntu (Classic), see if there's a noticeable difference.

---

