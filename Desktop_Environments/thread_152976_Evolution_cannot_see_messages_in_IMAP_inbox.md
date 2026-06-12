---
title: "Evolution cannot see messages in IMAP inbox"
date: 2006-03-31
forum: Desktop Environments
---

### Post by aaulick on 2006-03-31
I have set up Evolution with my IMAP account.  It successfully tells me I have 1 new message in my inbox, but it won't show any messages at all (there are hundreds)  It will happily show me messages in the various subfolders of my inbox.  
I could have sworn that last night it was working correctly, but maybe that was on my other machine.  Mac OS X mail shows the messages on the same account correctly.
Am I missing a "avoid work by pretending there's no mail" checkbox somewhere?

---

### Post by issueperson on 2006-03-31
that's odd...
if you don't have too many complicated settings for your imail account, i might just try deleting the email account from preferences and entering the information again (edit > preferences) (since it is IMAP and it should not affect your account at all).
i use Evolution with my IMAP account and it works great.
issueperson

---

### Post by elamericano on 2006-03-31
Ditto that. Evolution works perfect right out of the box. Do you get a password prompt? Can you ping the IMAP address you are using?

---

### Post by dcstar on 2006-03-31
[QUOTE=aaulick]I have set up Evolution with my IMAP account.  It successfully tells me I have 1 new message in my inbox, but it won't show any messages at all (there are hundreds)  It will happily show me messages in the various subfolders of my inbox.  
I could have sworn that last night it was working correctly, but maybe that was on my other machine.  Mac OS X mail shows the messages on the same account correctly.
Am I missing a "avoid work by pretending there's no mail" checkbox somewhere?[/QUOTE]
Clear the search bar above the message list.

---

### Post by GrumpyBob on 2006-03-31
[QUOTE=elamericano]Ditto that. Evolution works perfect right out of the box. Do you get a password prompt? Can you ping the IMAP address you are using?[/QUOTE]

My experience differs.  I find Evolution 2.4.1 buggy as hell.  However, it could well be the exchange server that is causing the problems - there doesn't seem to be straightforward way of figuring it out.

Robert

---

### Post by issueperson on 2006-03-31
[QUOTE=GrumpyBob]My experience differs.  I find Evolution 2.4.1 buggy as hell.  However, it could well be the exchange server that is causing the problems - there doesn't seem to be straightforward way of figuring it out.

Robert[/QUOTE]

do you use it in gnome, KDE, or something else?

what are some of the things you've run in to?

---

### Post by flyingfrog on 2006-04-04
Same identical problem using evolution 2.4.1 on gnome.
anybody else?
Could it be connected to the fact it's an IMAP account?

---

### Post by clee991 on 2006-04-05
I have had the same problem and followed this routine to fix

[http://www.nabble.com/Cleaning-up-Evo's-cache-t1310254.html]("http://www.nabble.com/Cleaning-up-Evo's-cache-t1310254.html")

> Re: Cleaning up Evo's cache
by Nigel Metheringham 2006-03-20 06:10 
On Mon, 2006-03-20 at 15:58 +0530, B S Srinidhi wrote:
> I *had* an IMAP folder that housed close to 5000 emails. Since, that was
> taking quite some amount of space on the server and the fact that I was
> not able to read all those emails, I decided to delete the directory
> from the server. The directory does not exist anymore on the server, but
> almost all of it remains in Evo's cache.
>
> How can I delete this directory (and many others) from the cache?
>
> Would it be enough to delete the directory from
> $HOME/.evolution/mail/imap/accountname/folders/INBOX/subfolders/ ???

I have never tried deleting individual directories from the imap tree.
However I do fairly frequently blow away everything under
$HOME/.evolution/mail/imap/ without encountering any problems (however
schedule this for a time when you are near to your imap server - doing
then when you are on low or laggy bandwidth to the server is likely to
result in frustration).

I do completely shut down evolution before lobotomising it (ie evolution
--force-shutdown).

        Nigel. 

---

### Post by GrumpyBob on 2006-04-06
[QUOTE=issueperson]do you use it in gnome, KDE, or something else?

what are some of the things you've run in to?[/QUOTE]

I am using Evolution in gnome, Ubuntu 5.10.

I have set up my mail profile.  When I start Evolution,  there are several possible outcomes:
1.  It works perfectly, connects to the Exchange server, without asking for password.  This happens about 5% of the time.
2.  Sometimes it connects to the Exchange server, starts doing the download etc, then loses contact with the Exhange server.  It has a pop up asking if I want to relay the info to the development team, but it isn't set to do so.
3.  Sometimes it never even appears to try to connect to the Exchange server - when I click on the relevant mail account, it asks for my password, three times, then says it's lost contact with the Exchange server.

It really is quite painful.  I hope that Evolution 2.6 has ironed out these problems when Dapper hits the streets.  When it deigns to work, it really can be quite good.

I would be happier if I could identify where the problem lies - maybe it's in a log file somewhere?  I guess it could be an issue with the exchange server - though via web access it seems fine (though Opera says it is using an old-fashioned security).

Robert

Robert

---

