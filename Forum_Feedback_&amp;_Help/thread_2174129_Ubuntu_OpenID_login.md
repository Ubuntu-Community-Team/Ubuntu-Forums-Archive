---
title: "Ubuntu OpenID login"
date: 2013-09-13
forum: Forum Feedback &amp; Help
---

### Post by Primefalcon on 2013-09-13
Ok I am not sure where else to post this... but I was logging into a few sites with Ubuntu's OpenID service... which doesn't seem to be working anymore.... was the URL changed from [https://launchpad.net/~username](https://launchpad.net/~username) when the forums changed over to an sso login?

---

### Post by lisati on 2013-09-13
*Thread moved to **Forum Feedback & Help**.*

---

### Post by Elfy on 2013-09-13
I'm not sure tbh, any change they might have made isn't associated with the forum though. They did change somethings to U1 - which is the new name apparently.

[http://fridge.ubuntu.com/2013/06/21/improving-web-services-for-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ubuntu-news+%28Ubuntu+News%29](http://fridge.ubuntu.com/2013/06/21/improving-web-services-for-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ubuntu-news+%28Ubuntu+News%29)

[https://login.ubuntu.com/](https://login.ubuntu.com/) shows most of my associated logins - askubuntu doesn't appear to show up though. 

Not sure about anywhere else.

---

### Post by Mephisto Pheles on 2013-09-13
Ubuntu Single Sign On service, acts as an OpenID Provider.

Stack Exchange supports OpenID login, so you can add this identity to your account:

Go to your profile page and click the my logins link near the top.
In the window that opens, pick add more logins...
On this page, enter [https://login.ubuntu.com](https://login.ubuntu.com) into the field for your OpenID (and clear the Launchpad username field if it contains anything).
Click Log In, and you should be presented with the same pages you see when logging in to the Ubuntu One site, for instance.

Once this is complete, you should be able to log in to your account on this site by using [https://login.ubuntu.com](https://login.ubuntu.com) as the OpenID URL.

from [http://meta.askubuntu.com/questions/3060/i-have-a-ubuntuone-account-why-cant-i-use-it-to-login-here](http://meta.askubuntu.com/questions/3060/i-have-a-ubuntuone-account-why-cant-i-use-it-to-login-here)

---

### Post by Primefalcon on 2013-09-14
I use openID login on other forums and I am getting back this message: The requested identifier did not return the proper information.

---

### Post by Elfy on 2013-09-14
You need to talk to the openid people - maybe SSO people, people here might be able to help - but it'll not be from us as an official answer.

---

