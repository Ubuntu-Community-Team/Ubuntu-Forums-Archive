---
title: "PHP broken after update"
date: 2005-10-15
forum: Desktop Environments
---

### Post by HJB on 2005-10-15
Hi all. Please help!!
I upgraded to all the latest repos and now when I try to open (previously working) php pages in Firefox, from my own Apache2 server **_Firefox wants to save them_** or something...It is as if Apache OR Firefoc doesn't know what to do with the php pages!

I reinstalled Apache2, PHP5 and mysql but stil the same
Anyone please help


I read something similar in other posts but their solution of reinstalling Ubuntu is just not on.

Thanks
H

---

### Post by Jordao on 2005-10-17
I have exactly the same problem...
I installed and reinstalled php5, mysql, apache2 and nothing... I've tried with php4 and still nothing...

i need help urgently...

---

### Post by HJB on 2005-10-21
Hi, I fixed mine. Got rid of Apache2, PHP5 and mysql and reinstalled firstly Apache2, then PHP5.1 (mmmm) and then mysql. Now everythings run smooth again.
Still dono why it happend, might be something with a dependant package that was reported as being removed when I installed (TRIED TO) php5.


Hope this helps someone.
Bye
H

---

### Post by LorenzoD on 2005-10-21
It sounds like a misconfiguration of Apache. It most likely happened when you upgraded your packages. Don't worry, there is *absolutely no need* to reinstall Ubuntu. You shouldn't even have to reinstall Apache or PHP. 

If somebody else has this problem, it would be nice to see your apache configuration files, so that we can see what is going wrong. You should probably file a bug report stating what you upgraded and what happened. Your apache configuration file is a good attachment to such a bug report.

---

