---
title: "Gnome Panel not loading on boot"
date: 2011-01-06
forum: Desktop Environments
---

### Post by altctrldel on 2011-01-06
Hey, 

Gnome panel is not loading at all (version 10.10 ubuntu btw)

All I get is about 1/3 of the top panel on the screen - no menu etc drawn and my desktop icons moving slightly up and down, which I guess due to gnome panels attempting to load.  When I try to boot using altctrldel I get the message gnome-panel is not responding.  I tried safe mode etc which no effect.  I think its clear I am using the windoz ideas - not sure how to start fixing this in ubuntu


I have tried a couple of things from this site in pervious threads

from the basic 
```
kill gnome-panel
```to this idea from this link

```

 [http://www.ubuntugeek.com/ubuntu-tip-howto-recover-gnome-panel.html](http://www.ubuntugeek.com/ubuntu-tip-howto-recover-gnome-panel.html)


Procedure to follow 1) First you need to Boot the system upto Login Window and now Press Ctrl+Alt+F1
 2) Now You will get a Text based login screen use your username and password to login
 3) run the following Command from your terminal[INDENT]$ rm -rf .gnome .gnome2 .gconf .gconfd
[/INDENT]Now Press Ctrl+Alt+F7 you get your normal GUI login window

```I not sure how else I can reinstate gnome....

Thanks

---

### Post by jesse.melhuish on 2011-01-06
Well, I just tried to see what I could do about restarting my panel.  I simply did this:

```
pidof gnome-panel
```

And then I took the number it gave(The process ID of the application, in this case gnome-panel) and killed it with this:

```
sudo kill whateverthepidwas
```

The panel disappeared, and then immediately restarted.  If that doesn't help it may be something to do with your graphics card.  This is, of course, assuming everything loads and the Gnome panel is the only problem.  Hope it works, post your problems if it doesn't.

---

### Post by Krytarik on 2011-01-06
> **jesse.melhuish said:**
> Well, I just tried to see what I could do about restarting my panel.  I simply did this:

```
pidof gnome-panel
```And then I took the number it gave(The process ID of the application, in this case gnome-panel) and killed it with this:

```
sudo kill whateverthepidwas
```The panel disappeared, and then immediately restarted.  If that doesn't help it may be something to do with your graphics card.  This is, of course, assuming everything loads and the Gnome panel is the only problem.  Hope it works, post your problems if it doesn't.
That does exactly the same as the command mentioned by altctrldel.

It's most likely a video driver issue. What card/chip are you using, what driver?

---

### Post by altctrldel on 2011-01-07
OK I try the commands given, just to see if that makes any difference. 

I need to check the video card details, which I will do shortly. I just need to get to that computer first.

But I have had no previous issues with the graphics card, I installed 10.10 very soon after release... either way I find out the details.

---

### Post by altctrldel on 2011-01-08
SiSM760GX integrated 3D graphics controller with 64MB shared RAM

That is the graphics card that comes with the laptop. However, i have run the computer for more than a month with ubuntu with no issues, there is no windows dual boot btw.



What I need to do is somehow refresh gnome, that is my guess.....

---

### Post by altctrldel on 2011-01-08
[http://www.ubuntux.org/gnome-panels-not-working-or-responding](http://www.ubuntux.org/gnome-panels-not-working-or-responding)

> **[Problems with gnome panels]("http://www.ubuntux.org/gnome-panels-not-working-or-responding#comment-482")**

        by jmatos - 2007-01-14 21:23  
        This problem ocurrs because the gnome-applets library is not  present or corrupted. Go to the Synaptic package manager and use the  find tool and find "trash" to locate the library and select it to  install or re-install.Best Regardsjmatos



I saw this at the above link. Any thoughts

---

### Post by Krytarik on 2011-01-08
> **altctrldel said:**
> [http://www.ubuntux.org/gnome-panels-not-working-or-responding](http://www.ubuntux.org/gnome-panels-not-working-or-responding)
I saw this at the above link. Any thoughts
This is a completely different behaviour.
> What I need to do is somehow refresh gnome, that is my guess..... 
Did you try the mentioned command then? (I would use "killall" instead of "kill", however.)

To reload the entire desktop:
```
killall nautilus
killall gnome-panel
```
Do you use the default driver or any custom one?

---

### Post by hansolo4949 on 2011-01-08
I think you should try reinstalling the gnome desktop. I believe the code is: sudo apt-get install --reinstall ubuntu-desktop. that might be able to fix your problem!


hansolo4949

---

### Post by altctrldel on 2011-01-08
OK I might of fixed it

First I tried the solution given here:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)
> **rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

This made no difference

Then I tried, as given in a comment:> 
killall gconfd-2
rm -r ~/.gconf/apps/panel    > NOTE this didnt work, presumably as I had already removed the folder.
killall gnome-panel

Returned back to gnome gui AltCtrlF7
Now working after rebooting.

---

### Post by altctrldel on 2011-01-08
Thanks [hansolo4949]("http://www.uluga.ubuntuforums.org/member.php?u=1217844")

I agree that was definately the next step, only thing stopping me was I needed the panel to turn on my internet connection... haha, wasnt sure exactly how to activate wireless via terminal.

thanks for replying and the others.

Also I hope this thread helps anyone in the future with the same issues ;)

---

### Post by Krytarik on 2011-01-08
Then it was a faulty panel config, I didn't thought of that until now.

Thanks for posting your solution.

---

### Post by hansolo4949 on 2011-01-09
You're welcome, altctrldel :).

If you're connected to the internet via ethernet if you tried to reinstall it, and you dropped down to the terminal, it should work.

hansolo4949

---

