---
title: "Installed Office 3, and Evolution spell check has gone to Turkish"
date: 2009-02-10
forum: General Help
---

### Post by Rockhoppers1964 on 2009-02-10
Hi there, i installed Open Office 3 on to Ubuntu 8.10, installation went well. but when i opened up Evolution, the language had gone to Turkish, as the spell check was not working right.

Looked on the forum and found i had to install the language-support-writing-en pack which i did and that uninstalled OO3 !

Help !

Andrew

---

### Post by sptrsn on 2009-09-28
I had the same thing happen. 

When I installed the english language from synaptic it said it was going to uninstall the Open Office debian menus. I didn't realize that meant the whole of Open Office. 

Should I just go ahead and re-install Open Office? I'm going to try. I'll let you know what happens.

Has anyone else run into this?

Ubuntu 8.1
Evolution 2.24.3
Open Office (hmmm. Can't remember, it's gone. LOL. But it was just last week I pulled it down.)

---

### Post by sptrsn on 2009-09-28
I've got a mess on my hands. 
I attempted installing Open Office again. got an error message saying:
"Error: Conflicts with the installed package 'openoffice.org-core'"

I attempted an uninstall with dpkg -r openoffice.org

To which the reply came...  
dpkg - warning: ignoring request to remove openoffice.org which isn't installed.

So. The installer says it can't install because it's already installed.
The uninstaller say it can't uninstall because it's not installed. 

Anyone have suggestions on where to go from here?

---

### Post by sptrsn on 2009-09-29
I think I fixed it. 
I'm a noob, so I don't know whether this is the right way or not, but it seemed to work for me. 
In Synaptic Package Manager, I selected every single OpenOffice item I could find for complete removal. 
I removed that english language add in from earlier. language-support-writing-en
I downloaded the current OOO file from Openoffice.org.
I then followed these directions closely...
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

3.1 is working. Evolution is working with an english dictionary.

Yeah.

---

