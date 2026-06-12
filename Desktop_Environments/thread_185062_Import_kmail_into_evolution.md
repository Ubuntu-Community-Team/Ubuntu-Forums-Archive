---
title: "Import kmail into evolution"
date: 2006-05-31
forum: Desktop Environments
---

### Post by nickle on 2006-05-31
How can I import my kmail files into evolution? Evolution offfers import options for may mail clinets but not kmail!!! Thats odd...

---

### Post by Tamihania on 2006-05-31
[quote=nickle]How can I import my kmail files into evolution? Evolution offfers import options for may mail clinets but not kmail!!! Thats odd...[/quote]

...just trying to help you! :) AFAIK both mail clients use the same format to import and export Contacts and Calendar...

tami :)

---

### Post by henriquemaia on 2006-05-31
[quote=nickle]How can I import my kmail files into evolution? Evolution offfers import options for may mail clinets but not kmail!!! Thats odd...[/quote] 
To import from Kmail, just go the **preferences** menu on evolution, go to **Mail Accounts**, choose **Add**, create a temporary account, giving it a suggestive name and using as **Server Type** the **Maildir-format mail directories**. Point it to the folder ~/Mail. Just create phony entries for everything else to get it going. After that, you'll see the entry on the side pane with the new created account. Just browse it and you can take everything out of the old folders to where you want them.

**WARNING**: backup your Mail folder first, since after you open it in Evolution and then revert back to Kmail, the folder structure in Kmail will be broken.

---

### Post by nickle on 2006-05-31
Thank you very much..

But it does seem rather an primative way for exchanging the information... I would have expected evolution and kmal would have had a better way of exchanging information???

---

### Post by henriquemaia on 2006-05-31
[quote=nickle]Thank you very much..

But it does seem rather an primative way for exchanging the information... I would have expected evolution and kmal would have had a better way of exchanging information???[/quote] 
Yes, I  also think so. It's rather strange, but maybe there aren't too many people doing migrations from Kmail into Evolution.

---

### Post by burlap on 2006-06-02
Evolution uses standard ways to deal with email, kmail is probably similar (I use Evolution) - import feature is necessary only when you need to import additional stuff (like account settings) or mailboxes come in a strange format. 

To import from kmail (workaround, as I said I don't use kmail):
1. Select all messages you want to export in kmail. 
2. Save these messages to a file (File -> Save or something like this).
3. In Evolution go to File -> Import and select "Import a single file". Find your file and select import. (You might also try to drag and drop this file into a relevant Evo folder - no need to go through importing).
4. Repeat for all kmail folders you want to export.

---

### Post by megadodo on 2006-06-02
Yet Another Way to Do it...
[http://www.ubuntuforums.org/showthread.php?t=156097](http://www.ubuntuforums.org/showthread.php?t=156097)
Worked for me. But yeah, its a pain that kmail or evoloution cant do this themselves.
Rich

---

