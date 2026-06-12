---
title: "KDE converion has one or 2 bumps"
date: 2006-10-07
forum: Desktop Environments
---

### Post by RudolfMDLT on 2006-10-07
Hi there,

Converted to KDE a while back but having a couple of issues:

1) There is no display config gui, I have a mate who has KDE and he has looked every where but not even he can find it. How can I add it? I need to be able to change my resolution. I can chnge it via console but it bugs me that some "things" are missing.
2) Where is the administrator mode button?
3) I'm running a couple of apps in the background, Amarok, Kopete, SKype. Is it normal for KDE to be using 941mbs of RAM for just basic stuff like this?
4) If your using a cool theme please post the name of it! :D 
5  The printscreen button doesn't want to work! I've tried using a keyboard remapping program but it will only allow remapping of my special keys! How kan I bind a key to a certain command? I know what the command for print screen is, I just need the to find the config file.
5) I have an annoying error at startup. 
[http://ubuntuforums.org/showthread.php?t=270925](http://ubuntuforums.org/showthread.php?t=270925)
 I linked the startup thing because i don't want to scare people off! :)

I know it's a long list but please help me! Really, even if you don't know any answers just post your theme name or a smiley! :rolleyes: 

Further than this, KDE Rocks! I really love it!

Thanks a lot for any help in advance!

Cheers,

Rudolf

---

### Post by jISh on 2006-10-07
1) Look for "Kcontrol". If all else fails, Alt+f2 and write in *kcontrol*.
2) There is no "admininstrator mode". If you need something with root access, you can prefix the command with "kdesu".
3) Linux uses a lot of RAM, different DEs have different ways of managing it and mixing it with your swap space, use the "free" command in a terminal to see your real stats.
4) Check [http://www.kde-look.org](http://www.kde-look.org). I'm using Milk, see attached thumb.

KDE does rock :)
Good luck.

---

### Post by RudolfMDLT on 2006-10-07
Thanks! But as I said, there is nothing under anywahere about Display or resolution. Youre desktop looks great! Thanks!

---

### Post by kerry_s on 2006-10-07
Most everything your looking for is in kcontrol(or> Kmenu>settings>control center).

1.  kcontrol> Peripherals
2. I use run command> kdesu konqueror /  <or> Go to [http://kde-apps.org/content/show.php?content=41801&PHPSESSID=6e26ccb2447714ae4ce4a42cdc021f98](http://kde-apps.org/content/show.php?content=41801&PHPSESSID=6e26ccb2447714ae4ce4a42cdc021f98) and grab that then as root copy it to > /usr/share/apps/konqueror/servicemenus <then you'll have a right click menu open root konqueror.
3. Those are memory intensive apps
4. I'm just running the stock icons and kwin-style-powder from the repos.
5. kcontrol> regional & accessibilty>keyboard shortcuts> Command shortcuts tab> graphics> ksnapshot < now click the "none" button at the bottom, a window will open press the keys you want to use, then press apply.
6. I'll answer that one on the other post.

---

### Post by der_joachim on 2006-10-07
> **RudolfMDLT said:**
> Hi there,
3) I'm running a couple of apps in the background, Amarok, Kopete, SKype. Is it normal for KDE to be using 941mbs of RAM for just basic stuff like this?


I have a fully pimped KDE desktop running @90 megs. This includes a Yakuake console in the background and two Superkaramba widgets. Amarok is heavy, but not *that* heavy. IMHO, both Thunderbird and Firefox are memory hogs. Thay have very long startup times as well. 

> 
5  The printscreen button doesn't want to work! I've tried using a keyboard remapping program but it will only allow remapping of my special keys! How kan I bind a key to a certain command? I know what the command for print screen is, I just need the to find the config file.


xmodmap.conf? :-k

---

### Post by kerry_s on 2006-10-07
I forgot you can also add keybindings via> right click kmenu>menu editor < click on the app you want bind to keys and press the none button and then the keys you want to use.

I use the win+print to take screenshots.

---

### Post by aysiu on 2006-10-07
Maybe [this](http://ubuntuforums.org/showthread.php?t=232259) will help.

---

### Post by RudolfMDLT on 2006-10-07
Guys! Thanks a lot! sorted! I'll try adding the display manager from the web like you said kerry_s! Thanks a lot for all the trouble that you went to! Works like a charm!

der_joachim, 90mb's? Thats effcient! You where right, firefox and them are really ram eaters! I'll see what i can find! I can't find the file you said to find. :) Thanks allot though!

aysiu, Thanks a lot! - I'll look into your KDE-core idea! 

Thanks for all the detail and help people! I really apreciate it!

---

### Post by RudolfMDLT on 2006-10-07
Totally off the piont - here's what I've done so far with the desktop!

---

