---
title: "Error Logs"
date: 2009-02-17
forum: General Help
---

### Post by RedSingularity on 2009-02-17
Is there a program installed in ubuntu that will allow me to view system logs?  I am having a problem and would like to track it down.

---

### Post by Titan8990 on 2009-02-17
All system logs are stored in the following directory: /var/log

The typically most useful: /var/log/messages  and   /var/log/dmesg

The tool to help you search and manage them: grep


There is a commercial tool called snort: [http://www.splunk.com/](http://www.splunk.com/)

I wouldn't recommend it for personal use as grep should work just fine.


What kind of problems are you having?

---

### Post by RedSingularity on 2009-02-17
The whole system was freezing up whenever i got to particular point installing something in my Vista Virtual.  It has never happened before so i found it odd.  I played with the settings in VirtualBox and it is working fine now.  I had one if the boxes for Vista unchecked and it was causing my problem.

---

### Post by RedSingularity on 2009-02-17
Can you give me a quick command example on how to use grep?

---

### Post by Titan8990 on 2009-02-17
Yes, if you are interested in say, problems with the vboxdrv module you would do: 

grep -i 'vboxdrv' /var/log/messages


-i means "ignore case", by default everything grep searches for is case sensitive. if you wanted to do the entire /var/log directory:

grep -i -r 'vboxdrv' /var/log


You can enter either of those commands into your terminal to get an example of what the log messages look like.

All system logs break log messages down in a single line, so they can be searched easily with grep. Grep is an advanced command and will do much more than you will probably ever use it for.

For my info: [http://unixhelp.ed.ac.uk/CGI/man-cgi?grep](http://unixhelp.ed.ac.uk/CGI/man-cgi?grep)

---

