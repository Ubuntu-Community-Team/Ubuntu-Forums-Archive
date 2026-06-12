---
title: "Scripts don't execute in a visible terminal"
date: 2007-05-28
forum: Desktop Environments
---

### Post by lamecheetah on 2007-05-28
I've set Nautilus to "run executable text files when they are clicked" (Edit->Preferences->Behaviour tab). Is there any way to have double-clicked shell scripts execute in a visible terminal window?   After changing the setting, when I double-click a script, it runs, but nothing appears on screen.

(My first post!! Linux noob here)


<bits>
- Ubuntu 7.04, desktop build   (Gnome and Nautilus both at 2.18.1)
- Pretty vanilla install, except I added firestarter, a nvidia driver, and a broadcom wireless driver.


<example>
#!/bin/bash
echo script begin > output
read -p "Press enter to continue..."
echo script end >> output

I set the file to executable, and left Nautilus at the default script setting ("ask each time"). I double-click the file, get the "do you want to run...or display its contents" prompt, and I click "Run in Terminal". A terminal window appears, and the script works as expected (write to file, pause at the prompt, then write to file, and quit).

I set Nautilus to "run executable text files when they are clicked" and double-click the file. It still runs, but it doesn't show a terminal. It also skips the read command - System Monitor doesn't show the process running, and the output file immediately gets both the "script begin" and "script end" lines.

Looking back at the "ask each time" prompt, I saw both the "Run in Terminal" and "Run" buttons. Seems that when I configure Nautilus to automatically run scripts, it is using the "Run" behavior.

So... is there any way to get the "Run in Terminal" behavior without getting the annoying prompt?


(this was just a silly example. Originally I wanted to run ifconfig;iwconfig with two clicks :)

---

### Post by aysiu on 2007-05-28
Not exactly the answer you're looking for, but have you thought of creating a launcher on the panel for that script? I believe there's a checkbox for panel launchers to *run in terminal*.

---

### Post by lamecheetah on 2007-06-04
Thanks aysiu, works great.
Also found out how to create similar launchers on the desktop. Very cool.

---

