---
title: "ProFTPd - slow login?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by aaronshaf on 2005-11-08
This might seem trivial but it really adds up. When I login to my ProFTPd server, it says, "Waiting for welcome message...", and takes a few seconds. This computer is about 10 feet from me. Shouldn't take that long, nor does Apache take that long for http requests. Any ideas? Like I said, it adds up...

Thanks for all your help! 

-Aaron

---

### Post by aaronshaf on 2005-11-08
Nevermind, I added the following to the .conf file and it's lightning now:

DefaultRoot ~
IdentLookups off
ServerIdent on "FTP Server ready."

---

### Post by iluminate on 2005-11-10
[QUOTE=aaronshaf]This computer is about 10 feet from me. Shouldn't take that long....
-Aaron[/QUOTE]
Don't think the distance is an issue :)
I'm having the same problem with the poor performance and setting up proftpd they way I want. Need to do a lot more reading here at the forum and the man pages.

Did you experiece better performance when adding the lines to the conf?
what does it acctually do?

Cheers and good luck

---

### Post by ariejan on 2007-06-01
If you want some more info on this issue, visit the following article. It also tells you how to fix slow logins with ProFTPd:

[http://ariejan.net/2007/05/29/slow-connections-with-proftpd/](http://ariejan.net/2007/05/29/slow-connections-with-proftpd/)

Cheers!

---

### Post by OsirisBlue on 2008-02-08
Also, check out:

snip

---

