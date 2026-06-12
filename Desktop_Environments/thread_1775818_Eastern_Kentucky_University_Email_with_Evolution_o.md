---
title: "Eastern Kentucky University Email with Evolution on Ubuntu/Linux Mint."
date: 2011-06-05
forum: Desktop Environments
---

### Post by Maximus_ARNP on 2011-06-05
Eastern Kentucky University Email setup with Evolution 2.30.3 on Ubuntu or Linux Mint 10.10. For POP & SMTP - fully functional.



Go to: [B][https://mymail.eku.edu/](https://mymail.eku.edu/)
[/B]
Click on "Configure Your Mobile Device." [I know, you are not configuring a mobile device. But this is how it works.]

With your regular EKU username and password **"Request Mobile Password"**

Now, logon to your regular EKU email via web-browser, and get your MOBILE PASSWORD from your inbox.



Now, Go to Evolution

EDIT --- ACCOUNT EDITOR ----  ADD

FULLNAME: <Your preferred name>

Email address: <your eku email>

Reply-to: <your eku email>

FORWARD



==== RECEIVING EMAIL ===

SERVER TYPE:** POP**

Server: **pod51004.outlook.com:995**

Username: <your full eku email>

Security: **SSL**

Authentication Type: Password

FORWARD



Set your own RECEIVING OPTIONS

FORWARD



=== SENDING EMAIL ===

Security: ***pod51004.outlook.com:587***

**CHECK --- Server requires authentication**

SECURITY: **TLS**

AUTHENTICATION: **Login**

Username: <Your Full EKU email>

FORWARD



Select Name of the Account.



DONE. 



IMAP users may try following (not tested):

IMAP setting

Server name:[B] pod51004.outlook.com
[/B]
Port: **993**

Encryption method: SSL



Enjoy.

---

