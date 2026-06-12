---
title: "Installing a usplash theme (I found)"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by KrotBot on 2007-11-22
Ok so I googled around and found a dynamite Haruhi usplash theme in .deb form from the french ubuntu forums but am having no luck. The deb package installs fine and puts the .so file in place but I am unable to set it as my splash screen. 

There are a load of follow-up commands to use but none work.

Any help would be great as this is all thats missing from form my complete Haruhi desktop.

Here's the link to the translated version of the french post [http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fpid%3D1145920&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dharuhi%2Busplash%2Btheme%26hl%3Den%26safe%3Doff%26sa%3DG]("http://translate.google.com/translate?hl=en&sl=fr&u=http://forum.ubuntu-fr.org/viewtopic.php%3Fpid%3D1145920&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dharuhi%2Busplash%2Btheme%26hl%3Den%26safe%3Doff%26sa%3DG")

Cheers

---

### Post by anubhavrocks on 2007-11-22
Use this
[http://ubuntuforums.org/showthread.php?t=295524](http://ubuntuforums.org/showthread.php?t=295524)

---

### Post by KrotBot on 2007-11-22
I've been using start up manager that sees the .so file in the usplash dir but won't set it.
I am asuming that the .deb file doesn't complete installation but am unsure of desired affects of the follow up code.

I tried to set it in the terminal but the ```
ubuntu-se usplash sos
``` gives this readout  
```
Usage: ubuntu-se command theme

Commands:
  usplash - set the bootup usplash theme
  gnome-splash - set the gnome splash theme

Themes:
  flames
  glass
  bat
  baphomet
  default


```

as you can see despite the presence of the .so file it is not seen as a theme.

Any ideas?

---

### Post by anubhavrocks on 2007-11-22
here's what u should do
1.Download the .deb
2.Extract the .so from .deb using ```

dpkg -x 
```
3.In the extracted directory you will find the .so you need.
4.Use startup manager and and give it the path to .so

---

