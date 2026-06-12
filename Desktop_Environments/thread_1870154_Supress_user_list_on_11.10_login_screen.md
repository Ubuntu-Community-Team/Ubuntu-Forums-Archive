---
title: "Supress user list on 11.10 login screen"
date: 2011-10-26
forum: Desktop Environments
---

### Post by Charlotte18 on 2011-10-26
Does anyone know how to make the login screen in 11.10 require users to type their usernames, whilst getting rid of the clickable list of users?

---

### Post by HowardChau on 2011-10-26
Here's what I've done to hide the user list and also disable guest login.

[http://www.puppychau.com/archives/130](http://www.puppychau.com/archives/130)

I just ```
sudo nano /etc/lightdm/lightdm.conf
```and added the two lines. in the
[SeatDefaults[FONT=Verdana]] section[/FONT]

 ```
greeter-hide-users=true
allow-guest=false
```

---

