---
title: "Xubuntu problems"
date: 2008-02-14
forum: Desktop Environments
---

### Post by super.rad on 2008-02-14
I'm having a few problems with Xubuntu, when I log on there are no panels I have to start them by running xfce4-panel in the terminal but then I can't close the terminal or they disapear again. Also everything looks really ugly (hard to describe so i've included a screenshot) and when I try to open settings manager or window manager settings the desktop and panels change to how they should look for a few seconds then change back but the settings manager never opens. If anyone has any solutions to these problems it would be great. Thanks

[IMG]http://i3.photobucket.com/albums/y94/loserkid_1/Screenshot-4.png[/IMG]

---

### Post by Pogeymanz on 2008-02-14
I'm sorry. I don't know a lot to help the situation, but if you type "xfce4-panel &" you will be able to close the terminal. The & sign is the key. also if you hit alt-F2 and type xfce4-panel, it will stay.

Edit: Everytime I have a weird problem in Xubuntu, I make sure I'm not saving the session on log-out and then delete the hidden file ".cache" in your home directory. Try that then restart. I don't know why it works, but it has solved some weird problems for me.

---

### Post by super.rad on 2008-02-14
placing the & in the terminal didnt work but i was messing around with some folders in my home folder and tried deleting the .config then logged out, back in and everything except the panels are working, any idea how to add programs so they start automatically when i log in? I will just put "xfce4-panel" in there so it starts up on it's own everytime

---

### Post by mmbates on 2008-02-20
I just had the same problem.  I have an inelegant solution (I'm sure there's a proper way to fix this), but this "just works".

This is the steps that I had to do to get my panels back, on startup.

1) Right click on the desktop.  Select "Desktop Settings"

2) Click the "Behavior Tab"

3) Tick "Show Desktop Menu" and then close

4) Right click the desktop again, and your normal "Applications" menu will pop up.  Go to "Settings" and then "Autostarted applications"

5) Click "Add" and fill it out as follows (less the "" of course)
5a) Name: "xfce4-panel"
5b) Description: "loads the panels on start up" (or whatever you want to call it)
5c) Command: "xfce4-panel"
5d) "Ok"
5e) "Close"

Next time you restart or log on, your panels will appear!

---

