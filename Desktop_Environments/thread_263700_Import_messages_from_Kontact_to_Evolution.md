---
title: "Import messages from Kontact to Evolution"
date: 2006-09-23
forum: Desktop Environments
---

### Post by michelev on 2006-09-23
Hi all,

last days I installed ubuntu, on my old pc I have Suse 9.3 and all my messages on Kontact.
somebody knows how can I import to Evolution all messages?
Tnx to all, bye

michelev
[-o<

---

### Post by henriquemaia on 2006-09-24
To import from Kmail, just go the **preferences** menu on evolution, go to **Mail Accounts**, choose **Add**, create a temporary account, giving it a suggestive name and using as **Server Type** the **Maildir-format mail directories**. Point it to the folder ~/Mail. Just create phony entries for everything else to get it going. After that, you'll see the entry on the side pane with the new created account. Just browse it and you can take everything out of the old folders to where you want them.

**WARNING**: backup your Mail folder first, since after you open it in Evolution and then revert back to Kmail, the folder structure in Kmail will be broken.

---

### Post by gnetgnat on 2006-10-07
I stumbled across a way to import mail from Kmail to Evolution.  This process saved me a ton of time.

First off, my Kmail version was 1.9.1, my Kontact version was 1.2, and my Evolution version was 2.6.1.

1)  In Kmail (Kontact) set up a folder in the MBOX format.

2)  Move the messages that you want transferred from Kmail to Evolution in this folder.

3)  Close Kmail.

4)  In your "Home Folder" in "View" click "Show Hidden Files".

5)  Goto the ".kde" folder and drill down to "/kde/share/apps/kmail/mail".

6)  Highlight the "mail" folder, right click the mouse and copy it.

7)  Go back to your "Home Folder" again and "Paste" the "Mail" folder in your "Home Folder".  You should see the mail folder in the main "Home Folder" once you paste it.

8)  Open the "Evolution" program.

9)  Under "File" click "Import".

10)  Click "Forward" when the Evolution Import Assistant appears.

11)  Click the "Import Data and Settings From Older Programs".

12)  Select "Mail" and click "Forward".  (I didn't do the addresses so I'm not sure of the results of that.)

13)  Click "Import" and all of the files that where in the "Mail" folder that you pasted in your "Home Folder" will be imported to Evolution.  The folder that you created in the "MBOX" format will be in that folder just as you put them there in Kmail/Kontact.

14)  Your other files like "Inbox, Outbox, Send Mail", etc will also import".  They will have subfolders and your messages will be in the "CUR" subfolder.

15)  By making the "MBOX" folder in Kmail/Kontact first eliminates this from happening.

Enjoy and I hope this helps as it helped me.

GnetGnat

---

### Post by michelev on 2006-10-08
DONE.

thanks to all
michelev

---

