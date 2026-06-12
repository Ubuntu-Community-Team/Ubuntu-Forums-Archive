---
title: "Fractional scaling issue, second 4k monitor is blurry (Ubuntu 22.04 GNOME)"
date: 2023-07-10
forum: Desktop Environments
---

### Post by cameronpoe on 2023-07-10
Hi all, I've posted about this issue on AskUbuntu.com and Reddit, but haven't had any answers the totally resolve this. See my original post [here]("https://askubuntu.com/questions/1477118/second-monitor-blurry-fractional-scaling-ubuntu-22-04").

I've seen this question asked in other places, but I couldn't find a definitive, system-wide answer. So, I have a second monitor, a 4K Gigabyte M28U that I'm running at 120 Hz with fractional scaling set to 175%. On Ubuntu 22.04, the text in many non-GNOME apps comes across as blurry, while default Gnome apps have nice, crisp text. Take for instance a comparison between a code snippet in my terminal vs. on Google Chrome in Stack Exchange:
[IMG]https://i.stack.imgur.com/LSWhd.png[/IMG]

Or a comparison of a PDF in Document Viewer vs. PDF viewer in VS Code:


[IMG]https://i.stack.imgur.com/elhPH.png[/IMG]


I assume this has something to do with fractional scaling. I also assume that images/video viewed on my 4K monitor are also getting blurred, but are just hard to see as the image is more complex than simple text.


Is there anything at all to be done about this? It's really frustrating splurging on a high-res monitor only for all the non-GNOME apps to be blurry.


Thank you!

---

### Post by ActionParsnip on 2023-07-11
Are you using Wayland or Xorg? If you try the other, does it help?

---

### Post by DuckHook on 2023-07-11
Fractional scaling can be a bear. If you are already on 175%, why not go to 200%?

Fractional scaling works far better with full integer scaling: 100%, 200%, 300% etc. It's the oddball in&#8209;between magnifications that require the computer to do all sorts of better&#8209;or&#8209;worse (usually worse) interpolation. If you don't force the CPU/GPU to do such algorithmic gymnastics, you will get better results.

---

### Post by cameronpoe on 2023-07-11
Thanks for the response. Unfortunately, whenever I go to 200% I get a really weird issue. If I have fractional scaling on and my second display set to 200%, then all my apps look 200% scaled, but I still get blurriness (just as bad as at 175%). Rebooting, closing apps, etc. does not fix this. When I turn off fractional scaling and set my scaling on my second display to 200%, my GNOME-native apps (i.e. running native wayland? like my terminal, my settings app, etc.) look scaled to 200% and crisp, but all my other apps look to be scaled to 100%. Again, rebooting, etc. doesn't help.

I also don't like cosmetically how big 200% is, but I would choose it if it gave me sharpness AND it actually scale my apps.

I've also tried running certain apps (VS Code, Chrome) on wayland natively using flags at execution. This works on my second display to give sharp apps correctly scaled, but when I drag windows over to my laptop monitor, the scale is now much smaller, so I have to make my laptop monitor's scale increased to 125% which is way too large for a 13" screen in my opinion. Again, I would do this option too, but what I run into is not all apps let me run them in wayland natively, which isn't a fix in my opinion.

The only setup I've tried that gives me the expected behavior with regards to blurriness and scaling is 100% scaling on both displays, and while I theoretically could squint at my 4K screen, the other issue I'm running into is chroma subsampling issues, so 100% scaling on my second monitor is out until I fix that (which is a whole separate problem).

---

### Post by cameronpoe on 2023-07-11
I am running GNOME in Wayland, so I guess Wayland, although most of my apps are Xorg via xWayland (I'm somewhat new to Ubuntu so don't know if this is technically correct).

---

