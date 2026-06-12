---
title: "How does a desktop environment shutdowns a computer without asking for password?"
date: 2014-04-23
forum: Desktop Environments
---

### Post by ehsanoo on 2014-04-23
Hello, Ubuntu lovers!

I want two brief explanations from you, I really cant understand them, specially the first one.

1. How is that possible that the *Shut Down...* option can shutdown the computer without asking for password when I click on the computer icon in the top panel, but I have to enter my password when I want to shutdown my computer using terminal? Why does the graphical interface has this permission? Is it running under an account that has SU rights?

2. When I open the right click menu by right clicking on something, function keys are disabled, like Pause, Volume Up/Down. Why these keys are disabled? also sometimes pressing them will close the menu.

Thank you.

---

### Post by m_duck on 2014-04-23
Hi there. For number one, this probably answers your question: [http://askubuntu.com/questions/361988/why-do-we-need-to-be-root-in-terminal-for-shutdown-and-restart](http://askubuntu.com/questions/361988/why-do-we-need-to-be-root-in-terminal-for-shutdown-and-restart). Basic point is that the shutdown/reboot etc. menus don't use /sbin/shutdown, but instead send a message via dbus (I think) which runs with the privileges needed for power-related commands.

And number two, I'm not sure.

---

