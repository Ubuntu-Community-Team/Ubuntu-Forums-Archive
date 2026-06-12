---
title: "Evolution inbox emails gone!"
date: 2010-12-01
forum: Desktop Environments
---

### Post by captainKrash on 2010-12-01
A friend of mine is using evolution on Ubuntu 8.04 (or 8.10) and all of a sudden he reports to me that his evolution inbox is gone/empty. 

I don't have access to his machine (being 300 miles away) and reconfiguring his modem/router for remote access is like too painful - it won't happen. 

I have tried to figure out what has happened and am stumped (I don't use Evolution myself). All I have to go on is this screenie. Does anyone have any suggestions - apparently a few thousand emails have just gone AWOL.

Any pointers would be appreciated - greatly. I have searched before posting and can't find anything that seems relevant to his situation (eg not exchange etc).

Thank you!

---

### Post by ajgreeny on 2010-12-01
Is this a pop or imap account he is using?

First thing to do is look in the hidden **home/user/.evolution** folder in his home where the mail may be still sitting.

If imap, there may be no problem, as the mail should still be on the server, assuming he has not deleted it from there manually.

If pop, it will depend on the settings he is using for the account, what the mail server is set to do when mail is downloaded, etc etc.

Try to find out more about the detail of his situation and report back.

---

### Post by captainKrash on 2010-12-03
Hi There,

Sorry for the delay replying. 

Yes, I got him to cd into his home dir and ls -al, the .evolution folder is there and further to this I got him to cd mail/local and ls -al. His output is something like this for inbox:

-rw------ 1 user user 221610049 2010-11-11 11:12 Inbox

Where the date and time is the last time he saw any email in the inbox.

It is set as pop (I think), but as he uses google apps for email the mail is all still accessible online. The main issue he faces now is more to do with being able to download mail to Evolution as he uses pgp to decrypt messages within Evolution. Something he is currently unable to do (if he presses send/receive - mail seems to disappear into oblivion).

I don't really want to get him uninstalling Evolution and reinstalling as pgp set up would be an utter nightmare.

Thank you!

---

### Post by ajgreeny on 2010-12-03
I am not sure I can help any more.  I certainly know nothing about pgp and evolution, and don't even use evolution myself, I am on thunderbird.

---

### Post by ZeroFossilFuel on 2011-01-18
I just ran into something very similar. I created my first filter to move incoming email from a particular domain to a sub-folder. It worked but unfortunately it also hid ALL of my read messages. Show hidden does not restore them.

If I navigate to /home/user/.evolution/mail/pop all of my email accounts still appear there as sub-folder names. Within those subfolders are cache/numbered_folders/messages, one to several messages per sub-folder. All of my Evolution accounts are set up as POP, even my Gmail.

How do I restore them to the tree view in Evolution? Very annoying.

---

