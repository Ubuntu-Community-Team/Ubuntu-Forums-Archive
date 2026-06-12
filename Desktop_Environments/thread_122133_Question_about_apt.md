---
title: "Question about apt"
date: 2006-01-26
forum: Desktop Environments
---

### Post by SuperMike on 2006-01-26
Gosh, this is complex to postulate and then ask you if I'm correct.  I believe it is possible that certain uses of apt could actually prevent one from getting critical updates or system patches. Perhaps I am wrong, and if I am, please let me know.

Take for instance Breezy and you want php4. However, Breezy prefers php5 now instead of php4. Therefore, you turn on the universe option in sources.list and do an apt-get update, then use apt-get install php4 to get it. Next, you don't want to live in this "beta" land of everything that the universe option brings you, so you comment it out again in sources.list and run apt-update again to return to "normal" Ubuntu. Finally, after a few days, you might be prompted to download and install Ubuntu system updates and security patches. You run these. But will you ever get any of these for php4? The point is that I believe you will *not*  because you have the universe option turned off. However, if you turn the universe option on, and you follow through with an update, and then you get prompted to update the entire Ubuntu, you could not only be updating php4, but also updating everything else into a kind of "beta" territory. That's not healthy.

Now, this could be php4 in this example, but it could be anything that only comes to you through the universe option in Breezy, such as tinyproxy.

So, if I'm right, then (a), using apt in this manner, you don't have a way to keep your php4 secure and could get hacked, and (b), you have no way of knowing whether you have a critical patch or security update for php4, and (c) you run the risk of updating your entire OS into a kind of "beta" territory if you turn on the universe option and leave it on. Again, it's not just about php4. It could be about anything that comes only from the universe option in Ubuntu.

Am I right? Please let me know.

---

### Post by psychicdragon on 2006-01-26
You're mistaken. The software in the universe repository isn't beta quality, it's just maintained by the community (the Masters of the Universe). You have nothing to lose by leaving the universe repository uncommented in your sources.list. All the packages are still tested before inclusion.

---

### Post by SuperMike on 2006-01-26
Okay, I'm game. Then how would I update (*) my PHP4, Apache2, and PostgreSQL by temporarily dipping into Universe waters, while leaving everything else in my OS alone?

* By update, I mean in this case download critical application and security patches.

---

### Post by psychicdragon on 2006-01-26
Use Synaptic. Right click on the package (php4 in this case) and select "Mark for Upgrade". Then Apply.

I'm sure there's also a way to do this from the console, but I don't know it.

---

### Post by RAOF on 2006-01-26
[QUOTE=SuperMike]Okay, I'm game. Then how would I update (*) my PHP4, Apache2, and PostgreSQL by temporarily dipping into Universe waters, while leaving everything else in my OS alone?

* By update, I mean in this case download critical application and security patches.[/QUOTE]
You could just hit "update" in synaptic, or "sudo apt-get update" from the console.  As psychicdragon said, the packages in the Universe/Multiverse repositories aren't beta packages.  Furthermore, they don't overlap with packages in the main Ubuntu repositories - you'll only get updates from universe to the packages you installed from universe.  Furthermore, apache2 and PostgreSQL are both in main, anyway.

---

