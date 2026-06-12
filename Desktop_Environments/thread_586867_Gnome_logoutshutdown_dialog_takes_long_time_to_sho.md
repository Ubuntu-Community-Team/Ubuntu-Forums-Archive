---
title: "Gnome logout/shutdown dialog takes long time to show"
date: 2007-10-22
forum: Desktop Environments
---

### Post by Eremit on 2007-10-22
When I click the logut/shutdown icon it takes about 30 seconds to a minute, until the dialog shows up. In the meantime I can move the mouse but clicking something has no effect.

Any ideas? :confused:

---

### Post by apple_and _linux on 2007-10-22
I've got the same problem!  However, there are about 8 other accounts on the same computer, and none of them have it.  Off the top of my head, Pidgin and KGmailnotify are two programs that I have and nobody else runs.  I suppose I could try disabling those and seeing how it works.  But it's really annoying to have to wait 47 seconds (it's the same every time) when I just want to log out!
I'll let you know what I find out.

---

### Post by Rajca on 2007-10-22
Have you guys disabled power-manager in sessions? It should be turned on. I have had the same problem, and when I enabled power-m it solved my problem.

---

### Post by Eremit on 2007-10-23
Don't have that in my Startup Programs, but anyway gnome-power-manager is running.

@apple_and_linux:
Interesting. This would suggest it has something to with user settings.

---

### Post by Achille on 2007-10-23
rm -fr ~/.config/autostart/

did the trick for me.

---

### Post by apple_and _linux on 2007-10-23
> **Eremit said:**
> Don't have that in my Startup Programs, but anyway gnome-power-manager is running.

@apple_and_linux:
Interesting. This would suggest it has something to with user settings.

Well, I shut down the notifier and Pidgin before logging out, but it didn't make any difference.  I'll check into that power manager thing, though, and maybe try that code somebody posted...

---

### Post by apple_and _linux on 2007-10-23
> **Rajca said:**
> Have you guys disabled power-manager in sessions? It should be turned on. I have had the same problem, and when I enabled power-m it solved my problem.

Yay, you solved it!  As soon as I enabled this, my problem was fixed.  I remember now- I disabled it, thinking, "I don't have a laptop, so why do I need a power manager?"  Well, lesson learned. Thanks, Rajca!

---

### Post by Eremit on 2007-10-23
> rm -fr ~/.config/autostart/

This solved it for me too. It puts the sessions config back to default.
Or if you still have the Power Managment entry - simply activate it.

Guess this is solved.

---

### Post by Rajca on 2007-10-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/138811](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/138811) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				That was posted on Launchpad. 
> Guess this is solved.
Yea, that's right. By default power-men is enabled so:
```
rm -fr ~/.config/autostart/
```
Took it back. That's all.

---

### Post by apple_and _linux on 2007-10-24
> **Eremit said:**
> This solved it for me too. It puts the sessions config back to default.
Or if you still have the Power Managment entry - simply activate it.

Guess this is solved.

You don't have to reset your sessions manager just because it's gone.  Simply click "Add", then for command, type: gnome-power-manager
That's what I did.

---

### Post by lorsban on 2007-10-30
I had this problem as well right after I messed around with the configuration for Palm sync set up (which still doesn't work). It took about a minute for the shutdown dialog to start. 

Well, I'm happy to report that the rm -fr...trick worked even better than expected. Now, I get near instant shutdown and it vastly improved startup as well! Awesome! Thanks a bunch!

---

