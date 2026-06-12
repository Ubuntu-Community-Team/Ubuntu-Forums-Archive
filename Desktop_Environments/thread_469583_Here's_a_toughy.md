---
title: "Here's a toughy"
date: 2007-06-10
forum: Desktop Environments
---

### Post by Genecks on 2007-06-10
Alright, I recently played with Xmacro. It was ok except for one thing: It took over the desktop. Now, I was wondering something.

Is it possible to create multiple instances of the Ubuntu desktop, thus allowing me to run several macros. For example, imagine I create a click-and-type macro that took over the Window's Desktop. Well, now I can't use that computer, because its busy doing what the macro is programmed to do.

Can I create like another instance of Ubuntu, regain control of the keyboard and mouse, and also have that macro run in the background? I assume it's like having multiple operating systems all accessed at once, but I don't want to use tons of RAM and resources for it.

I think these are in relationship to what I want. Do you think they are?


>  Switching between Running X Sessions

How can I have multiple X sessions running at the same time? That is to say, if I'm logged in as root and also log in on Ctrl-Alt-F2 and give the command startx -- :1 to fire up X, everything works fine. If I go back to Ctrl-Alt-F7, all is fine there too. But, when I go to Ctrl-Alt-F2 again, X has crashed there, but it still is up on F7. Is there some command that I can give so X stays up on F2 when I'm going back and forth?

--
Bjarni Valsson


[email]bjarniv@hotmail.com[/email]

X does not run on F2 (pty 2). Each X instance you start creates its own pty, hence the switch to pty 7. If you go back to pty 2, you actually can put X in the background (Ctrl-Z, then type bg) and continue using that console for other tasks. If you start up another copy of X, and X already is running, it creates a new pty (now 8, in this case). You must then press Ctrl-Alt-F8 to switch to that copy of X. Remember, X is a user-space application. Two running X processes should not interfere with one another unless you are doing something odd with your hardware; certain video card driver settings might cause trouble.

--
Chad Robinson


[email]crobinson@rfgonline.com[/email]

and this also [http://groups.yahoo.com/group/codlug/message/217?l=1](http://groups.yahoo.com/group/codlug/message/217?l=1)

---

### Post by dominator22 on 2007-06-11
Run gdmsetup and make sure "Disable multiple logins..." is not ticked. 

Run gdmflexiserver and login as yourself.
This will run a second instance of the x server.  

To switch back and forth between x sessions use Ctrl+Alt+F7, Ctrl+Alt+F8, ...

---

