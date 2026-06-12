---
title: "Unity gone after upgrade"
date: 2011-08-27
forum: Desktop Environments
---

### Post by stimpie on 2011-08-27
I recently installed  a few updates. 

Now instead of unity gnome is shown. 

I still have the 'ubuntu' session selected. What could have gone wrong?

---

### Post by wildmanne39 on 2011-08-27
Hi, is sounds like your video card driver got updated and it needs to be changed back the old one.

---

### Post by Frogs Hair on 2011-08-27
Open the software center and check history and that will tell you what updates were installed .

---

### Post by stimpie on 2011-08-27
Thanks for the pointers.

The cause was that the nvidia-common package was updated and the nvidia driver was enabled (i have a sandybridge with intel integrated video + external nvidia) 

The system should use the intel driver.

Removing the nvida driver fixed it.

---

### Post by wildmanne39 on 2011-08-27
Hi, I am glad you got it working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

