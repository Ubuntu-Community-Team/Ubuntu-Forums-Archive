---
title: "PHP Send Mail Problem"
date: 2008-12-11
forum: General Help
---

### Post by Black Mage on 2008-12-11
I am having a problem sending mail with PHP. I think my problem lies in the fact that my mail server is different from my web server. I am using the PHP-PEARL to send mail and I set my php.ini to this:

sendmail_path = /usr/sbin/sendmail -i -t

But could it be because the path is on the web server than it is preventing me from sending mail?

And there error I recieve is: unable to connect to smtp server [email]ddixon@my-lan.us[/email]:25

Thanks

---

### Post by fragos on 2008-12-12
Mail will sent from the server. The following PHP example works for me on my GoDaddy host and on my desktop apache localhost which doesn't use sendmail.

		// Send confirmation email.
		$body = "Thank you for registering with FragosTech.com!
Your username is {$_POST['username']}. Your password is {$_POST['password1']}.";
		mail ($_POST['email'], 'Thank you for registering with FragosTech.com!', $body, 'From: [email]fragos@gmail.com[/email]');

---

