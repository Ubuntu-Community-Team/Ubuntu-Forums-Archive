---
title: "E-Mail Questions"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Ingla on 2005-11-02
Hello.

I'm trying to switch to Linux completely. That may not yet be possible because of an apparent lack of some programs, but I'm trying to find out what's possible.

_1. HTML Mail_

I use the computer for business. Usually, I use Incredimail. It's a problematic program in some ways, but I use it because I can create various kinds of business letterhead stationery.

There may be a way to make it work in Linux (I doubt it, based on a few Google searches), but I would like to see if I can work around the problem with native Linux programs.

Under Windows, I have a program called GroupMail. It's kind of a mailing list manager which allows you to created e-mails and send them to lists (actually, I send them from GroupMail to a separate e-mail server to go out).

You can type a text message and then create an HTML page with the same text (but also anything else you can put in HTML) and the program creates a multipart message (which is received in the appropriate format for the recipient's client).

All this is much less convenient than using Incredimail, but not so terrible that I wouldn't do things that way, if necessary.

The question is, how can I do something similar under Linux?

I saw a system mentioned somewhere (can't find It at the moment) which works through a server. I don't have a server set up, but that shouldn't be the problem of the century. Anyone know anything about this? Or any way of accomplishing the same thing?

_2. Checking and Deleting Mail from Server_

I also use Incredimail's Advanced feature to see what's on the server and delete spam and viruses before downloading the e-mail (I get quite a bit). Even under Windows, I haven't found too many clients that can do this. I saw a mail checker for Linux, but it said it was for KDE. 

Does anyone know of such a program for Gnome? Can I run a KDE program in Ubuntu (you're talking to a Linux newbie)?

If anyone can help with either or both of the above issues, I'd appreciate it.

Thanks very much.

---

### Post by earobinson on 2005-11-02
cant thunderbird do all this?

---

### Post by Ingla on 2005-11-02
Not that I'm aware of. If Thunderbird has any way to check and delete from the server (without downloading), I'd very much like to know about it. I looked for extensions that could do that, but didn't find any.

Also, as far as I know, Thunderbird doesn't have any stationery options. In fact, when it receives one of my customized messages, it strips out the graphics and puts them in an attachment.

If you (or anyone) knows how to get more out of it, please let me know.

Thanks.

---

### Post by foxy123 on 2005-11-02
what about evolution? It's more business like suite I guess, though I have nt used it myself...

---

### Post by bk452 on 2005-11-02
I think Evolution has what you're asking for.  It comes standard.  Go to Office > Evolution. When you get Evolution up,  go to Edit > Preferences.

I think you'll find what you need.

---

### Post by Ingla on 2005-11-02
It doesn't look like Evolution can do those things either. It does have the advantage of being configurable for real time antivirus scans...which Thunderbird seemingly does not.

But no stationery or server checking.

---

### Post by dbott67 on 2005-11-02
I've never used Incredi-mail before, but you may be able to run it using wine, or perhaps one if it's comercial derivatives like Cross-over Office. These apps allow many Windows applications to be run under Linux.

I also found this link on their homepage regarding [download & installation]("http://www.incredimail.com/english/help/ts/show_result.asp?parent_id=19&parent_name=Compatibility%20and%20minimum%20requirements&locationBar=1;IncrediMail%20Xe%5E1;Download%20and%20Installation"), but I'm currently getting an error message:

[http://www.incredimail.com/english/help/ts/display_article.asp?article_id=122](http://www.incredimail.com/english/help/ts/display_article.asp?article_id=122)

-Dave

---

### Post by bmdavis on 2007-09-06
Then you have to export out of incredimail into ANY other mail client in XP(let alone Linux/Ubuntu). This is a nightmare - anyone know how to do it?!

---

### Post by mdbarton on 2007-09-06
I access my email with thunderbird using the IMAP protocal, rather than POP3.  this means that all email remains on the server and is not downloaded to the PC. Thunderbirds junk mail controls are reasonably good at filtering the spam and moving them to a seperate folder, the occasional spam that gets through I add to the junk list.  You can create new folders in your IMAP account and the folders are stored on the mail server.  Most email providers let you use IMAP or POP3.  If you have webmail access, this has the advantage that you can access all your email from anywhere (because it has not been downloaded to a PC), and if you have more than one PC in the house (I have a desktop and a laptop, both running Ubuntu), then you can access email and email folders from either.  It also means you can access the emails from a windows email client as well (if you really have to!).

Evolution probably does all the above as well.  I tried it for a while and decided to go back to Thunderbird.

As for viruses, why worry - you're on Linux!

So, if incredimail and your email provider support IMAP, change to IMAP, create folders on the server and copy all the emails up.  You only have to do it once!

---

