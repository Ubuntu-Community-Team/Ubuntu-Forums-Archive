---
title: "Synchronise KMail folders with Akonadi database"
date: 2017-04-26
forum: Desktop Environments
---

### Post by oygle on 2017-04-26
I use Kubuntu and KMail and have been having major problems with KMail, due to akonadi. At present I need to ensure that what is showing in the file system (under ~/Mail path) is exactly the same as what is stored in the akonadi database.

I have looked at only 2 folders and there are discrepancies in both. What is stored in the file system is less than what is showing in KMail. There are approximately 800 KMail folders, including sub-folders.

I have looked at akonadi server, akonadi console, the KDE forums, Ubuntu forums, and other MySQL tools, but am anuable at present to find any documentation on how to synchronise KMail folders with akonadi database.

Can someone tell me how to do this please ?

---

### Post by oygle on 2017-04-29
Whilst I couldn't get akonadi to synchronise with KMail (tried from KMail and from akonadi console), I was able to use the 'Copy' function on 3 folders, and the missing emails ('missing' , as in not in the ~/Mail path, but 'somewhere' within akonadi database) were copied out to a new folder. Those 3 folders were small in size.

When I tried the 'Copy' folder on larger folders, KMail crashed everytime with an error message.

At this stage, as it has been 7 months of problems with KMail , decided to use what I had in ~/Mail , and use another email client. One that is stable. The email data was a good as it was going to get, and I was not prepared to have to repeatedly restart the akonadi server many times each day.

Found a Perl script to convert KMail folders to Claws email. Been using Claws for a few days now; very impressed with it. Lightweight and fast.

During the last 7 months, as I attempted to get this problem fixed, many people on forums and mailing lists told me that KDE was bloated and it was unstable.

---

