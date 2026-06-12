---
title: "Window titlebars have disappeared!"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Gris on 2006-08-25
Hi everyone

Because 2D performance on my ATI equipped PC with 1920x1200 screen is slower than 3D performance I thought I would try Xgl. I followed the instructions at [http://www.tectonic.co.za/view.php?id=916]("http://www.tectonic.co.za/view.php?id=916") and got Xgl working. However, it did not work well with [CodeBlocks]("http://www.codeblocks.org") so I followed the 'uninstall' procedure of deleting ~/.Xsession. Unfortunately, when I log in now I have no window titlebars and all windows that open are in the top left corner of the screen. If I log in using the 'failsafe' mode I get the window titlebars etc, so I suspect that there is some config issue with the main log in. Anyone know how I can get back my window titlebars?

Cheers

Gris

---

### Post by Greycloak on 2006-08-25
In a terminal window type:

```
metacity --replace
```

Also, if you created a script to run compiz you might want to disable that.

---

### Post by Gris on 2006-08-25
Thanks for the suggestion. Unfortunately, when I started the computer up it said "Failed to start the Xserver...". I can get to a log in prompt with Alt-F1, but when I type metacity -- replace it says that it cannot find the X server. Help!

Cheers

Gris

---

### Post by Gris on 2006-08-25
Hi everyone

Is there a way to re-install xserver and gdm etc (all the user interface stuff)?

I can only use ubuntu from the command line as when I try to restart normally it says it cannot find the Xorg executable and I've tried everything I could find through Google, but I fear I have really just made things worse!

So how do I re-install the GUI for ubuntu?

Cheers

Gris

---

### Post by backdoc on 2006-08-26
Try typing startx on the command line.  This may start X, without Xgl.  That worked for me.  Then, I set my start up X server to standard by going to Administration->Login Window->Security Tab and choosing the "Configure X Server" button from the bottom right of that window.

I don't have Xgl anymore, but if it's going to break with every upgrade, I'd rather not have it.

---

### Post by Gris on 2006-08-26
> **backdoc said:**
> Try typing startx on the command line.  This may start X, without Xgl.  That worked for me.  Then, I set my start up X server to standard by going to Administration->Login Window->Security Tab and choosing the "Configure X Server" button from the bottom right of that window.

I don't have Xgl anymore, but if it's going to break with every upgrade, I'd rather not have it.

Hi backdoc

When I type startx at the command line I get:

Fatal server error:
Can't find XOrg executable

So I can't start the X server. How do I repair the installation?

Cheers

Gris

---

### Post by backdoc on 2006-08-26
If there is a *Ubuntu* way to do it, I don't know how.  X problems are never easy for me to resolve, but I always manage to do it.  I have no super sequence of steps that always work, though.

What does the X log file say?  If you look closely, you can see a legend of marks that indicate what failed.  I think "EE" represents the problem.  The line before it gives a clue, too.

Post that portion of the error log.

---

