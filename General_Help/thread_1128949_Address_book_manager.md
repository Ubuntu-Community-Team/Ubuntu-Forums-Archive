---
title: "Address book manager"
date: 2009-04-18
forum: General Help
---

### Post by rakan_dr on 2009-04-18
Hi, I need a "STANDARD" address book manager to manage my contacts. What i mean by standard is that the CSV file that it generates to export contacts, can be imported by ALL email clients. Because Hotmail contacts export service isn't good. It doesn't' generate a good CSV file, all my email clients can't import my contacts well.

So what do you recommend guys?

---

### Post by Therion on 2009-04-18
> **rakan_dr said:**
> Hi, I need a "STANDARD" address book manager to manage my contacts. ...  So what do you recommend guys?
Most people will probably tell you to try Mozilla Thunderbird.  It allows for contacts to be exported using CSV.

If you want something more along the lines of a PIM (Personal Information Manager) take a look at [Chandler](http://chandlerproject.org/).  

The website has .deb files if it floats your boat.

---

### Post by rakan_dr on 2009-04-18
What about Evolution?

---

### Post by rakan_dr on 2009-04-18
I tried Mozilla Thunderbird, it has a LOT of bugs in the GUI. When i change the theme for example, the GUI of the program get crazy!! Strange colors!

---

### Post by Therion on 2009-04-18
> **rakan_dr said:**
> What about Evolution?
I don't see an option to export to CSV for one thing, only vCard (.vcf) files.  

I've changed the theme on Tbird numerous times and never had an issue.  Not sure what to tell you there.  Have you tried the latest version?  Maybe try a different theme.  Like I said I've never had an issue with theming Tbird, so I dunno.

---

### Post by rakan_dr on 2009-04-18
What does Tbird have over Evolution?

What's wrong with vCards? Can't i import contacts using them?

---

### Post by rakan_dr on 2009-04-18
As i said i need a standard thing please.

---

### Post by Therion on 2009-04-18
[QUOTE=rakan_dr]

What does Tbird have over Evolution?[/quote]
You'll have to research that yourself.


[QUOTE=rakan_dr]

What's wrong with vCards? Can't i import contacts using them?[/QUOTE]
Nothing is "wrong" with them; you indicated you wanted a .csv file in your first post.  You asked what I recommned, I recommend you try Thunderbird.

---

### Post by rakan_dr on 2009-04-19
are CVS-to-vCards converters good? As i understood is that vCards are used to exchange contacts through mobile phones where CVS are used in email clients.

---

### Post by kimda on 2009-05-20
You can export evolution addressbooks to csv format by using the following command: 

evolution-addressbook-export --output=/home/username/file.csv --format=csv

It will export the addressbook which is marked as default. So if you have multiple addressbooks make sure that you mark the one you want to export as default otherwise it will export another addressbook.

---

