---
title: "Where does minimized windows go?"
date: 2011-08-16
forum: Desktop Environments
---

### Post by googleye on 2011-08-16
Still new here so sorry if I've posted this wrong.

Just wondering what happends to minimized windows? If i click it in unity it just opens a new one(Chrome can be used as an example here).

---

### Post by sanderd17 on 2011-08-16
A minimized window goes to the unity bar in the default configuration. You need to mid-click or right-click to open a new instance.

It seems like your settings are changed for some reason, or that the program isn't minimised but closed.

Can you install ccsm (in the software center) and look into the Unity settings? Please do not edit other settings. Most settings destroy the desktop and you need to go via command line to restore everything (Unity shouldn't be released yet, it's still buggy).

What happens if you don't minimize the window, but just bring another one in front of it? 

Like:

[LIST]
[*]Open chrome
[*]open firefox
[*]maximize firefox if needed
[*]click on the chrome button in the unity task bar
[/LIST]

Does it now opens a new instance of Chrome or not?

---

### Post by googleye on 2011-08-16
Yes, that opens a new instance of Chrome. But I'm pretty sure that open programs get an arrow next to their icon in unity? And I haven't altered any settings. 

I have no idea what ccsm is but a search for it in the software center brings upp a settings manager for windows and stuff, I already have it, but I can't find any settings for unity.

---

### Post by sanderd17 on 2011-08-16
So you have CCSM installed and you don't know why? I think this is weird.

Normally CCSM should have a separate icon for Unity settings. You should also get there by pressing ALT+F2 and executing "about:config" (without quotes).

Can you try resetting the CCSM settings? Open up a terminal and do
```

gconftool-2 --recursive-unset /apps/compiz-1
unity --reset

```

And log out and back in afterwards.

---

### Post by googleye on 2011-08-16
I might have it installed because a friend of mine installed Compiz(don't know if it's named the same in every language), they're related, right? Although for some reason it dissapeared after the update, haven't installed it since.

After entering unity --reset i got loads of lines i didn't get and what I only can describe as explorer in windows dissapeared. However two windows that I had minimized earlier showed up. One could be closed but the other one lacks the upper row of buttons(minimize, close etc). I'll have to shut down through the power button and boot it up again.

---

### Post by sanderd17 on 2011-08-16
> **googleye said:**
> I might have it installed because a friend of mine installed Compiz(don't know if it's named the same in every language), they're related, right? Although for some reason it dissapeared after the update, haven't installed it since.


Unity uses Compiz for it's effects, so Compiz is always installed. But CCSM is one of the settings editors.

> 
After entering unity --reset i got loads of lines i didn't get and what I only can describe as explorer in windows dissapeared. However two windows that I had minimized earlier showed up. One could be closed but the other one lacks the upper row of buttons(minimize, close etc). I'll have to shut down through the power button and boot it up again.

Ok, let's hope it is fixed after reboot.

---

### Post by googleye on 2011-08-16
Well, after rebooting it all works as it should and minimized windows now go straight to unity as you said. Plus alt+tab now works, since it didn't before I just assumed ubuntu didn't have that shortcut.

Thank you very much for your help, loving the speed in ubuntu, not just the OS but in the forums aswell :)

If I might I'd like to ask something off-topic since the thread is solved. How is LibreOffice? So far I've been using Docs but it would be nice to have a local program to work with for those horrible moments without an internet connection. OK to use for someone with lots of Office experience?

---

### Post by sanderd17 on 2011-08-16
> **googleye said:**
> Well, after rebooting it all works as it should and minimized windows now go straight to unity as you said. Plus alt+tab now works, since it didn't before I just assumed ubuntu didn't have that shortcut.

Thank you very much for your help, loving the speed in ubuntu, not just the OS but in the forums aswell :)

No problem, glad I could help you. Btw, I don't use Ubuntu anymore, but I stay on the forums to help.
> 
If I might I'd like to ask something off-topic since the thread is solved. How is LibreOffice? So far I've been using Docs but it would be nice to have a local program to work with for those horrible moments without an internet connection. OK to use for someone with lots of Office experience?

I don't use office programs a lot (I prefer markup languages like LaTeX for documents and presentations), but there is not much difference from OpenOffice.org yet. They support the Office format a bit better, and there are some other tweaks, but really nothing big.

I have seen some users call it superior to MS Office if you learn to work with it how it is meant. But I really don't know since it's 4 years ago that I worked the last time with Word 2003 and about 2.5 years ago that I worked with OpenOffice (I mean working, not quickly testing).

Don't forget to mark the thread "solved".

---

### Post by googleye on 2011-08-16
I'm sure it will be enough when Docs aren't available, thanks again, marked as SOLVED.

---

