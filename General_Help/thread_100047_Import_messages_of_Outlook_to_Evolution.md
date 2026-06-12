---
title: "Import messages of Outlook to Evolution"
date: 2005-12-06
forum: General Help
---

### Post by filipenetto on 2005-12-06
Hy folk ...

I have a lot of messages on Outlook, and I wan't to export them to Evolution. I found a little application that export all messages of Outlook to Evolution. That is what it say ... I do the export process, and it export all messages to .html, but, I can't import this. 

I know that I could import this .html messages to other mail client (like Thunderbird), and them, export to Evolution, but is a lot of work :???: 

So, if someone know a way to do that, tell me, please.

Tks ... :)

---

### Post by flopsy on 2005-12-06
One way would be to sign up for a mail service that does IMAP. Transfer your messages from Outlook to the IMAP server (drag and drop). Then drag from the IMAP server to Evolution. Fastmail.fm is a free service which does IMAP.

If your mail provider (ISP?) has IMAP, consider using that instead of POP.

---

### Post by filipenetto on 2005-12-12
Hi flopsy, 

So, I found an application called "libpst". He read a .pst file and export messages to MBOX format. He works greatly! I export all my messages to Evolution.

Thank you for your sugest. :p

---

### Post by acegolfer on 2006-03-20
If you are using Outlook 2003 as in my case, libpst will not work. 

After researching for 2 hours, I found the simplest way to convert the messages in Outlook to Evolution is using IMAP. The following is a step by step procedure.

1. Set up a free IMAP account (google it) with at least 10MB storage.
2. In Outlook, add the IMAP account.
3. Starting from the latest emails in Personal Folders Inbox, copy them to the IMAP Inbox folder. (You should see 2 separate inbox folders, one for local and another for IMAP. Click Send/Receive to upload these emails to your remote IMAP server.) Don't be greedy and copy too many, or it will exceed your quota. 
4. In Evolution, add the IMAP account. Call this account "IMAP" not to confuse with your "On this Computer" folder. (You should see 2 inbox, one for local and another for IMAP.)
5. Click Send/Receive (Evolution will download the emails from the IMAP server)
6. Copy the emails in IMAP inbox folder to your local inbox folder (inbox folder in "On  this computer').
7. Delete and expunge (empty trash) your IMAP inbox folder (not the local inbox folder). Don't worry, the copied messages to your local inbox folder will not get deleted. 
8. Go back to Outlook and you should see empty inbox for your IMAP account because all messages were expunged in step 7.
9. Go back to step 3 and repeat until all emails are synched.

For example, if your inbox is 500 MB and your email quota at IMAP is 10MB, you need to make 50 trips. Google for free IMAP service with huge quota. With little cost, I managed to find 150MB IMAP account. Just 4 trips needed.

---

### Post by ArizonaKid on 2006-03-20
I know you said you don't prefer the Thunderbird method, but that really has been the most useful to me.

Outlook handles IMAP very bad, and I always had a lot of problems.  I admit using Thunderbird is a bit of a pain, but I haven't found any other methods more useful.

If anyone has any, please share.

---

### Post by jreinis on 2008-06-09
> **ArizonaKid said:**
> I know you said you don't prefer the Thunderbird method, but that really has been the most useful to me.

Outlook handles IMAP very bad, and I always had a lot of problems.  I admit using Thunderbird is a bit of a pain, but I haven't found any other methods more useful.

If anyone has any, please share.
Thunderbird does not correctly convert non-english languages (Cyrrilic, German, Arabic,Hebrew,Hindu and so on encodings) - this is the bug comes from netscape engine almost 10 years!

The REAL solution for non-english people is ONE only -> USE IMAP server :
You can run virtualbox - install windows + free IMAP Mail server software;
than just moved all messages from outlook accounts to your IMAP mail account;
than just connect evolution (open new temporary local account) to new IMAP mail server - as regular as Google etc. servers - and move all messages to your local evolution account.
This is simple and will be proper convert non-eglish encodings.
Because it will do as real as in real internet if you use real (google,yahoo etc.) mail servers.

---

