---
title: "How to setup a dual monitor Ubuntu Wiki"
date: 2010-10-27
forum: Documentation and Community Wiki Discussions
---

### Post by COKEDUDE on 2010-10-27
I put several hours into adding a "How to setup a dual monitor" in Ubuntu's Wiki. I hope this will help other people. I know if I would have been able to read this that it would have saved me a lot of time. I hope this saves other people time. 

[https://wiki.ubuntu.com/X/Config/Resolution/#How%20to%20setup%20a%20dual%20monitor](https://wiki.ubuntu.com/X/Config/Resolution/#How%20to%20setup%20a%20dual%20monitor)

---

### Post by COKEDUDE on 2011-05-30
I just updated the .xprofile information. I added information on how to set a primary monitor. 

```
  xrandr --output VGA1 --mode 1024x768 --rate 60

  #Laptop right extra Monitor Left
  #xrandr --output VGA1 --left-of LVDS1

  #Laptop left extra Monitor right
  #xrandr --output LVDS1 --left-of VGA1

  #This is to set your primary monitor.
  
  #This sets your laptop monitor as your primary monitor. 
  xrandr --output LVDS1 --primary
  
  #This sets your VGA monitor as your primary monitor. 
  #xrandr --output VGA1 --primary
```

---

### Post by sectshun8 on 2011-05-30
Nice [IMG]http://metaldetectingforum.com/images/smilies/waytogo.gif[/IMG]

---

