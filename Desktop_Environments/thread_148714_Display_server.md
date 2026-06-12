---
title: "Display server"
date: 2006-03-22
forum: Desktop Environments
---

### Post by Flipsod on 2006-03-22
I cant think of any action i took to mess this up ](*,) 
I was editing some settings and files in cedega (not graphics related) when i noticed my firefox window dissapear. I'm new to Linux and Ubuntu but I have noticed Cedega tends to work better with a reboot right before and after I do something with it. so I reboot.

When the boot sequence gets to just past my Nvidia splash screen (where you see the cursor) it re inits the splash screen and twitches out graphically for a while flashing me console login prompts and boot status information intermixed with an Nvidia logo, and eventually reaches an error screen:

"The display server has shut down 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting 2 minutes before tryng again on display :0"

The first time it occured it halted before this message and I was forced to reset power to reboot, on each following attempt to boot it doesnt actually freeze my systemand  I am able to send a "reboot" command and end the session poperly.

I checked my hardware, seemed fine but I remoeved the graphics card and gave the card (and my whole system) a good dousing of canned air, then re-seated all my hardware and triple checked all my connections.

Being new to Linux, I have absolutely no clue where to go from here. any information will be very much appriciated.

---

### Post by Ramses de Norre on 2006-03-22
Can you get into recovery mode and post the contents of /var/log/Xorg.0.log and ~/.xsession-errors ?

---

### Post by Flipsod on 2006-03-22
I'm again for being a noob here, but i cant use gedit. it returns the message:

"(gedit:7493): Gtk-WARNING **: cannot open display"
in normal boot mode at the console

in recovery mode
"(gedit:7493): Gtk-WARNING **: cannot open display"

how should I access these logs?

---

### Post by Flipsod on 2006-03-22
I'm again for being a noob here, but i cant use gedit. it returns the message:

"(gedit:7493): Gtk-WARNING **: cannot open display"
in normal boot mode at the console

in recovery mode
"(gedit:6535): Gtk-WARNING **: cannot open display"

how should I access these logs?

---

### Post by Ramses de Norre on 2006-03-22
In shell you can't use a graphical program like gedit, the most userfriendly program for terminal to watch text files is less, just type less path_to_file and use the arrows to go back and further through the output.

---

### Post by Flipsod on 2006-03-22
wow im not typing all that verbatum...  thats a huge list of events... the part at the end appears to e erronious... 


Warning: font renderer for ".pcf" allready registered at priority 0

listed for multiple extensions ie: ".snf" ".bdf" etc.

thats in the Xorg.0.log 

i dont have /.xsession-errors

---

### Post by Flipsod on 2006-03-22
what type of messages did you want to see from that log? it would take me all day to type the whole thing out

---

### Post by Flipsod on 2006-03-22
here is something i noticed in the log that might be of use :
(II) Load module "nvidia"
(II) Reloading /usr/X1186/lib/modules/drivers/nvidia_drv.o
(II) Unload Module: "nvidia"
(EE) Failed to load module "nvidia" (once-only module, 136464984)

---

