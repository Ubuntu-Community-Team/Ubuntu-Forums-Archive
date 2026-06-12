---
title: "Login Troulbe."
date: 2007-06-17
forum: Desktop Environments
---

### Post by jdewire04 on 2007-06-17
When I boot up my computer ubuntu begins to load but then I just get a blank screen where my login should be. I beleive its because I tried changing my login screen around and now It doesnt have anything to load there. I was hoping there was some code i could type in to reset my login screen to default, so i can get into my desktop without having to do anything too drastic (reinstall ubuntu). If anyone knows the code I'd need to reset that, I'd really appreciatte it thanks.

---

### Post by hasardeur on 2007-06-17
that depends. try bypassing the entrance manager completly. 

if you use xubuntu type "startxfce4", for kdm "kdm-start" and for gnome... i dont know (i only use xfce). you might just type "startx" and see if it gets you anywhere. once you are inside your desktop enviroment change the login manger back to what it was.

hope it works...good luck

---

### Post by jdewire04 on 2007-06-20
Hrmm.. tried that but doesn't  get me anywhere... is there somewhere I can go online that has a list of commands? or does anyone know the ubuntu code I need? Thanks for the help.

---

### Post by coffeecat on 2007-06-21
I think I have half an answer.

Boot up and when the bootup process gets stuck, press ctrl-alt-F1 simultaneously to get a virtual terminal. Login. You now have to work entirely at the command prompt for a while. Type the command:

```
sudo nano -w /etc/gdm/gdm.conf-custom
```The nano text editor opens with the gdm configuration file. Scroll down to the line "GraphicalTheme=XXX" where XXX will be whatever you chose when you tried to reconfigure gdm. Put a single hash mark in front of that line so it reads:

```
#GraphicalTheme=XXX
```Press ctrl-o to save and ctrl-x to quit nano. Do:

```
sudo reboot
``` to reboot the machine.

I'm not in Ubuntu at the moment and, although I can view my Ubuntu gdm.conf-custom file, I can't give you the default gdm login screen name for that line because I've changed it too and you probably won't have the login screen installed that I have. I'm hoping that by commenting out the line, gdm will go to some sort of default and you'll be able to login to the desktop and then reconfigure gdm from the GUI. If that doesn't work, post back. I'm having to go out for a few hours but when I get back I'll check this thread and if need be I'll log into Ubuntu, change the login screen and see what it's called so I can give you that line complete.

---

### Post by coffeecat on 2007-06-21
**jdewire04**, I've now had a chance to experiment in Ubuntu Feisty. If you do as I suggest and comment out the GraphicalTheme line it simply defaults to the Human GDM theme when you next boot up or if you restart X. Which makes me think that perhaps your problem is more fundamental.

If you are still around can you post some more details, particularly what you mean by 'changing my login screen around ' . Also, please confirm that you are using Ubuntu/gnome and not Kubuntu or one of the other Ubuntu variants. For the record the default line in that gdm configuration file is:

```
GraphicalTheme=Human
```

---

### Post by jdewire04 on 2007-06-21
Yeah thanks I just read your suggestions, Ill comment again to let you know if it worked. 

What I meant by "changing my login screen around" was that I put a custom login gdm on, but I get the feeling now that it wasnt a login, but a splash screen... Thanks for the help
Oh and I am using ubuntu.

---

### Post by jdewire04 on 2007-06-21
I just tried your suggestions, I got to the lines under [greeter] where it says     "graphicaltheme=   "     and changed it to human, and under that line is another that says     "graphicalthemes=   "     and i changed that to read human also. 
I rebooted as suggested but the problem persists... any other ideas? 

do you have the two lines that read   graphicaltheme= human    and under that    graphicalthemes=human or is that unusual? 

I even commented them out by putting the hash infront of them, and rebooted to the same problem.

Capitalizations dont matter do they?

Thanks for all the suggestions

---

### Post by coffeecat on 2007-06-22
> **jdewire04 said:**
> What I meant by "changing my login screen around" was that I put a custom login gdm on, but I get the feeling now that it wasnt a login, but a splash screen... 

I really don't understand what you mean. Was that the gnome splash you tried to change? That's quite a different thing. It's possible that your problem is not in the gdm configuration file.

> **jdewire04 said:**
> do you have the two lines that read   graphicaltheme= human    and under that    graphicalthemes=human or is that unusual?

I would think it is. This is the greeter section in my gdm.conf-custom with the theme changed back to Human. The colour will be different from yours - I've changed mine from the default yukky pink.

> [greeter]
GraphicalThemedColor=#71180a
GraphicalTheme=Human
UseCirclesInEntry=false
> **jdewire04 said:**
>  Capitalizations dont matter do they?

Oh yes they do. Very much so. This isn't Windows. Linux is case-sensitive.

---

### Post by jdewire04 on 2007-06-23
Ok ill try eplaining again, I apologize for the lack of clarity. 

The last modifications I did before rebooting, were to change the login screen (gdm) from human to some sort of design that I downloaded. I also tried to put a splash screen on that would be displayed either before of after the login screen.(not really sure which this was my first attempt at it) Both changes i made without going to the command screen. Now when i boot up instead of seeing a login screen, i get linuxes equivent of the "sand in the hour glass" mouse graphic. 

Because its the last thing i changed AND because it doesnt display now, i suspect the problem lies with either the splash screen or the GDM.

Right now I've edited the gdm.conf-custom file so it reads

[greeter]
GraphicalTheme=Human
Welcome=

I hope this sheds some new light on the problem, I'd appreciatte any Ideas.

---

### Post by coffeecat on 2007-06-23
Perhaps it's the splash screen that's causing the problem. The splash is the relatively small image that appears briefly after the gdm logon screen that tells you of the progress of the startup of gnome. [Here's a link for you.]("http://art.gnome.org/faq.php#q8") Look at #8. I can't remember whether the gnome configuration editor appears in the menus of a default install of Feisty. It should be under Applications > System Tools. If it's not there, go into System > Preferences > Main Menu and activate it. Open it and go to apps > gnome-session > options and look for splash_image in the right pane. The splash image is normally in /usr/share/pixmaps/splash.

---

