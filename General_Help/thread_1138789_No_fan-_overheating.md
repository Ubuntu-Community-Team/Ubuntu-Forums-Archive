---
title: "No fan- overheating"
date: 2009-04-26
forum: General Help
---

### Post by d42 on 2009-04-26
It seems that the fan never runs on my panasonic cf-ts, and it commonly gets very warm to the touch. I have 4 vertical lines of dead pixils now, and I'm thinking it's related to overheating.

I know nothing about this, but I found proc/acpi/fan and didn't find anything in the file (even checked for hidden files)

It may be this isn't why I'm having problems at all- looking at the case I see no air vents at all. How is this thing suposed to keep from overheating normally???

Thanks for any input.

Edit: I found the Thermal_Zone file- that has stuff in it. I still have absolutly no idea what I'm doing.

---

### Post by Thalarse on 2009-06-27
I'm having a similar issue with my HP tx1000 (1210ca). There's nothing at all in /proc/acpi/fan, and while I can feel a faint breeze and hear fan noise, that could be due to other devices inside and maybe thermal convection causing the airflow. At the moment the gpu is 79c and the cpus are 56c - with only firefox and a terminal open. 

On my machine there is only one fan as far as I know - the gpu and cpu share. But nothing shows up in the obvious areas. Though I'm still noobish so I could be missing something.

(Edit) I've had this problem in 9.04 and 8.04. I ran 8.10 for a while but I can't remember if the issue was there then. It probably was as I don't remember the gpu going below 80 degrees ever.

---

### Post by Favux on 2009-06-27
Hi Thalarse,

See tapsevarg's post # 25 here:  [http://ubuntuforums.org/showthread.php?t=1040872&page=3&highlight=tx1000](http://ubuntuforums.org/showthread.php?t=1040872&page=3&highlight=tx1000)

Especially the part about increasing the ram for video in the bios.  And of course clean your vents if you haven't already.

---

### Post by Thalarse on 2009-06-27
Ah thanks for that, I've been scouring the mark 1 tx1000 thread, but didn't notice the new one. I've seen a tutorial on dismantling the tx1000 and replacing the heat transfer paste, but I had trouble with the small screws in the dvd drive bay. I'm going to have another crack at it when I find a small enough screw driver. 


I find it odd that the fan doesn't show up at all though, despite the fact that it physically exists.

---

