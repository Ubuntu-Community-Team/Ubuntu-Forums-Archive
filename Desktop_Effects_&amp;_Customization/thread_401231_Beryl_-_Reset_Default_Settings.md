---
title: "Beryl - Reset Default Settings"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by mjhasbach on 2007-04-04
Kind of a noob question, but how would I go about resetting all of the Beryl settings that have to do with Beryl Manager and Beryl Settings manager to the default settings? I would need to do this without opening Beryl Manager, as a mistake that I made in configuring it causes it to freeze when it is loaded. TIA.

---

### Post by Stickymaddness on 2007-04-04
Right click the Beryl Icon->Window Manager-> Set your window manager to your default window manger eg: Metacity 

Then you should be able to start the Settings manager since it won't have loaded Beryl. 

Hope this helps.....

---

### Post by mjhasbach on 2007-04-04
Well...heres my problem. Once I run Beryl (i.e. Beryl Manager) my computer freezes because I changed some Xgl option; however, I can open Beryl Settings Manager with no problems. So I need some way to reset the defaults without opening Beryl manager.

---

### Post by dhaus111 on 2007-04-09
run this:

[CODE]metacity –replace &[CODE]

from a virtual terminal.  should replace beryl with metacity

I'm on a hunt right now for resetting all beryl settings to default, but my setup doesn't cause everything to crash

i'll post what i find out if anything

---

### Post by dhaus111 on 2007-04-09
you need to go into your home folder and delete the .beryl dir and .beryl-managerrc file.  then reboot or relogin and restart beryl-manager

---

### Post by Nooi on 2008-03-06
Thanks dhaus111 .I've got that problem too.
You hel me a lot.

---

