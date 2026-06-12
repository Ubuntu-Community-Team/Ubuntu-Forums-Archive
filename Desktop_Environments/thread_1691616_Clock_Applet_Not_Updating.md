---
title: "Clock Applet Not Updating"
date: 2011-02-20
forum: Desktop Environments
---

### Post by omeganow on 2011-02-20
I used gconf-editor to change the format of the date and time displayed on the panel (I wanted sortable
strings  for pasting into a table of OpenOffice base, since base can not  automatically insert the current timestamp value into a column with the  create time of its table row).

Using the the strftime() manual page as a guide, I entered   

 %Y/%m/%d - %H:%m  

as the value for custom_format in gconf, and  entered 

custom 

as  the value for attribute  format, and it worked to the extent that the  clock applet now displays the date and time looking like this:  

2011/02/20 - 03:02

This  is what I wanted to see in the panel, and the copy time function  returns that string, which meets my requirement for a sortable timestamp  string. However I now have other problems:

1. The displayed time  in the clock applet is  no longer updating: it is stuck at the time I  changed the        format. Reboot of ubuntu did not help.  Any ideas?

2. The applet's copy date function returns 

      Sunday, 20 February 2011

which  is not the default formatting, and the gconf-editor dialog does not  show a separate attribute for setting the format of the date separately  from the time format. Where is the format string for the date portion of  the current date and time value ?

---

### Post by omeganow on 2011-02-20
OK - small change to the previous post.

The clock applet's reformatted  time dispaly updates once per hour.

How do I get it to update once per minute?

---

