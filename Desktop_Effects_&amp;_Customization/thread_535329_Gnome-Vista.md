---
title: "Gnome-Vista"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by ikki_72 on 2007-08-26
extracted it into Desktop and try to copy 'glass-icons' folder to /usr/share/icons, here's the result on terminal: 
```

umarzuki@umarzuki-desktop:~/Desktop/Gnome-Vista$ sudo cp "glass-icons" -v /usr/share/icons
cp: omitting directory `glass-icons'
umarzuki@umarzuki-desktop:~/Desktop/Gnome-Vista$ 
```

What should I do?

---

### Post by Dark Star on 2007-08-26
Why you are trying it to copy in /usr/share/icons Simply open Themes from System -> Prefrences and click on install select  .tar.gz file of icon and click ok .. It will get installed :). Btw if you wanna try to copy folder copy here
```
 /home/<user name>/.icons
```

---

### Post by hyperair on 2007-08-26
It omits directories because you didn't tell it to recurse through directories. Adding a "-r" just after "cp" will do the job.

---

### Post by ikki_72 on 2007-08-30
thanks

---

