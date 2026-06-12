---
title: "messed up open office title bar - xubuntu and ati mobility m4"
date: 2006-08-18
forum: Desktop Environments
---

### Post by zip22 on 2006-08-18
i installed ubuntu on an older laptop with ATI mobility m4 video.  i needed to use the safe graphics mode on the live cd.  i liked open office, but didn't like how slow ubuntu felt.  

i just installed xubuntu (also while in safe graphics mode) and i didn't find open office.  i installed it using synaptic.  the title bar and some of the window border are really messed up.  it doesn't always seem to be the same but right now the title bar is completely black.  the buttons and icons are random colors and jagged lines.  inside the window, everything is normal - its just the title bar and window border.  it only seems to be in open office.  i tried removing and re-installing with synaptic, but its the same.

any suggestions?

---

### Post by gunksta on 2006-08-18
Could you post a screenshot? It might show something you aren't noticing.

One quick question. Did you install xubuntu-desktop on top of Ubuntu    OR    did you do a fresh Xubuntu install? It sounds like you did a fresh install, I just want to be sure.

If this is a fresh install, and you then added openoffice, I am willing to bet you didn't install openoffice.org-gtk. So try this. First close OpenOffice.org and make sure it doesn't have any processes still running. Then

```
sudo aptitude install openoffice.org-gtk
``` 
Or just use Synaptic to install the package. Now restart OpenOffice.org and see if your problem is still there. I don't know why installing this would help it work with the window-manager, but it's a thought.

--andy

---

### Post by zip22 on 2006-08-18
i did do a fresh xubuntu insall.  

installing openoffice.org-gtk fixed the problem.  thanks very much for your help.

---

