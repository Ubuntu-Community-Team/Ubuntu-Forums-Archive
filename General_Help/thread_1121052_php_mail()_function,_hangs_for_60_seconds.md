---
title: "php mail() function, hangs for 60 seconds"
date: 2009-04-09
forum: General Help
---

### Post by dcparham on 2009-04-09
php mail() function, hangs for 60 seconds:

{code} is simple mail() function:

$to='dcparham@gmail.com';
$subject='test email';
$mailBody='msg Body content';
mail($to, $subject, $mailBody);

then it hangs for 60 seconds, every time.

any ideas??  thanks for your time!

---

### Post by dcparham on 2009-04-17
The machine name definition in etc/hosts, and /etc/hostname files was only "webserver" which resulted in an error "not a fully qualified host name."  i had seen that error here and there but did not connect it with the email hang.  after changing the /hosts and /hostname files as follows, the email went through immediately:

hosts file was:
127.0.0.1 webserver
111.1.1.1 webserver

hosts file now:
127.0.0.1 cshwebserver.domain.com localhost
172.16.1.30 cshwebserver.domain.com
[resulting in "non a fully qualified host name"]
ALSO

hostname file was:
webserver

hostname file now:
webserver.domain.com

thx to [http://symbiotix.net/articles/sendmail-60-second-delay](http://symbiotix.net/articles/sendmail-60-second-delay).

---

