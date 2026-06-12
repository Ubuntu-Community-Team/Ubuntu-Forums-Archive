---
title: "Customers Database package - small business"
date: 2008-09-23
forum: Desktop Environments
---

### Post by Berduchwal on 2008-09-23
I am looking to set up small business and one of the things it will be doing is storing information about customers in a database.

I would be looking for preferably packaged application that can store details like: name, address, phone, email, account no, and few other custom columns.

I would be best if it could have its files on network drive and few pc could access those files at the same time. Encryption of those files would be important.

Additional features that I would benefit from:
- ability to print labels from the application or custom documents using details from the database
- automated mailing?

Any suggestions?

---

### Post by Idefix82 on 2008-09-23
Sounds like you want to set up a database server (eg MySQL) and write a frontend for that that suits your needs, eg with PHP.

---

### Post by Berduchwal on 2008-09-23
I would prefer something out of the box not bespoke.

---

### Post by Idefix82 on 2008-09-23
I think that might be tough, such things rarely come completely out of the box since different people have slightly different needs. However, a rudimentary application with MySQL wouldn't be difficult to program. An experienced web programmer would probably need a couple of days at most.

---

### Post by Berduchwal on 2008-09-23
That is great but then I would need to ask him or someone else to support it and fix bugs and so on.

That is why I would prefer to settle for something that does not necessarily meet all the requirements but is widely supported for free.

---

### Post by mdebusk on 2008-09-23
> **Berduchwal said:**
> I am looking to set up small business and one of the things it will be doing is storing information about customers in a database.

I think something from [37Signals]("http://www.37signals.com/") would work for you. I use HighRise for contact management, and it's great. It also meets your "network" criterion, as it's Internet-based.

I don't know about printing or mailing, as I never use those features, but 37Signals is known for its responsiveness to customers.

---

### Post by Berduchwal on 2008-09-23
thanks but it does not look free :)

---

### Post by mdebusk on 2008-09-24
> **Berduchwal said:**
> thanks but it does not look free :)

Then you didn't [look in the right place]("https://signup.37signals.com/highrise/Free/signup/new"). HighRise is free for two users and 250 contacts. If your business reaches 250 active customers, you can afford to upgrade. Good CRM is an expense only from an *accountant's* perspective; for marketing, it's an investment.

There's [Zoho CRM]("http://www.zoho.com/crm/zohocrm-pricing.html") as well. I looked at it and found it way too complex for my needs. You, a business owner, might like it, though.

Here's [an article on open source CRM tools]("http://www.insidecrm.com/features/top-open-source-solutions-121307/") if you want to do the sweating yourself instead.

---

### Post by Berduchwal on 2008-09-24
this depends what is your average income per customer if you are only getting lets say 0.5$ then 250 customers only gives you 125$

I am looking for something open source and free regardless of number of customers.

---

### Post by mdebusk on 2008-09-27
> **Berduchwal said:**
> I am looking for something open source and free regardless of number of customers.

I'm curious as to what you'll do if you can't find a turnkey solution that is also open-source and free.

---

### Post by Berduchwal on 2008-09-28
I will use kmail where I can create custom field.

---

### Post by shane2peru on 2008-10-28
I have been searching for something like this for years.  It doesn't exist in Linux.  I always used ACT! for windows, and have contacted them about writing something up for Linux (of which they are considering).  Evolution, Kontact and are just not quite up to par with these things.  It is a great frustration for us that need to manage a large amount of contacts with relatively little revenue generated.  I want something that I don't need to be connected to the Internet to use.  And I'm not a programmer, and don't know of a programmer.  I continually search for this kind of information.

Shane

---

### Post by JohnJackson on 2009-01-22
I am looking for something like this too, I haven't found anything yet. I'm surprised there isn't anything that is free, would make a good open source project.

---

### Post by hobbestec on 2009-01-22
There are a number of projects out there that will do this for you that are free and open source.  My project is citrusdb.  It provides a customer database and can bill for most any service.  It is available from [www.citrusdb.org](www.citrusdb.org).  It requires you have your own web server running MySQL and PHP on your LAN or PC to hold the information.

Some of the other open source billing projects out there are:
freeside
bambooinvoice
jbilling

They all have pros and cons and differing levels of complexity to meet different customer requirements.

---

### Post by XanTrax on 2009-01-22
You can use flat files if MySQL is too complicated for what you want.  Try out OpenOffice-base which is a way for you to run queries, create databases, and etc in openoffice.  I am pretty sure openoffice is flat file database which means it is not an object oriented database...pretty much, it makes it complicated to keep it clean BUT if you are only storing information on customers and do not need to make a lot of tables, or in this case, files; then openoffice-base is where you wanna go.

---

### Post by shane2peru on 2009-01-22
We are usually just regular old computer users that are requesting this stuff.  Working with MYSQL or SQLITE or databases in general is a real mind boggling thing at least for me.  Basically that means it is not user friendly to us the end user.  Also, for these web based things, that may be good for the big guy, but that also spells complex setup and installation.  I have setup a server on my box before, but believe me when I say it wasn't simple.  We are looking for something that is as simple as Evolution to install (in a simple deb installation format) that runs easily and simply.  You really need to look at Symantec ACT! (I think the maker has changed to SAGE) and see what we are talking about.  NO php server sql setup stuff, just an application, that perhaps even uses that stuff, but the user doesn't have to try and figure out it's complex installation issues.  Just my 2 cents worth of info on what I'm looking for.  Egroupware is very similar to what I need but once again deals with that php stuff, and web interface.  It is installable as 1.2 version in the repos, however they are on 1.4 with some significant fixes.

Shane

Hey I just checked the repos and egroupware 1.4 is in!!!  Also checked egroupware site, and they are up to 1.6 :( sigh.  But I think 1.2 had some serious bugs, that was holding me back from using it.

---

