---
title: "Security Concerns..."
date: 2006-04-20
forum: Desktop Environments
---

### Post by Whhpssh on 2006-04-20
I installed vsftpd a couple weeks ago and it's currently running.  I originally had it set up for anonymous access but removed it due to what I've been seeing in the logs.  Each day I see a bunch of these log records:

Thu Apr 20 06:29:18 2006 [pid 31296] [Administrator] FAIL LOGIN: Client "218.1.65.196"
Thu Apr 20 06:29:21 2006 [pid 31296] [Administrator] FAIL LOGIN: Client "218.1.65.196"
Thu Apr 20 06:29:23 2006 [pid 31296] [Administrator] FAIL LOGIN: Client "218.1.65.196"
Thu Apr 20 06:29:25 2006 [pid 31296] [Administrator] FAIL LOGIN: Client "218.1.65.196"

Each day it's a different IP address but the pid never changes, the user always tries to login as Administrator, and the IP address is always from somewhere in China.  This wouldn't concern me if every login attempt failed but, occasionally, I'll see an active connection when I look in Firestarter and I'll see a log entry where the user has managed to login under the Administrator login.

I don't have a user named Administrator on my machine and I've changed my root password to something only I know.  Should I be worried?  Is this just a nuisance and nothing more?  Is this someone using a back door into my machine?

Any information is appreciated.  I'd like to know if I should be worried and what I can do to stop this from happening.

Thanks.

---

### Post by localzuk on 2006-04-20
First, it is a very bad idea to run an anonymous FTP server. Very bad.

Second, it is likely a bot checking to try and use the ftp server (similar to ssh bots that try a series of usernames with which to log in).

Finally, the reason someone would want a ftp server is most likely to fill with warez.

---

### Post by Whhpssh on 2006-04-20
[QUOTE=localzuk]First, it is a very bad idea to run an anonymous FTP server. Very bad.[/quote]

Yeah, I turned off anonymous.  I just wanted to see if I could create a server and I did.  I then gave access to family members only.

[QUOTE=localzuk]Second, it is likely a bot checking to try and use the ftp server (similar to ssh bots that try a series of usernames with which to log in).[/quote]

Figured that, but is there a way to stop it?  Also, why would they be able to login with a username of Administrator when that username isn't setup on my machine.

[QUOTE=localzuk]Finally, the reason someone would want a ftp server is most likely to fill with warez.[/QUOTE]

Not sure if you're accusing me of setting it up for this reason or if you're saying that's why they want it.  If it's the former, I'd appreciate contructive suggestions, not accusations from someone who doesn't know me.  If it's the latter, that's what I figured they were trying to do.  I'm just concerned that I saw some successful logins with a username I haven't set up.

---

### Post by Whhpssh on 2006-04-20
Anybody else?  Should I be concerned?  Is there something I should know about the Administrator login they are using?

---

### Post by localzuk on 2006-04-20
It was the latter :) I don't accuse people of things without evidence :)

One of the things I would suggest is looking in to 'sftp'. It would mean not using ftp at all and just using ssh. This way, the username and password are encrypted so cannot be sniffed by packet interception.

To use sftp, simply install the ssh server packages on your machine, set up user accounts for the users you wish to log in and use an sftp client for the users to use it.

I think the 'Administrator' username logging in is actually not happening though - it is just that you are catching a connection during a log in attempt, IMO. Administrator is normally only ever used on Windows machines, IME.

---

### Post by Whhpssh on 2006-04-20
[QUOTE=localzuk]It was the latter :) I don't accuse people of things without evidence :)

One of the things I would suggest is looking in to 'sftp'. It would mean not using ftp at all and just using ssh. This way, the username and password are encrypted so cannot be sniffed by packet interception.

To use sftp, simply install the ssh server packages on your machine, set up user accounts for the users you wish to log in and use an sftp client for the users to use it.

I think the 'Administrator' username logging in is actually not happening though - it is just that you are catching a connection during a log in attempt, IMO. Administrator is normally only ever used on Windows machines, IME.[/QUOTE]


Thank you.  No offense meant by my last message.  Just wasn't sure how to read it.  I appreciate the follow up.

I'll look into sftp.  :)

---

