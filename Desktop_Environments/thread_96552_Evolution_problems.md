---
title: "Evolution problems"
date: 2005-11-29
forum: Desktop Environments
---

### Post by auer on 2005-11-29
Hi,
I am using Ubuntu Breezy for some time now, but since last week, I am experiencing problems with evolution. The problems started last week when no messages in the INBOX folder where displayed anymore, even if the info said that there are unread messages. For subfolders, everything works fine and all mesagges are displayed properly. When a new message arrives, it even gets correctly inserted in one of the subfolders based on the filter rules I defined.

I tried to reconfigure evolution, but since then, I can't access my IMAP account any more. I know that the account is working, because I can access it from Thunderbird, but evolution does not even log in to get the certificate from the server, it just times out.

---

### Post by ad noiseam on 2005-11-29
I am not sure that this will help, but try this:

-create a subfolder somewhere in Evolution
-go to your Home folder, "show the hidden files", and go to the "./evolution/mail/local" folder.
-copy the "inbox" file (the one without an extension) to your desktop
-drag and drop this file from your desktop to the message list pane in your newly created subfolder (this means: click on the subfolder in evolution, then drag the file where messages would be listed)

If everything works, your messages which you could not read should appear there.

Good luck, I hope it works.

Nicolas

---

### Post by auer on 2005-11-30
Thanks for your help, I tried it, but it doesn't work. The only message displayed is the evolution welcome message, but none of my emails in the INBOX gets displayed there.

Looking at the files in the .evolution directory, I noticed that the mail/inbox/myemailaccount/folders/INBOX contains a file for every mail, so it fetches the mail correctly. I'm really out of options now, the last one seems to use another mail client.

---

### Post by ad noiseam on 2005-11-30
[QUOTE=auer]Looking at the files in the .evolution directory, I noticed that the mail/inbox/myemailaccount/folders/INBOX contains a file for every mail[/quote]

For every mail? This is weird, I personally have files for every folder, but not for every message.

In this case, did you try drag and dropping these files in a folder in evolution?

Also, stupid question, but are you sure that your search bar (on the top of the message list pane) is not set to filter your emails according to some criteria?

Nicolas

---

### Post by brummie on 2005-11-30
You are not alone, i had a similar problem.

i use IMAP and altough evolution could see all the folders it would not show me the contents of my Inbox. 

i switched over to thunderbird in the end because i couldnt figure it out.:(

---

### Post by auer on 2005-11-30
[QUOTE=ad noiseam]For every mail? This is weird, I personally have files for every folder, but not for every message.

In this case, did you try drag and dropping these files in a folder in evolution?
Nicolas[/QUOTE]
There are even two files for every message: One file with the extension .HEADER and one file containing the message itself (The files are numbered, so for the first message there are files 1 and 1.HEADER). Just to make sure, these files are in the .evolution/mail/imap/folders/INBOX folder, not in the .evolution/mail/local hierarchie.

[QUOTE=ad noiseam]
Also, stupid question, but are you sure that your search bar (on the top of the message list pane) is not set to filter your emails according to some criteria?
Nicolas[/QUOTE]
This was my first initial guess, I've hit the clear button several times now :-)

---

### Post by ad noiseam on 2005-11-30
[QUOTE=auer]There are even two files for every message: One file with the extension .HEADER and one file containing the message itself (The files are numbered, so for the first message there are files 1 and 1.HEADER). Just to make sure, these files are in the .evolution/mail/imap/folders/INBOX folder, not in the .evolution/mail/local hierarchie.[/QUOTE]

Ah, sorry. From your first post, I thought you had problems with POP and IMAP, and I tried to help you with the POP emails trouble. I have no idea how IMAP works. :-(

Good luck.

Nicolas

---

### Post by BathroomNinja on 2005-12-03
I'm having the EXACT same problem.  It was working fine for 3 days, then BLAM! the Inbox doesn't display any emails, but other folders display fine.  The Inbox even shows how many unread emails I have.  Everything works great in Thunderbird and on another Ubuntu system with Evolution.

Also, I'm using IMAP

---

### Post by nerdroger on 2006-01-07
Has anybody fixed this yet?  I am having the exact same problem.  Other folders display fine.  Inbox knows how many emails are there.  No filters active.   I cannot see anything in the Inbox.

In the interim, I am using Thunderbird.  But I would like to use Evolution to take advantage of its organizational qualities.

Any ideas to fix this?
Roger

---

