---
title: "Weird Panel Icons in Ubuntu 18.04"
date: 2018-05-20
forum: Desktop Environments
---

### Post by rupam-bezbarua on 2018-05-20
Hi,

I have some weird looking panel icons resembling refresh buttons in Ubuntu 18.04 running gnome shell. I can't click on them but they keep on piling up for some reason. I am not sure what's causing them but I was playing with gnome shell extensions earlier and started noticing them. If I log off, they disappear but start piling up after sometime of working on the PC. I am attaching a screen-shot for reference. I searched but do not seem to find anyone else facing a similar issue. Any help is greatly appreciated. 

Thanks,
-Rupam

---

### Post by deadflowr on 2018-05-20
What extensions have you installed/played with?
(You can look in Tweaks to see. It looks like you have Tweaks installed.
Is that Tweaks two over to the right of VLC in the dock?)

---

### Post by rupam-bezbarua on 2018-05-20
Thank you for helping out. I have a number of them installed/enabled. I am sharing the screenshots from Gnome Tweaks for your reference.

Thanks,
-Rupam

---

### Post by Frogs Hair on 2018-05-20
Do you see this with all gnome-shell themes ?

---

### Post by rupam-bezbarua on 2018-05-20
Yes, I just checked by changing the shell themes and I see it with all of them. One thing to note is that if I leave the PC unattended for sometime, the number of those icons increase for some reason. I logged out once and logged back in and see just one now. You should see that in the 3 screens shared earlier.

Again, thanks a lot of helping out.

Thanks,
-Rupam

---

### Post by Frogs Hair on 2018-05-20
You might try disabling all extensions ,  reboot, and enable the extensions you use one by one to figure out which one might be causing the problem. Be sure that the extensions you use are up to date and compatible with 18.04.

---

### Post by kerry_s on 2018-05-20
i think that's the update icon, check in notifications.

you might want to check in terminal:

sudo apt update && sudo apt full-upgrade

---

### Post by rupam-bezbarua on 2018-05-20
I disabled all extensions now, rebooted and still see that icon in the panel. I am really confused on what's going on now. Any ideas?

---

### Post by rupam-bezbarua on 2018-05-20
I ran that command but it didn't fix the issue. It certainly looks like some update icon but not sure what to update. I have all extensions disabled now removed the native host connector as well but that icon is defiant and steadfast:-)

---

### Post by kerry_s on 2018-05-20
you should be careful with extensions, check the web site, click on version make sure your gnome-shell version is supported.

how are you installing extensions?

---

### Post by rupam-bezbarua on 2018-05-20
I go to [https://extensions.gnome.org/](https://extensions.gnome.org/), enable and install. I thought incompatible ones won't install but I could be wrong. With the extensions disabled now, would it matter? Again, I know these are lame questions but can't seem to understand this.

---

### Post by kerry_s on 2018-05-20
what does it show in installed extensions?
[ATTACH=CONFIG]279779[/ATTACH]

---

### Post by rupam-bezbarua on 2018-05-20
Sharing the screenshots of the installed extensions. These are all disabled now but it was taken earlier when someone asked me to share the list of extensions installed.

---

### Post by kerry_s on 2018-05-20
i saw those from your earlier post, i want to know if the browser/web matches up or are they still showing as enabled/disabled?

gnome-tweak is not always accurate, you have to alt+f2, r  to reload gnome-shell or reboot. it also doesn't always show "error" when there is a issue.

---

### Post by rupam-bezbarua on 2018-05-21
Yes, they are disabled both in [https://extensions.gnome.org/local/](https://extensions.gnome.org/local/) as well as under Gnome Tweaks. Have rebooted/logged-off a couple of times as well to verify. Any thoughts?

---

### Post by kerry_s on 2018-05-21
i still think it's a messed up extension not compatible with your gnome version & it's still running a startup.
[ATTACH=CONFIG]279785[/ATTACH]
you should check each 1, if it does not say at least 2.24-> 3.28 you need to remove it, ubuntu is on gnome-shell 3.28, but i've had no problems with extensions that are at least 3.24.

you sure that top panel is part of gnome, cause it looks like tint panel to me?

---

### Post by rupam-bezbarua on 2018-05-22
You were right - It was infact a rogue weather extension that was causing it. I disabled it and it is working now. Thank you so much for all your help. Appreciate it.

---

