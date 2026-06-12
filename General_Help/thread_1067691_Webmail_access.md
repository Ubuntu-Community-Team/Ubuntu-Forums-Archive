---
title: "Webmail access"
date: 2009-02-12
forum: General Help
---

### Post by Ole Andersen on 2009-02-12
Hi all

I am running ubuntu/mint and often testing new distros, so I like to use webmail, to stay care-free of backing up my e-mail all the time.
So i wondered if there is an application/mail-client that can work as a remote-client for any webmail.

I want it to access my e-mail, but not "downloading" them for good, but leaving them in the webmail. Otherwise i need an app that can log into my webmail account at only a few mouseclicks from my desktop.

Any idears?

---

### Post by kellemes on 2009-02-12
> **Ole Andersen said:**
> Hi all

I am running ubuntu/mint and often testing new distros, so I like to use webmail, to stay care-free of backing up my e-mail all the time.
So i wondered if there is an application/mail-client that can work as a remote-client for any webmail.

I want it to access my e-mail, but not "downloading" them for good, but leaving them in the webmail. Otherwise i need an app that can log into my webmail account at only a few mouseclicks from my desktop.

Any idears?

[Thunderbird]("http://www.mozilla.com/en-US/thunderbird/") with the [WebMail extensions]("http://webmail.mozdev.org/") works fine for me..

---

### Post by davec64 on 2009-02-12
Have you thought about using IMAP instead of POP3 with your provider?
IMAP leaves the emails on their servers meaning you can access from any email client you've configured.
Not all providers give IMAP as an option though. :)

---

### Post by Ole Andersen on 2009-03-05
Better late than never :-) 
Thank you for the answers - IMAP seems to be the right thing to go for! Than you for introducing  it.
one.com supports it, so Im lucky :-)

//Ole

---

### Post by Slim Odds on 2009-03-05
> **davec64 said:**
> Have you thought about using IMAP instead of POP3 with your provider?
IMAP leaves the emails on their servers meaning you can access from any email client you've configured.
Not all providers give IMAP as an option though. :)

POP3 does not automatically delete email from the server. The email client must explicitly issue a DELE command.

I believe that the default setting in Thunderbird is to delete email from the server when retrieved. You can change that. (just using Thunderbird as an example).

---

### Post by dcstar on 2009-03-05
> **Slim Odds said:**
> POP3 does not automatically delete email from the server. The email client must explicitly issue a DELE command.

I believe that the default setting in Thunderbird is to delete email from the server when retrieved. You can change that. (just using Thunderbird as an example).

Exactly, every POP3 mail client I have seen has the option to leave messages on the server, it is just set on as default (which is appropriate for 99.9% of all users).

---

### Post by fragos on 2009-03-06
The IMAP interface to Gmail works flawlessly for me. I even use it with native mail aps on mobile devices like my Nokia N810.

---

