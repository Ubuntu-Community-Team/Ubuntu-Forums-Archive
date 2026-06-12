---
title: "3D cube"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by Cedrick12 on 2007-11-10
I am new to Ubuntu and I having trouble getting the 3D cube feature.  Can you help me get this working properly???

---

### Post by spiff95 on 2007-11-10
> **Cedrick12 said:**
> I am new to Ubuntu and I having trouble getting the 3D cube feature.  Can you help me get this working properly???
Do you have compiz installed? If so, click on System, Preferences, Advanced Desktop Settings. Check the box for Desktop Cube, then open the property sheet by clicking on the cube icon. You can adjust the cube's behavior there.

---

### Post by creeco on 2007-11-10
Also, to make sure that you have a graphics driver that supports compiz, open up system/administration/restricted drivers manager

---

### Post by Cedrick12 on 2007-11-10
yea I installed it and I have Intel Graphics Media Accelerator X3100 will that work

---

### Post by TadH on 2007-11-10
lets find out
go o system prefs>appearances>clickvisual effects>custom or extra whatever is there
go to system >prefs>advanced desktop settings>geberal>desktop size>hiorizontal desktop set it to 4
go back, tick off 3d cube and rotate cube and therer you go

---

### Post by Cedrick12 on 2007-11-10
I have both options, "custom and options", but neither of them will enable after I click on  them  it just returns the message "Desktop effects could not be enabled"

What do I have to do...

---

### Post by Forlong on 2007-11-10
What output gives ```
compiz
``` in a terminal?

Also tell us about your graphics card and driver.

---

### Post by Cedrick12 on 2007-11-11
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 

is what was returned...What does this mean???  What must I do now??

---

### Post by Forlong on 2007-11-11
Your graphics chip is known to have issues with compositing effects and has been therefore blacklisted by Ubuntu to prevent that Compiz is used by default.

Try running Compiz like this and tell us how it works:
```
SKIP_CHECKS=yes compiz
```

---

### Post by JBAlaska on 2007-11-11
Check this;
```
http://wiki.compiz-fusion.org/Hardware/Blacklist
```

Edit: beat me to it Forlong lol

---

