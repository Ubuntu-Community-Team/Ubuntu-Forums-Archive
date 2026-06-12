---
title: "can't move windows anymore"
date: 2011-08-10
forum: Desktop Environments
---

### Post by vanspud on 2011-08-10
Hi,

ubuntu 11.04, sony vaio laptop

I was messing around with trying to install themes and I must have knocked something important in compiz settings as now I am unable to move my windows around on my desktop. 

Now whenever I open an application, however it opens I can't move it.

Any idea's how I can enable window movement again?

Many thanks.

---

### Post by HiFlight on 2011-08-10
> **vanspud said:**
> Hi,

ubuntu 11.04, sony vaio laptop

I was messing around with trying to install themes and I must have knocked something important in compiz settings as now I am unable to move my windows around on my desktop. 

Now whenever I open an application, however it opens I can't move it.

Any idea's how I can enable window movement again?

Many thanks.


I think it is inherent in Unity in 11.04 as I have the same problem.  I solved it by using Classic desktop.

---

### Post by vanspud on 2011-08-13
I did switch to classic desktop and couldn't move windows. Running "unity" from terminal fixed it and now I can move the windows again.

---

### Post by N1GHTS on 2011-08-13
I had this happen to me like a *million times* since its very easy to break the **Compiz** settings so this is how to get it back to normal:

Type "**ccsm**" in a terminal; Alternatively use **_System_ / _Preferences_ / _CompizConfig Settings Manager_**. Then click the **Preferences** Tab, then click the "**Reset to Defaults**" button.

Ideally you should ***Export*** your **Compiz** settings when you are happy with your settings so you can **Import** them in emergencies, but the default is a great *fall back plan*.

The reason _your solution worked_ was because the **Compiz** settings were being set to the *defaults* for **Unity** and **Ubuntu Classic**, so it naturally undid your messed up **Compiz** settings. So it only got fixed by accident.

---

### Post by HiFlight on 2011-08-13
> **HiFlight said:**
> I think it is inherent in Unity in 11.04 as I have the same problem.  I solved it by using Classic desktop.


I finally got my issue fixed...I needed to go into the compiz menu and uncheck and recheck "Windows  Decoration" and suddenly the title bars reappeared on my open child windows when running unity.   Everything was always normal in classic mode.

---

### Post by wascrash on 2011-08-28
> **N1GHTS said:**
> I had this happen to me like a *million times* since its very easy to break the **Compiz** settings so this is how to get it back to normal:

Type "**ccsm**" in a terminal; Alternatively use **_System_ / _Preferences_ / _CompizConfig Settings Manager_**. Then click the **Preferences** Tab, then click the "**Reset to Defaults**" button.

Ideally you should ***Export*** your **Compiz** settings when you are happy with your settings so you can **Import** them in emergencies, but the default is a great *fall back plan*.

The reason _your solution worked_ was because the **Compiz** settings were being set to the *defaults* for **Unity** and **Ubuntu Classic**, so it naturally undid your messed up **Compiz** settings. So it only got fixed by accident.

Thank you so much for this. I just installed Ubuntu 2 days ago and have not a clue about linux. I did the same thing.Downloaded an app from software center to get that cube desktop lol. well it didn't work and when i tried to go back I could not move my open windows and the top of them were gone. Unity worked fine but I don't like it. I like the classic. I didn't have any compiz on preferences so I tried the terminal like you said and it told me what to type to install compiz config. After that I reset to defaults and rebooted and worked like a charm .....Thank you.

---

### Post by mrincredible on 2012-01-04
I had the same problem in 11.04 after switching to "Classic Desktop". I had to run ccsm and tick the "Move Windows" option.

---

### Post by simptechmike on 2012-02-05
> **mrincredible said:**
> I had the same problem in 11.04 after switching to "Classic Desktop". I had to run ccsm and tick the "Move Windows" option.

This is exactly what fixed this issue for me. Just wanted to add that the "Move Windows" option is under "Windows Management" in CompizConfig Settings Manager (CCSM)

---

