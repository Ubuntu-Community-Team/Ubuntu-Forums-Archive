---
title: "I thought Gutsy already came with Xgl..."
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by japtar10101 on 2007-12-06
Last time, when I updated from Feisty to Gutsy, it told me there was no need to start with the session beginning with xgl.  Since I re-imaged my computer to Gutsy instead (too many errors after updating), I thought Xgl would be in there already.  And apparently, I was wrong!
```
desktop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```
While it *sounds* like all I need to do is download Xgl, I just wanted to make sure.  Has there been any troubles as of late in this new iteration of compiz?  Also, what is the "safest" (package, preferebly) way of downloading Xgl?  Any other possible dependencies I should worry about?  Thanks in advance!

---

### Post by -grubby on 2007-12-06
no......I'm pretty sure that XGL comes by default. You can always try installing XGL

---

### Post by FuturePilot on 2007-12-07
Gutsy does not have XGL by default. However you shouldn't have to take any other steps in setting it up besides installing it. Logging out and back in should get everything going after installing it. The best way would be to 
```
sudo apt-get install xserver-xgl
```

---

