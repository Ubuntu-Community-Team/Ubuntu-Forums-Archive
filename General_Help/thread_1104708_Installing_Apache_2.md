---
title: "Installing Apache 2?"
date: 2009-03-23
forum: General Help
---

### Post by iflymyhelishigh on 2009-03-23
Hello. I am currently learning Ubuntu and the whole UNIX command system all around, and have a question.

I am trying to set up a web server for a company website, mainly because I hate godaddys hosting. When I try to do the 

sudo apt-get install apache2

it always comes up with Failed to fetch etc.

The error message I get is

Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I don't know what to do from here on, help would be greatly appreciated, thanks

---

### Post by iflymyhelishigh on 2009-03-23
I just read up on apt-get upgrade or update, none of them work. It gives me something like could not resolve us.archive.ubuntu.com

for now, I am going to go to bed. Tomorrow I will check it to see if it was the server.

---

### Post by bodhi.zazen on 2009-03-23
did you try :

```
sudo apt-get update
```See also : [https://help.ubuntu.com/8.10/serverguide/C/httpd.html](https://help.ubuntu.com/8.10/serverguide/C/httpd.html)

---

### Post by James_Lochhead on 2009-03-23
I do not recommend that method. The following command will install Apache, MySQL and PHP for you. 

```
sudo tasksel install lamp-server
```

Everything should now be working. Now you need to configure the Apache virtual hosts. See:

[Click here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual Hosts")

That web page is a great reference for installing PHP/MySQL/Apache.

---

