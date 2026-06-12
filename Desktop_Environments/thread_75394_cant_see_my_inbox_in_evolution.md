---
title: "cant see my inbox in evolution"
date: 2005-10-13
forum: Desktop Environments
---

### Post by soma on 2005-10-13
HI!

After upgrading to breezy, i can't see my mail in the inbox in evolution. The mails are there though, and when i get new ones they appear in the left listning as a "new mail" but they are not listed in the main window, nothing is.

I get the mail from an IMAP server, and the funny thing is that the other folders i have with emails in them, with the same account, actually appear. Just not the INBOX.

Any clues why this is like this?

---

### Post by meeiw on 2005-10-14
I have the same problem :( 
The first time i started evolution i saw my messages (I'm pretty sure), but after a restart they dont appear anymore.

---

### Post by ajhobbs on 2005-10-14
Same issue.  Hoary upgrade to Breezy, completed with no other issues.

Evolution worked fine in Hoary, however it does not display any messages in the INBOX of my IMAP4rev1 server account.  Server is a Courier IMAP system that orders by

\INBOX
\INBOX\Sent
\INBOX\Archive
etc.

Can check by webmail, but still somewhat annoying.  Any ideas?

---

### Post by calvinpriest on 2005-10-14
I have the same problem.  

I've discovered that if I drag a message from another folder into the Inbox, it too disappears.  But then if I go into Thunderbird, I can see that message in the Inbox.  So clearly it can access the Inbox folder, but for some reason it's just not displaying.

I am also using Courier IMAP.

---

### Post by calvinpriest on 2005-10-14
Ok, turns out this can be fixed by unsubscribing and resubscribing to all folders:
[http://www.ubuntuforums.org/showthread.php?t=64222&highlight=breezy+evolution+inbox](http://www.ubuntuforums.org/showthread.php?t=64222&highlight=breezy+evolution+inbox)

---

### Post by ajhobbs on 2005-10-14
Tried.  Unfortunately, Evolution proceeds to claim that Subscriptions are not supported by my IMAP server.  Given that I can subscribe/unsubscribe all day long with Squirrelmail makes me wonder what's going on.

I found a message thread that stated Evo sometimes has issues.  The solution proposed there was to remove the courierimapsubscribed file in the Maildir folder of the server.

Removing that doesn't help.

For now, moving to Thunderbird until I find a better fix.

---

### Post by calvinpriest on 2005-10-14
You might also try creating a new mail account/profile in Evolution (Edit->Preferences->Add).  That's what I was going to try next if the Re-subscribing thing didn't work.

---

### Post by Hendrik van den Boogaard on 2005-10-15
I have the exact same problem here and it's driving me nuts!

After upgrading a few machines first to breezy RC, this started to appear. I have the following layout on my own IMAP server:

/home/hendrik/mbox
/home/hendrik/IMAP-Mail
/home/hendrik/IMAP-Mail/Sent Items
/home/hendrik/IMAP-Mail/Drafts
/home/hendrik/IMAP-Mail/Some Folder
/home/hendrik/IMAP-Mail/Some Folder/Person 1
/home/hendrik/IMAP-Mail/Some Folder/Person 2

etc.

Further I have a lot of other folders in /home/hendrik and a lot of other files too (obviously, it is my home dir :))

I tried the following options:
1. Just took all my settings from ubuntu hoary to breezy, INBOX disappears (which is is mbox file in /home/hendrik) but all other IMAP-Mail folders are there.
2. Tried settings from my Debian Unstable, same problem appears
3. Tried to remove .gconf/evolution and .evolution, made new IMAP account, same problem
4. Tried to set it to IMAPv4 instead of standard IMAP, ah there is my INBOX again but NOT the other folders!
5. Tried my girlfriends account, same problem
6. Tried my girlfriends account on IMAPv4, ALL WORKED WELL. however, after some checking I found out that in her homedir a file '.mailboxlist' was there and that when using IMAPv4 it checked THIS file for all subscribed folders, though 'only show subscribed folders' was not ticked and subscribing to folders does not work.
7. Tried subscribing on my own account in IMAP settings, still the INBOX does not appear and evolution does not seem to check that .mailboxlist file at all.
8. Tried all kind of combinations of ticking and unticking boxes to override the folder name space but nothing works. Only thing that works is to setup 2 accounts, with same login, 1 as IMAP (for all the folders) and 1 as IMAPv4 for the INBOX. But that's not really a soltution to me and all worked fine before even in my Debian Untstable, updated till last week.
9. Tried to check thunderbird if I was crazy, there it works just fine.

So there does not seem to be a solution and I think it's a nasty bug. Now, how does this situation gets fixed....

Glad to hear some options or see a 'security update' to be released :)

---

### Post by gdcondor on 2005-10-15
unsubscribing from the INBOX (menu Folder/Subscriptions - not sure about the translation i'm using the french version) and then subscribing again solved the pb for me !
maybe during the updating process it forgets to create a new file used by Evolution 2.4 (and not 2.2) to deal with subscriptions...

I hope it can also work for you as it's really annoying !

---

### Post by Hendrik van den Boogaard on 2005-10-17
The problem is that in the subscriptions the INBOX just is not listed, so I cannot subscribe to it. Furthermore, I have not ticked the box 'show only subscribed folders' so it *should* display everything. (However I tried using the options 'show only subscribed folders' too resulting in the same behavior; no INBOX is shown).

I really think this is a bug, Thunderbird works fine and my old Evolutions worked fine for that last 2 years (using Debian Unstable, which I kept updating).

---

### Post by jetpeach on 2005-10-19
have the same problem trying to set up evolution.  but for me, I'm also having no luck in thunderbird.  on my windows machine, it works fine and I've double checked the settings/name of the server 10 times now.  for SSL connections on port 993, do I have to install additional packages in Breezy?

---

### Post by Mokona on 2005-11-02
A thing worked for me : my mail box was in IMAP4rev1 and some folders were not shown.

I edited it (in Preferences) and put the box in IMAP4. All the folders appeared. But in the subscription panel, the folders were not checked. I checked them, put the box back to IMAP4rev1 and there they are, the folders are shown.

---

### Post by amasidlover on 2005-11-03
I also have this problem on my wife's laptop - it is solved by unsubscribing and subscribing, but I have to do all folders and have to do it each time I restart evolution! My wife only has 8 folders so its just very annoying for her, I have over 100 which  means this is blocking me from upgrading my own laptop and desktop - does anyone know whether this is unique to ubuntu or does it occur with other distros?

---

### Post by amasidlover on 2006-01-13
Hi,

This bug is now fixed in Evolution 2.4.2.1!

Alex

---

### Post by jesterfred on 2006-06-28
But broken in version 2.6.1

I am using the 6.06 ubuntu server install and its dovecot for the IMAP server.  I use 6.06 and its Evolution for the client which is currently 2.6.1.  I have no Inbox.  If I use Thunderbird, all is well.

---

### Post by x-static on 2006-10-22
I am running Evolution 2.6.1 and I also had this problem.

I found changing the ServerType from IMAP4rev1 to IMAP in the account settings corrected the issue.

[http://www.ourborus.biz]("http://www.ourborus.biz")

---

### Post by marx2k on 2006-11-06
I am running evolution 2.8.1 and am experiencing this exact same problem.  Unable to see the INBOX folder in the main screen.

---

### Post by marx2k on 2006-11-06
I am able to read my mail with a text editor... it's  ~/.evolution/mail/local/inbox

---

### Post by marx2k on 2006-11-09
Does no one have a solution for this problem?? It seems like a number of people are having the same issue, including myself! Anyone? Anyone?

---

