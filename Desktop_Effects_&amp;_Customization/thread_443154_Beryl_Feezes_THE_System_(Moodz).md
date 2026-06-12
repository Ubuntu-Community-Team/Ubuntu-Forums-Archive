---
title: "Beryl Feezes THE System (Moodz)"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by Moodz on 2007-05-14
Hello.
Im new to Ubuntu and i Installed Beryl on my system .
It was working for 3 or 4 Days very good.
But yesterday i clicked on the Gem icon and i changed a setting and i cant remember what it was 
but since i changed the system freezes.
i restarted, then when i run BEryl the system freezes. then i removed beryl from Synaptic then install again. it still the same problem.
so ALways when i run Beryl the system freezes.
What can i do. ???

---

### Post by Death_Sargent on 2007-05-14
what ever the setting is it won't go away through reinstall because ubuntu preserves application settings during uninstall. 

Your best bet is to manually check for posiible settings changes as you don't have to have beryl running to do so. 

Water effects, blur, and cube transparency are all posibilities. 

See if you can just reset to default. 

If all else fails delete the beryl profile and make a new one.

---

### Post by Moodz on 2007-05-14
Hey thank u for replying .
But as i remember i changed the settings of Beryl From OpenGL To XGL.
And im sure if i can make Beryl runs for 30 seconds i can change it back.
But the Problem is i explained B4. when i run it all my system freezes.
SO i need a way to change the drawing mode to OpenGL from terminal i think
coz i searched a lot in all the Ubuntu System Tools, and nothing i found.


So PLz I Need Help and Thanks For U All

---

### Post by Chang An on 2007-06-01
rm -r ~/.beryl
rm ~/.beryl-managerrc

These changed the settings back to default for me.  I dont think the first command did any thing but I tried them both and it fixed my beryl.  Gook luck:p

---

