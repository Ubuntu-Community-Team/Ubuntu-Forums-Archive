---
title: "Kurumba app sensors problems"
date: 2005-09-30
forum: Desktop Environments
---

### Post by Omnios on 2005-09-30
Hi I have a p4 1.6ghz with a Asus mother board. The problem im having is im trying to config a sensor applet I managed to set up but a few things. In the config its set up as type="temp1" which does not work, in gnome sensor applet sensors i2c-sys which works in gnome it states the file as temp1_input, anyways I tryed that in the config and that did not work either. I do have lm sensors installed but found a long time ago the gnome dock apps sensors would not configure properly either. On the brighter side a lot more things work in the KDE dock apps than the Gnome for me as I could not even get the cpu frequency going in gnome. 

 Anyways any help would be apreaciated.

---

### Post by Takis on 2005-10-01
When you say Karamba, do you mean Karamba or SuperKaramba?

---

### Post by Omnios on 2005-10-01
Kuramba im trying to get super kuramba but its broken link on synaprtic right now

---

### Post by Omnios on 2005-10-02
Reply got it working, I   used the command sensors in term (that god for programmer notes) to get sensor type mine was the first entrys  in the out put. Then editing the kuramba config file for the wigit I replaces the sensor=sensror (<== no  mod to this part)  type="temp1' <= changed this part to type="CPU temp" etc this also holds true for  network I had  to chaange mind to type=ethO etc. Another trick is to load a hole bunch of sensors till you get one that works and look for the info you need then modding your other sensors with the config info.

---

