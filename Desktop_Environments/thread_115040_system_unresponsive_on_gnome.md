---
title: "system unresponsive on gnome"
date: 2006-01-09
forum: Desktop Environments
---

### Post by kasemodz on 2006-01-09
alright last night I installed ubuntu with gnome on my server. Everything is working fine. I left it on overnight. This morning, I saw the hard drive activity a lot. I ignored it. However, I just logged into the server via tightvnc. I tried opening various programs and nothing opened. So I connect the server with a monitor and still had the same problem. 
Then I noticed my hard drive activity still blinking excessively. Basically the computer tries to open a program, but in the end it doesn't do anything. It does do that squiggly circle and then stops. 
So I pressed ctrl + alt+ backspage to restart gnome. I got a login screen. My hdd activity was still high. So I tried logging in but the password field never came. So I eventually restarted it. Ubuntu booted just fine. Then after startup its suppose to go gdm but it remained at text mode. 
It came with an error, that xserver couldn't launch. Would you like to display information? However, in the end it remained in text console. I logged in successfully. So I tried running gdm. First, it said root can only do this. So then I logged in as root and then ran gdm. It said gdm already running. I don't know what to do.

What should I do fix this problem and how can I find out what was taking that much hard drive activity?

---

### Post by super on 2006-01-09
try a '[FONT="Courier New"]sudo killall gdm[/FONT]' then try running '[FONT="Courier New"]sudo gdm[/FONT]'

if you have the same xserver and disk activity problem again, instead of killing x, try pressing 'alt+ctrl+f1' to get to another console and running '[FONT="Courier New"]top[/FONT]'. it will report on running processes and the amount of memory and cpu they are using.

have fun!

---

