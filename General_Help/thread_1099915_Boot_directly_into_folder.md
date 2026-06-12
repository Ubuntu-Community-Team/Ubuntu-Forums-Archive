---
title: "Boot directly into folder?"
date: 2009-03-18
forum: General Help
---

### Post by seebold on 2009-03-18
I am replacing 36 computers in 3 day care centers. The new ones are refurbished Dells with XP. I will be wiping XP and installing Edubuntu. I have two issues I haven't yet figured out.

One is that I need to make the startup as simple as possible. These are kids computers and won't be connected to any network. They are used to flipping a switch and having it boot directly into a dos screen with their games on it. Any way to do something similar? It would be nice to bypass the login screen and then go straight to a folder with the games.

I also need to figure a way to lock the little buggers out of the rest of the system. I've been looking at kiosk mode but it seems like it leaves too many doors open.

If I can figure out how to make this all work with these centers there are a bunch of other centers that will be more than happy to make the switch from Windows.

---

### Post by MaindotC on 2009-03-18
Well one thing with which I can help you is removing the login process.  Go to System -> Administration -> Login Window and select the "Security" tab and click "Enable automatic login".  If every child is just using a generic login and nothing that ties them to their session then you probably don't need to be concerned with security.

Locking down the system is, in my opinion, a rather complex task because of the number of angles you can take.  Granted, I don't think little children will be doing ctrl + alt + f2 to access a terminal, but there is a lot to address.  One way to lock them out of the rest of the system is to go to System -> Preferences -> Main Menu and uncheck any menu items or applications that you do not want accessible from the main menu.

---

### Post by seebold on 2009-03-18
Thanks for the help. And I agree, they are not likely to hit certain key combos, but if enough monkeys hit enough keys........

I have another 3 or 4 days till the computers are here so I will keep tinkering whenever I can.

---

### Post by MaindotC on 2009-03-18
Another suggestion would be to go to System -> Administration -> Users & Groups and remove all unnecessary priviledges.  Definitely research on how to disable key combinations like ctrl + alt + f2 or even shift + alt + f2.  Try System -> Preferences -> Keyboard Shortcuts.

---

