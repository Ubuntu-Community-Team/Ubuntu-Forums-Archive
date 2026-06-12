---
title: "evolution 2.4 can't retrieve contacts"
date: 2005-10-14
forum: Desktop Environments
---

### Post by iimess on 2005-10-14
I was using evolution 2.2 with exchange connector. After upgrade to 2.4, it asks for my password for Mail, which is ok, but it also asks for password for Contacts, which I don't remember it did back in 2.2. I went ahead to enter it anyway, but it says:
> Unable to perform search.
This query did not complete successfully.
And fails to retrieve my contacts.
(There are 3 contacts categories:
Personal: I had nothing there
Global Address List from Exchange: It never worked in 2.2 anyway
Contacts from Exchange: This is the one that gives the above error.)

---

### Post by kaktusztea on 2005-10-17
I have the same problem, but I can not connect to the calendar also :( 

I think Evolution should be an important point of Gnome, because a lot of people need it to connect to the company's Exchange server.

Contrarily, I wouldn't say that it is stable.
Evolution-exchange backend process dies regularly, can not connect to Contacts, Calendar, etc. ](*,)

---

### Post by department27 on 2005-10-17
I had the same problem. Played around with it a bit. What I found was that if I deleted my mail accounts, and then recreated they worked for a bit and as I changed things for example changing autocompletion settings it would stop. 
Tried this an number of times and different settings but could nto get it to work.
Then for some reason it started to work. Never had a problem since.

What I would do is delete you accounts and recreate, that sort of did the trick for me.

Not really a solution, but it fixed my contacts and calendar.

---

### Post by jadajada on 2005-10-22
Just giving this a bump. It does not work. No contacts and no calendar. Fresh install of official 5.10 and apt-get upgrade. 

Anyone getting this to work, besides recreating account, which did not help.

---

### Post by department27 on 2005-10-22
try this one. change the server name for the global cataloge server.

for example:

mail.fred.com to mail.

save then try it, it will fail. Then reset it back to ou original. save and try it again

---

### Post by PeterAB on 2008-03-18
Department 27:  thank you that is exactly what I was looking for![http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

what's department 27 anyway?

---

### Post by department27 on 2008-03-18
Actually I hear department27 in a song back in the eighties, and it stuck in my mind :-)

---

