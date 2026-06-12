---
title: "Close a frozen fullscreen game?"
date: 2007-02-02
forum: Gaming &amp; Leisure
---

### Post by kripkenstein on 2007-02-02
I play Sauerbraten, which is a great game. But every few days it freezes on me. Since it's in fullscreen, and has control of the mouse&keyboard, I can't do anything but shut down X with control-alt-backspace, which is sort of annoying. All I need to do is shut down one app.

Is there any way to set a keyboard shortcut to close the current application, something like that?

---

### Post by Richard Kut on 2007-02-02
Hello! You can start another terminal session by hitting Ctrl+Alt+F1. This will bring you to another teletype terminal, also known as a tty. Login, and then locate the process id of the locked-up game, probably using ps -ef and scanning for a keyword.If it is 'sauerbraten' then 

ps -ef | grep sauerbraten 

will isolate that process from the list. Note the process ID number, and then issue the command

kill -9 processID#

When that is complete, logout of the tty by hitting Ctrl+D.

Now go backj to your graphical shell by hitting Ctrl+Alt+F7.

I hope that the above is clear enough. Good luck!

---

### Post by pseudonym on 2007-02-02
What you can do is drop to a console by pressing Ctrl+Alt+F1, logging in, and running the 'top' command to view your running processes.

Scroll through using Shift and < > and find your game executable. Note the name and process ID number then quit 'top' by pressing 'q'.

Now type 'killall -9 name_of_your_game'. If that doesn't work you try 'kill process_ID_number'. If you *still* can't shut down your game you'll need to kill X by running 'sudo killall -9 Xorg' or pressing Ctrl+Alt+Backspace from within X like you've been doing.

But you shouldn't need to do that.

EDIT: someone got in first :)

---

### Post by kripkenstein on 2007-02-02
Thanks for the quick responses guys!

Ok, now I know what to do when it next freezes on me, great.

---

