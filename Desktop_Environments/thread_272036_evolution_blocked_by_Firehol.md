---
title: "evolution blocked by Firehol"
date: 2006-10-05
forum: Desktop Environments
---

### Post by skaramanger on 2006-10-05
Greetings fellow ubuntu users,

I have been using Firehol with evolution for sometime now without problems. I decided the other day to reconfigure firehol in an attempt to plug some perceived holes.

I commented out the statements server accept all and client accept all and began adding services that I wanted to permit access.  I successfully got dns,ftp and others that permit me to surf here login and post this note. However, after this I was unable to download my email (pop3).  I added the obligatory:

server "pop3 pop3s imap" accept and client "pop3 pop3s imap" accept. but still no go.](*,)  (I already have server/client accept smtp setup). I stopped the firewall and was able to connect and download my email. So...after searching the forums here and on the net, I decided to post. Is there another service/port that evolution accessess that I need to configure? Any idea? I've attached my firehol.conf for those kind enough to check it out and give me some feedback.

TIA

skaramanger

---

