---
title: "Thunderbird doesn't understand docx/xlsx attachments"
date: 2011-10-19
forum: Desktop Environments
---

### Post by pinkunicorn on 2011-10-19
Due to [http://ubuntuforums.org/showthread.php?t=1864844](http://ubuntuforums.org/showthread.php?t=1864844) I have temporarily (I hope) switched to Thunderbird to read my mail, but it doesn't seem to handle attachments well.

I have mail messages with attached docx/xlsx files, but Thunderbird only has archive handler and save as as options for the file, not LibreOffice which would be the obvious choise. Looking at old messages in Evolution, that has options for opening the files directly in LibreOffice. How to add them?

---

### Post by vanadium on 2011-10-26
In 11.10, where Thunderbird is the default mail application, the same annoyance persists.

You can change the association yourself: Edit - Preferences, Attachments, look up the appropriate file type, select "Use other" under "Action", and navigate to /usr/bin/soffice

---

### Post by caryb on 2011-10-31
Nope still wont work for me. have pointed to /usr/bin/soffice & still throws the error message.


Cary

---

### Post by hornetster on 2011-11-14
Sorry to break into this thread, but having an issue with docx attachments in 11.10, but the docx extension does not exist (doc etc does and works). How do you add the actual extension?
Thanks.

---

### Post by caryb on 2011-11-14
For 2 industry applications/formats I find it quite bizarre that this is still outstanding


Cary

---

