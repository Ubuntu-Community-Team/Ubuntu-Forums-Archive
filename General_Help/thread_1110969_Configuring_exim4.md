---
title: "Configuring exim4"
date: 2009-03-30
forum: General Help
---

### Post by john.parten on 2009-03-30
Can anyone help regarding setting up exim4 ?
I am trying to make the "mail" command work from a $ prompt.
I have done the following steps:-

1) Login in as su to get # prompt
2) run dpkg-reconfigure exim4-config
3a) selected "mail sent by smarthost, no local mail"
3b) mail name = XXX.com where my email address is [email]john.parten@XXX.com[/email]
3c) ip address list to listen on is set to empty
3d) recipient domain = "localhostname"
3e) visible domain name = "XXX.com"
3f) hostname of smtp server = "authsmtp.YYY.net"
3g) DNS queries minimal = "no"
3h) split config files = "yes" (I have also tried "no")
4) edit the file /etc/exim4/passwd.client
4a) added the line authsmtp.YYY.net:john.parten@XXX.com:ZZZ
5) run update-exim4.conf

Still my $ mail command does not send, eg ...
$ mail -s "Test" [email]john.parten@HHH.com[/email]
does not work. There is no error message at the $ prompt. Meanwhile, the remote account [email]john.parten@HHH.com[/email] does not receive the "Test" email. 
If I type mail on its own I don't get any messages (I did not expect any anyway). Using evolution on the same computer, configured for the same SMTP server "authsmtp.YYY.net" and same account details [email]john.parten@XXX.com[/email] and password ZZZ works fine. I am able to send to, and receive from, [email]john.parten@HHH.com[/email] all OK. 

So have I missed a critical step ?

NB XXX, YYY, ZZZ and HHH represent personal strings.

Anybody got any ideas ?

---

