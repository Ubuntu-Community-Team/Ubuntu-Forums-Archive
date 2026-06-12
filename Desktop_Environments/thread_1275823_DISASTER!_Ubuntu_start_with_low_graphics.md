---
title: "DISASTER! Ubuntu start with low graphics"
date: 2009-09-26
forum: Desktop Environments
---

### Post by argos3016 on 2009-09-26
I'm posting from another computer that's isn't mine. When I booted Ubuntu says this:

"Ubuntu is running in low-graphics mode
The following error was encountered. You may need to update tour configuration to solve this.
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) [drm] drmOpen failed.
(EE) intel(0):[dri]DRIScreenInit failed. Disabling DRI.
(EE) intel(0):Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0):Couldn't allocate video memory"

I copied FULLY the error message.
Any idea?:(

---

### Post by wdzieczny on 2009-09-27
[FONT=Arial]You could try adding this command to your boot Parameters options:    	[/FONT] 	 	 	 	 	  [FONT=Nimbus Roman No9 L, serif][FONT=Arial]```
linux resolution=1024x768 noprobe
``` It will boot into 1024x768 without probing for your video driver. Is this a new problem or has it always done this? [/FONT]
[/FONT]

---

### Post by argos3016 on 2009-09-27
Thanks. It works

---

