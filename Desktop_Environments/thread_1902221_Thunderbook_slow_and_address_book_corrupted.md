---
title: "Thunderbook slow and address book corrupted"
date: 2011-12-30
forum: Desktop Environments
---

### Post by chandra on 2011-12-30
I am on Kubuntu 11.10 with Thunderbird 8.0 installed from the repo package thunderbird 8.0+build1-0ubuntu0.11.10.1.

Recently, Thunderbird has been very slow to connect to IMAP mailboxes and to download emails. Then, suddenly, my address book stopped working.

I have since discovered that the address book was corrupted and once it was cleaned and restored, the address book started working and Thunderbord also loaded fast as usual.

The nature of the corrupting lines in the address book are:

```
[COLOR="Red"]@$$[/COLOR]{SOME NUMBER HERE{[COLOR="Red"]@[/COLOR]
A LOT OF STUFF HERE
ENDING WITH
[COLOR="Red"]@$$[/COLOR]}SAME NUMBER HERE}[COLOR="Red"]@[/COLOR]

```

These "additions" are in paragraph form and can be distinctly identified in the corrupted address book as they are appended to the end.

Has anyone else encountered this strange behaviour and know its cause and cure?

Thanks.

---

