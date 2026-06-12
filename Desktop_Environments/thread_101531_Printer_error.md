---
title: "Printer error"
date: 2005-12-10
forum: Desktop Environments
---

### Post by WBC on 2005-12-10
On a new install of Kubuntu I have the printer installed as a network printer and it found it and it is installed but when I print I get this error:

A print error occurred. Error message received from system:

cupsdoprint -P 'HP720C' -J 'KDE Print Test' -H 'localhost:631' -U 'bill' -o ' multiple-document-handling=separate-documents-uncollated-copies orientation-requested=3' '/usr/share/apps/kdeprint/testprint.ps' : execution failed with message:
client-error-not-possible 


Does anyone know what the above indicates?
 What should I do?

WBC

---

### Post by WBC on 2005-12-10
This is WBC again,
I reinstalled the printer using the KDE GUI - system settings, printer, add, other printer type, SBM windows, Hp720C".

The printer installs, and when I test the printer the screen reports that it sent "Test page successfully sent to printer" but nothing happens?
I checked the system log and it reports:
--  
12/10/2005 10:27:10 AM	localhost	pnm2ppa[7116]	read_config_file(): error parsing config file at line 18 
--
What should I do?  I am out of ideas as this is the same Linux print driver that other Linux app's have used when installing a printer with no problem?
Thanks,

WBC








































'System settings, printer"!

It is attached to a network Windows XP system on my lan with the same workgroup name.  The printer installs normally and uses the same print driver that any other Linux printer uses for a SMB Cups printer but after clicking test printer I get "sent successfully" but nothing happens.  I looked in the system Log and it reports on the last line:
---
12/10/2005 10:27:10 AM	localhost	pnm2ppa[7116]	read_config_file(): error parsing config file at line 18 

---
What do I do about that?
Does anybody know how to fix this?

WBC

---

