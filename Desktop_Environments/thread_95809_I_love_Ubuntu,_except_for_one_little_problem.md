---
title: "I love Ubuntu, except for one little problem"
date: 2005-11-27
forum: Desktop Environments
---

### Post by ardchoille on 2005-11-27
I switched to Ubuntu from Fedora yesterday. First of all.. I love this distro :)
Ubuntu blows Fedora out of the water as far as speed.. and the package repos for Ubuntu 5.10 are huge compared to Fedora Extras and livna. Apt-get is waaaaaaaay faster than yum.

Ok, I have my box all set up except for one thing. I use Thunderbird for email and it worked flawlessly in Fedora. But, it doesn't work in Ubuntu 5.10. When I try to connect, it simply says "connecting.. " and then times out. I am connecting to my host for pop/smtp work.

Well, I am a happy camper because that is the only problem I have run into thus far.

Anyone have any ideas?

---

### Post by Turtle.net on 2005-11-27
I do not think the problem is related to the distribution because i use Thunderbird in Ubuntu (Hoary and Breezy) without the slightest problem :)
I am sure you verified your POP settings, so maybe try to uninstall Thunderbird and re-install it using synaptic...

---

### Post by aspr1n on 2005-11-27
I'd check your mail settings and server conections (Edit > Account Settings) - can you ping your pop3/imap server, check server port is correct etc

Finally in a terminal session try:

telnet pop3.yourserver.com 110
telnet smtp.yourserver.com 25

I just bought my entire Thunderbird mailbox over from Windows without a hitch - dead impressed!

asp

---

### Post by ardchoille on 2005-11-27
[QUOTE=aspr1n]I'd check your mail settings and server conections (Edit > Account Settings) - can you ping your pop3/imap server, check server port is correct etc

Finally in a terminal session try:

telnet pop3.yourserver.com 110
telnet smtp.yourserver.com 25

I just bought my entire Thunderbird mailbox over from Windows without a hitch - dead impressed!

asp[/QUOTE]
Hmm.. I tried what you said and it doesn't return. Also, ping mail.myserver.com doesn't return anything either. So, maybe it's a server side problem rather than Thunderbird. I know my TB settings are ok because I simply copied the ~/.mozilla-thunderbird dir over from Fedora. Thanks for the info.

---

### Post by ardchoille on 2005-11-27
[QUOTE=aspr1n]I'd check your mail settings and server conections (Edit > Account Settings) - can you ping your pop3/imap server, check server port is correct etc

Finally in a terminal session try:

telnet pop3.yourserver.com 110
telnet smtp.yourserver.com 25

I just bought my entire Thunderbird mailbox over from Windows without a hitch - dead impressed!

asp[/QUOTE]
OK, it was indeed a server side problem. Fixed now. Thanks to you both for your kind replies.

---

