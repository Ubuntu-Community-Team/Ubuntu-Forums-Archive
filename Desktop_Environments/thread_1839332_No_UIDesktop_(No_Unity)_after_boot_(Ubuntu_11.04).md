---
title: "No UI/Desktop (No Unity) after boot (Ubuntu 11.04)"
date: 2011-09-05
forum: Desktop Environments
---

### Post by asad.bukhari on 2011-09-05
I was messing with compiz one day. When I started my computer there was no desktop display. The computer starts, I log in, the keyring asks for my passwords, but there is no interface, just my background.

I'm not ubuntu-savy and need help fixing this...

---

### Post by e79 on 2011-09-05
You might want to reset Unity to its default state. Have a look here :

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

[http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](http://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)

Hope this helps

---

### Post by asad.bukhari on 2011-09-08
I used the links.

First, I simply tried to reset unity using the "unity --reset" code.
It did not work.

I then tried to use "unity --reset-icons" code which also did not work.

Lastly, I used "gconftool-2 --recursive-unset /apps/compiz-1" and "unity --reset."
This did not work either.

After entering these codes into the terminal, it starts running processes but they usually get stuck. After initializing several options (which end in ...done) the terminal stops at "Setting Update 'run_command_terminal_key'" and "Setting Update 'fullscreen_visual_bell.'"  After waiting several minutes, I lose patience and close the terminal (it notifies me that a process is still running and advises against closing it, but the process never finishes so I close it anyway).  I do not know what else to do, I have not interface except for the icons on my desktop.

---

### Post by Frogs Hair on 2011-09-08
One more thing to try would be to run the unity reset command from recovery console . It is located on the session list below the greeter box on the login screen .

If you see an output in the terminal after entering the command pay attention to what it says . If there is no output try again. Reboot after entering the command and select Ubuntu from the session list prior to login.

---

### Post by asad.bukhari on 2011-09-08
I tried what you said. But same situation, it does not move past those two updates I mentioned in my previous post. How long should I have to wait for them to complete? Should the process be quick or take long?

---

### Post by asad.bukhari on 2011-09-09
Well, ubuntu still does not display the unity bar or the top panel.. Is there anythign else I can do so that I may use it again?

---

