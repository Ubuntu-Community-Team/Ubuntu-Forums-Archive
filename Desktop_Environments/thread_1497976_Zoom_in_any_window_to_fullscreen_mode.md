---
title: "Zoom in any window to fullscreen mode"
date: 2010-05-31
forum: Desktop Environments
---

### Post by kontiky on 2010-05-31
Is it possible to zoom in any window to fullscreen mode with hiding gnome panels? Is there any shortcuts to zoom in/out for this?

---

### Post by stinkeye on 2010-05-31
In system > preferences > keyboard shortcuts 
you can bind a key to toggle full-screen mode.

---

### Post by Lampi on 2010-05-31
usually that's already set to F11, isn't it?

edit: nope, this might be desktop dependent as well (kde,gnome,fluxbox)

just do as stinkeye says and you're good to go

---

### Post by kontiky on 2010-05-31
> **stinkeye said:**
> In system > preferences > keyboard shortcuts 
you can bind a key to toggle full-screen mode.
I haven't my Ubuntu near me to try this now... but could you also say in what "keyboard shortcuts" subgroup is this "toggle full-screen mode" command?

---

### Post by kontiky on 2010-05-31
> **Lampi said:**
> just do as stinkeye says and you're good to go
Do you remember exact toggle full screen mode command name?

---

### Post by stinkeye on 2010-05-31
> **kontiky said:**
> Do you remember exact toggle full screen mode command name?
You can use wmctrl to toggle the active window to fullscreen.

Install wmctrl
```
sudo apt-get install wmctrl
```



To toggle fullscreen of the active window use...
```
wmctrl -r :ACTIVE: -b toggle,fullscreen
```


or you can specify the window ...eg for firefox
```
wmctrl -r firefox -b toggle,fullscreen
```

---

### Post by kontiky on 2010-05-31
> **stinkeye said:**
> You can use wmctrl to toggle the active window to fullscreen.
So, by default, gnome hasn't fullscreen command?

---

### Post by stinkeye on 2010-05-31
> **kontiky said:**
> So, by default, gnome hasn't fullscreen command?
Probably has but I don't know it.

---

### Post by stinkeye on 2010-05-31
> **kontiky said:**
> I haven't my Ubuntu near me to try this now... but could you also say in what "keyboard shortcuts" subgroup is this "toggle full-screen mode" command?

Window Management

---

### Post by kontiky on 2010-05-31
> **stinkeye said:**
> Window Management
Thanks. I tried to assign shortkey to "Window Management/Toggle fullscreen mode" command but, unfortunately, without any effect  for Eclipse and Nautilus windows ;(

---

### Post by stinkeye on 2010-05-31
> **kontiky said:**
> Thanks. I tried to assign shortkey to "Window Management/Toggle fullscreen mode" command but, unfortunately, without any effect  for Eclipse and Nautilus windows ;(

I don't use eclipse but assigning f11 to Toggle fullscreen works for all my windows
including nautilus.

---

### Post by kontiky on 2010-06-04
> **stinkeye said:**
> I don't use eclipse but assigning f11 to Toggle fullscreen works for all my windows including nautilus.
I've found what Gnome "Toggle fullscreen" command works if I switch off Compiz in my Ubuntu.
But how to force this command with working Compiz?

---

### Post by stinkeye on 2010-06-04
> **kontiky said:**
> I've found what Gnome "Toggle fullscreen" command works if I switch off Compiz in my Ubuntu.
But how to force this command with working Compiz?

You probably need to activate the **Extra WM Actions** plugin under Window Management in CCSM.
When you set the the fullscreen toggle to f11 in keyboard shortcuts it also sets it for compiz but it wont work unless you have the plugin enabled.

---

### Post by kontiky on 2010-06-04
> **stinkeye said:**
> You probably need to activate the **Extra WM Actions** plugin under Window Management in CCSM.
When you set the the fullscreen toggle to f11 in keyboard shortcuts it also sets it for compiz but it wont work unless you have the plugin enabled.
Bingo! Finally, it helped!
Thanks a lot!

---

### Post by lukanova on 2010-10-13
i was looking for this solution for ages! i loved the ability to full screen anything you're working on. and at some point in past few years this stopped working. now i know why and now it works!

thanks for this solution.

l.

---

### Post by shell-fu on 2010-12-02
A note for Ubuntu 10.10 users. I found that the "Extra WM Actions" plugin wasn't available in CompizConfig Settings Manager. To make sure you have everything installed, run the following in a terminal:

sudo aptitude install -y compizconfig-settings-manager compiz-fusion-plugins-extra

Then open System -> Preferences -> CompizConfig Settings Mangager. The "Extra WM Actions" plugin should now be available under "Window Management". Check it and click "Close".

Restart your X-server by logging out and back in again. The "Toggle fullscreen" keyboard shortcut should now work with whatever you set in the main Gnome keyboard shortcuts settings.

---

