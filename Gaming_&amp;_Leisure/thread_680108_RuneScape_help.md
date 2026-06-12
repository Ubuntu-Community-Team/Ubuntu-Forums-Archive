---
title: "RuneScape help"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by jeff_flynn on 2008-01-27
I had to install Linux ubuntu 7.10, the Gutsy Gibbon, on my computer because Windows XP was toast. How do i install the java(s) i need to play RuneScape?

thanks

---

### Post by Lord Illidan on 2008-01-27
Check out the 3rd link in my signature about java browser plugins.

---

### Post by remyxcore on 2008-01-28
> **Lord Illidan said:**
> Check out the 3rd link in my signature about java browser plugins.

I went to the site and after using the 

```
sudo apt-get install sun-java6-plugin
```

I get this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

```

---

### Post by maconga on 2008-01-28
Hey I play the Game also, 

(I'm still new to Ubuntu, I hope you understand) 

**Do this Below, I did it and it worked for me**

Applications > System > Synaptic Package Manager 

Now Click, Settings > Repositories 

for the "Ubuntu Software" Tab check the following 
(main)
(universal)
(restricted) 

Now the "third-Party Software Tab" have the two check, that have the website address 

Now the "updates" tab, select 
(gusty-security)

Now click close, and click "Reload" 

Now search for "sun" and install 
sun-java6-bin
sun-java6-fonts
sun-java6-jre
sun-java6-plugin

that should get the game to work, also search for "flash" and install 
flashplugin-nonfree


My Runescape Name is "Maconga"  
lvl 106

---

