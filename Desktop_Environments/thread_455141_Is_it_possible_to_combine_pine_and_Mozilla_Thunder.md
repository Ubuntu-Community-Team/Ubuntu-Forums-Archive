---
title: "Is it possible to combine pine and Mozilla Thunderbird?"
date: 2007-05-26
forum: Desktop Environments
---

### Post by nereid on 2007-05-26
Hi folks,

haven't found anything using the search function. I recently enabled ssh access to my box and now I was just wondering if it ain't possible to let pine read my Thunderbird mails, so that I could ssh from my laptop to my box and read my mail via pine. I know it is possible to forward Thunderbird through the ssh tunnel, but it is really slow on a normal internet connection and, additionally, most of the time Thunderbird is still running on my box (there can only be one Thunderbird ;) ).

My question is now, is it possible to let pine read my TBird mailbox and allow me to read my mails via ssh? Thanks in advance.

---

### Post by astoltz on 2007-05-26
I've thougt about doing what you describe as I'm in your same situation (reading mail both locally and though ssh).  But I haven't actually tried to set it up.  It should be possible as Thunderbird will read the standard "mbox" style files that pine uses.  So it should be just a matter of getting the configuration right on both Pine and Thunderbird to use the same set of mbox files.

Like I say, I've not tried it so there's bound to be some catch.  Let us know how you come out.

---

### Post by nereid on 2007-05-26
Can you change the Thunderbird mailboxes to the pine format without a problem?

If I can get this to work, I will post a small how to.

---

### Post by dbott67 on 2007-05-26
There's a few issues to consider:

1. Do you use POP3 or IMAP protocol for your e-mail?
2. Do you want to read existing mail (i.e. stuff in your INBOX, SENT ITEMS, etc.) or only new mail?

If you use IMAP, all messages & folders are stored on the server, so you can just use Thunderbird on the remote machine and just create a new account that links to your IMAP account (unless your work/school prohibits this).

If you use POP3, you could try navigating to ~/.mozilla-thunderbird/xxxxxx.default/ and using the 'less' command to view the contents of each folder (i.e. less Sent):
```
dbott@feisty:~/.mozilla-thunderbird/fds01u68.default/Mail/Local Folders$ ls -all
total 32
drwx------ 2 dbott dbott 4096 2007-04-24 22:26 .
drwxr-xr-x 3 dbott dbott 4096 2007-04-24 22:26 ..
-rw-r--r-- 1 dbott dbott    0 2007-04-24 22:26 Drafts
-rw-r--r-- 1 dbott dbott 1775 2007-05-07 12:31 Drafts.msf
-rw-r--r-- 1 dbott dbott 1233 2007-04-26 11:54 Junk.msf
-rw-r--r-- 1 dbott dbott    0 2007-04-24 22:26 Sent
-rw-r--r-- 1 dbott dbott 1773 2007-05-07 12:31 Sent.msf
-rw-r--r-- 1 dbott dbott 1408 2007-04-28 23:40 Templates.msf
-rw-r--r-- 1 dbott dbott    0 2007-04-24 22:26 Trash
-rw-r--r-- 1 dbott dbott 1327 2007-05-07 19:59 Trash.msf
-rw-r--r-- 1 dbott dbott    0 2007-04-24 22:26 Unsent Messages
-rw-r--r-- 1 dbott dbott 1559 2007-05-07 12:31 Unsent Messages.msf

```_**No Machine ([www.nomachine.com]("http://www.nomachine.com"))**_

No Machine is a secure thin client/server application that allows remote access over port 22.  It's extremely fast and easy to setup. I use it to access my home machine from work to test various web applications from a remote location.  I also use SSH & WinSCP, as shown in the attached screenshot.

-Dave

---

### Post by dbott67 on 2007-05-26
Another alternative for checking new mail would be to SSH home and then telnet to your mail server.  Of course, you would need to make sure that Thunderbird is not running.  Here's a couple of good tutorials:

[http://www.bobpeers.com/technical/telnet_imap](http://www.bobpeers.com/technical/telnet_imap)

[http://www.bobpeers.com/technical/telnet_pop](http://www.bobpeers.com/technical/telnet_pop)

---

### Post by nereid on 2007-05-26
Thanks dbot67 for the reply. The problem is, that I use the POP3 protocol. As long as my home pc is running, Thunderbird fetches all new mail every 10 minutes. Currently I'm using the IMAP protocol on my laptop, but Thunderbird fetches all mails away, before I could read them, hence I'm searching for a new solution.

I was aware, that you could read these files. Maybe I will have to write a simple script to get access to the mails (one command to list all subjects and another one to display the specified mail).

I only found ways on how to convert pine or mutt mail accounts to Thunderbird accounts but not vice versa.

---

### Post by nereid on 2007-05-26
So this is a small script to just get the subject of all available mails from the Inbox file (which is in the mbox format):

```

cat .mozilla-thunderbird/xyz.default/Mail/Local\ Folders/Inbox | grep Subject:

```

replace xyz.default with your own random folder name. Now I just have to write something small to get the body of a specified mail.

---

### Post by dbott67 on 2007-05-26
> **nereid said:**
> Thanks dbot67 for the reply. The problem is, that I use the POP3 protocol. As long as my home pc is running, Thunderbird fetches all new mail every 10 minutes. Currently I'm using the IMAP protocol on my laptop, but Thunderbird fetches all mails away, before I could read them, hence I'm searching for a new solution.

I would switch both clients to IMAP, that way you'll have access to all e-mails regardless of the computer.  If that's not possible, set the POP3 client to "leave a copy" of the mail on the server.  At least you'll still be able to see any new e-mails even if the POP3 client has already downloaded them.

-Dave

---

### Post by nereid on 2007-05-26
I could do that and change everything to IMAP. This would be in the end the easiest solution. But I don't think that you can upload old mails again, so that you could access them through IMAP.

---

### Post by dbott67 on 2007-05-26
> **nereid said:**
> I could do that and change everything to IMAP. This would be in the end the easiest solution. But I don't think that you can upload old mails again, so that you could access them through IMAP.

Sure you can:

1. Leave your POP3 account configured for the time being
2. Add the new IMAP account.
3. Create any desired folder structure in the IMAP folders
4. Drag & drop and messages from the POP3 account (Local Folders) into the IMAP folders.  The messages will automatically upload to the server.
5. Remove POP3 account.
6. Done! :)

---

### Post by nereid on 2007-05-26
Thanks, I will try it out. But still this mbox parsing is very interesting ;)

---

