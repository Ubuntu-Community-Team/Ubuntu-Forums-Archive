---
title: "Firefox print freeze"
date: 2007-11-29
forum: Desktop Environments
---

### Post by emilong on 2007-11-29
Firefox has just started to freeze as soon as I try to print.  When I select print from the menu, it doesn't even get a chance to close the menu before freezing completely.  Has anyone else experienced this or know an easy way for me to debug it?  top shows that firefox isn't really using the CPU when this happens.  This is using Firefox 2.0.0.10 on Ubuntu 7.10, recently upgraded.

TIA

---

### Post by ubuntubrian on 2008-01-31
this just started happening on my box too. I'm on Dapper w/ either FF1.5 or 2.0 same problem. It also happens if I try printing in Konqueror. I did update some cups packages through UpdateManager about 2 weeks ago. this is the first time I've noticed the problem.

---

### Post by Arcturus691 on 2008-02-01
emilong, 
Not sure if my issue is exactly the same, Firefox does not freeze but it does not print.  Cups Jobs states that it is completed. I think this is related to the cups updates from last week.  I'm no expert but I think cups has new parameters that fire fox does not understand. 
Open your Error console before you print   Firefox>_T_ools>Error _C_onsole

Here are the error messages from Firefox Error Console  when I try to print:
--------------------------------------------------------------------------------------------------
Warning: Unknown property 'border-radius'.  Declaration dropped.
Source File: [http://localhost:631/cups.css](http://localhost:631/cups.css)
Line: 204

Warning: Unknown property 'box-shadow'.  Declaration dropped.
Source File: [http://localhost:631/cups.css](http://localhost:631/cups.css)
Line: 206

Warning: Expected end of value for property but found 'font-weight'.  Error in parsing value for property 'background'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-4a44d1c2-00074.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-4a44d1c2-00074.css)
Line: 1961

Error: $ is not defined
Source File: [http://ubuntuforums.org/](http://ubuntuforums.org/)
Line: 1025
--------------------------------------------------------------------------------------------------

There are 21 errors in all, they were repeats of the errors listed above.

Here is my browser/system info:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11
My printer is a Canon Pixma IP3000 and is using CUPS+Gutenprint v5.0.1 Simplified

I think this is a bug with Firefox.  

Should it be reported to Ubuntu or Firefox?
Also what is the url for reporting the bug?

---

### Post by Arcturus691 on 2008-02-05
--bump--

---

### Post by Arcturus691 on 2008-02-08
Two updates for firefox are available via the Update Manager.  Looks like they fix many bugs. I did not see anything about freezing but it is worth a try.  Printing from firefox worked for me before updating so I am not sure what changed to fix the issue for myself.

---

### Post by ubuntubrian on 2008-02-19
Turned out to be an issue with my local network configuration that I had reconfigured when I was traveling out of the country. I had disabled the lo interface and that screws up printing and other stuff.

---

