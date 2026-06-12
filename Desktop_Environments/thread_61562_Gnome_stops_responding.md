---
title: "Gnome stops responding"
date: 2005-09-01
forum: Desktop Environments
---

### Post by Milton on 2005-09-01
I installed ubuntu the other day and all seems very nice, though for some reason my desktop stops responding at random intervals, when doing random things.

What happens is that the cursor remains the same though still moves as expected, clicking does nothing, the keyboard stops responding so I can't ctrl alt esc or ctrl alt f1or even ctrl alt delete (whatever I press nothing happens).

it appears that things are still happening as earlier today when it happened xmms continued playing the music. Just now it crashed with firefox and gnome-terminal the only open applications and I wasn't even touching the mouse or keyboard.

any help appreciated since I don't like pressing the reset button!

---

### Post by frodon on 2005-09-01
Do you use xcompmgr ? If yes you could have this problem when the screen saver start. If not .. no idea, sorry.

---

### Post by Milton on 2005-09-01
I'm not sure... if it's setup that way by default then yes.

it generally happens while the computer isn't idle (while I'm in the middle of my work)

---

### Post by ~jaime on 2005-09-04
I am having exactly the same problem. I have tracked several programs that crash my system automatically. One of them is Azureus. Yesterday it was OO spreadsheet the only thing open. Also while recording a dvd, browsing the web with firefox and chatting with gaim (at the same time)

This is very weird... isn't linux supposed to be more stable than windows? XP works flawlessly on this same machine, so we can discard any hardware issues.

---

### Post by ~jaime on 2005-09-04
and no, the xcompmgr packet is not installed

---

### Post by vruum on 2005-09-04
which graphics card do you use and which drivers? I'm pretty sure that the proprietary ATI drivers had this problem at some point

---

### Post by ~jaime on 2005-09-04
I have an nVidia GeForce2 Ti and the drivers are the propietary 1.0-7174

---

### Post by vruum on 2005-09-04
it looks like nvidia has this problem too, but I don't have one, so I can't really be helpful (if the problem is with the drivers) if you've got a couple of days to kill, I did find [about 20 pages of debuggy goodness](http://www.nvnews.net/vbulletin/showthread.php?t=31858) 
anyways, maybe someone more qualified will repy

---

### Post by ~jaime on 2005-09-04
Thank you I will take a look. This is quite annoying for a linux newbie like me  ](*,)

---

### Post by ~jaime on 2005-09-04
All I have clear now is that nVidia says my card is "Legacy" and it will not be supported on the newest drivers :-x

---

### Post by ~jaime on 2005-09-06
I have now discovered several ways to freeze my pc. 

- I open firefox, then open [this page](http://www.google.es/url?sa=t&ct=res&cd=2&url=http%3A//www.globalshareware.com/Internet/Email/HTML-Email-Template-Pack.htm&ei=ooMbQ8iPIKiURdyy_dMM ) and in another tab [this other page](http://www.google.es/url?sa=t&ct=res&cd=4&url=http%3A//www.alouwebdesign.ca/free/free-email-template/free-email-template-instructions.html&ei=ooMbQ8iPIKiURdyy_dMM ). This will happen also in ff safe mode and under any circunstances (disabling java, javascript, images, image animations, css, cache...) , but not under Epiphany or Opera.

- Azureus will freeze it after less than a minute
- Same with OpenOffice Spreadsheet. In less than a minute.

I also found out the power button of my computer closes it nicely in a few seconds (no need to reset it).

Any help? I can't believe it happens to everyone using an nvidia card...

 ](*,)  ](*,)  ](*,)

---

### Post by Irony on 2005-09-06
This infrequently happens to me as well - I have a radeon X800 card. I don't really know what causes gnome to freeze. The last time it happened I was viewing this forum and then I right clicked on a desktop item to view its properties and gnome froze. Had to push the reset button.

---

### Post by SilvioTO on 2005-09-06
search for hardware problems; for example, your ram is ok?

---

### Post by vruum on 2005-09-06
you should definatly check for other problems, eg. the ram thing SilvioTO suggested. the graphics card was just an idea cause I had that once. So maybe, first off, changre the driver back to whatever it was before, basically do what you did when you installed them only backwards, if the problems persist, the problem is not the drivers/graphics card, if problems stop, what i got from skimming the nvidia forum thread was to try to turn nvagp off or on, the opposite of whateverit is now.

---

### Post by elrohir_telperien on 2005-12-01
Hi,

I have this problem as well.

Usually, the keyboard would stop responding, ie. pressing num lock did not turn off the "light", ctrl alt backspace did not restart server, etc.

However the mouse cursor did move freely though.

The only reason I could think of is the nvidia driver - when I enabled the driver, gnome freezes randomly. When I do not enable the nvidia driver, my up time could go as far as 7 days (and more...).

I am sure the problem lies at nvidia drivers.

By the way I am using GeForce 2 MX.

---

### Post by Hobbes on 2005-12-01
I started having this problem recently as well...

Just after switching cards to an older geforce4 card from a 9800 pro, it's gotta be something to do with the nvidia driver/xorg settings.

I'll keep searching for answers..... :)

---

### Post by Hobbes on 2005-12-01
After searching around I found a link to this [post]("http://ubuntuforums.org/showpost.php?p=132408&postcount=19").  Hopefully that will help both me and you.  I just turned renderaccel back off, we'll see if there are anymore freezes.

---

