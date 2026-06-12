---
title: "Window Manager Ubuntu 10.04"
date: 2010-04-17
forum: Desktop Environments
---

### Post by zjagannatha on 2010-04-17
I upgraded to Ubuntu 10.04 (wiped root partition, so it's a clean install) and I'm having issues with my window manager.

It displays all my windows without the toolbar at the top with the Close, Maximize and Minimize Buttons. (Screen shot below)

It might have something to do with the fact that I used to run Emerald before I upgraded, but I deleted the "~/.emerald" folder and it didn't help.

---

### Post by howefield on 2010-04-17
Do the window decorations return with

```
metacity --replace
```

---

### Post by zjagannatha on 2010-04-17
That turns the toolbars back on, but turns off Desktop Effects.

---

### Post by howefield on 2010-04-17
It is so long since I used Emerald for window decoration.

What does it say in Compizconfig Settings Manager > Effects > Window Decoration >  Command ?

If it references emerald, try changing it to compiz-decorator, eg mine says /usr/bin/compiz-decorator

---

### Post by mcduck on 2010-04-17
> **zjagannatha said:**
> I upgraded to Ubuntu 10.04 (wiped root partition, so it's a clean install) and I'm having issues with my window manager.

It displays all my windows without the toolbar at the top with the Close, Maximize and Minimize Buttons. (Screen shot below)

It might have something to do with the fact that I used to run Emerald before I upgraded, but I deleted the "~/.emerald" folder and it didn't help.

How did you set emerald to run automatically when you installed it? Undo that change and things will start to work agan.

If you added "emerald --replace" to startup comamnds in System/PReferences/Startup Applications, then remove it.

R, if you did it properly and configured Compiz to use Emerald as it's decorator, then open CompizConfig Settings Manager, go to Window Decoration-plugin's settings and set the command to "/usr/bin/compiz-decorator" (or just click the brush icon next to this option to automatically reset it to defaults).

---

### Post by zjagannatha on 2010-04-17
That fixed it, thanks a bunch!

---

### Post by Eredeath on 2010-04-26
I know this thread is a tad old but i'm having the same issue. I never used emerald but did use compiz. I can get the window boarders and desktop effects working but after a re-start I loose the window boarders and desktop effects.Any suggestions on how to keep them on?

---

### Post by zjagannatha on 2010-04-26
Are you using compiz now?

---

### Post by Eredeath on 2010-04-26
yes

---

### Post by Eredeath on 2010-04-26
I figured it out. I had to add Compiz to my startup programs. I didn't have any window managers running at startup.

---

### Post by MrByte1 on 2010-04-30
@Eredeath
  what command did you add to the startup?
  For some reason I keep having the same issue, no title bar after login. I open the Compiz Fusion Icon and do a Reload Windows manager and all is backup to normal.... But I shouldn't have to do this after every login .....
Thanks!

---

### Post by mathfreak123 on 2010-04-30
> **MrByte1 said:**
> @Eredeath
  what command did you add to the startup?
  For some reason I keep having the same issue, no title bar after login. I open the Compiz Fusion Icon and do a Reload Windows manager and all is backup to normal.... But I shouldn't have to do this after every login .....
Thanks!

Hello. I have my windows back to normal after the upgrade by adding a new entry that uses the command ```
/usr/bin/compiz
```

Hope this helps!

---

### Post by MrByte1 on 2010-04-30
Hey thanks!!! That fixed it. I could swear I had tried that, but evidently that wasn't it. Now after Log in, all is it should be ...
Thanks again...

---

### Post by mathfreak123 on 2010-04-30
> **MrByte1 said:**
> Hey thanks!!! That fixed it. I could swear I had tried that, but evidently that wasn't it. Now after Log in, all is it should be ...
Thanks again...

You're welcome! Are you sure you didn't try /usr/bin/compiz-decorator first instead of just /usr/bin/compiz?

---

### Post by MrByte1 on 2010-04-30
> **mathfreak123 said:**
> You're welcome! Are you sure you didn't try /usr/bin/compiz-decorator first instead of just /usr/bin/compiz?

That's quite possible. I tried so many things.....

---

### Post by peterpan7191 on 2010-05-01
even  - 'compiz --replace'  can be added to the startups....

but isnt there ny bettr wrk around ovr this. ??
i simply cant do that bcoz i smtimes boot into kde session (n startup items r shared between sessions donno y it happens like dat)
compiz --replace (or any other compiz related command) there is sure 2 crash the 'kwin'  (window manager 4 kde) ??
hopelessy sad as it is a choice btween my 2 beautiful desktop sessions :( ..

---

### Post by zjagannatha on 2010-05-01
> **peterpan7191 said:**
> even  - 'compiz --replace'  can be added to the startups....

but isnt there ny bettr wrk around ovr this. ??
i simply cant do that bcoz i smtimes boot into kde session (n startup items r shared between sessions donno y it happens like dat)
compiz --replace (or any other compiz related command) there is sure 2 crash the 'kwin'  (window manager 4 kde) ??
hopelessy sad as it is a choice btween my 2 beautiful desktop sessions :( ..

One could theoretically write a simple script that detects if you're using Gnome or KDE, and starts compiz accordingly. I'm not really familiar with Bash, but I'll see what I can dig up.

---

### Post by zjagannatha on 2010-05-01
> **zjagannatha said:**
> One could theoretically write a simple script that detects if you're using Gnome or KDE, and starts compiz accordingly. I'm not really familiar with Bash, but I'll see what I can dig up.

Ok. Here's a simple script that detects if you're using gnome and starts compiz if you are.

You should save it to (for example) ~/bin and add it to the startup programs list.

---

### Post by peterpan7191 on 2010-05-02
thanx a lot ... :)

---

### Post by Xanthomryr on 2010-05-02
Bug report ahoi: [https://bugs.launchpad.net/ubuntu/+bug/563161](https://bugs.launchpad.net/ubuntu/+bug/563161)

---

### Post by naitsirhc on 2010-05-03
Thanks to Christophe Weis responding to the bug reported here:
[https://bugs.launchpad.net/ubuntu/+bug/563161](https://bugs.launchpad.net/ubuntu/+bug/563161)

to fix the issue, you can simply add a symlink to get things working:
sudo ln -s /usr/bin/compiz /usr/bin/compiz.real

Apparently after upgrading to 10.04, the file /usr/bin/compiz.real is missing as Christophe points out is mentioned in syslog.

---

### Post by cudaboy on 2010-05-04
I had a similar issue, but with the Compiz Fusion Icon app I was using with 9.10 and something similar to this fixed it. Old command in the Start Apps was grey (unavailable) so I just removed it and created a new one with the command:
```
/usr/bin/compiz-decorator
```


thanks!



> **mathfreak123 said:**
> Hello. I have my windows back to normal after the upgrade by adding a new entry that uses the command ```
/usr/bin/compiz
```

Hope this helps!

---

### Post by felixq78 on 2010-05-04
I've just upgraded to Ubuntu 10.04 and my window manager icons are on the LEFT HS of the window not on the right as usual. How do I change it back to normal.

---

### Post by mathfreak123 on 2010-05-04
> **felixq78 said:**
> I've just upgraded to Ubuntu 10.04 and my window manager icons are on the LEFT HS of the window not on the right as usual. How do I change it back to normal.

Easiest solution (or it worked for me):
System -> preferences -> Appearance. Select "Human-Clearlooks", then customize based off of that theme.

---

### Post by bancs on 2010-05-05
have a try to turn the toolbars back on, but turn off Desktop Effects.

---

### Post by Xanthomryr on 2010-05-05
> **felixq78 said:**
> I've just upgraded to Ubuntu 10.04 and my window manager icons are on the LEFT HS of the window not on the right as usual. How do I change it back to normal.

As normal user type into the terminal:

gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"

---

### Post by MrByte1 on 2010-05-05
> **cudaboy said:**
> I had a similar issue, but with the Compiz Fusion Icon app I was using with 9.10 and something similar to this fixed it. Old command in the Start Apps was grey (unavailable) so I just removed it and created a new one with the command:
```
/usr/bin/compiz-decorator
```
thanks!


I was also able to solve this by placing the Compiz Fusion Icon in the startup (fusion-icon). It causes a) the Icon to be in the Panel and b) to have it accesible anytime and most importantly c) the windows manager on startup fixes the windows decorator issue.....

---

### Post by milesnapue on 2010-05-09
> **mathfreak123 said:**
> Hello. I have my windows back to normal after the upgrade by adding a new entry that uses the command ```
/usr/bin/compiz
```

Hope this helps!


Perfect, thanks, this fixed my small problem perfectly!

---

### Post by leona on 2010-05-09
> **mcduck said:**
> How did you set emerald to run automatically when you installed it? Undo that change and things will start to work agan.

If you added "emerald --replace" to startup comamnds in System/PReferences/Startup Applications, then remove it.

R, if you did it properly and configured Compiz to use Emerald as it's decorator, then open CompizConfig Settings Manager, go to Window Decoration-plugin's settings and set the command to "/usr/bin/compiz-decorator" (or just click the brush icon next to this option to automatically reset it to defaults).

Oh thank you, thank you , thank you so much, that fixed my problem too, great.

---

### Post by AbeJarano on 2010-11-29
Thanks, that worked for me, also.

---

### Post by noletolucas on 2011-07-03
same problem. :(

[LIST]
[*]doing the "metacity --restart" on console only works while the terminal remains opened.

[*]setting "system -> appearences -> effects -> normal" only works until reboot.
[/LIST]

---

