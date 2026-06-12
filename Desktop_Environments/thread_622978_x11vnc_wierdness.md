---
title: "x11vnc wierdness"
date: 2007-11-25
forum: Desktop Environments
---

### Post by Cr0n_J0b on 2007-11-25
Well, I've finally got X11VNC running on my new 7.10 build, but there is something strange happening.  I can connect to the server and see the desktop and cursor...I can evan move a window...once. then things, just freeze.  I can see the cursor moving on the target system's monitor and I can see my input is going through, I'm just not getting anything back.

Both systems are on the same internal, small LAN, so it's not bandwidth...nothing is running on the network right now.  My server is pretty big, with 2GB RAM and an X2 processor.

Any thoughts?

---

### Post by Cr0n_J0b on 2007-11-25
Ok, so now I'm getting miffed!:mad:

I have one system running Edgy (7.06 i think) and one running 7.10.  They are both on the same network and similarly configured.  The Edgy system works great, no issues with VNC, but the Gusty is giving me hell.  The screen isn't repainting on my client.  I can see it on the server...but it's not coming across.  I have tired different VNC viewers and the same behavior in both. the 7.10 is a brand new install which leads me to believe something is amiss.  

Anyone have a thought?

I have searched and can't see anyone else with a similar bug.

thanks

---

### Post by Cr0n_J0b on 2007-11-26
Well I've given up.  I just reloaded Gutsy from scratch and used the Rmote Desktop, which I think is simple VNC and it works ok now.  It's still very sluggish however...but I can live with it.

I still haven't figured out what was up with X11VNC...

---

### Post by krunge on 2007-11-26
> **Cr0n_J0b said:**
> Well, I've finally got X11VNC running on my new 7.10 build, but there is something strange happening.  I can connect to the server and see the desktop and cursor...I can evan move a window...once. then things, just freeze.  I can see the cursor moving on the target system's monitor and I can see my input is going through, I'm just not getting anything back.

Both systems are on the same internal, small LAN, so it's not bandwidth...nothing is running on the network right now.  My server is pretty big, with 2GB RAM and an X2 processor.

Any thoughts?

Did you try this x11vnc option? ```
-noxdamage
```  You can search this forum for more info and also here [http://www.karlrunge.com/x11vnc/#faq-beryl]("http://www.karlrunge.com/x11vnc/#faq-beryl")

---

### Post by Cr0n_J0b on 2007-11-27
thanks I'll try that out tonight.

---

