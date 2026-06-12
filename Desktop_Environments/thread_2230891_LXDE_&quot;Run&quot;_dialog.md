---
title: "LXDE &quot;Run&quot; dialog"
date: 2014-06-21
forum: Desktop Environments
---

### Post by jason105 on 2014-06-21
Hi!
I'm running Lubuntu Trusty.
Can anyone please tell me if there is a way either through python or a shell command to cause the "Run" dialog from the LXDE menu to pop up? I'm writing a hotkey script and I suppose I could write an arbitrary GTK launcher app with the same functionality and that there are probably innumerable such apps that I could install. But I'm particular about my Linux desktop and I want it to be the same dialog. Or is there a trivial way to set up a hotkey within my Lubuntu environment that I'm just too ADHD to have picked up on? (I would still like to know how to use Autokey to do it 8D )
 
:guitar:
Thanks and rock on!
J

---

### Post by grumblebum2 on 2014-06-21
Does Alt+F2 bring it up.
Command to run is **gmrun** I think.

---

### Post by BazBear on 2014-06-22
Alt+F2 brings it up on my Lubuntu 14.04, but gmrun in terminal doesn't work.

---

### Post by jason105 on 2014-06-22
Lol I'm an ubuntu user from back in the day--alt-f2 does nothing. But inferring that gmrun is a functional alternative to the "Run" dialog, I asked whereis if I had it, figured out I didn't, installed it and could now just use AutoKey with the same effect and not have to learn a new graphics toolkit api (or try using fltk) today :) Sweet, thanks! 

Strange that your Lubuntu lets you alt+f2 and yet mine does not. Maybe I accidentally installed 13.x instead of 14.04.

---

### Post by grumblebum2 on 2014-06-23
Have you disabled the lxpanel in your session?
The default command to bring up the run dialog is
```
lxpanelctl run
```

and will fail, as will alt+F2 if the lxpanel is not running.
```
lxpanelctl - LXPanel Controller
Usage: lxpanelctl <command>

Available commands:
menu	show system menu
run	show run dialog
config	show configuration dialog
restart	restart lxpanel
exit	exit lxpanel
```

P.S. I have a 13.10 Lubuntu test install that I don't really use.
I thought it was gmrun but realize now I had disabled lxpanel
and installed tint2 and gmrun.

---

### Post by jason105 on 2014-06-23
I think that I did actually install 13.x instead... now that I think back the v14 CD that I had burned didn't work and I used an old one. However, lxpanel is running in the default session:
```

$ ps -A | grep lxpanel
 2412 ?        00:00:02 lxpanel


```

Curious.

---

### Post by grumblebum2 on 2014-06-23
Odd...does **lxpanelctl run** work?

---

### Post by jason105 on 2014-06-30
> **grumblebum2 said:**
> Odd...does **lxpanelctl run** work?

Sorry, thought I said yes already but I guess I wasn't paying attention. Yeah, `lxpanel` is running (see above) and more to your point, `lxpanelctl run` does indeed cause the "Run" dialog to be displayed.

:KS

---

### Post by jason105 on 2014-06-30
Also: I am running Lubuntu 14.04, not 13.10. I'm wondering if it's keyboard related; my Fn keys don't perform the way I would like them to (my mute key mutes my sound but won't un-mute it)

...I *gnu *I should have installed Gnome...........

---

