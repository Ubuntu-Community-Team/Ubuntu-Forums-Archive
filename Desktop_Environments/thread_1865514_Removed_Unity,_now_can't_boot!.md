---
title: "Removed Unity, now can't boot!"
date: 2011-10-20
forum: Desktop Environments
---

### Post by Tubbytee on 2011-10-20
Hi,

I just upgraded from 11.04 to 11.10.

Went fine but upgraded version was running Unity and making my old wheezy laptop run ridiculously slowly. So, in my wisdom, I opened synaptic and removed anything to do with Unity. Now after the splashcreen (which incidentally has been just a series of vertical white lines since updating to 11.04!) it just stops and nothing more happens!

Any ideas on how to solve this? (Bit of a newb I'm afraid so words of one syllable would be appreciated!)

TIA for any help

Pierce

---

### Post by nothingspecial on 2011-10-20
Plug it into your router.

Boot it.

Press Ctrl-Alt-F1

Login (You won't see your password when you type it btw)

Type ```
sudo apt-get update && sudo apt-get install unity
```

See if that reinstalls what you removed.

---

### Post by tartalo on 2011-10-20
If you have another desktop environment you only need to reinstall the lightdm greeter called unity-greeter.

There is also a lightdm-gtk-greeter but it doesn't work for me.

EDIT: I guess you could also install another DM, like GDM, KDM, LXDM...

---

### Post by Tubbytee on 2011-10-22
Thanks guys,

Installed unity-greeter and it worked!

As another question,

If I wanted to use XFCE, would it be better to uninstall all the other DE's? And if so, how do I go about it without screwing things up like before?

Cheers again for your help.

Pierce

---

### Post by nothingspecial on 2011-10-22
Just install the xfce4 meta-package then choose it from the login screen.

You have to click the wheel thing next to your username.

---

