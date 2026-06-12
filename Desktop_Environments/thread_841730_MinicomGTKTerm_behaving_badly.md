---
title: "Minicom/GTKTerm behaving badly"
date: 2008-06-26
forum: Desktop Environments
---

### Post by imog on 2008-06-26
Lesbians behaving badly would have probably been a better title to get this thread attention. Sigh. Anyways...

I need help with minicom gtkterm.  I'm testing both of these when configuring network hardware via COM1 to the Serial port - lantronix print servers, like the EPS2-100.

I have configured the serial port settings in these apps for 9600 8N1, and its working alright.  Its just the display of information is a lot lousier than I get with Hyperterminal on a windows host.

For example, if I issue a basic command to a lantronix box such as "show server", in hyperterminal it will give me back a nicely formatted output with all characters in the words present.  I get the same results if I telnet into the box over the network.  If I do the same in Minicom or gtkterm, I get a similarly formatted output, with missing characters in the words.  If I run the command again the output will be similar again, but different characters will be missing than the time before.  Sometimes the prompt itself is missing letters, like instead of saying "local_1>" it will say "lcal_1>".

This does not alter behavior in any way - the information is not displayed to me correctly, but the info itself is correct.  I mean, even if the prompt says "lcal_1>" which looks wrong, I can issue commands and they are handled properly.  Its an annoyance because if I'm configuring the IP address, subnet mask, and gateway, I need to do a "show server" to make sure I made the settings correctly.

Does anyone have experience using these application and have any advice for me?

---

### Post by chewearn on 2008-06-27
This might not be of any help, but the "lesbians behaving badly" phrase attracted my attention. :wink:

I use picocom as hyperterminal replacement in ubuntu.  It worked perfectly.

However, one time, I found a problem with missing characters, broken communication and even application crashes.  I then discovered this was after I added gnome-pilot applet, and both application is fighting for access to ttyS0.

So, maybe it might help to check if there is more than one application trying to access the serial port.

.

---

### Post by imog on 2008-06-30
> **AstalaVista said:**
> This might not be of any help, but the "lesbians behaving badly" phrase attracted my attention. :wink:

I use picocom as hyperterminal replacement in ubuntu.  It worked perfectly.

However, one time, I found a problem with missing characters, broken communication and even application crashes.  I then discovered this was after I added gnome-pilot applet, and both application is fighting for access to ttyS0.

So, maybe it might help to check if there is more than one application trying to access the serial port.

.

Thank you for the input, thats a direction I had not looked in. It makes sense that something of that nature could cause this issue. I'll look into things that could be interfering with com1/ttySO.  I should have probably thought of that, thanks.

Any other thoughts out there?

---

### Post by imog on 2008-07-01
Shame on me, but I found the issue.

Something was hung in the background - I'm not sure what.

I downloaded updates for Ubuntu today which required a reboot, and after reboot any application of my choice is talking with /dev/ttyS0 without issue.

---

