---
title: "Switch Desktop Environments via Terminal"
date: 2013-10-19
forum: Desktop Environments
---

### Post by maerlyn-broadbent on 2013-10-19
Hi All,


Does anyone know if it's possible to switch desktop environments via the terminal?


I'm writing a script to install Cinnamon on Ubuntu and I would then like to remove unity but at the moment I have to ask the user to log out, log in with cinnamon and then continue the script to remove unity.

---

### Post by 3rdalbum on 2013-10-19
Why, can't you remove Unity while it's running? It sounds like a stupid question but it's not - if you try and remove a file that's in use, Linux just marks it to be removed when it's no longer in use.

Otherwise, a command like "cinnamon --replace" would do the trick.

---

### Post by maerlyn-broadbent on 2013-10-19
Thanks for your advice. I'm not just removing unity, I'm also removing compiz which causes all of my windows to disappear except for the terminal which I'm worried will frighten the user.
[I]
cinnamon --replace[/I] kinda worked but the process seems to be tied to the terminal so when it's closed, cinnamon closes as well. It will also prevent the rest of my script from running.

---

### Post by Frogs Hair on 2013-10-19
What version of Ubuntu and Cinnamon. ? Cinnamon is included in the 13.04 and 13.10 repository and starting with 2.0 is its own desktop environment not just a modified gnome shell. It is possible to change the login default to a different desktop environment after it is installed. The replace command was effective in gnome 2 for switching between compiz and metacity , but doesn't work well for changing window managers in gnome 3 .

---

### Post by maerlyn-broadbent on 2013-10-19
I'm using Ubuntu 13.10 and Cinnamon 2.0. Is there another command or method that will work with this setup.

The reason I want to do this in a script is because I'm in the process of writing a set of Ubuntu configuration scripts in a similar style to cb-welcome which is featured in CrunchBang Linux. I want to give users the ability to choose to use a new desktop environment and I thought it would be best if I could switch directly to the new environment instead of asking them to logout and log back in.

If there isn't a feasible way to do this, I should be able to leave this command for the last step and then let the user know that the script will log them out. I'd just rather not have to do that.

---

### Post by Frogs Hair on 2013-10-19
This is getting a bit over my head with the Debian  reference , but I think if there were a direct route via a menu of some type it would have been done. Threads with similar subjects tend to disappear and I have never seen a solution. The replace commend is not likely work consistently thus logging out may actually save time if the window manager doesn't load properly on ever users computer  .

---

### Post by maerlyn-broadbent on 2013-10-19
> This is getting a bit over my head with the Debian reference
cb-welcome in CrunchBang is simply a post-installation script to help people install new software to make a new installation feel more customised. I was already writing my own Ubuntu configuration scripts but cb-welcome inspired me to re-write it to make it interactive and to give the user some control. Also, I couldn't find anything similar already written for Ubuntu and I think it will come in handy for newer users.

> Threads with similar subjects tend to disappear and I have never seen a solution.
That's a shame, I'll keep the desktop change as the last step for the moment then until I have come up with a better solution.

> The replace commend is not likely work consistently thus logging out may actually save time if the window manager doesn't load properly on ever users computer .
I haven't been getting the output I wanted during testing in VMs but I wasn't sure if it was just me doing something wrong since this is my first time bash scripting.

If anyone is interested, my non-interactive first attempt can be found here:
[https://github.com/maerlyngb/UbuntuCinnamonSetupScripts](https://github.com/maerlyngb/UbuntuCinnamonSetupScripts)

v2 coming soon!

---

