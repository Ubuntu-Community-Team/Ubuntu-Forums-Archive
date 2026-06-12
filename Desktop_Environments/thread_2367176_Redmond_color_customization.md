---
title: "Redmond color customization"
date: 2017-07-26
forum: Desktop Environments
---

### Post by darthkelly on 2017-07-26
Hey all,

Sorry if this has already been discussed, but I'm having trouble finding an answer.

Since Win98, I've used the "Lilac" theme. I want to replicate that on my lubuntu machine. I've got the Redmond theme active, and I'm aware that I can edit the colors by editing /usr/share/themes/Redmond/gtk-2.0/gtkrc, but I'm not sure which thing is which. 

That is, how does this:
```
  fg[ACTIVE]        = { 0.0, 0.0, 0.0 }  fg[INSENSITIVE]   = { 0.5, 0.5, 0.5 }
  fg[NORMAL]        = { 0.0, 0.0, 0.0 }
  fg[PRELIGHT]      = { 0.0, 0.0, 0.0 }
  fg[SELECTED]      = { 1.0, 1.0, 1.0 }


  bg[ACTIVE]        = { 0.83, 0.81, 0.78 } 
  bg[INSENSITIVE]   = { 0.83, 0.81, 0.78 } 
  bg[NORMAL]        = { 0.83, 0.81, 0.78 } 
  bg[PRELIGHT]      = { 0.83, 0.81, 0.78 } 
  bg[SELECTED]      = { 0.04, 0.14, 0.41 }


  base[ACTIVE]      = { 0.04, 0.14, 0.41 }
  base[INSENSITIVE] = { 0.83, 0.81, 0.78 }
  base[NORMAL]      = { 1.0, 1.0, 1.0 }
  base[PRELIGHT]    = { 0.04, 0.14, 0.41 }
  base[SELECTED]    = { 0.04, 0.14, 0.41 }


  text[ACTIVE]      = { 1.0, 1.0, 1.0 }
  text[INSENSITIVE] = { 0.5, 0.5, 0.5 }
  text[NORMAL]      = { 0.0, 0.0, 0.0 }
  text[PRELIGHT]    = { 1.0, 1.0, 1.0 }
  text[SELECTED]    = { 1.0, 1.0, 1.0 }
```

correspond to this:

```
activeCaption
activeCaptionBorder
activeCaptionText
control
controlDkShadow
controlHighlight	
controlLtHighlight	
controlShadow	
controlText	
desktop	
inactiveCaption
inactiveCaptionBorder
inactiveCaptionText	
info	
infoText	
menu	
menuText	
scrollbar
text	
textHighlight	
textHighlightText	
textInactiveText	
textText
window	
windowBorder
windowText
```


Again, I apologize if this has been covered already, For some reason my google-fu is failing me today. If anyone can point me to some form of documentation or other resource, I'd greatly appreciate it!

Best, 
K. Kelly Meine

---

### Post by vasa1 on 2017-07-27
> **darthkelly said:**
> ...
..., and I'm aware that I can edit the colors by editing /usr/share/themes/Redmond/gtk-2.0/gtkrc, but I'm not sure which thing is which. 
...
I did most of my theme color changes by trial-and-error. Documentation for gtk2 themes isn't particularly abundant. Plus, each theme engine seems to go its own way.

All I can suggest is that, before doing anything serious, you could copy over the relevant theme to ~/.themes and make your changes there.

---

