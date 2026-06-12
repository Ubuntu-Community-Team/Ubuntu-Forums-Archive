---
title: "Changing my theme"
date: 2009-03-01
forum: General Help
---

### Post by kogger on 2009-03-01
I'm trying to adjust my themes, but when I change my theme it only changes for the root user, for some reason. When I open Synaptic or something that requires me to type in my password, it uses the new theme no problem; but everything else, for the most part, still uses the old theme. So I have no idea how to change my theme unless I log in as root.

Any idea how to fix this?

---

### Post by kogger on 2009-03-01
Okay, I got it to change by removing the folder from /usr/share/themes, but I still don't think I should have to do that just to get the theme change to kick in.

---

### Post by chriskin on 2009-03-01
are you sure you have installed the theme in the correct way? usually it is the other way round, root staying the way it was and user having the theme ok

---

### Post by kogger on 2009-03-01
I know, but I'm pretty sure I installed it correctly.

---

### Post by kogger on 2009-03-01
I don't know if it's related, but none of the new themes I install show up when I go to change my theme. I can adjust them by clicking customize and selecting their options for controls and such, which show up, but the themes themselves don't appear as an option.

---

### Post by handy on 2009-03-01
Were there instructions with your new theme(s)?

Did they include installing in the /home/<your user>/.themes/

---

### Post by kogger on 2009-03-02
No, I just have it in /usr/share/themes.

---

### Post by handy on 2009-03-02
> **kogger said:**
> No, I just have it in /usr/share/themes.

Then get your file manager to look in your /home/<user>/ & have it "show hidden", which should reveal a .themes folder.  If it doesn't then try making one & copying your themes in there.  Then try choosing the theme you want for you normal user account?

---

### Post by fragos on 2009-03-03
There's something wonky with themes if you customize and save. Specificaly it forgets the colors. I've found if I specifically set the colors individualy it doesn't seem to hapen. I also stoped saving themes and just depend on my last changes being used which works.

---

