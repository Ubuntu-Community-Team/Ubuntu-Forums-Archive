---
title: "Desktop effects cannot be enabled"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by LaxFreek on 2008-02-06
When I type in compiz in the terminal I get this. 
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
And when I go to system>pref>display and to the effects it gives me the "desktop effects cannot be enabled" message. 

Anybody know what I should do?

---

### Post by FuturePilot on 2008-02-06
What is your graphics card?
If you don't know post the output of
```
lspci | grep VGA
```

---

### Post by LaxFreek on 2008-02-06
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
That is what I got

---

### Post by FuturePilot on 2008-02-06
Try installing XGL
```
sudo apt-get install xserver-xgl
```

---

### Post by SIXAXIS on 2008-02-09
> **FuturePilot said:**
> Try installing XGL
```
sudo apt-get install xserver-xgl
```

I have the same problem and when I do this, my computer becomes EXTREMELY laggy. So I just uninstalled it. I have an ATI Radeon XPRESS 200M and I have the same output as the other guy. glxgears works fine running at about 700FPS and I have the official ATI restricted graphics driver.

---

### Post by mrmiserable on 2008-02-09
you could try for no whitelist driver problem

sudo gedit /usr/bin/compiz

line 54 add fglrx to line (compiz does not whitelist official ati driver)

hope this works for you it does for me

---

