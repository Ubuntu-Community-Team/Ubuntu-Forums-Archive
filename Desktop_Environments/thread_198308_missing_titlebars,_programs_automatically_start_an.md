---
title: "missing titlebars, programs automatically start and more, oh my..."
date: 2006-06-17
forum: Desktop Environments
---

### Post by gbinal on 2006-06-17
So this one confuses me.  I believed a few days ago, when I clicked to save my session and either restart or hibernate.  From then on, whenever I logged in with GNOME (though not into GNOME-failsafe), a few programs (gaim, a certain file folder, and my notes program) automatically open but they and every other program that I load later are sans titlebar. 

[IMG]http://gbinal.googlepages.com/Screenshot-2.png[/IMG]

 Also, windows in the background cannot come to the foreground without closing the programs on top.  

Rebooting without the session saved doesn't help. Neither does (yes, I am a silly newbie) hard rebooting. 

Am using U 6.06 (though the problem began with 5.10 and stayed with me during the upgrade) on an older toshiba laptop.  If more/other specs would be helpful, please let me know.  

Thanks for any advice or help.  As a struggling, but believing neophyte, I am grateful to you all.  Peace,

[Note, this post is repeated from the Breezy section, partly b/c no one was replying]

---

### Post by bluevoodoo1 on 2006-06-17
Hmm. Strange. Here's an idea. When these windows without title bars popup, iIf you can get to a terminal perhaps this command may help...

```
nohup metacity --replace &
```

---

### Post by x64Jimbo on 2006-06-17
I've seen very similar symptoms in KDE when kwin gets killed or crashes. I'm not sure what the gnome equivalent would be, but it's worth looking into.

---

### Post by gbinal on 2006-06-18
[QUOTE=bluevoodoo1]Hmm. Strange. Here's an idea. When these windows without title bars popup, iIf you can get to a terminal perhaps this command may help...

```
nohup metacity --replace &
```[/QUOTE]


Bluevoodoo - Thank you!  I'll leave it at that.  Anyhoo, that fixed the problem and I'm able to use regular, not failsafe gnome easily again.

Jimbo, it didn't come to that, but thank you for the word.  

Peace, folks, and have a good day.

---

### Post by slinky on 2006-06-18
i also had that a while back and i pressed alt down and left clicked on the top bar and it came back. just a thought

---

### Post by RoNoVe on 2006-06-18
x64Jimbo: Metacity is the window manager in gnome, just so you know it ;)

---

### Post by xinelo on 2006-08-20
Thank you so much!
xinelo

---

### Post by leakleakleak on 2007-09-10
Hi There! I want to say thank you! I would like to confirm that this problem also arose on a Toshiba P105 running Sabayon Linux 3.4 running GNOME and compiz & beryl with Emerald. 

Typing the following fixed the problem immediately:
nohup metacity --replace &

Thank you!
Leak
:guitar:

---

### Post by leakleakleak on 2007-09-10
As a qualification to my last comment, although that command (nohup metacity --replace &) did bring my toolbars back, I found that all other features of compiz & beryl stopped working immediately. When I restarted my computer, the toolbars were still gone (with cube and other fancy features working just fine), and then when I typed the nohup command, everything else stopped working again.

Any ideas?
Thanks!
Leak

---

### Post by pkcs11 on 2007-09-24
The nohup solution only runs metacity, switching from beryl/compiz to metacity as a window manager.

It does certainly return the titlebars though! :)

---

### Post by giosico on 2007-12-25
The reason compiz stops working is because when you type that command you switch from using compiz to metacity ... 

instead type
compiz --replace
or similar as described earlier ...

my problem does not happen at login, it does not stick if I reboot, and I am not sure what is causing it yet ... but it seems intermittent ... 

so if anyone has any ideas of how this is caused or even better how to fix it ... that would be great.

oops it looks like the last reply basically said the same thing as this one

---

