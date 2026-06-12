---
title: "403 Forbidden"
date: 2009-05-07
forum: General Help
---

### Post by daggerx on 2009-05-07
So I was setting up lamp using this article [here]("http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06#more-669") Everything worked and I followed everything.

I got to the end and did this:

```
http://localhost/wordpress
```

Like the article says and I got this:

```
Forbidden

You don't have permission to access /wordpress/ on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80
```

Please help and thanks in advance.

---

### Post by BslBryan on 2009-05-07
Hello, daggerx. :-)

I was going to write you out some things to try, but I wasn't sure if I was remembering them correctly, so I Googled my advice, and stumbled upon [this thread]("http://ubuntuforums.org/showthread.php?t=656294") that explains it just as well as I would have.  :-)

I hope that it comes in useful!  :-)

Best to you, and good luck.

---

### Post by daggerx on 2009-05-07
sweet, that worked.

sudoing nautilus and changed the permissions to access files for that folder.

now, wordpress is up and running.

How can one see it from the outside..
what url is this wordpress blog?
yes, I realize this is a different question.

---

### Post by webtechquery on 2010-02-27
Hi.

As about your mentioned problem, which is already solved. But the next question you have asked is kind of strange. May be you are confused in running the wordpress locally and working it on live, to be accessible for others. Please note that no one will be able to access your blog if it is installed on your local machine. For making it accessible, you have to signup on wordpress.com, and there you dont have to install any API on local. And if you want to have your own domain i.e. .com, .net etc., and install the wordpress API in it then its a different thing.

For installing installing API on your own domain, check out the follwing web:
[http://www.webtechquery.com/index.php/2010/01/install-wordpress-on-your-domains/](http://www.webtechquery.com/index.php/2010/01/install-wordpress-on-your-domains/)

---

### Post by DrMelon on 2010-02-27
> **webtechquery said:**
> Hi.

As about your mentioned problem, which is already solved. But the next question you have asked is kind of strange. May be you are confused in running the wordpress locally and working it on live, to be accessible for others. Please note that no one will be able to access your blog if it is installed on your local machine. For making it accessible, you have to signup on wordpress.com, and there you dont have to install any API on local. And if you want to have your own domain i.e. .com, .net etc., and install the wordpress API in it then its a different thing.

For installing installing API on your own domain, check out the follwing web:
[http://www.webtechquery.com/index.php/2010/01/install-wordpress-on-your-domains/](http://www.webtechquery.com/index.php/2010/01/install-wordpress-on-your-domains/)

He is using LAMPP, which is basically an all-in-one webserver package - I use it myself, and my stuff is accessible from the outside world.

What you have to do, daggerx, is if you have a router, forward the ports used by LAMPP (which you set up during install) to the PC it is hosted on.

Then, anyone who wants to view your page needs your External IP Address (or you can buy a domain name and link it to your IP).
If you are going by the IP method, they would have to type something like [http://123.321.123.123:8080](http://123.321.123.123:8080) where the number after the colons is the port you chose during setup.

---

### Post by webtechquery on 2010-02-28
> **DrMelon said:**
> He is using LAMPP, which is basically an all-in-one webserver package - I use it myself, and my stuff is accessible from the outside world.

What you have to do, daggerx, is if you have a router, forward the ports used by LAMPP (which you set up during install) to the PC it is hosted on.

Then, anyone who wants to view your page needs your External IP Address (or you can buy a domain name and link it to your IP).
If you are going by the IP method, they would have to type something like [http://123.321.123.123:8080](http://123.321.123.123:8080) where the number after the colons is the port you chose during setup.

Well, if talking about a one home system, then it is really strange that one wants it to be accessed throughout the world, by using his own PC, through static ip. As PC could be restarted, burst etc., even is the internet wire or wireless connection be disconnected somehow, then what ? 
I seriously dont think that running a blog through a home PC is a good way. Why not to try wordpress, blogspot etc. Even there are free packages while using wordpress subdomains.

---

