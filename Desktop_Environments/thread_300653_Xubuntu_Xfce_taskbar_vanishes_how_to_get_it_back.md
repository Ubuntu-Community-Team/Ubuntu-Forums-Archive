---
title: "Xubuntu Xfce taskbar vanishes: how to get it back?"
date: 2006-11-16
forum: Desktop Environments
---

### Post by eeried on 2006-11-16
Hello,

I've had some misadventure with Xfce taskbar in Xubuntu Dapper after customizing the upper and lower taskbars.

I've removed the bottom taskbar and I've made the top taskbar look like the one in XFCE default. That is it's shorter and set in the top middle part of the screen. I've added launchers and stuff using the "add an item" feature.

in particular I've added the window list which shows the list of opened apps, even if they're minimalized (!). Only one icon shows, you click on it and you have the full list.

It seems clicking on the first icon to display the list can cause the taskbar to disappear. Logging out solves the problem and the taskbar reappears. However Imust have check the save session option when logging out and now I can't get the blasted taskbar back!

How can I get it back? -- of course clicking on the panel setting doesn't do anything at all, the setting being simply inactive when you click on its icon in the settings panel.

Why this Xfce-Xubuntu strange taskbar vanishing?](*,) 

The config files display my taskbar settings.

Cheers

---

### Post by leikao on 2006-11-16
You can type the command:

xfce4-panel

in the terminal to get the taskbar reappears.

---

### Post by eeried on 2006-11-16
Okay the command works fine but of course if I close the terniman the taskbar disappears again. How do i make the taskbar come back once and for all?

Why clicking on the window list icon can cause the taskbar to disappear?

---

### Post by bonjun on 2006-11-17
at terminal: xfce4-panel

don't close terminal yet

logout, be sure save session is check

login, after that you can close your terminal


======
if something is abnormal happening when you click something on the panel, do this step:

> Delete all panel, right click panel > customize panel > click minus sign (-) until all panel is deleted.

type this in terminal: cp -r /etc/xdg/xcfe4/panel ~/.config/xfce4

again at terminal: xfce4-panel

logout, be sure save session is check

login, after that you can close your terminal


---

### Post by leikao on 2006-11-17
You could type 
> 
xfce4-panel &

The "&" means to let this command run background, then you can close the terminal now.

---

### Post by collapse on 2007-01-15
> **leikao said:**
> You could type 


The "&" means to let this command run background, then you can close the terminal now.

it dosen't works...pls help...

---

### Post by Froman on 2007-01-15
ive been having a similar problem in that i accidently did something and the taskbars (both top and bottom) dissapear i tried following some of the advice given but none seems to work. im not sure why this is happening but this seems to be a bit of a problem with xubuntu. Is there anyone who can help?](*,) ](*,) ](*,)

PS... im not sure if this has to do with anything but when i click the help button then try to access the panel manual it says that the file cannot be found

---

### Post by kerry_s on 2007-01-15
Press> alt + F2 <then enter the command> xfce4-panel

---

### Post by mak1084 on 2007-12-23
> **kerry_s said:**
> Press> alt + F2 <then enter the command> xfce4-panel

yes this solution is good it also helped me once.

---

### Post by wPwLUi3N on 2008-06-07
> **bonjun said:**
> at terminal: xfce4-panel

don't close terminal yet

logout, be sure save session is check

login, after that you can close your terminal



Worked like charm, thanks.

---

