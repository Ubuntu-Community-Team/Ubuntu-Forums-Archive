---
title: "display problem: incomplete theme deployment..?"
date: 2011-02-19
forum: Desktop Environments
---

### Post by RafikiSanchez on 2011-02-19
After installing my video card driver (restricted), my desktop theme seems to not be completely applying itself to my desktop. Parts of the UI are blocky, with battleship gray and solid black lines.. etc... rough. When I disable the driver, display goes back to normal. I've posted a subdomain of my website where I've published the before and after shots [here]("http://nowhere.divsharp.com").

I guess I don't even need a solution.. If someone could point me to where Ubuntu 10.10 stores the "fallback" icon (/theme) set (the one it seems to be reverting to in the "after" picture) so I can start to figure out how it works.

I'm not sure how to best describe this problem or where to post it. I already posted a [thread]("http://ubuntuforums.org/showthread.php?t=1690596") in General help, but I wanted to try a thread here under a different title, and I think it warrants a new thread because of my different approach to the problem.

---

### Post by RafikiSanchez on 2011-02-19
So, I still don't know what caused the problem, or what the real fix is.. but I solved it, though not elegantly. After some digging, I found out the preinstalled themes for 10.10 are in

/usr/share/themes

And once I read the gtkrc files for each, I found one in theme "Raleigh" which said that it was the theme that the system falls back to if no other theme is selected. I just copied the theme files from "Radiance" into that dir and after a reboot, finally, nice looking theme.

I can't figure out still why that "Raleigh" was being used at all, especially because the windows borders for "Radiance" were displaying fine the whole time. If anyone knows how this could have happened, I would definitely appreciate the answer.

Also, if anyone knows a more elegant way to fix this, I'm all ears.

---

