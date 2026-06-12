---
title: "Evolution - How to create a folder for each account"
date: 2009-02-24
forum: General Help
---

### Post by Meados on 2009-02-24
Hello, I am having a problem with evolution, I have some accounts, but the emails received from all go to just one folder, I would like to have a folder for every single account.

How can I configure that?

Thanks.

---

### Post by demosthenese on 2009-02-24
Create the folders then Message->Create Rule->Filter on Recipients.

Set the recipient to your account email address and the action to Move to Folder and select the relevant folder.

---

### Post by Meados on 2009-02-24
> **demosthenese said:**
> Create the folders then Message->Create Rule->Filter on Recipients.

Set the recipient to your account email address and the action to Move to Folder and select the relevant folder.

There aren't other way?

Because I still receive emails that the recipient is not any of my emails..

---

### Post by demosthenese on 2009-02-24
Untested here but...

First you will need to look at the full headers of one of the messages you want to route to the folder. Use View-> All message headers.

What you are looking for is a header that is unique to a particular mail server. For example the mail I collect from gradwell.net always contains a header line starting: 'X-gradwell-pop3:'

Then open Edit->Message Filters

Add a filter and change the filter option to 'specific header', add the header string (e.g. X-gradwell.pop3) to the first text box. Alter the next option list from 'contains' to 'exists'.

Finally select your action as 'Move to Folder' and select the folder.

---

### Post by dcstar on 2009-02-24
> **Meados said:**
> There aren't other way?

Because I still receive emails that the recipient is not any of my emails..

Use IMAP connections.

---

