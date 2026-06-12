---
title: "Text To Speech Time On New KDE 4.3 Beta"
date: 2009-06-10
forum: Desktop Environments
---

### Post by zenarcher on 2009-06-10
This may be a function not fully working as of yet, but I thought it is worth asking.

I have all the latest KDE updates installed and there is an option for setting the time so you get an audio time announcement every minute, two minutes, etc.

I have set that up in the digital clock settings.  Likewise, I've installed the required ktts packages.  I do hear a sound at the minute, ten minutes or whatever I've set, but it's just a short sound and not the actual time.  I'm wondering if anyone else has tried to use this function.  Possibly I don't have something configured properly, or perhaps the entire KDE package is not yet working properly, so just wondered if anyone else has tried or has any ideas.

Thanks,
zenarcher

---

### Post by Stonerocker on 2009-09-08
Hi zenarcher.
For me the same on KDE 4.3. I only hear something strange that sounds a little like "it is" maybe. Unfortuntately I cannot switch this text-to-speech function off anymore. So my computer is now telling "it is" every 5 minutes or so. Deinstalling the kttsd package leads only to an error message whenever the kttsd would be activated.
Did you manage to disable the function again? How did you do?
Thanks, Stonerocker

---

### Post by krazyd on 2009-09-08
I think text-to-speech is still experimental. To disable:
Right click Clock > Digital Clock Settings > General > Speak Time
Decrease this value until it says "Never".

---

### Post by Stonerocker on 2009-09-09
Thanks. That's actually what I tried first. The speak time value has no effect on the speech output. I tried "60 minutes" and "Never" and I hear the sound every 5 minutes.

---

### Post by Stonerocker on 2009-09-11
Hi everybody,
now I updated to KDE 4.3.1 but the problem still exists. 
Is it only me who has this problem? Did someone test to switch the text-to-speech function of the digital clock on and off again? Or maybe does someone have an idea how I can solve this?

---

### Post by krazyd on 2009-09-11
that's weird - I'm on 4.3.1 and set mine back to "Never" and the sound disappeared.

Maybe try playing with the settings again? or uninstall the festival package? (festival provides the text-to-speech function)

---

### Post by Stonerocker on 2009-09-11
You are the best.
I deinstalled fetival and three of its dependencies. After that the sound stopped and no error messages were appearing. I even reinstalled festival again and now everything works without annoying disturbances.
Thanks alot!

---

### Post by Stonerocker on 2009-09-12
You have to keep festival uninstalled. Otherwise the sound will start after reboot.

---

