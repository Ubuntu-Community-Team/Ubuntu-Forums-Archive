---
title: "Evolution and imap"
date: 2005-11-08
forum: Desktop Environments
---

### Post by joselin on 2005-11-08
Hi all,

I have a problem when I access my email account via imap server. When i use any webmail I can see all messages in all the folders (inbox, sent, trash, and all custom folders), but when I access it via evolution, I can see all folders contents except inbox (the inbox shows only the number of unread messages, but I can't see the messages).  
  
Someone have the same problem? I need help...

Regards

---

### Post by nocturn on 2005-11-08
[QUOTE=joselin]Hi all,

I have a problem when I access my email account via imap server. When i use any webmail I can see all messages in all the folders (inbox, sent, trash, and all custom folders), but when I access it via evolution, I can see all folders contents except inbox (the inbox shows only the number of unread messages, but I can't see the messages).  
  
Someone have the same problem? I need help...

Regards[/QUOTE]

Can you try to subscribe to it?

---

### Post by joselin on 2005-11-08
[QUOTE=nocturn]Can you try to subscribe to it?[/QUOTE]

Yes, but without success.

Regards.

---

### Post by joselin on 2005-11-17
Anybody?

---

### Post by dcstar on 2005-11-17
[QUOTE=joselin]Hi all,

I have a problem when I access my email account via imap server. When i use any webmail I can see all messages in all the folders (inbox, sent, trash, and all custom folders), but when I access it via evolution, I can see all folders contents except inbox (the inbox shows only the number of unread messages, but I can't see the messages).  
 
Someone have the same problem? I need help...

Regards[/QUOTE]
Make sure that you clear any (and all) "Find now" searches for that folder.

I once made the mistake of inadvertently doing a search on my Inbox (which didn't find anything), then forgot that I had done it and didn't realise that it "stuck" and kept me from seeing any new posts as well as the existing ones!

Accidentally putting something in the "Find Now" area may well cause your problem.

---

### Post by brdweb on 2005-11-17
I have the same problem with evolution. Thunderbird is working just fine.

---

### Post by joselin on 2005-11-18
My search is complete clear.

With thunderbird work fine for me too.

Can be a bug in evolution?

---

### Post by viniosity on 2005-11-21
Check to see which kind of IMAP server you are set up to use.  There are two in evolution: IMAP and IMAP4v1.  You may need IMAP but are using IMAP4v1.

---

### Post by joselin on 2005-11-21
Now i know that there is a known bug.

This is the reply from the evolution team:


```

------- Additional Comments From Andre Klapper  2005-11-20 10:56 -------
hi, thanks for reporting this. it is a duplicate of the fixed bug 228929. should
be fixed when 2.4.2 is out (end of november).

*** This bug has been marked as a duplicate of 228929 ***

```

---

### Post by viniosity on 2005-11-21
That's interesting.. I'm using 2.5 in Dapper and I had the same issue which I resolved using the method I described above.  <shrug>

---

### Post by joselin on 2005-11-21
Yep, i tryed with both of them, with same results.

---

### Post by cjj on 2006-03-24
here i thought I just did something wrong...

I have a slightly weirder case to report of the same basic problem though. 

I have done 2 Badger installs (one 64 bit one 32 bit). In total, set up 3 email accounts on the 2 evolutions. For two of the accounts (on same domain, which happens to be the "work" one...), same exact problem: I see all folders but the inbox. 

On the other account (same server, different domain), I see the Inbox! 

For the non-working ones, I have tried both forms of IMAP. 

It seems like the unfortunate conclusion of this thread is that it is an evolution bug with no fix yet...(even in the 2.5 v in Dapper, [apparently]("http://http://www.ubuntuforums.org/showthread.php?t=145673&highlight=evolution+imap")). Anyone have any better news? If not, I guess on to thunderbird (which works fine). Man, I will miss the calendar...

---

### Post by joselin on 2006-03-26
[quote=cjj]here i thought I just did something wrong...

I have a slightly weirder case to report of the same basic problem though. 

I have done 2 Badger installs (one 64 bit one 32 bit). In total, set up 3 email accounts on the 2 evolutions. For two of the accounts (on same domain, which happens to be the "work" one...), same exact problem: I see all folders but the inbox. 

On the other account (same server, different domain), I see the Inbox! 

For the non-working ones, I have tried both forms of IMAP. 

It seems like the unfortunate conclusion of this thread is that it is an evolution bug with no fix yet...(even in the 2.5 v in Dapper, [apparently]("http://http://www.ubuntuforums.org/showthread.php?t=145673&highlight=evolution+imap")). Anyone have any better news? If not, I guess on to thunderbird (which works fine). Man, I will miss the calendar...[/quote]

Hi,

I reported it as a bug, and someone reply me saying that will be fixed in the next release. Now i'm on dapper, v. 2.6 and works fine for me.

Cheers.

---

### Post by Hendrik van den Boogaard on 2006-04-11
I still have the same bug upgrading from Breezy to Dapper. I tried re-creating accounts, but still without luck. Thunderbird works just fine.

It seems like such an easy bug to fix... I think the 'override namespace' option ALSO overrides the 'inbox' location where this inbox is just a standard mbox file in my homedir where all the rest of the OTHER maps are in the map supplied in 'override namespace' location.

I might as well dig into it myself someday, this is really anoying. No replies on my post here either:

[http://ubuntuforums.org/showthread.php?t=145673]("http://ubuntuforums.org/showthread.php?t=145673")

---

