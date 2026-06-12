---
title: "Exchange via Kontact"
date: 2006-07-14
forum: Desktop Environments
---

### Post by MrDomino on 2006-07-14
I've been trying to get KDE's Kontact to play nicely with my company's MS Exchange server. Setting up the IMAP/SMTP account was easy enough, and I discovered that I could pull users' e-mail addresses from LDAP. Then, using [this guide](http://wiki.kde.org/tiki-index.php?page=KOrganizer%20and%20the%20MS%20Exchange%20plug-in), I was able to get personal contacts and calendars working. Now, though, there are a few things I still haven't figured out.
[list]
[*]The guide states that "it maybe that accessing the WebDAV URL only works as long as you're logged in via the HTTP User Interface in parallel," and this seems true in practice. Does anybody have the slightest clue why, or better still, how I could get around this? Having to have a spare browser window logged in to Outlook Web Access constantly is kind of stupid.
[*]Is it at all possible to get shared calendars working? This is by no means necessary, but it'd be kind of cool to have.
[*]Is there any way to send/receive e-mail via http? Right now, I need to be at work to access my e-mail in Kontact--the server seems to only accept imap or smtp connections locally. I've considered trying to use our Netscreen VPN, but that is looking as though it's a beast all its own.
[/list]
Any help or pointers would be appreciated.

EDIT: Turns out, on investigation, that the KDE Groupware Wizard utility doesn't include an Exchange option. That might be the reason I couldn't use it. :-k

---

