---
title: "Thunderbird and root mail!"
date: 2012-03-18
forum: Desktop Environments
---

### Post by youngunix on 2012-03-18
I have spent a couple of hrs trying to configure thunderbird to receive root mail, using these tutorials (they are pretty much the same):
[http://ubuntuforums.org/archive/index.php/t-7321.html](http://ubuntuforums.org/archive/index.php/t-7321.html) 
[http://ubuntuforums.org/showthread.php?t=7321](http://ubuntuforums.org/showthread.php?t=7321)
[http://www.ubuntugeek.com/howto-forward-roots-mail-to-your-inbox.html](http://www.ubuntugeek.com/howto-forward-roots-mail-to-your-inbox.html)

[SIZE=2]**None of them work!**[/SIZE]](*,)

If anybody happened to solve this issue, shout!

---

### Post by SeijiSensei on 2012-03-18
Why not just add an alias for root that directs its mail to your own account?  Edit (as root with sudo) the file /etc/aliases and add a line like this:

```
root:      myusername
```

replacing "myusername" with your own username.  Then run the command "sudo newaliases" and all root's mail will come directly to you.

Another option, if you have [procmail]("http://partmaps.org/era/procmail/mini-faq.html") installed, is to write a .procmailrc file in /root that contains "recipes" for how root's mail should be handled.  With procmail, you can write a rule that sends mail with specific headers to one account, mail with other headers to another account or a folder within an account, and delivers the remainder by default to root's inbox.  If procmail is installed, type "man procmailrc" and "man procmailex" at the terminal prompt to get help on its syntax.

---

### Post by youngunix on 2012-03-18
> **SeijiSensei said:**
> Why not just add an alias for root that directs its mail to your own account?  Edit (as root with sudo) the file /etc/aliases and add a line like this:

```
root:      myusername
```replacing "myusername" with your own username.  Then run the command "sudo newaliases" and all root's mail will come directly to you.
Already tried that, does not work.

> Another option, if you have [procmail]("http://partmaps.org/era/procmail/mini-faq.html") installed, is to write a .procmailrc file in /root that contains "recipes" for how root's mail should be handled.  With procmail, you can write a rule that sends mail with specific headers to one account, mail with other headers to another account or a folder within an account, and delivers the remainder by default to root's inbox.  If procmail is installed, type "man procmailrc" and "man procmailex" at the terminal prompt to get help on its syntax.

I only use thunderbird, not interested in other mail services.

thx tho

---

### Post by PapaGary on 2012-03-18
> **youngunix said:**
> 
I only use thunderbird, not interested in other mail services.
Thunderbird is not a mail service, it is a client.

---

### Post by youngunix on 2012-03-18
> **PapaGary said:**
> Thunderbird is not a mail service, it is a client.

I don't see how that is helping with the issue!

---

### Post by SeijiSensei on 2012-03-19
> **youngunix said:**
> Already tried that, does not work.

You realize that I'm talking about adding an alias on the mail server, not the machine running Thunderbird, yes?  The same holds true for procmail.  That's a "mail delivery agent" that used by the "mail transfer agent" to handle local delivery.  On stock Ubuntu systems the "MTA" is Postfix and the MDA is either mail.local or procmail.

None of this has anything to do with Thunderbird.  These suggestions concern what the server does with mail addressed to the root account before it is read with a POP or IMAP client like Thunderbird.

---

### Post by chaarmann on 2012-05-31
First step: copy all already existing root messages (emails) to your user account:
Copy /var/mail/root  to /var/mail/username. 
You must replace the word "username" with your own account name that you can get by typing "whoami" in a terminal window.
Set the access rights for the copied folder so your user account can read and write to it. (owner=username:mail)

Second step: get future messages from root delivered to your own email account:
Just make the  alias as described above or forward from root by creating the file /root/.forward with the text "username@localhost" inside. You must replace the word "username" with your own account name that you can get by typing "whoami" in a terminal window.

Third step: read the messages from your account intoThunderbird:
In Thunderbird, select from menu: "Edit" --> "Account Settings" --> "Account actions" --> "Add other Account". Then checkmark  "Unix Mailspool(movemail)" and click "next".  The last edit box reads "Email Address: username@(none)". Replace "(none)" with "localhost". and click "next". In this page with title "Server Information" I unchecked "Use Global inbox", because I didn't want to mix my normal mails with the system mails. Then I clicked "next". Now it asks about the new inbox. I named it "System". After some more settings (I selected all options to automatically check and download messages) the new email account was finally showing up on the left side below my old account. Then I went to its inbox and pressed "get mail" and voila, the inbox was filled with all the system mails for root.

---

