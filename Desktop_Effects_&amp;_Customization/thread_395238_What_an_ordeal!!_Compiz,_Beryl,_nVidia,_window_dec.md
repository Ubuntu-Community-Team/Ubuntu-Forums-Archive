---
title: "What an ordeal!?! Compiz, Beryl, nVidia, window decorations,etc.."
date: 2007-03-27
forum: Desktop Effects &amp; Customization
---

### Post by mrguytx on 2007-03-27
My goodness!
I finally, after 7 hours of reading posts got beryl working in Feisty.
I had compiz in Edgy but after my upgrade it didn't work due to the nvidia driver change and probably numerous other things.
The thing is, i have no idea what the final fix was!
I tried the feisty nvidia-glx and glx-legacy drivers, nvidia binary drivers, tweaks to xorg.conf, and a hundred other tips.
Finally the last thing I did was uninstall the very latest nvidia binary, uninstall via apt *anything* that said nvidia or compiz or beryl, rebooted, reinstalled nvidia-glx-legacy and bery and whammo, it came up.
The final thing was the window decorations missing and luckily a post here fixed that:

emerald --replace

in a terminal brought them up and now themes work.

It's really a piece of work and I like it, but boy that was an ordeal.

Hope everyone enjoys tweaking this as much as I do, but one day I hope the average user doesn't have to do these things to see the beauty of an OS like Ubuntu (with eye-candy).

Thanks to everyone here that posted about beryl or nvidia, I believe I read each and every one of your posts!

---

### Post by zivley on 2007-05-01
I understand you so much!
I spent also half a day trying to set all up, I also managed getting my very old Video Card (nVidia VANTA 16M) to fully support GL and 3D, and I also managed to get beryl running without crashing or display blank screens...
But... I have the same windows decoration/buttons/borders problem, when I saw this post I thought "THIS IS IT", I tried it but it didn't help it, I still have the same problem.
I ran the command *emerald --replace* in a terminal and all I get is:
Engine settings loaded
and then it just remains stuck up there...
What is this command supposed to do?

I'll appreciate some help

Thanks,
Ziv

---

