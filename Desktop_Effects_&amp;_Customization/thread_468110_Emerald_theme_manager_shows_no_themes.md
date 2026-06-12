---
title: "Emerald theme manager shows no themes"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2007-06-08
I recently installed Beryl on someone's computer using the following guide:

[http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html](http://technowizah.com/2007/02/debian-how-to-aiglx-beryl.html)

The install went perfectly.  Beryl functions like a champ.

But upon opening the Emerald theme manager to show the different themes...there were none listed.  Not even the one it had selected as a default theme was there.

How do I fix this?

---

### Post by Soybean on 2007-06-08
In Synaptic, install the "emerald-themes" package (or "sudo aptitude install emerald-themes" from a terminal). That should be all it takes. :)

---

### Post by Youresorock on 2007-12-19
```
sudo aptitude install emerald-themes 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for emerald-themes

```

---

### Post by FuturePilot on 2007-12-19
Try 
```
sudo apt-get install subversion
```
Then run this for the Non-gpl themes
```
svn ls https://svn.generation.no/emerald-themes
```
Accept the certificate permanently. 
Now go into Emerald Theme Manager and click the Repositories tab.
Then click the Fetch buttons.

---

