---
title: "maybe bug of Desktop Effects?"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by chunchengch on 2007-04-28
In order to use Desktop Effects normally, I have re-installed Ubuntu 7.04 (Feisty Fawn) for three times, although I had tried many ways to solved problems such as modified files sources.list and gdm.conf-custom etc. according to the article "XGL/Compiz Nvidia 32bit" (knowledge 76), such as installed Beryl Manager, but the fact is everything gets worst. 

Finally, I discover one thing and I suppose it may be a bug, after I newly install Feisty, if I activate the Desktop Effects, I **must not** change the setting any more, otherwise the cube effect will no more appear and the applet "Switch between workspaces" remains only one workspace. however, because I am just a linux newbie, I tried Mandriva for about two weeks and then switched to Ubuntu for just four days, I am not pretty sure all what happened?!

When I installed Feisty the first time, the beautiful startup music came out from my laptop, you know, I was so exciting, because Mandriva played no sound, although it offers a excellent 3D desktop effect "Metisse", I preferred a "phonic" linux environment to begin my learning, while I am still keen to use Beryl and Compiz to fulfill my Ubuntu Feisty Fawn, so, looking forward to the update of this problem. thanks!

Paul
from Taiwan R.O.C.

---

### Post by Hmarroqu on 2007-04-28
i have the same problem, the first time i used the effects, both the cube and window effects worked, then its either i use only the window efect or the cube effect and when i go bak to using the cube effect i have to reset my workspaces to 4 since they go back to 1 for some  reason.

---

### Post by Chris11 on 2007-04-30
same thing here. Worksapces go from 4 to 1 activating the desktop effects,  although the one workspace that shows up might be clicked on to the very right, right midle, left midel and very left to change between the workspaces. 

I desactivated the efects,  but now at restart the workspaces loos there specific names and show up with the default name.  I have to rename every time.


Chris

---

### Post by chunchengch on 2007-05-03
I recommend to install Beryl and leave this problem behind, I enjoy very much Beryl's desktop effects, except the Emerald theme manager seems buggy.

For the sake of installing Beryl properly, please refer to my another thread "Personal summary of installing and enabling Beryl in Feisty" if you have a nVidia card and Ubuntu 7.04.

---

### Post by HKiCore on 2007-05-23
> **chunchengch said:**
> Finally, I discover one thing and I suppose it may be a bug, after I newly install Feisty, if I activate the Desktop Effects, I **must not** change the setting any more, otherwise the cube effect will no more appear and the applet "Switch between workspaces" remains only one workspace.

I found out this myself too by installing Beryl. Beryl was bit too much for my taste so I decided to switch back to Ubuntu's own cube and wobbly windows, but no deal... 

I finally managed to get the cube working by installing gnome-compiz-manager from the Synaptics. After the installation I opened the Gnome Compiz Preferences -window (System->Preferences->GL Desktop).

I opened the Workspaces-tab from the Gnome Compiz Preferences -window and checked the Skydome and Animate-options. 

I hope this helps someone.;)

---

