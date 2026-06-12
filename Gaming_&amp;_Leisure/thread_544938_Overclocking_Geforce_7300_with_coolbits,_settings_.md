---
title: "Overclocking Geforce 7300 with coolbits, settings won't stick."
date: 2007-09-06
forum: Gaming &amp; Leisure
---

### Post by BeastlyKings on 2007-09-06
I enabled the coolbits overclocking feature in my nvidia control panel and it all worked fine, but then I went too high and the comp froze. I restarted but now whenever I try to raise the frequency, as soon as I hit "Apply" the slider jumps back to stock frequency. Sometimes I can raise it, but most times I cannot.
I uninstalled and then reinstalled the nVidia driver but it still won't work right. How do I fix it? and if it can't be fixed... How do I use nvclock?

---

### Post by hikaricore on 2007-09-06
The Linux nvidia driver is made this way for a reason.  If you mess up, it doesn't stay that way.

Unless you've actually damaged your card in some way (unlikely), the following would be the simple way to keep your settings.

What you need to do is create a bash script like such:

```
#! /bin/bash
nvidia-settings -a GPUOverclockingState=1 -a GPU2DClockFreqs=**xxx**,**xxx** -a GPU3DClockFreqs=**xxx**,**xxx**
```

Find the values that work for you in the nvidia-settings window and make a note of them. 
Then pop them in that script. (in place of the appropriate *xxx*

Toss this script (which is just a text file) in your home directory (or wherever) and make it exectuable via the properties window or **chmod +x filename**.

Add this file to your session startup in under Preferences/Sessions and it will run everytime you login.  ^_^

---

### Post by BeastlyKings on 2007-09-07
I should have mentioned that I tried clocking it by using that exact same script, after I execute the script bash tells me that the values have been updated but when I run  "nvidia-settings -query all" they are the same as before. Also I think it might be worth noting that the highest I can go without the slider resetting itself is 614 on the 3D clock and 828 on the memory clock. After that the slider resets.
Is thefre a way manually clean/clear the prob I have created because re-installing the driver doesn't work anymore (it did the first time)?

---

### Post by hikaricore on 2007-09-07
The settings aren't saved between sessions, nothing should be causing an issue for that reason.

The only thing I can think of is removing:

**.nvidia-settings-rc** (file)

and possibly

**.nvclock**  (folder)

From your home directory.  Otherwise I'm not sure what to tell ya.

---

### Post by BeastlyKings on 2007-09-07
Well I guess thats just how it goes.
Do you know how I could use nvclock? I installed it from synaptic but I don't know how to use it...

---

### Post by hikaricore on 2007-09-07
nvclock is no longer useful since the nvidia setting utility got OC support.

I suggest uninstalling it as that may be causing your problems..

---

### Post by BeastlyKings on 2007-09-07
but could I still use it?
I know what clock frequency's I need/can-handle, I don't need a GUI.
Oh and after uninstalling nvclock I still have the same prob.

---

### Post by PhillipJ on 2007-11-02
this happens to me too (7600GS x2, SLI). I found that it ONLY happens if I forget to change from 2D clocks to 3D clocks before touching a slider. If I accidentally change something while 2D is selected nothing works and I have to reboot (although restarting X might do it too). If i select 3D first all is good. Auto-detect clocks causes the system to lockup though.

---

### Post by ph1 on 2008-01-26
I have the same problem--I can't get my settings to stick using coolbits or nvclock; whatever I change is instantly set back to default, and nvidia-settings returns the default info.  I'm trying to underclock my 7950 Go to save power and reduce heat--I'm not even trying to overclock beyond hardware limitations.  

I've mentioned this in a couple of threads, with no results.  Any help would be appreciated greatly, and if I find anything useful I'll post.

Thanks.

---

### Post by Huzudra on 2008-01-27
i have a 7600GT and am running ubuntu 7.10.

ive edited my xorg.conf and no luck either :confused:  the section i should be seeing isnt showing up.  i dont get it :confused:

---

