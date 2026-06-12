---
title: "What are your backup rituals?"
date: 2009-01-19
forum: General Help
---

### Post by Maheriano on 2009-01-19
In the past I've simply had 2 drives; one for use and one for backup. The problem I see with this is if my house burns down, I have no backup because they're both burnt. So what I'm setting up now is my main computer networked to a server in the same house where the backups will be done nightly. Then an external hard drive which is a mirror of the backup drive that I keep in a safety deposit box at the bank and take it out once a month to update it with the newest backup from the server. Can anyone make this more efficient? The only other option is to keep the server at my girlfriend's house but her ISP blocks port 80.

What do you do?

---

### Post by hyper_ch on 2009-01-19
I setup a box at my parents' house and use rsync over ssh... so port 22 is needed... works fine.

---

### Post by Yashiro on 2009-01-19
> The only other option is to keep the server at my girlfriend's house but her ISP blocks port 80.That's a harsh ISP.

---

### Post by adamlau on 2009-01-19
Backups are a necessary ritual, your method appears sound except for the fact that you only backup on drive media. Consider write-only disc media, archival quality MAM if you desire. As long as you have parity files available, should prove to have a longer shelf life than drive media. I use dar to backup my files in 4.5 GB slices and check it's integrity (-t) before creating par2 files against the results. I then burn two copies onto DVD+R media before moving the backup files to a secondary USB HD. I keep one backup DVD at work and the other in my vehicle. The secondary USB HD stays with me. Encryption is handled by a combination of TrueCrypt and GnuPG before the backup slices are created.

---

### Post by LoneWolfJack on 2009-01-19
> That's a harsh ISP.

I love geek humor. :D

---

### Post by Slim Odds on 2009-01-19
> **Maheriano said:**
> The only other option is to keep the server at my girlfriend's house but her ISP blocks port 80.

What does port 80 have to do with anything? That's the HTTP port. Are you going to backup with a web browser?  :)

---

### Post by Maheriano on 2009-01-19
> **Slim Odds said:**
> What does port 80 have to do with anything? That's the HTTP port. Are you going to backup with a web browser?  :)

Ha no, I'll be backing up to a server so if I keep it at her house, the server won't be able to fulfill its other duties of serving my web pages. I guess my best option is to take a drive home and set it up in my parents' machine on the other side of the country next time I'm there. They have a habit of messing things up though.

---

### Post by albinootje on 2009-01-19
> **Maheriano said:**
> The only other option is to keep the server at my girlfriend's house but her ISP blocks port 80.

An ISP which blocks port 80.. are you joking ?
What kind of ISP is that ? Which ports are still open then ?
Or is the ISP doing this temporarily, because of an abuse-report, leaving only port 443 open to their own ISP website + webmail ?

I'd go for rsync, for that you need a ssh-server running on the remote machine.
Openssh can be configured to run on every port you like.

---

### Post by Maheriano on 2009-01-19
> **albinootje said:**
> An ISP which blocks port 80.. are you joking ?
What kind of ISP is that ? Which ports are still open then ?
Or is the ISP doing this temporarily, because of an abuse-report, leaving only port 443 open to their own ISP website + webmail ?

I'd go for rsync, for that you need a ssh-server running on the remote machine.
Openssh can be configured to run on every port you like.

Well port 80 is open for receiving web pages but nothing is allowed to go out. They block it so you can't serve web pages from your IP.

---

### Post by albinootje on 2009-01-19
> **Maheriano said:**
> Well port 80 is open for receiving web pages but nothing is allowed to go out. They block it so you can't serve web pages from your IP.

Okay.
But then I would not expect them to let you run any other services, although you can have more luck with any ports above 1024 I assume.

---

