---
title: "Importing Outlook to Eudora to Evolution"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Enigmatic on 2006-06-03
I'm trying to move from Outlook to Evolution, but couldn't do it the Thunderbird way as it would always crash while importing (pst file too large?)

So I imported into Eudora, then tried importing the mbx file to Evolution.

It works pretty well, except there are a large number of older emails with the date as ? and are just blank.

The biggest problem is that HTML emails just display the HTML code, but don't actually render the HTML. ](*,) 

Any suggestions?

---

### Post by warjowuch on 2006-06-07
Same here, really irritating since I want to move a lot of email here.
It seems eudora adds x-html-tags to emails, without changing the body to real x-html. This causes the problem.
Using an imap-server works pretty good, it has nog unreadable emails, but still the stupidity of no html-rendering but just htmlcode...
Someone found an elegant solution?

---

### Post by nixternal on 2006-06-07
I have Outlook 2003 so for me there was only 1 way to import. And that is to have Outlook 2003 installed and then install Thunderbird and have it import. My problem was that I don't run MS at all, and Outlook wasn't going to happen with Wine very easily for me. So I installed a VMWare Server and install MS on a 10gb virtual drive, installed Outlook 2003. Imported my Outlook.pst file into Outlook 2003. I then installed Thunderbird on the MS virtual drive and it automatically imported my Outlook contents. Then I just copied the Thunderbird /mail directory over to my system and utilized Kmail's mailbox/maildir import. I tried everything in order to import the 2003 .pst file, but none of them would read the file correctly and would actually give me an error that would ask if the file was an Outlook 2003 .pst. readpst didn't work for me at all, and was the application that gave me the error. If anyone has a quick and easy fix for this, I would really like to see it.

---

### Post by Enigmatic on 2006-06-08
What I ended up doing is importing to OE, and then to Thunderbird before copying over the mbox files into Evolution's folder.

Worked much better than an IMAP server, and Thunderbird crashed everytime it tried to import my pst file.

---

