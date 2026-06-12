---
title: "titlebar disapears when using desktop effects"
date: 2009-03-27
forum: Desktop Environments
---

### Post by sheshdd on 2009-03-27
whenever i enable desktop effects,be it "normal" or "extra",i lose the whole titlebar,including the close/maximize/minimize buttons.i tried installing compiz config,but it's still not working.
what could it be...

---

### Post by Lunx on 2009-03-27
Have you got the compiz settings manager installed?

---

### Post by kaibob on 2009-03-27
I had that same problem, but it went away when I switched to a different theme. You may want to give that a try.

---

### Post by sheshdd on 2009-03-27
i did install the compiz manager and the settings app,but still no titlebar.i tried switching themes,but the problem won't go away :\

---

### Post by FraggedLocust on 2009-03-27
I believe this problem is caused by compiz and/or the nvidia 177 driver. the workarounds for this are:

-switch to the metacity compositor
```
sudo metacity --replace
```

-upgrade nvidia driver to 180.xx
-switch titlebars to clearlook

---

### Post by sheshdd on 2009-03-27
still no titlebar

---

### Post by Therion on 2009-03-27
```
compiz --replace
```

Check CCSM to be sure the **Window Decorations** plugin, under the "Effects" section, is enabled.

---

### Post by sheshdd on 2009-03-27
it's all enabled,should be working i guess.damn

---

### Post by sheshdd on 2009-03-28
ok,fixed it,a guy from the irc told me to do this
> 
 To fix your compiz window decorations (titlebars) with an NVIDIA graphics card, run « sudo nvidia-xconfig --add-argb-glx-visuals -d 24 », then restart !X.

worked like a charm 

people,check out the #compiz-fusion channel at freenode network,fast answers

---

### Post by natrik on 2009-05-06
> **sheshdd said:**
> 

**[FONT="Courier New"][SIZE="3"][COLOR="Green"]sudo nvidia-xconfig --add-argb-glx-visuals -d 24[/COLOR][/SIZE][/FONT]**

...  Then restart X!

AHH!!! YAY!  I had this same problem when I did the 8.04 -> 8.10 upgrade (hardy to intrepid)... But that was a while ago, and I forgot the fix.  
Now the same thing with 8.10 -> 9.04.  

This fix worked last time, and it's what fixed it just now too.   

OMG Thank you!

-- Nate

---

### Post by jesterthejedi on 2009-05-14
Thank you! After 3 hours of fussing this was the trick I needed. So much junk on this forum didn't point to the right fix. I'm def saving this thread.

---

### Post by buddhi on 2009-05-16
> **sheshdd said:**
> still no titlebar

Please check Following link!

[http://www.pendrivelinux.com/ubuntu-desktop-effects-fixing-the-missing-titlebar/]("http://www.pendrivelinux.com/ubuntu-desktop-effects-fixing-the-missing-titlebar/")

---

### Post by TaskmasterC on 2010-06-13
I just had to do the same thing to mine, but it is not saving it. I fI shut the computer down, I have to do it all over again. Any advice on how to save it?

---

