---
title: "Mediawiki/webhttrack conflicting with xampp"
date: 2009-06-22
forum: General Help
---

### Post by hellocatfood on 2009-06-22
I have xampp/lampp installed on Ubuntu Jaunty and I usually start xampp typing into the terminal:
```
sudo /opt/lampp/lampp start
```
I installed Mediawiki from the repository as well as [Httrack](http://www.httrack.com/) and I think that one or both of those is interfering with xampp. Whenever I try to start xampp I get the follwing error:
```
Starting XAMPP for Linux 1.7.1...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
```
I have a feeling that I somehow need to stop mediawiki and/or webhttrack but how do I do that? Or, how do I stop the other daemons from running?

---

### Post by madverb on 2009-06-22
What now? Mediawiki isn't a daemon...
Apache is the web server you are using. It just seems like it is already running. What is the problem you are having if there is any?

---

### Post by hellocatfood on 2009-06-22
I try going to [http://localhost/xampp/](http://localhost/xampp/) and it says that the page couldn't be found. This is before and after using /opt/lampp/lampp start

---

### Post by madverb on 2009-06-22
Why are you using xampp? Just do a LAMP install and install whatever else you need.

---

### Post by hellocatfood on 2009-06-22
Sorry, I'm not being very clear.

I installed mediawiki [as explained here](https://help.ubuntu.com/community/MediaWiki). So, right now, I could just go to [http://localhost/mediawiki](http://localhost/mediawiki) and start using it

I did install lampp*, and now, whenever I start it it gives me the error that another daemon is already running.

I suspect it's mediawiki causing problems as it's the only other application (that I know of) that is using localhost. webhttrack only seems to use localhost when I launch it. Is there a way to stop mediawiki whilst I'm using xampp?




*I thought the name lampp/xampp was interchangeable. I've had lampp from the beginning

---

### Post by madverb on 2009-06-23
I'm still not understanding what your problem is.
You can't stop MediaWiki... you can take it out of the apache config or you can delete the symlink to it found in the /var/www folder.
I can't exactly figure out what the problem is? Are you trying to access the original XAMPP index page?

---

### Post by hellocatfood on 2009-06-23
> **madverb said:**
> Are you trying to access the original XAMPP index page?

Yes, that's it! Right now when I go there ([http://localhost/xampp](http://localhost/xampp)) I'm getting a 404.

---

### Post by madverb on 2009-06-23
Ahh ok. You might want to find the settings for the xampp site.
Usually the site will be located under /usr/share directory.
If the directory /usr/share/xampp exists you might just need to add a symlink like this:
```
sudo ln -s /usr/share/xampp /var/www/xampp
```
Then refresh that link in the browser.

---

### Post by hellocatfood on 2009-06-26
Going on the instructions from the lampp website I installed it to /opt/lampp.
The other two directories you mentioned in the code don't exist. Do I need to create those?

---

