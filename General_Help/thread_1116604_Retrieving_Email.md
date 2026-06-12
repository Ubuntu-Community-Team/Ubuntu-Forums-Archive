---
title: "Retrieving Email"
date: 2009-04-05
forum: General Help
---

### Post by Grimble Gromble on 2009-04-05
How do you retrieve all of your email with Evolution? I did it once but unable to do it again. My email client is Gmail and I followed the instructions on setting up everything. While I love Gmail, I am wanting to try out Evolution and also tinkering around with Thunderbird to get an idea of what I like better.

---

### Post by CLomax on 2009-04-05
**EDIT**
·First you must edit a setting on your account outlined in these instructions (<1 minute): [https://mail.google.com/support/bin/answer.py?answer=13273](https://mail.google.com/support/bin/answer.py?answer=13273)
**/EDIT**

_**Thunderbird**_

·File -> New -> Account
·Select Gmail -> Enter your name and email address.
·Next -> Finish

·Right click the new account on the left side of the window -> Properties
·Under **Server Settings** set the server name to **pop.gmail.com**.
·Enter your username  '<_username_>@googlemail.com'.
·Select SSL for **Security Settings**.

·Now on the left of the **Properties** window select the lowest item on the tree **Outgoing Server (SMTP)**. If "Gmail - smtp.gmail.com(SMTP)" is not there click **Add** and create it.

You should now be able to read your messages through Thunderbird. :)

_**Evolution**_

·Edit -> Preferences -> Add
·Fill in the form -> Next
·Select **POP** for the server
·Under **Configuration** the server name is **pop.gmail.com**
·Enter your username below that
·Under **Security** choose **SSL encryption** -> Next -> Forward
·The **Server Type** is **SMTP**
·Under **Authentication**, Type = **PLAIN**
·Enter your username underneath
·Enter a name for your account

Done :)

---

### Post by agd19682 on 2009-05-20
> **CLomax said:**
> _**Thunderbird**_

·File -> New -> Account
·Select Gmail -> Enter your name and email address.
·Next -> Finish

·Right click the new account on the left side of the window -> Properties
·Under **Server Settings** set the server name to **pop.gmail.com**.
·Enter your username  '<_username_>@googlemail.com'.
·Select SSL for **Security Settings**.

·Now on the left of the **Properties** window select the lowest item on the tree **Outgoing Server (SMTP)**. If "Gmail - smtp.gmail.com(SMTP)" is not there click **Add** and create it.

Done :)

I have tried the steps mentioned above but the thundermail client keeps giving me a "username or password not accepted" message. 

If I delete and recreate the mail account settings, then it works but only for the first time. The next time I open the Thunderbird client again, its the same story all over again.....

any help would be greatly appreciated.

Thanks & Regards,

---

### Post by CLomax on 2009-05-20
> **agd19682 said:**
> I have tried the steps mentioned above but the thundermail client keeps giving me a "username or password not accepted" message. 

If I delete and recreate the mail account settings, then it works but only for the first time. The next time I open the Thunderbird client again, its the same story all over again.....

any help would be greatly appreciated.

Thanks & Regards,

Silly me, I forgot a minor detail. You'll need to enable POP in the googlemail settings. To do this you need to go to your googlemail inbox and follow the two instructions as per this page: [https://mail.google.com/support/bin/answer.py?answer=13273](https://mail.google.com/support/bin/answer.py?answer=13273)

If you have completed the steps outlined in my previous post you can then restart your mail client and it should work.

:KS

---

### Post by halmeida on 2009-06-02
> **CLomax said:**
> **EDIT**
·First you must edit a setting on your account outlined in these instructions (<1 minute): [https://mail.google.com/support/bin/answer.py?answer=13273](https://mail.google.com/support/bin/answer.py?answer=13273)
**/EDIT**

_**Thunderbird**_

·File -> New -> Account
·Select Gmail -> Enter your name and email address.
·Next -> Finish

·Right click the new account on the left side of the window -> Properties
·Under **Server Settings** set the server name to **pop.gmail.com**.
·Enter your username  '<_username_>@googlemail.com'.
·Select SSL for **Security Settings**.

·Now on the left of the **Properties** window select the lowest item on the tree **Outgoing Server (SMTP)**. If "Gmail - smtp.gmail.com(SMTP)" is not there click **Add** and create it.

You should now be able to read your messages through Thunderbird. :)

_**Evolution**_

·Edit -> Preferences -> Add
·Fill in the form -> Next
·Select **POP** for the server
·Under **Configuration** the server name is **pop.gmail.com**
·Enter your username below that
·Under **Security** choose **SSL encryption** -> Next -> Forward
·The **Server Type** is **SMTP**
·Under **Authentication**, Type = **PLAIN**
·Enter your username underneath
·Enter a name for your account

Done :)
Hi. I've set up accordingly, usign ports 995 for pop and 587 for smtp, as instructed by Gmail. But I get the following error "MAIL FROM command failed: Must issue a STRATTSL command first". What am I doing wrong... sorry, couldn't find the question mark yet...

---

### Post by CLomax on 2009-06-02
> **halmeida said:**
> Hi. I've set up accordingly, usign ports 995 for pop and 587 for smtp, as instructed by Gmail. But I get the following error "MAIL FROM command failed: Must issue a STRATTSL command first". What am I doing wrong... sorry, couldn't find the question mark yet...

It turns out that I have made another small mistake.

If you're using Evolution this guy fixed the same problem by selecting SSL encryption when setting up the SMTP part: [http://ubuntuforums.org/showpost.php?p=4017151&postcount=4](http://ubuntuforums.org/showpost.php?p=4017151&postcount=4)

If that does/doesn't help let me know.

---

