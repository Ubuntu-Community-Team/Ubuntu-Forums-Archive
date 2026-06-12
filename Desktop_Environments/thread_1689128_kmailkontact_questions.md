---
title: "kmail/kontact questions"
date: 2011-02-16
forum: Desktop Environments
---

### Post by barna on 2011-02-16
Hi,
I have been using pine/alpine for about 15 years, and I am about to migrate (maybe) to kmail (indexing and searching in my emails, more advanced (?) addressbook integrated into other apps, etc). I would have a few questions:

- Is there any other way to set up a local mail folder (in my home directory) other than deleting ~/.kde/share/apps/kmail/mail and soft-linking it to the directory I want to use? Can I not set up another local mailbox directly defined to use the directory I want?

- The great advantage of (al)pine's addressbook was that it was stored on the same email server wher all my emails were also stored. I could log in to our linux servers from everywhere in the world (using putty from windows), and I had all my addresses available. If I now set up a kde addressbook, can I sync it to an alpine addressbook in the mail server, so that if I am away from my notebook, I can still have access to my contacts from alpine? (of course the kde addressbook can contain far more information than alpine's addressbook - I would only want to upload the necessary info to the server)

- In KDE I can set up contact groups, and I can send emails to all members of the group by specifying this group as the recipient. Alpine expanded groups immediately, so I could see who are the actual recipients, so it was easy to add a few more if needed, or remove a few if I wanted to skip somebody from the list. Can this be done in kmail? It would be a necessary feature for me. 

- I created a contact group, but I can not find the corresponding file (vcard?). Where does it get stored?

Thanks

---

### Post by barna on 2011-02-16
I am getting totally confused. Where are my personal contacts stored in kde? The 'Personal C ontacts' addressbook seems to be located in /home/barna/.local/share/contacts/. If I populate this directory with more .vcf files, they simply do not show up in Personal Contacts. 

I created another addressbook as a vCard directory. I populated this directory with .vcf files. They do show up in this addressbook, but none of the contacts (in this addressbook or Personal Contacts) are available from kmail...

I removed ~/.kde to have a clean start, but still my old contacts were there. I have discovered now that everything might be stored in ~/.local/share/akonadi. Is this the directory which I need to remove to have a clean start? What is stored here? Contacts, calendars, passwords? 

My major concern is that I want to have my
- local email folders 
- personal contacts
- calendar
at a well-defined place, so that if I need to remove ~/.kde, all of these are kept safe. 

Thanks

---

### Post by barna on 2011-02-16
So finally I could do (I believe) a clean start:
- I exported my calendar into a .vcs file
- deleted ~/.kde
- deleted ~/.local/share/akonadi
Then 'kontact' complained it can not start akonadi, I managed to do it following [http://brahmalok.wordpress.com/2010/02/13/akonadi-error-solved/](http://brahmalok.wordpress.com/2010/02/13/akonadi-error-solved/)
All is nice, I could then import my saved calendar. However, whatever contacts I put into the default addressbook "Personal Contacts", they do not show up when I want to compose messages. Any idea?
Thank

---

### Post by barna on 2011-02-16
I have set up a clean new user, tried to add entries to the addressbook, and then access them from kmail. No success. Can somebody tell me how to use the addressbook from kmail?

---

