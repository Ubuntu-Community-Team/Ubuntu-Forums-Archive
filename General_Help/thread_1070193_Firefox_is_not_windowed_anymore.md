---
title: "Firefox is not windowed anymore"
date: 2009-02-14
forum: General Help
---

### Post by orangesoda on 2009-02-14
My firefox browser is not windowed anymore. It also blocks both of my toolbars. I checked to see if it was in fullscreen mode but it wasn't. I feel that this is a simple fix and I tried fixing it for about 10 minutes and decided to ask here.

here's a screenshot: [IMG]http://i44.tinypic.com/a9u2ja.jpg[/IMG]

Thanks in advance for all the help.

---

### Post by djbushido on 2009-02-14
big screenshot.
try running firefox from the terminal with this command:
```
firefox -height 640 -width 480
``` and see if that helps. It's probably not a permanent fix, but it's a start. Also, what is your system display resolution?

---

### Post by orangesoda on 2009-02-14
it's 1680 x 1050

I tried that command in the terminal and it just opened up another firefox window with the same problem.

---

### Post by Perryg on 2009-02-14
Is this by any chance Kubuntu?

Reason I ask is it looks just like mine when I shut off Borders.
Is so use <alt-f3> and it will open a window to turn them back on.

Under advanced.

I have not seen this on my other flavors of Ubuntu

---

### Post by SonnHalter on 2009-02-14
[SIZE="7"]press F11[/SIZE]

---

### Post by malusdomestica314 on 2009-02-14
Are you by any chance running any Desktop Effects, Compiz Fusion or the like? If so I think I have your answer, Go to the Compiz manager (I think its called the Desktop Effects Manager, or Compiz Fusion Manager, I'm not sure since I'm not on my Ubuntu box right now) It's under System->Preferences. Once you get to the manager go to Utilities->Workarounds and disable Legacy Fullscreen Support, I had the same problem last month and it this seems to have worked for me. Hope it works for you too. I'll try to find some other fixes if it doesn't.

---

### Post by SonnHalter on 2009-02-14
> **malusdomestica314 said:**
> Are you by any chance running any Desktop Effects, Compiz Fusion or the like? If so I think I have your answer, Go to the Compiz manager (I think its called the Desktop Effects Manager, or Compiz Fusion Manager, I'm not sure since I'm not on my Ubuntu box right now) It's under System->Preferences. Once you get to the manager go to Utilities->Workarounds and disable Legacy Fullscreen Support, I had the same problem last month and it this seems to have worked for me. Hope it works for you too. I'll try to find some other fixes if it doesn't.

YES YES YES that was what i meant to say. Had the same problem about a year ago

---

### Post by orangesoda on 2009-02-15
okay I tried all of the suggestions and at first none of them appeared to work.

So I got really annoyed and held down my f11 key and noticed that the top toolbar was covering the window bar. Thanks for all the help.

---

### Post by tuskenraider on 2009-02-15
> **SonnHalter said:**
> [SIZE="7"]press F11[/SIZE]


do what?? im sorry i missed that.... lol  actually thats very good advice.  IDK why it does that.. but mine does that all the time...  for some blasted reason.. and thats the only way ive found to correct the issue. 


tusken

---

### Post by -kg- on 2009-02-15
OK, here's what you need to do.

If you have Compiz Settings Manager installed, you will be able to launch it under "System/Preferences/Advanced Desktop Effects Settings."  Go to Utilities, and click on "Workarounds."  At the top of the list you will see "Legacy Fullscreen Support."  You want to _uncheck_ the checkbox.

If you don't have ccsm (the short name for the Compiz Settings Manager) installed, you won't find the above under System/Preferences.  In that case, launch Synaptics, do a search for "compiz," and install "Compizconfig-settings" from the list.

---

### Post by malusdomestica314 on 2009-02-15
Thank you, you've put it in a much clearer and more precise way than I did.

---

### Post by newagelink on 2009-02-15
I sometimes have the same issue with this Ubuntu 8.10 live disc; I go to System -> Preferences -> Appearance -> Visual Effects and select "None" (instead of the default "Normal" of the live disc) and that fixes it for me.

It appears you've already received that suggestion. Hope your problem is resolved soon.

---

