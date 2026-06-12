---
title: "Right click mouse issue with Compiz Fusion"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by imcc on 2007-10-04
I have an unusual problem with Compiz Fusion. When I right click items such as links in Firefox or icons on the desktop, sometimes the context menu does not appear. Sometimes it flashes up very briefly and then disappears. Sometimes I have to hold right click. This happens fairly randomly, but quite often. It's almost at a point where it renders Ubuntu unusable. 

I love Compiz Fusion, as its an amazing new way to procrastinate! I could just turn it off as this does fix the problem. 

Has anyone else had similar issues, or can someone suggest where to start looking for solutions to this issue? I've done forum searches and googled it but can't seem to find anything.

Im using Gnome, Compiz and an MS usb optical mouse. 

Thanks

---

### Post by raindog on 2007-11-03
I am having this problem too.  I have yet to find a solution, but I'm going to continue to tinker with my compiz-fusion settings.

---

### Post by dentaku65 on 2007-11-03
Open ccsm and choose Animation plugin, in the Animation plugin options choose Focus Animation tab and set
```
Fade 150 (type=Normal | Dialog | ModalDialog | Utility | Unknown)
```

Delete any other entries in this Animation Selection dialog

---

### Post by raindog on 2007-11-04
My CCSM Animation|Focus Animation is already set that way.  I'm presuming that is the default.  I disabled the Animation plugin entirely to see if that would help to no avail.

---

