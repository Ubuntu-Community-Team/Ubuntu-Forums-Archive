---
title: "CUPS doesnt work"
date: 2005-12-18
forum: General Help
---

### Post by Brando569 on 2005-12-18
i posted a thread on here a few days ago asking how i could save my printer settings in cups and someone responded and what they said didnt work, so i was browsing through stuff and wondered into the cups configuration, i changed something but i forget what and now it wont let me print anything! ive tried deleting and reinstalling my printer and all of the cups packages except for cupsimage cuz that would of taken out a lot of things in KDE and that hasnt solved the problem. when i go into the cups config now via kcontrol it says this before i go into it:

Some options were not recognized by this configuration tool. They will be left untouched and you won't be able to change them.

configfileperm=0600
runasuser=yes
include=cupsd-browsing.conf

and this when i click the "save" button:

Unable to retreive the printer list. Error message received from manager:
Connecting to CUPS Server failed. Check that the CUPS server is correctly installed and running. Error: connection refused.

i really need to fix this ASAP. thanks

---

### Post by Brando569 on 2005-12-18
ahh error logs are a wonderful thing :) for some reason there wasnt a classes.conf in my /etc/cups directory so i just created an empty text file called classes.conf and as for those unknown commands i think thats what was throwing it off. at the end of cupsd.conf it said:

#unknown
then the commands were here

so i commented them out, deleted the error log, restarted cupsd as root and tried to print something voila! it worked :)

---

