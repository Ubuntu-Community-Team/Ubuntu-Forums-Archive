---
title: "Continuing HP Printer problems"
date: 2006-09-06
forum: Desktop Environments
---

### Post by useResa on 2006-09-06
I have continuing problems with my HP All-In-One printer (PSC 1410).

The problem is the fact that when I print, the printer light starts blinking.
The job is shown, but it NEVER comes past 64.0 kb and never prints out anything. Hereby also blocking all prints that come after this printjob.
Furthermore the only way to delete the job is to unplug the printer, restart the PC, delete the job and plug in the printer again.

Some background information:
1. I have installed the latest available hplip driver (1.6.7)
2. The printer is shared via a Dell Desktop running WinXP


I can install the printer either via System --> Administration --> Printing and by using CUPS (see attachments).
However when I start the HP Device Manager (hp-toolbox when using a terminal), it indicates that NO HP devices are found (see attachment).
When I try to run 'sudo hp-setup', I get the following message:
> [B]HP Linux Imaging and Printing System (ver. 1.6.7)
Printer/Fax Setup Utility ver. 2.1[/B]

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

[COLOR=Red][B]error: No devices found.
error: Error occured during interactive mode. Exiting.[/B][/COLOR]

Is there a relation between the two problems?
If not, how can I solve these problems?

I really hope that someone can help me.
Kind regards

---

### Post by mssever on 2006-09-06
Some random thoughts...

Do you get the same problem if you hit the print test page button in CUPS?

You can almost certainly avoid rebooting if you simply restart CUPS:
```
sudo /etc/init.d/cupsys restart
``` 
My guess as to why the hp tools don't see your printer is because they only look at local printers, IIRC.

I think that XP is capable of using IPP instead of windows networking. What if you try setting up the printer that way? Also, for testing purposes it would be helpful to plug the printer in to your Linux box and try to print that way. That way, we know a little more about where the problem is.

EDIT: For what it's worth, [here's what linuxprinting.org]("http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1410") knows about your printer.

---

### Post by useResa on 2006-09-06
The only thing that I have been trying to print until now are the test pages, either from the installed printer through the gnome-cups-manager or by using CUPS.

You indicate IPP, can you please explain how I should do this?
I am quite new to both Linux and "networking".

I have a wireless connection from my laptop to a router. The Windows machine is wired directly to this router. When I use Places --> Network Services I can see the shared folders etcetera.
I hope this all makes some sense.

Connecting the printer directly to the laptop is something I also considered, but (unfortunately) the printer and the wires are quite built in so I probably won't be able to do so until this weekend (will take me some time :rolleyes:)

If you need any more information, please let me know.
Anything to get this solved!

---

### Post by mssever on 2006-09-06
> **useResa said:**
> The only thing that I have been trying to print until now are the test pages, either from the installed printer through the gnome-cups-manager or by using CUPS.
OK, then we know that it isn't an application problem, but either a CUPS problem or a driver problem.
> You indicate IPP, can you please explain how I should do this?
I am quite new to both Linux and "networking". Setting up the printer to use IPP is someting that you do on XP when you share the printer. I don't use Windows anymore, so I don't know how to do it. Look for some option along the lines of IPP, Unix, Web-based, HTTP or something of that ilk. And I've only used XP Pro. I don't know what's available in XP Home. On the Linux side, you'll create a new printer and choose Internet printing protocol. Use IPP or HTTP depending on how you set the printer up in XP.
> I have a wireless connection from my laptop to a router. The Windows machine is wired directly to this router.This is the same as my setup. My printer is plugged in to my desktop via USB (both machines are running Ubuntu).

> Connecting the printer directly to the laptop is something I also considered, but (unfortunately) the printer and the wires are quite built in so I probably won't be able to do so until this weekend (will take me some time :rolleyes:) Could you set your laptop on top of your desktop and pull the USB (assuming it's USB) cable from the desktop and plug it into the laptop? The reason I ask is that I think that this is an important diagnostic step. For example, if it doesn't work when plugged in to your laptop, then you don't need to worry about trying to use IPP, because the problem isn't in how the printer is connected.

By the way, am I correct in assuming that the printer works properly from your XP computer?

---

### Post by useResa on 2006-09-07
Thank you for your clear explanations.

I'll try your suggestion on connecting the printer directly to the laptop first. Currently I am not at my home location (we do have to pretend working for the boss occasionally ;)), but I can hopefully try this coming evening.

 I will let you know the outcome of this test.
Regards

---

