---
title: "KDE mail questions"
date: 2005-04-17
forum: Desktop Environments
---

### Post by drx on 2005-04-17
These are some simple questions, but i could not find out to resolve them so i'd like to ask some people with more KDE experience:

On an IMAP account, how i can i set that sent messages go to the remote "sent" folder and not to the local one?

And, if i set the attachment icon to appear in the list view, how to permanently position it in front of the subject line? By dragging it into position, it will only stay there for the current session of the Kmail software. After exiting it and starting again, the attachment icon will be after the subject line again.

Thanks!

---

### Post by claydoh on 2005-04-17
My Sent folder for my imap mail acount is not local, I just set it up in kmail and all  my sent/trash/etc  that I had set up in Thunderbird were automatically set up. I believe when you create a folder locally it iis created on your mail server and your mail cliient just syncs to that.

In thunderbird I had no trouble moving my attachment icon to the front, it stayed there for me, can anyone else reproduce this?

---

### Post by drx on 2005-04-18
[QUOTE=claydoh]My Sent folder for my imap mail acount is not local, I just set it up in kmail and all  my sent/trash/etc  that I had set up in Thunderbird were automatically set up. I believe when you create a folder locally it iis created on your mail server and your mail cliient just syncs to that.

In thunderbird I had no trouble moving my attachment icon to the front, it stayed there for me, can anyone else reproduce this?[/QUOTE]
 Sorry, i meant the program KMail, the Mailer of KDE.
Thunderbird works fine, that's true. I just thought for the sake of better Desktop integration i should try KMail.

---

### Post by kal_zakath on 2005-04-18
Hi,

To set KMail using your imap sent folder and dratfs folder, you have to :

- Correctly set up an identity for the email adress of this account (Configure --> Configure Kmail --> Identities)

- Go to : Configure --> Configure Kmail --> Identities -> Advanced options and there you can set up the folders you want.

About the attachement icon, I don't exactly understand what you really want to do... ?

---

### Post by drx on 2005-04-22
Thanks kal_zakath, this setting with sent folders worked fine! I feel stupid for not finding it myself.
What i want to do in the message list pane is to move the column with the attachment icon in front of the subject line. For this i right click on the column header and choose "attachment", then the icon appears behind the subject. I can drag it to another position, but it will not stay there. Probalby a bug in the KDE Mail client?

---

