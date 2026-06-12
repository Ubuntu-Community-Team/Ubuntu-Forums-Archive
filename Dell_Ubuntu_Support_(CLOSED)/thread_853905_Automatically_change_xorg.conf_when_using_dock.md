---
title: "Automatically change xorg.conf when using dock?"
date: 2008-07-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chrisab508 on 2008-07-09
Hey guys,
I have a latitude D620 notebook from Dell and I'm currently using a latitude dock with twin view enabled (22in Acer monitor + 14in laptop monitor).  I am currently using hardy and have configured an xorg.conf file for my dual monitors that works correctly and I have also configured a separate xorg.conf file to use uniquely with the notebook (i.e. while not connected to my dock).  Do any of you know if there is a way to get Ubuntu to recognize the presence of my dock and automatically switch my xorg.conf files?  In /etc/X11 I have xorg.conf_dual ( for the dual monitors ) as well as xorg.conf_orig (for just the laptop monitor).  Presently, depending on what I want to use, I just copy the needed file as xorg.conf and restart X, but I wanted to know if there was a little more automated way of doing this.

Thanks in advance,

- Chris.

---

### Post by cellulararrest on 2008-07-11
I would love to be able to do this as well. When I put my laptop on my Dock I'd like to switch monitors.

---

### Post by Crinos512 on 2009-11-30
Here's what I have found... [Here]("http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7001151&sliceId=1&docTypeID=DT_TID_1_1")

> 
With Linux there are always a number of creative solutions for the same issue.  This is just one suggested method of working around this issue.

First step is to configure the system so it is working correctly while undocked (using the internal display).  If you are having trouble getting the display (internal or external) configured correctly, Technical Information Document 3564938 may be of some help.  When satisfied with the display settings make a backup copy of the /etc/X11/xorg.conf.  In my example I will assume that the internal display uses a resolution of 1440x900.  Here's the command to make a backup copy of the file with a new name that identifies the resolution:

cp /etc/X11/xorg.conf /etc/X11/xorg.1440x900

With the "undocked" display configuration saved the next step is to dock the system and configure the system for the external display.  When satisfied with the settings make a backup copy of the now modified xorg.conf file again.  For this example let's assume the external display resolution is 1280x1024.  Here's the command to make the backup copy:

cp /etc/X11/xorg.conf /etc/X11/xorg.1280x1024

With the two backup configuration files in place a script can be added to the file /etc/init.d/boot.local that will search for specific information returned from the "hwinfo" command to determine if the system is docked or not and then copy the appropriate xorg.??? backup file to xorg.conf.

For Dell systems the bios information returned by "hwinfo --bios" will include the string "Docking Station" when the system is docked.   Here are the lines to add to the /etc/init.d/boot.local (create it if it does not exist and make the first line "#!/bin/bash"):

```
# Check to see if system is docked and copy appropriate xorg.conf file.
#
DOCKED="`hwinfo --bios | grep "Docking Station" | wc -l`" 
# The following line can be uncommented for debugging.
# echo $DOCKED > /root/docked-state.txt 
if [[ $DOCKED -gt "0" ]] 
  then 
  cp /etc/X11/xorg.1280x1024 /etc/X11/xorg.conf 
else 
  cp /etc/X11/xorg.1440x900 /etc/X11/xorg.conf 
fi 
# End of setup for docked vs. undocked. 

```
Here's another example, written by one of the other engineers, for testing the docked status of an IBM or HP notebook system.  The value "LTN121XJ" was found as the unique value when the system is docked and the command "hwinfo --monitor" is run.  Notice that he has used a little different logic in his example.  If the value of "LAPTOPMON" is "0" (meaning it is not using the internal display) then copy the xorg.conf that is for the external monitor:

```
# Check to see if system is docked and copy appropriate xorg.conf file.
LAPTOPMON="`hwinfo --monitor | grep "LTN121XJ" | wc -l`" 
echo $LAPTOPMON > /root/laptopmon.txt 
if [[ $LAPTOPMON = "0" ]] 
 then 
 cp /etc/X11/xorg.1280x1024 /etc/X11/xorg.conf 
else 
 cp /etc/X11/xorg.1440x900 /etc/X11/xorg.conf 
fi 
# End of setup for docked vs. undocked.

```

---

