---
title: "Cannot download email"
date: 2005-12-10
forum: General Help
---

### Post by MartinS on 2005-12-10
Hi,

I originally posted this in the beginners forum, I still feel I am but have come a long way in 24 hours so I am going to put this on here in the hope that perhaps somebody else might see and be able to help.

My installation of 5.10 has gone well. I have access to my NTFS partitions, I can watch DVD's and do just about anything I want with two exceptions. The most major of these is email.

No matter what I use as an email client, Evolution, Thunderbird, Opera. All hamg when trying to download email and eventually time out.

I can ping both the pop and smtp servers, fetchmail seems to work, sortof, see below:

martin@fujlin:~$ fetchmail -ku XYZ pop.myisp.com
Enter password for [email]XYZ@pop.myisp.com[/email]:
29 messages (25 seen) for XYZ at pop.myisp.com.
skipping message [email]XYZ@pop.myisp.com[/email]:1 not flushed
skipping message [email]XYZ@pop.myisp.com[/email]:2 not flushed
skipping message [email]XYZ@pop.myisp.com[/email]:3 not flushed

etc

skipping message [email]XYZ@pop.myisp.com[/email]:23 not flushed
skipping message [email]XYZ@pop.myisp.com[/email]:24 not flushed
skipping message [email]XYZ@pop.myisp.com[/email]:25 not flushed
reading message [email]XYZ@pop.myisp.com[/email]:26 of 29 (3454 header octets) ...fetchmail: SMTP connect to localhost failed
fetchmail: SMTP transaction error while fetching from pop.myisp.com
fetchmail: Query status=10 (SMTP)
martin@fujlin:~$

Seems to indicate some sort of localhost connection problem, but what?

Any ideas on where to go next would be appreciated. I have tried all the various security options and Evolutions 'check for supported types' but that hangs too.

Regards
Martin

---

### Post by mustang on 2005-12-10
You might want to double check the settings in whatever email client you use with your ISP. Often times, their smpt/pop/imap servers run on a certain port and/or require SSL encryption. I know for a fact my client timed out because I didn't check the setting for SSL encryption. 

So try that and let us know what happens.

---

### Post by MartinS on 2005-12-14
Hi,

Well after a few days of messing with other things I have tried to return to this problem. Very strange things going on now. Evolution works, sometimes, actually fails about once every ten times, usually on startup and then about once every ten times after that. I did update fetchmail to 6.2.5.4 and also installed fetchmailconf which allowed me to set up various things that seemed otherwise blank. I'm not sure if Evolution uses fetchmail either. Kmail always works and it seems always did so that is clearly doing something different.

It is still rather unreliable for me to want to rely on it but I seem to have made some progress, just not really sure how?????

Martin

---

