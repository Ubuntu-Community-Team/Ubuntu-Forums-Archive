---
title: "Installing Wine"
date: 2009-06-05
forum: General Help
---

### Post by 54321 on 2009-06-05
What do I need to do? Thanks.

---

### Post by HOLY COW on 2009-06-05
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

That should get you started.

PS : If you are new to this then i suggest getting "ubuntu tweak" for further needs until you feel comfy with the ubuntu environment. 

^_^

---

### Post by 3rdalbum on 2009-06-05
If you haven't already, enable all the repositories. Go to System > Administration > Software Sources and make sure that the checkboxes in a group at the top of the window are all checked.

Now go to Synaptic Package Manager (System > Administration > Synaptic Package Manager) and do a search for "wine". Right-click it, choose Mark For Installation, and then click Apply.

To run Wine, you need to run a program WITH it. Usually you should be able to double-click a Windows program and have it open. Otherwise, you might need to open a terminal and type "wine " (no quotes, but include the trailing space) and then drag the Windows program to the terminal, click on the terminal window and press Enter. That says "Run Wine, with this program".

Be aware that, statistically, most programs don't work with Wine and you should be trying to find Linux equivalents wherever possible. If you run into troubles with a specific program, check out the Wine HQ website for tips.

---

### Post by scouser73 on 2009-06-05
I'd recommend that you first install Ubuntu Tweak, not only does this fantastic software come with WINE, but a plethora of programs.

[http://ubuntu-tweak.com/downloads]("http://ubuntu-tweak.com/downloads")

Select this file **ubuntu-tweak_0.4.7.1-1~jaunty1_all.deb**, and install open Ubuntu Tweak by looking under **System Tools**, then click **Applications** then **Add/Remove** and scroll down to **WINE Microsoft Windows Compatibility Layer** and then check the tick box, click **Apply** and that's it.

---

