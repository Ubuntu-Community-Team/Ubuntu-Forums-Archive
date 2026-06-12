---
title: "Trying to install ATI Catalyst Control Center"
date: 2009-07-15
forum: Desktop Environments
---

### Post by n00binberg on 2009-07-15
They say in their installer guide PDF that the default drivers Ubuntu used during original OS install need to be removed in order to get their Catalyst Control Center installed properly. However, the directions they give to take out the old driver don't work...Is there someone who can tell me how to do this properly? 
 
This is on the un-installation guide: 
 
If the ATI Proprietary Linux Driver was installed using either the Automatic or 
Custom options, then do the following: 

1 Launch the Terminal Application/Window and navigate to the /usr/share/ati folder 

***I DON'T KNOW HOW TO NAVIGATE IN TERMINAL SO THIS MAY BE MY ERROR***
I entered the line exactly as they wrote it but to no avail...

2 With superuser permissions, enter the command "sh ./fglrx-uninstall.sh" 
You have now successfully uninstalled the ATI Linux Proprietary Driver.

---

### Post by in0v8 on 2009-07-17
When you open the Terminal you should see something the equivalent of:

username@machinename:~$

Type this:

cd /usr/share/ati

Which will give you:

username@machinename:/usr/share/ati$

Then type the command you quote, i.e.

sudo sh ./fglrx-uninstall.sh

---

