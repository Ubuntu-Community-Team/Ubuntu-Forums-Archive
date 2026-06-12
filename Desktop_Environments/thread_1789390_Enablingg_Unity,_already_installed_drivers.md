---
title: "Enablingg Unity, already installed drivers"
date: 2011-06-23
forum: Desktop Environments
---

### Post by KevinRK on 2011-06-23
Hey everyone, I started using ubuntu in 10.10. When 11.04 came I decided I would wait to upgrade. I finally did upgrade two days ago and I am no running 11.04. Upon my first log in it told me the usual "Drivers/hardware not compatible with unity" message. I updated my drivers to the recommended and restarted my computer. I logged in using the default "ubuntu" session and all I get is a fancier version of Gnome then I did in 10.10. My main reason for upgrading is that I liked unity. If I try to start unity via terminal (I just use the commands "unity") My computer freezes. I assume this is because Gnome is still running also. Where can I set it so unity runs by default instead of gnome?

Or did I do something wrong?
______EDIT_____
Extra g in the title, sorry I typed this pretty fast

---

### Post by Krytarik on 2011-06-23
First, Unity is based on Gnome, so no conflicts there. It's rather just a plugin of Compiz, and Gnome Panel is (usually) not running, that's basically all, apart from some further extra settings for Compiz, possibly.

Do you really have Gnome Panels if you log in to the "Ubuntu" session?

Please see this troubleshooting guide:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Greetings.

---

### Post by KevinRK on 2011-06-23
I found a video on youtube that showed me how to fix it, for some reason Unity wasn't installed by default. Is there any way to make the task bar (Official Name?) On the left not tile over open windows?

---

### Post by Krytarik on 2011-06-23
> **KevinRK said:**
> Is there any way to make the task bar (Official Name?) On the left not tile over open windows?
That thing is actually called Launcher (hard to not to confuse it with the application launchers it can itself also host).

And it seems like you are meaning the "Backlight Mode", you may want to set it to "Backlight Always Off":
[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)

---

### Post by KevinRK on 2011-06-23
> **Krytarik said:**
> That thing is actually called Launcher (hard to not to confuse it with the application launchers it can itself also host).

And it seems like you are meaning the "Backlight Mode", you may want to set it to "Backlight Always Off":
[http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)


Thanks I can Probably figure it out from there, but I was actually wondering how to make the Launcher "Hide" under the window. It always seemed to be the top layer for some reason

---

### Post by Blasphemist on 2011-06-23
In ccsm, click on the unity plugin (not it's checkbox) and you'll see my screen shot. The hide launcher setting is what you are looking for.

---

### Post by Krytarik on 2011-06-23
> **KevinRK said:**
> Thanks I can Probably figure it out from there, but I was actually wondering how to make the Launcher "Hide" under the window. It always seemed to be the top layer for some reason
I was thinking that way initially, but the wording wasn't really that indicative to me, and neither the sense. As you have the option to autohide it, but then it would, of course, shove itself over a window. And the other way around, not autohide, makes even less sense, to want to have it below of a window.

---

### Post by KevinRK on 2011-06-24
Thanks for your help everyone, I've learned what I needed. Think I'm going to stick with Gnome for now after all!

---

