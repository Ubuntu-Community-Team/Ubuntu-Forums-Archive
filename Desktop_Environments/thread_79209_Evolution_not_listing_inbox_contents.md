---
title: "Evolution not listing inbox contents"
date: 2005-10-19
forum: Desktop Environments
---

### Post by idn on 2005-10-19
Evolution won't display the contents on my inbox from my IMAP server - the server is fine, it lists the contents of the other draft and sent folders, but it doesnt list anything in the inbox folder.

Has anyone else had any trouble with this?

---

### Post by idn on 2005-10-19
Just installed thunderbird and everything works ok, so its not my settings. Also, I just added a second mailbox in evolution but it only lists the one, shown in the screenie below:

---

### Post by matthew on 2005-10-19
The mailserver I use allows connections using both IMAP and POP. When I use Evolution to connect to the IMAP server it creates new folders in the section on the left of the screen for each folder on the IMAP server in my account.
i.e. Inbox, Sent, .bash_profile, everything...

In that mode I can read and interact with my email online, but it remains on the server. It is not downloaded and stored locally on my machine. I can still compose email.

If I connect to the same account using POP3, it works as you were expecting.

EDIT: I don't have a solution to offer, just an experience that might help you add a piece to the puzzle.

---

### Post by Mustard on 2005-10-19
I had a problem like this with Evolution once when I deleted some viruses  using some method outside of evolution to delete them.

I can't recall exactly how it happened now, but I was using clamd to scan some attatchments that had virii in them, I then deleted the virus attachments and from that time on I could not see anything in my inbox in Evolution.  I have a feeling that it was not long after that, that I restored the system from a  backup, so that might have been how I ended up getting it fixed.

As above, no solution, but perhaps a clue?

---

### Post by jpt2433 on 2005-10-19
I have the same problem using Evolution, but I prefer Thunderbird because it just works and Evolution always gives me so much trouble.

---

### Post by idn on 2005-10-20
Thanks for your comments, have gone to thunderbird, its a real shame because I would much rather use evolution. I think I may downgrade to hoary until breezy + when everything is a bit more faster and stable.

---

### Post by Hendrik van den Boogaard on 2005-10-21
The same problem is described in the following topic, however there does not seem to be a solution, except, changing to Thunderbird.

[http://www.ubuntuforums.org/showthread.php?t=75394](http://www.ubuntuforums.org/showthread.php?t=75394)

---

### Post by Andilek on 2005-10-21
I am using breezy, evolution and 3 IMAP email accounts. No problem with folders.

---

### Post by amanda on 2005-10-21
Hmph. Well, it was helpful to know that I am not crazy. I just installed breezy badger and was testing out evolution (and imap for the first time, so I can stop trying to move my filters around all the dang time between computers).

I can see that I have 12 unread messages in my evolution inbox, but they aren't showing up. 

Sounds like the solution is just to use thunderbird.

---

### Post by idn on 2005-10-21
Crap, hopefully it will get fixed with a backports update, I will file a bugzilla report

---

### Post by neptoon on 2005-10-21
Had the same problem some weeks ago ([http://www.ubuntuforums.org/showthread.php?t=68541](http://www.ubuntuforums.org/showthread.php?t=68541))

A solution is described in the Gnome bugtracking system: [http://bugs.gnome.org/show_bug.cgi?id=316369](http://bugs.gnome.org/show_bug.cgi?id=316369)

---

