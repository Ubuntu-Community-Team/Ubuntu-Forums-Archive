---
title: "Finally a &quot;Howto&quot; to install the extra plugins in compiz fusion"
date: 2007-11-21
forum: Desktop Effects &amp; Customization
---

### Post by RSingh on 2007-11-21
For the past 3 weeks i have been trying to install the extra plugins like the screensaver and snow ones. I came across this post today and it worked perfectly for so i am sharing it.
This guide does not require one to compile the entire package, only the plugins need to be compiled.

Just take care to use "sudo" when doing "make install".

The command sequence should be:

make
sudo make install

[URL="http://forum.compiz-fusion.org/showthread.php?t=5303"]
http://forum.compiz-fusion.org/showthread.php?t=5303[/URL]

Cheers!:guitar:

---

### Post by vampire666eng on 2007-11-21
Thanks a lot for the link.

I was just wondering that at one point it says:

"2) You already have Gutsy's default compiz working (0.6.1)."

Then I look to "System--->Preferences--->Advanced DeskTop settings--->Preferences--->About CCSM" and it says Compiz Config Setting Manager 0.5.2

So I have compiz fusion 0.5.2 and not 0.6.1? I made a fresh install of uBuntu 7.10 (Gutsy).

---

### Post by RSingh on 2007-11-22
Yeah thats what i actually also thought before, but it seems that ccsm is the old version while the compiz that is installed is the latest one (0.6.1)

you can check the version by typing this in the terminal:

[HTML]compiz --version[/HTML]

Check the last line of the output. If it says 0.6.1 then you can install these plugins

---

### Post by vampire666eng on 2007-11-22
Yep. Thanks. 0.6.1 version. :)

---

### Post by meindian523 on 2007-11-22
Um,I'm using Feisty.....compiz version 0.5.5(found using compiz --version)...which repo do I use to upgrade?

---

### Post by Onay on 2007-11-22
Awesome link. I just made a quick script that does most of the plugins that I think people would want, plus this helped me a lot. Great job

---

### Post by patryk77 on 2007-11-22
i can't get the snow plugin to work...

i also don't seem to have any of the textures

where can i get those?

---

### Post by mrmiserable on 2007-11-22
patryk



```
i can't get the snow plugin to work...

i also don't seem to have any of the textures

where can i get those?
```


[http://forum.compiz-fusion.org/showthread.php?t=208](http://forum.compiz-fusion.org/showthread.php?t=208)

the snow .tgz in this thread has textures and how to make them work

---

### Post by santiagoward2000 on 2007-11-23
Hey, I've installed them a couple of days ago, and they work quite well (and look awsome! :) )
But I'm having a problem. If I click on **Quit** to turn my computer off, restart it or whatever, while **freewins** is enabled, my desktop dims as usual, but the window with the buttons never shows up. I know the window is there, because randomly clicking I got to click on Log Out, but I can't see it.
Has anyone else experienced this problem?

---

### Post by anubis3000bc on 2007-12-22
No but my log out window does come up kinda slow now and my freewins doesn't work at all.

---

### Post by santiagoward2000 on 2007-12-22
> **anubis3000bc said:**
> No but my log out window does come up kinda slow now and my freewins doesn't work at all.

Hmm... I'm starting to think my problem has something to do with XGL...
What do you mean by "doesn't work at all"? Could you compile it?
I think in this page they forgot to mention that, before making:
```
make
make install
```
for **Freewins**, you have to do:
```
make clean
```

You can read this thread for a complete how-to:
[http://ubuntuforums.org/showthread.php?t=602062&highlight=freewins]("http://ubuntuforums.org/showthread.php?t=602062&highlight=freewins")

---

### Post by rainwalker on 2007-12-22
Using these extra plugins won't mess up Compiz Fusion, right? Like interfering with updates or anything?

---

### Post by santiagoward2000 on 2007-12-22
> **rainwalker said:**
> Using these extra plugins won't mess up Compiz Fusion, right? Like interfering with updates or anything?

No, there are no problems like that. These plugins don't change Compiz's package. Updates will still work.

---

### Post by rainwalker on 2007-12-22
> **santiagoward2000 said:**
> No, there are no problems like that. These plugins don't change Compiz's package. Updates will still work.

Alright, thanks :)

---

### Post by santiagoward2000 on 2007-12-22
> **rainwalker said:**
> Alright, thanks :)

You're welcome!

---

### Post by rainwalker on 2007-12-23
> After unpacking 111MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Um...what's this all about?

---

### Post by Dark_X on 2007-12-23
You need to put your installation cd in.

---

### Post by rainwalker on 2007-12-23
Why?

---

### Post by Dark_X on 2007-12-23
I think there are files on there that it needs.

---

### Post by Islington on 2007-12-23
awesome, I still dont see the use of freewins though.

---

### Post by BobCFC on 2008-01-08
> **Islington said:**
> awesome, I still dont see the use of freewins though.


Best I saw was a transparent Terminal with no borders set to lean back so the text looked like the Star Wars intro!

If you install xfce4-terminal you can disable the borders/scroll bars

---

### Post by anubis3000bc on 2008-04-28
anybody know where i can download freewins plugin cause mines not working again.

---

### Post by Lord Xeb on 2008-04-28
[Link]("http://ubuntuforums.org/showthread.php?p=3701101")

---

### Post by anubis3000bc on 2008-04-28
ok i'll try what you said, only thing i can tell you that freewins is still checked even after restart so i know it is on just missing something.

---

### Post by anubis3000bc on 2008-04-28
freewin still not working lol it crashed my ubuntu twice when i try to use flat file and when i try to change the buttons.

---

