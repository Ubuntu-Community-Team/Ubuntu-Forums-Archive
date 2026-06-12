---
title: "Evolution keeps regenerating my cleared trash"
date: 2009-11-06
forum: Desktop Environments
---

### Post by silbar on 2009-11-06
Greetings,

Running 9.04.  My Evolution has been set up, for some time, to empty the trash when I exit Evolution.  However, lately it somehow has begun regenerating the trashed messages that were earlier emptied.  Has anyone else seen this problem?  And solved it?

I tried looking in the .eveolution/mail/local/mail/ directory for a Trash folder, but there is none there.  These emptied out messages must be stored somewhere on the computer (and in my account?), but where are they?

   Dick Silbar

---

### Post by silbar on 2009-11-11
Greetings, again,

There were 20 folks who looked at my previous posting but no comments or suggestions.  Has no one else seen this problem?

Anyway, for reasons unknown to me, the problem seems to have gone away.  When I booted up this morning the trash folder was empty.  I have no idea if it was something I did or not.

   Dick Silbar

---

### Post by dumblebee100 on 2009-11-11
> **silbar said:**
> Greetings, again,

There were 20 folks who looked at my previous posting but no comments or suggestions.  Has no one else seen this problem?

Anyway, for reasons unknown to me, the problem seems to have gone away.  When I booted up this morning the trash folder was empty.  I have no idea if it was something I did or not.

   Dick Silbar

I have some similar problem but not the same as yours
I have gmail account 
even when I delete some mails it remains in ALL MAIL folder 
when I delete from ALL MAIL ..temporarily it gets deleted but when synced second time all mails come again ( which are deleted previously) 
at present I have only one solution ...goto gmail web interface and delete those mails even from the ALL MAIL folder 

this applies to you only if u are using gmail imap account

---

### Post by dumblebee100 on 2010-01-11
> **dumblebee100 said:**
> I have some similar problem but not the same as yours
I have gmail account 
even when I delete some mails it remains in ALL MAIL folder 
when I delete from ALL MAIL ..temporarily it gets deleted but when synced second time all mails come again ( which are deleted previously) 
at present I have only one solution ...goto gmail web interface and delete those mails even from the ALL MAIL folder 

this applies to you only if u are using gmail imap account

hey I found a solution for my problem ..hope you can also work on it 

All I have to do is to select the messages which are to be deleted then move to the GMIAL folder thrash ..I mean network folder thrash( not local trash ) ..then goto the GMAIL: --> Trash then delete the mails ...then these mails get to the local trash folder ..then u can delete the mails from local trash by using shift delete I mean permanently ...whenever you are in network trash I mean gmail trash you only get option to delete and not shift delete ..thats what u need to see where you are and which trash folder you are in ...
telling u the procedure in simpler ways

select mails to be deleted
move them to GMAIL:Trash
goto GMAIL:trash select all the mails
move to Trash folder (local ones)
then goto Trash and delete mails

This is the case with Gmail for me ..now I need not goto web interface to delete my mails 
Hope this works for u

---

### Post by Aleksandar_B on 2010-02-26
I also had this problem. Here are the steps I took to solve the it.

Note: I set Evolution to empty Local Thrash when closed.
Note: Messages moved to Gmail Thrash (in Evolution) are also found in Thrash folder through Gmail's web interface. 
Note. Messages deleted from All Mail folder are deleted permanently from all folders including Inbox and Labeled folders.

Delete from Inbox:

[LIST=1]
[*]Select message(s) to be deleted from Inbox
[*]Delete message(s)
[*]Message(s) goes to Local Thrash
[*]Close Evolution or right click on Local Thrash folder -> Empty Thrash
[*]Local Thrash empties, and the message is gone
[/LIST]
  The above method is also aplicable for deleting messages from Labeled folders besides from Inbox, but a copy of the message(s) is saved in All Mail folder regardles of do you delete them from Inbox or not.
When I delete a message from Inbox and go to Local Thrash and try to restore them they do not appear in Inbox any more.

Delete from All Mail (the wrong way):

[LIST=1]
[*] Select message(s) to be deleted from All Mail
[*]Delete message(s)
[*]The message(s) go to Local Thrash
[*]Restart Evolution or right click -> Empty Thrash
[*]Deleted message(s) are restored in All Mail
[/LIST]
  Messages deleted from the All Mail folder in the proces described above are restored in All Mail folder after Evolution is restarted or Empty Thrash command is given, so here is the right way to delete message(s) from All Mail folder.

Delete from All Mail (the right way):

[LIST=1]
[*] Select message(s) to be deleted from All Mail
[*]Drag the message(s) to Gmail Thrash
[*]Delete message(s) from Gmail Thrash
[*]Deleted message(s) go into Local Thrash
[*]Restart Evolution
[*]Message(s)are deleted.
[/LIST]

---

