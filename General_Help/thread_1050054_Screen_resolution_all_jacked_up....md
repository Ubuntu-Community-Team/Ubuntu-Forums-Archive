---
title: "Screen resolution all jacked up..."
date: 2009-01-25
forum: General Help
---

### Post by tiger.woods on 2009-01-25
How can I run the setup routine for modifying my screen hardware and screen resolutions?

I tried running nvidia-xconfigure and get nothing - I thought that was how you ran the setup routine..?

Can someone shed some light?

Thanks,

---

### Post by diablo75 on 2009-01-25
Just assuming you have an nvidia video card since you attempted to run nvidia-settings.  Did you run that command in a terminal window?  If so, what did it say in response to the command, because if nothing came up I would expect it to say something like, "Command not found."

So if you need to install it, type:

```
sudo apt-get install nvidia-settings
```

Then to run it (with root privilages):

```
sudo nvidia-settings
```

If you just ran "nvidia-settings" by itself you wouldn't be able to save configuration changes to your xorg.conf file using the Save button at the bottom of the nvidia settings control panel; just mentioning that.

---

### Post by tiger.woods on 2009-01-25
Is that the GUI that is installed - nvidia-settings?

If so, then that is already installed but doesn't have my screen size for an option...

TW,

---

