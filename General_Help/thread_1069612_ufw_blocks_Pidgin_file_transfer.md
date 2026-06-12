---
title: "ufw blocks Pidgin file transfer?"
date: 2009-02-14
forum: General Help
---

### Post by antony_css on 2009-02-14
I can receive files from my friends, but my friends cannot receive my files.
According to the default setting of ufw, all outbound connections are enabled. How come my friends cannot receive my files?

---

### Post by brian_hayward on 2009-02-19
What are your friends using for a system (linux or windows), are they also using ufw?  I don't want to insult your intelligence or your friends, but do they have all the necessary ports opened on their firewalls?  are they using Pidgin as well?  Please provide some additional information.

---

### Post by antony_css on 2009-02-20
Umm... They use live-messenger in xp.
I am using an msn account, and I suppose my friend do not see any difference?

I know sometimes we just can't send a exe file due to some unknown restrictions in xp... But in my case, even a file as simple as an empty text file cannot be sent.

BTW, my pidgin is v2.5.4, which is the getdeb.net verion.

---

### Post by antony_css on 2009-02-20
I created another account for myself and try to send files from account A to account B (utilizing the multiple account function in pidgin). I found that it works.

Then, I looked up the messages in the debug window of pidgin. And I found the error dated on the time I failed to send files to my friends :
> 
(19:44:41) dns: Wait for DNS child 10063 failed: No child processes
(19:44:42) msn: cal_error: command CAL gave error 217
(19:44:42) msn: Unable to send msg: {INVITE MSNMSGR:xxxxxxx@hotmail.com MSNSLP/1.0

To: <msnmsgr:xxxxxxxx@hotmail.com>

From: <msnmsgr:xxxxxxxx@yahoo.com.hk>

Via: MSNSLP/1.0/TLP ;branch={85BAAA5E-42A6-3D03-AB0E-40C35C8B9B2C}

CSeq: 0

Call-ID: {28CB7B41-7E7A-51D9-B137-32E6AA4D7497}

Max-Forwards: 0

Content-Type: application/x-msnmsgr-sessionreqbody

Content-Length: 288



EUF-GUID: {A4268EEC-FEC5-49E5-95C3-F126696BDBF6}

SessionID: 599023529

AppID: 1

Context: PG1zbm9iaiBDcmVhdG9yPSJlbmVyZ3lmYWlAaG90bWFpbC5jb20iIFNpemU9IjI0ODEiIFR5cGU9IjMiIExvY2F0aW9uPSIwIiBGcmllbmRseT0iY2dCMEFIRUFiZ0J6QUhrQUFBQT0iIFNIQTFEPSJqaDF3OEhKNTFucGFua2djOFU1RmxyK244eDg9Ii8+



}
(19:44:42) msn: cal_error_helper: command CAL failed for reason 3
(19:44:42) msn: Error: Unable to call the user [email]xxxxxxxx@hotmail.com[/email] for reason 3

Anyway, what happened?

---

### Post by antony_css on 2009-02-20
I re-visited the getdeb.net and found that the corresponding package was removed.
According to the contributor *lamego*,
> The package for hardy was not installable (it needs some changes). I have pulled the release until we get a working package.
Sorry for the problem. 

So the only option left for me is to compile from source:
[http://ubuntuforums.org/showthread.php?p=6133812]("http://ubuntuforums.org/showthread.php?p=6133812")

Wish me good luck...

---

### Post by Archmage on 2009-02-20
Kindly note that since SP1 in Window XP is a firewall automatical installed that forbid all incomming connections, unless turned of or specifice.

---

### Post by antony_css on 2009-02-20
Really thanks for your kindly reply.
The deb package from getdeb.net is actually corrupt. I compiled and installed from source - and I can now send files to my friends!

---

