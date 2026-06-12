---
title: "Klipper does not want to &quot;autostart&quot; in Gnome panel..."
date: 2009-05-08
forum: General Help
---

### Post by Cezy on 2009-05-08
I am using Klipper even on Gnome as it's the best clipboard-manager I found, but I have to start it manually every time I log in my account.
There is a way to make it to start automatically? Thank you.

PS: I have this problem on every version of Ubuntu.

---

### Post by geirha on 2009-05-08
Have you added it to System -> Preferences -> Sessions ?

---

### Post by Cezy on 2009-05-08
> **geirha said:**
> Have you added it to System -> Preferences -> Sessions ?

Yes, I tried but it doesn't work :(
(I already use System -> Preferences -> Sessions to kill PulseAudio ;) )

---

### Post by Cezy on 2009-05-13
Any idea? :confused:

---

### Post by geirha on 2009-05-13
Not sure why that won't work, but we can see if we can figure out why. Make sure klipper is set to start during login in Sys.->Pref.->Sessions. Then log out (if you are currently logged in) and log in. Edit .xsession-errors by hitting Alt+F2 or run a terminal and run ```
gedit ~/.xsession-errors
``` Do you see any error messages regarding klipper?

---

### Post by stinkeye on 2009-05-13
Dont know what you want in a clipboard manager but you could try
parcellite in the universe repos.

---

### Post by Cezy on 2009-05-15
@stinkeye
Klipper is better ;)

@geirha
I will try, thank you :D

@all
Thank you ):P

---

### Post by Cezy on 2009-05-18
I tried to put it in system->preferences->sessisons, it works on 9.04! :confused:

It did not work the previous versions!!! :confused:

---

