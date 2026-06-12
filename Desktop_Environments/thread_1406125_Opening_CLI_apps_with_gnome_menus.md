---
title: "Opening CLI apps with gnome menus"
date: 2010-02-13
forum: Desktop Environments
---

### Post by J_dillinger on 2010-02-13
I would like to be able to open application on the command line from the gnome menus.  The first one I added was midnight commander and it worked just fine with the command /usr/bin/mc, but when I add some others I get a response but the gnome-terminal opens and the closes.  how can I make the terminal window remain open.  I would also like to add some options to activate or suspend services.  I think it works when I use the following:

/etc/init.d/networking restart

but again, I do not receive any message from the terminal.  Is there any way to cause the terminal to remain open?

---

### Post by weblordpepe on 2010-02-13
> **J_dillinger said:**
> I would like to be able to open application on the command line from the gnome menus.  The first one I added was midnight commander and it worked just fine with the command /usr/bin/mc, but when I add some others I get a response but the gnome-terminal opens and the closes.  how can I make the terminal window remain open.  I would also like to add some options to activate or suspend services.  I think it works when I use the following:

/etc/init.d/networking restart

but again, I do not receive any message from the terminal.  Is there any way to cause the terminal to remain open? Hi dude. That was an interesting question (I tried everything, and ticking the 'run in terminal' thing doesnt even allow a terminal window to stay open afterwards) but I found a solution.

Its a bit rough, but it certainly works.
You can set the following to be part of a shortcut, or type it manually from that Ctrl-alt-F2 menu or whatever its called. 
```
gnome-terminal -x bash -i -c '**ls** && bash'
```Simply replace the **ls** with whatever command you would like to have run. 

The key to this being difficult was gnome-terminal AND bash like to quit immediately after executing anything they were given as 'execute this when launched'.
I wanted to get gnome-terminal to run XYZ then run bash, to keep itself open. But it gave me some wacky error about child processes. (!?)
The trick was to tell gnome-terminal to run bash, and tell bash to run XYZ and then another bash instance afterwards.

So there you have it. A complete spaced out way of doing it but it works.

---

### Post by mbsullivan on 2010-02-13
I agree with weblordpepe, that's pretty much the way of doing it.

So, in summary, you right click on your applications menu, and place the entire command as the "command" part of the entry.

One caveat in your case is that the "/etc/init.d/networking restart" command requires administrative access. Therefore, you could do something like:

```
gnome-terminal -x bash -i -c 'sudo /etc/init.d/networking restart; bash'
```

Whereupon it will ask for your password in the opened terminal. If that's not acceptable, you could make that command not require administrative privilege by changing its group or permissions or editing your sudoers file (ask me how if it's a problem).

Mike

---

### Post by J_dillinger on 2010-02-13
You guys are the champs... That was beautiful.  I have managed to add all my services to the menu and all the CLI tools I have installed and forgotten about to the menus.


Thanks

---

### Post by weblordpepe on 2010-02-16
:guitar:=D>=D>:-({|=:-\"8-)\\:D/:guitar:

---

