---
title: "World of Warcraft help!"
date: 2008-09-17
forum: Gaming &amp; Leisure
---

### Post by Alfx on 2008-09-17
-I copied my World of warcraft installation in unbuntu

When I try to run wow through the terminal through wine.

This is the errors I get:

wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000005

What does that means and how do I fix it?

---

### Post by Alfx on 2008-09-17
-I copied my World of warcraft installation in unbuntu

When I try to run wow through the terminal through wine.

This is the errors I get:

wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000005

What does that means and how do I fix it?

---

### Post by Alfx on 2008-09-17
> **Alfx said:**
> -I copied my World of warcraft installation in unbuntu

When I try to run wow through the terminal through wine.

This is the errors I get:

wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000005

What does that means and how do I fix it?
Anyone???

---

### Post by Alfx on 2008-09-17
Anyone???

---

### Post by karlr42 on 2008-09-17
Have patience. And don't keep posting the same thread, if people know a solution, they'll respond to your original thread.

---

### Post by Woody1987 on 2008-09-17
opengl32.dll is the problem from the looks of it, what graphics card do you have? and do you have the drivers installed?

---

### Post by Alfx on 2008-09-17
> **Woody1987 said:**
> opengl32.dll is the problem from the looks of it, what graphics card do you have? and do you have the drivers installed?


I have an ATI radeon 4870.

I installed the drivers 8-6(manual) with EvnyNG

EDIT: When I go into System -> Administration -> hardware drivers, I see the drivers, their status is "In use"
Must I check the box next to it or?

---

### Post by binbash on 2008-09-17
> **Alfx said:**
> I have an ATI radeon 4870.

I installed the drivers 8-6(manual) with EvnyNG

EDIT: When I go into System -> Administration -> hardware drivers, I see the drivers, their status is "In use"
Must I check the box next to it or?

If you want to use ati's , nope dont check it.

---

### Post by Alfx on 2008-09-17
> **binbash said:**
> If you want to use ati's , nope dont check it.
Thanks

But now how do I fix that opengl32.dll problem?

---

### Post by dagoth_pie on 2008-09-17
Hey there, have a read through this
[http://ubuntuforums.org/showthread.php?t=579378&highlight=wow+wine](http://ubuntuforums.org/showthread.php?t=579378&highlight=wow+wine)
theres part of it where you edit a text file to tell it to run it under opengl instead of directX
Hope this helps, and also, you may want to go into system/preferences/sound, and change the default mixer track to one of the ones with "playback:" at the start of it, so far with all my friends machines, this has fixed up problems with having multiple applications playing sounds at the same time, and i think part of your error message was telling you this

---

