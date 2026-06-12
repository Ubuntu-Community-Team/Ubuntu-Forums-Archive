---
title: "Evolution - Gmail contacts"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Zodiac on 2006-02-22
How can I take the csv file that gmail supplies and import it into Evolution?

I cannot for the life of me figure out how to get this to work...

I don't understand, is the "comma separated list" a proprietary format or something??? Why is this so difficult??

---

### Post by Zodiac on 2006-02-22
Holy Moly! 

I figured it out... and let's just say, it wasn't easy.

See below, you don't have to PM me! :)

---

### Post by paquito on 2006-03-05
hey,

been looking at finding a way of synchronising my evolution contacts with those from gmail... quite easy to set up mail, but contacts has been a bit tricky...  

I'd appreciate if you could let me know what u used? It would be great if you could synchronise your address books without having to import and export any files... there must be a way... when i have more time to look at it...

---

### Post by Zodiac on 2006-04-21
[QUOTE=paquito]hey,

been looking at finding a way of synchronising my evolution contacts with those from gmail... quite easy to set up mail, but contacts has been a bit tricky...  

I'd appreciate if you could let me know what u used? It would be great if you could synchronise your address books without having to import and export any files... there must be a way... when i have more time to look at it...[/QUOTE]

I thought I would save myself some PMs and just post what I did.

It isn't possible per say from GMAIL itself&#8230; **BUT**...

It **IS possible** from yahoo mail.

So, what you should do is:

Import your Gmail contacts into a **free **yahoo account, edit them however you want, and then export them as a Netscape LDIF file. 

Once you have done that, it should be a breeze to import them into evolution. 

It sounds a lot more time consuming than it is, and it never hurts to have another spam account ;)!

Hope that helps!

---

### Post by ryu kun on 2006-11-14
I just did it from Gmail itself. Just export Gmail contacts as importable by Outlook then import that file to Evolution.

---

### Post by cvmostert on 2007-07-08
> **ryu kun said:**
> I just did it from Gmail itself. Just export Gmail contacts as importable by Outlook then import that file to Evolution.

I did exactly what you did and it did not import the fields correctly, sorry.

will need to see if i can convert the current gmail.csv to evolution-read.csv

If there is another solution, please post it here.

---

### Post by fsufitch on 2007-12-25
I did a little googling and I found the problem: Google exports in CSV of Full Name, EMail and Evolution wants First Name, Last Name, Nickname, E-mail. You can use oocalc to screw around with the CSV or... you can tell GMail to "export to vCard" and import that into Evolution.It works!

---

### Post by electedfreedumb on 2008-01-12
Just tried the Vcard thing and it works excellent. Nice. This is my second install and the first time I did it with outlook style and spent a good while re-formatting the layout of the contacts to work right.

:popcorn:

---

