---
title: "Help! Ubuntu Freezes"
date: 2006-09-30
forum: Desktop Environments
---

### Post by osarusan on 2006-09-30
I'm fairly new to Ubuntu, and this problem just started happening after Ubuntu had been working really nicely for about a week...

I rebooted, and now whenever I right click, or open any menu, or even let a hover-tooltip appear, the system completely locks up. No mouse, keyboard... nothing. I need to kill the power to restart it.

I have been able to quickly open a terminal window, as long as the tooltip doesnt show up. However, I don't know what on earth could be causing it to freeze like this.

Can anyone give me some clue as to what might be making this happen? At least with the terminal I might be able to fix it without reformatting. :-(

Thanks for any help you can give!

---

### Post by osarusan on 2006-09-30
Update:

I've figured out what the problem was... it was the Wacom drivers.

In the Ubuntu help wiki, there were instructions on setting up a wacom tablet. I guess its those drivers that cause everything to screw up.

So... the good news is I was able to restore my xorg.conf to fix them. The bad news is I can't use my wacom cintiq on ubuntu anymore. :-(

(It was working perfectly with the new drivers before I rebooted... for some reason rebooting seems to have caused the problem to start)

---

