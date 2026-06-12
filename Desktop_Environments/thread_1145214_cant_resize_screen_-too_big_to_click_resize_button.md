---
title: "cant resize screen -too big to click resize button"
date: 2009-05-01
forum: Desktop Environments
---

### Post by jesse c on 2009-05-01
I just put Jaunty on my old laptop that i had Ibex on but the resolution size was bigger than my Ibex set up so i went to system/pref/screen resolution and mistakenly went the wrong direction and now the resolution is so big the 'return to old settings' button is off the page.how can i reset the resolution size? I only had 2 options,which was a whole different issue to resolve but now my screen is so big i cant even change any settings.While your here how can i get more resolution options that would match my Ibex set-up?

---

### Post by pastalavista on 2009-05-01
Press the alt key, click anywhere in the window and drag it to the part you need to use.

---

### Post by jesse c on 2009-05-01
Thanks pastalavista the alt key worked once i figured out you had to grab it with left mouse button at the same time,and i think i figured out that my nvidia card does not have driver running,at least when i go into system/admin/hardware driver the only driver listed is an atheros wifi driver and a statement that 'no proprietary drivers in use on this system'.I went to Nvidia web site and downloaded driver but i dont know how to get it into system and synaptic has a nvidia modaliasis(?) checked in green whatever that means

---

### Post by pastalavista on 2009-05-01
You might try installing 'envyng' ```
sudo apt-get install envyng-core
```and then, in terminal run ```
sudo envyng -t
```Envy is a video driver installer, it runs in text mode but is very simple to use. Don't apply it if it doesn't find any compatible drivers for your particular card.

---

### Post by jesse c on 2009-05-01
Success again pastalavista,i copied and pasted your commands but this time it didnt work till i installed medibuntu repositories first,lucky i even thought of that though most nubies wouldnt even have heard of those third party extras.I just might try a clean install on my desktop now.Different observation while i think of it-inever saw an option for ext4 on my Jaunty install

---

