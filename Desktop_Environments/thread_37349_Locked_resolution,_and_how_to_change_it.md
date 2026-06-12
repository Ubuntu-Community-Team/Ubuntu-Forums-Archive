---
title: "Locked resolution, and how to change it?"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Govinda on 2005-05-26
My resolution is locked in 1024 and 640 (I can change between those two). So my question is how can I change it?

I know I can do it manually in the xorg.conf but how? It there maybe a howto somwhere? Or can anyone explain it by posting there lines and so on? Or is there another _easy_ way to fix it without the risk to burn down your gpx-card?

I also know many people have been having this problem so if someone know a good solution, please post it so everyone can take part of the solution.

Govinda.

btw: I have a NVIDIA Ti 4200 gpx-card.

---

### Post by MrTom on 2005-05-26
in your xorg.conf there are a number of sections like this:

```

SubSection "Display"
	Depth		1
	Modes		"1024x768" "640x480"
EndSubSection

```

one for each depth your system supports, adding new resolutions is as simple as it seems, just add in new numbers. The list is in preference order.

for example mine says
Modes		"1280x1024"
because thats the only resolution i need for my tft, however you may need a line like
Modes		"1024x768" "800x600" "640x480"

---

### Post by Govinda on 2005-05-26
Thx for the answer!

I've not tried that one out but I fixed my problem by just typing "sudo dpkg-reconfigure xserver-xorg" in a terminal and then leaving everything at default except what resolutions I wanted to use, and then I just rebooted X and it worked :)

---

### Post by MrTom on 2005-05-27
haha, I always choose the complicated method!

dpkg-reconfigure would rewrite the xorg to add those lines anyway, so same result.

---

