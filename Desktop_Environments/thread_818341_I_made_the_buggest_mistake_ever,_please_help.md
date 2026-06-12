---
title: "I made the buggest mistake ever, please help"
date: 2008-06-04
forum: Desktop Environments
---

### Post by AlexisMclovin on 2008-06-04
I have been using ubuntu for about a month now, making the transition from windows. I wanted to try a different Desktop environment then gnome. I used Synaptic package manager and installed FVWM crystal but it didnt automatically switch to the new environment. So in a moment of brilliance i say " Hey maybe i have to delete Gnome and it will enable the new environment." I delete everything that has to do with gnome but it doesnt go away. I still have gnome i just have deleted all the essential programs needed to do anything with the desktop. I cant add new programs, cant use terminal , cant use synaptic. So i figured im screwed. Any suggestions would be much appreciated ,because i am stuck.

---

### Post by ChameleonDave on 2008-06-04
Hit Ctrl + Alt + F1 to go to the terminal.

Log in.

Enter this:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by ChameleonDave on 2008-06-04
To enable a new environment, you just have to choose it when you log on.  There should be a button to click, allowing you to choose between GNOME, FVWM, KDE, XFCE, or whatever is on your system.

---

### Post by omegamike3 on 2008-06-04
> **ChameleonDave said:**
> To enable a new environment, you just have to choose it when you log on.  There should be a button to click, allowing you to choose between GNOME, FVWM, KDE, XFCE, or whatever is on your system.

That button to click is usually a "Session" button, by the way :D

---

### Post by AlexisMclovin on 2008-06-04
Thanks so much , i panicked there for a second. The desktop is installing now

---

### Post by AlexisMclovin on 2008-06-04
how do you exit the terminal when its finished installing

---

### Post by OmniCloud on 2008-06-04
> **AlexisMclovin said:**
> how do you exit the terminal when its finished installingtype in exit;) 

you should have all the necessary apps again to use Synaptic. There you can build your desktop back up with any applications you need. 

I would restart after you finish..

btw--you shouldn't go removing huge files like Gnome-desktop without doing a bit of research. I think there's a newbie section here, and of course wiki is your best friend when learning how to use Linux. 

Learning a few basic terminal commands will of course come in handy;)

---

### Post by AlexisMclovin on 2008-06-04
thanks guys, yea i need alot of help with linux, but ill make sure i dont do anything as drastic next. I have my computer back

---

### Post by ChameleonDave on 2008-06-04
> **AlexisMclovin said:**
> how do you exit the terminal when its finished installing

There is a screen assigned to each function key.  Ctrl + Alt + F7 will probably bring you back to your desktop or log-in screen.

On any graphical screen, you can hit Ctrl + Alt + Backspace to restart the graphical server.

You can also type "reboot" to restart the machine, or "shutdown -h now" to switch it off.  You may need to put "sudo" before them.

---

### Post by OmniCloud on 2008-06-04
> **AlexisMclovin said:**
> thanks guys, yea i need alot of help with linux, but ill make sure i dont do anything as drastic next. I have my computer backsometimes drastic pays off...

Now you know a few basic things about the terminal...lol

Practice is practice;) Trust me, once you get to a certain point of efficiency in Linux, you'll probably never use anything else. 

Many only boot-up windows for gaming or for those Windows only applications that some professional need like a photoshop or something. 

Customizing how linux looks is the only the tip of the iceberg.

---

