---
title: "evolution and gmail"
date: 2005-04-10
forum: Desktop Environments
---

### Post by Zlatan on 2005-04-10
how to configure evolution for gmail properly ?

---

### Post by Nis on 2005-04-10
[QUOTE=Zlatan]how to configure evolution for gmail properly ?[/QUOTE]
 You'll need to enable POP access in the GMail config first.
Then for Evolution you need to set the pop host name to pop.gmail.com.
Set user name to "username@gmail.com" where user name is your GMail user name.  The "@gmail.com" is important.
Set "Use Secure Connection" to "Always" and "Authentication Type" to "Password"

For SMTP access (sending mail with Evolution) set "Server Type" to "SMTP"
Host = smtp.gmail.com.  Server does require authentication.
"Use Secure Connection" to "Whenever possible"
"Authentication Type" to "Login" and "username" to "username@gmail.com".  Again, the "@gmail.com" is important.

This should work.

---

### Post by Zlatan on 2005-04-11
[QUOTE=Nis]You'll need to enable POP access in the GMail config first.
Then for Evolution you need to set the pop host name to pop.gmail.com.
Set user name to "username@gmail.com" where user name is your GMail user name.  The "@gmail.com" is important.
Set "Use Secure Connection" to "Always" and "Authentication Type" to "Password"

For SMTP access (sending mail with Evolution) set "Server Type" to "SMTP"
Host = smtp.gmail.com.  Server does require authentication.
"Use Secure Connection" to "Whenever possible"
"Authentication Type" to "Login" and "username" to "username@gmail.com".  Again, the "@gmail.com" is important.

This should work.[/QUOTE]

thanks, I was really worried about all those SSL's and ports

---

### Post by Tsjoklat on 2005-04-11
Also:

pop.gmail.com:995
smtp.gmail.com:465

I myself had major issues sending through gmail's smtp but perhaps you will have more luck.

D

---

### Post by MaX on 2005-04-12
Works fine for me without the @gmail stuff in the username.

---

### Post by Martin Witte on 2005-04-12
Sending with gmail uses port 587 - in the 'Sending Email' tab enter after the 'Host:' label   
'smtp.gmail.com:587', and sending mail works fine with evolution

---

