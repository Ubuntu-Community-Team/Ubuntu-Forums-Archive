---
title: "shortcut"
date: 2008-05-20
forum: Desktop Environments
---

### Post by Robocoastie on 2008-05-20
I didn't have any luck with search but that may have been for lack of using the right keyword. So here goes...

I've been moving away from the cursed mouse and trackball which both hurt my wrists now. What do I do to enable keywords to start a program? For example alt-f2 pulls up the run application box. I'd to be able to just type ***writer*** and hit enter then OpenOffice Writer will start. I can get the ooffice wizard to open by typing ***openoffice*** but haven't figured out how to make that for the individual parts (like writer) much less any other program in my gnome launcher.

I actually found the built-in voice activation of Vista VERY good the more I used it but there is soooo many bugs in Vista that drive me up a bloody wall the biggest of which is simply opening a window, it sits and thinks for several seconds about whether to display my documents or not gawd that OS is slower than molasses even with "aero" shut OFF.

---

### Post by dushkal on 2008-05-20
Why don't you just use softlinks?

e.g. Create a soft link in /usr/bin (where oowriter exists) and then when you say writer, oowriter will start..

```
sudo ln -s /usr/bin/oowriter /usr/bin/writer
```

---

