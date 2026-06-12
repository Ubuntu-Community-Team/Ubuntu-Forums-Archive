---
title: "Swiftfox icon won't stay in dock"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by PaulFXH on 2007-06-10
This is very strange.
I have Beryl installed and the AWN (avant-window-navigator) dock. Currently I have 17 icons (launchers) in the dock and these all work very well.
As I have been looking at Swiftfox browser recently, I have made a launcher icon for this with the intention of adding this to the AWN dock.
However, although I can get it to stay in the dock for the duration of the session, if I reboot it dissappears. Note that this does not happen with any of the other launchers.
What's up with this?

---

### Post by notwen on 2007-06-10
Create your swiftfox launcher and move it to .avant in your home directory. CTRL+H in Nautilus will bring up your hidden files/folders.  Hope this helps. =]

---

### Post by PaulFXH on 2007-06-10
Thanks for your suggestion but, actually, I had already done that and it still wasn't working.
What did work was to include this in my sources list
```
deb http://getswiftfox.com/builds/debian unstable non-free
```
and then reload Swiftfox from Synaptic. Now, Swiftfox appeared in Applications>Internet and I could place the "official" launcher on the Desktop ( actually in ~/.awn) and from there to the AWN dock. Now everything's fine.
It seems that AWN may not like half-*ssed launchers that you make yourself.

---

