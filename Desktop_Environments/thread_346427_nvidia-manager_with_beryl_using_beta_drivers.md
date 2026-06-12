---
title: "nvidia-manager with beryl using beta drivers?"
date: 2007-01-25
forum: Desktop Environments
---

### Post by tisk on 2007-01-25
I have beryl running with the beta drivers for nvidia.
Is there a way to get nvidia-manager with the drivers I am using?
When I had the standard drivers I had the manager, but when I started off with a clean version of ubuntu and put on beryl the nvidia-manager wasn't installed- is it compatible with the beta drivers?

any help appreciated:)

---

### Post by tito2502 on 2007-01-25
Hmm, running Beryl here and nvidia-manager does nothing.

What is it?

---

### Post by tisk on 2007-01-25
well if you are used to running nvidia in other OS, basically it's a small application that allows you to adjust all you display settings.. gamma etc..
it comes as standard with the non-beta drivers

---

### Post by jual_mahal1 on 2007-01-25
**Tisk**, I believe you mean "nvidia-settings".

In the times where **Beryl** is known as **Compiz-Quinnstorm**, **nvidia-settings** must be installed together with **nvidia-glx **in Ubuntu repository. Removing **nvidia-glx** will remove **nvidia-settings** as well. Except, in the case of you are installing from Nvidia-provided driver, then you will have Nvidia version's of **nvidia-settings** utility. Search the original path of **nvidia-settings** by typing either:
"locate nvidia-settings" or "which nvidia-settings"

And, if you set up **Xgl** as a session instead of the normal default Gnome session and you are using Nvidia driver that does not support an extension needed by **Compiz-Quinnstorm** (or old versions of **Compiz**) , most probably you will set up **Xgl** and **xorg** side-by-side at display :1 and :0 respectively. Therefore, you need to run **nvidia-settings** at display :0 to access all Nvidia extension features from **xorg** instead of **Xgl** by typing at the command prompt:
"$DISPLAY=:0 nvidia-settings"

Now, Nvidia has provided all extension support needed by **Beryl **(and variants of **Compiz**), you can just type "nvidia-settings" at the command prompt.

You can also create an application launcher in Gnome to launch **nvidia-settings** if you prefer to.

---

### Post by tisk on 2007-01-26
thanks I've found the manager.
could you help me by telling me how to set up a launcher for gnome?

---

