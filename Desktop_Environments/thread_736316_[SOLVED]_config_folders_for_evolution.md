---
title: "[SOLVED] config folders for evolution?"
date: 2008-03-26
forum: Desktop Environments
---

### Post by brook adams on 2008-03-26
Hi There,

I am running evolution 2.12.1 on ubuntu 7.10...

I used the restore utility to move old email from another machine running ubuntu 7.4

Everything worked except that the old machine had a different username which was backed up into evolution on the new machine. So now when I reply to an email, I get an error message that says I can't make a copy of the email into home/<olduser>/.evolution/mail/local so it is saving the copy into the current local folder.

The only problem is the error message because evolution thinks it is in the old machine.

How do I tell evolution that the .evolution folder is now in home/<newuser> not home/ <olduser> ?

Brook Adams

---

### Post by unoodles on 2008-03-26
couldn't you just copy and paste over?

or you could create a symbolic link in the new user pointing to the old users .evolution folder

---

### Post by brook adams on 2008-03-27
thanks for your reply...

I guess what I'm looking for is a config file with a PATH variable that looks like this:

home/<username>/.evolution/config or something like that.

I can find the mailbox files in there but I want to know where evolution keeps it's path info.

I've looked in /etc and /home/<username>/.evolution/config but to quote the band U2, "I still haven't found what I'm Lookin' for..."

Brook Adams

---

### Post by donniep152 on 2008-04-10
I've got the same issue and so far have not found an answer.
Anybody smarter than me is more than welcome to contribute.

Thanks,

---

### Post by brook adams on 2008-04-13
I went to the evolution forums and an English guy named Keith gave me this...

It worked for me.

        Edit Menu -> Preferences
        In Mail Accounts select your email account and click Edit
        Change to the Defaults tab
        Change the settings Drafts Folder and Send Messages Folder

Good Luck,

Brook Adams

---

