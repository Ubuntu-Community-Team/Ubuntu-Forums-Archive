---
title: "Beryl problems"
date: 2006-11-07
forum: Desktop Environments
---

### Post by Anonii on 2006-11-07
Greetings!

I know that most of you are not Beryl experts, but I also know, that some people here can help me with these questions because they are probably easy to answer, and I just cant understand the problem. Anyway, let me continue:

A week ago, I installed Beryl. Unfortunately I didnt have the chance to configure it correctly, because I'm having many problems, and I also have lots of studying. My problems:

1) 75% of the times I startup , I'll get stupid window borders. By stupid, I mean, window borders that blink. (dissapearing and after a while appearing and dissapearing instantly). Its really annoying, and it doesnt let me work. I tried restarting Emerald. Adding ```
"Option AddARGBGLXVisuals" "True" 
``` and ```
Option          "TripleBuffer" "true" 
``` to my xorg.conf. Disabling Emerald and Beryl, uninstalling and reinstalling, and then enabling it (That would work for one session.). And i still get this problem >:

2) My windows many times wont refresh. I'll have to switch between other windows to make them refresh. That requires a reboot to temporary fix it. I know that I'm not the only one who has that problem. I've seen other posts in this forum , and in ubuntuforums.org, desribing the same situation.

3) Many times, when I double click a window border to hide the rest of the window, when I try to restore the rest of the window, I'll get my first problem.

4) I cant use the Greek Language. I have it enabled in the GNOME Language Choser, and it works alright in my normal GNOME session, but it wont work in Beryl. It will just input English Character.

5) Less important: If I solve the problems described above, is there an article to get me starting. Or some nice configurations for me to import?

I'm using Ubuntu (GNOME). ATI 9600 with fglrx and direct rendering.
Please if you want something else, like logs or config files, tell me!
[I]
(I also made this post in the official beryl forums, but I got 0 answers after 2days.)[/I]

Thank you!

---

### Post by zgornel on 2006-11-08
Well, beryl is buggy because is still in a (in my opinion) over-rated beta stage. Try compiz - it offers the same features (less configurable though) and is far more stable.

---

### Post by Anonii on 2006-11-08
> **zgornel said:**
> Well, beryl is buggy because is still in a (in my opinion) over-rated beta stage. Try compiz - it offers the same features (less configurable though) and is far more stable.
I see :/

I cant find debs or anything of it :/ Isnt it unsupported, now?
Are there any guides available? For ati fglrx and Edgy?

---

### Post by PriceChild on 2006-11-08
The flickering window borders are because emerald is started twice and they both fight.

I get it too and i wrote the big guide! :P

There's no real reason for triplebuffer as far as i know...

I do a ```
killall emerald
emerald
``` to get rid of the flickering.

Pricey

---

### Post by Anonii on 2006-11-08
Thats great! Thanks, I'll check it out next time I have the same problem (I rarely login into Beryl, tho, because I dont want to risk rebooting.)

Now, I have to solve (2) and I'll have a Beryl that I can , at least, work into.

Here: [http://ubuntuforums.org/showthread.php?t=292142&highlight=refresh+windows](http://ubuntuforums.org/showthread.php?t=292142&highlight=refresh+windows)
[http://forum.beryl-project.org/topic-2447-desktop-doesnt-redraw-refresh-fonts-elusive-titlebars](http://forum.beryl-project.org/topic-2447-desktop-doesnt-redraw-refresh-fonts-elusive-titlebars)
Examples of (2)

btw, have you made a bug report? Should we?

---

### Post by calvinthomas on 2006-11-08
I had this problem but last night I updated to the latest version of beryl (v0.12) and have not had the problem since, thats 3 restarts so far with no issue. I wouldn't of made that previously.

Calv

---

### Post by ohGrbyte on 2006-11-19
I've had this issue as well. Glad to see I was not the only one.

My question is where do I put the killall emerald code at?

---

### Post by zgornel on 2006-11-21
After login, hit ALT+F2, write *sudo killall emerald && emerald* and make sure you tick the run in terminal box. Try also adding emerald to the gnome startup list in System/Preferences/Sessions (worked for me).

---

