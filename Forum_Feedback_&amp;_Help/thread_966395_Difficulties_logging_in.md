---
title: "Difficulties logging in"
date: 2008-11-01
forum: Forum Feedback &amp; Help
---

### Post by Alaric on 2008-11-01
I'm having some pretty major problems logging into the site right now.  The only way that I manage to log in is by going to the forum FAQ section and entering my password at the top of the screen there.  Otherwise, when I try to log in it gives me the "Thank you for logging in, please click here if your browser doesn't automatically redirect you" and I get dropped back to the page I was on *Not* logged in.  I'm running Firefox 3.0.3 on an updated Ibex.  Have you guys heard about anything like this before?

---

### Post by pp. on 2008-11-01
What, exactly, is the URL of the page which does not accept your login?

---

### Post by Alaric on 2008-11-01
Anything that's not [http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48) it seems like.  I've tried going to post comments, that's got me locked out.  I've tried logging in from the welcome page, no dice.  I've tried logging in from forum main screens and I had no luck there either.  But for some reason (this has worked twice now) when I went to check that Forum FAQ to see if I was banned or something it let me log in from there.

---

### Post by pp. on 2008-11-01
What, ***exactly***, is the URL of a page which does ***not*** accept your login?

---

### Post by Alaric on 2008-11-01
Well, I had been having trouble from [http://ubuntuforums.org/](http://ubuntuforums.org/), but it seems to be working now.  Maybe it was a problem with firefox.  I'll post back if it happens again.

---

### Post by mockdeep on 2008-11-19
I'm having this same problem.  Some pages will show me as logged in and others won't.  Obviously, I'm logged in here, whereas when I am on [http://ph.ubuntuforums.com/showthread.php?t=889317](http://ph.ubuntuforums.com/showthread.php?t=889317) it will have me as not logged in.  When I try to log in it gives me the "Thank you for logging in, mockdeep" message and then just redirect me to the login screen again.

---

### Post by pp. on 2008-11-20
> **mockdeep said:**
> when I am on [http://ph.ubuntuforums.com/showthread.php?t=889317](http://ph.ubuntuforums.com/showthread.php?t=889317) it will have me as not logged in.

The correct URL of this page is 
[http://ubuntuforums.org/showthread.php?t=889317](http://ubuntuforums.org/showthread.php?t=889317)

It's always 'http://ubuntuforums' and not 'http://ph.ubuntuforums' or 'http://www.ubuntuforums'.

---

### Post by mockdeep on 2008-11-20
> **pp. said:**
> The correct URL of this page is 
[http://ubuntuforums.com/showthread.php?t=889317](http://ubuntuforums.com/showthread.php?t=889317)

It's always 'http://ubuntuforums' and not 'http://ph.ubuntuforums' or 'http://www.ubuntuforums'.

Strange, when I click your link it just redirects me to the forum start page. [http://ubuntuforums.org/redirect.php?t=889317](http://ubuntuforums.org/redirect.php?t=889317).  Looks like it should be ubuntuforums.org not .com.  But that helps.  Now I am logged in when I go to the page.  How does the ph. end up in the address, though?  And the .com now that I think of it...  It's not like I went and changed the address in the bar.  Could it be because I found the link from a Google search?

---

### Post by pp. on 2008-11-21
> **mockdeep said:**
> Looks like it should be ubuntuforums.org not .com. 

Quite. That was an oversight on my part. It is, indeed, .org and not .com.

---

### Post by FuturePilot on 2008-11-21
> **mockdeep said:**
>  Could it be because I found the link from a Google search?
Most likely. I've seen a number of different urls in Google's results. ph. being one other them. How it actually gets there, I have no clue. :)

---

### Post by drubin on 2008-11-22
> **FuturePilot said:**
> Most likely. I've seen a number of different urls in Google's results. ph. being one other them. How it actually gets there, I have no clue. :)

Do the admins know about this? and it not be resolved? It seems that *.ubuntuforums.org | *.ubuntuforums.com points to the same server, and same vhost. This is a valid url > [http://asdfasdfasdf](http://asdfasdfasdf) . ubuntuforums . org  I added spaces as I do not want Google re-indexing odd stuff that it shouldn't.

I would submit this as a bug. mainly because logins and preferences do not carry through with the subdomains. Can we not redirect the browser for any thing that is not ubuntuforums.org/ ?

---

### Post by pp. on 2008-11-22
That issue has been discussed time and again. I don't know, however, if any kind of resolution has been arrived at.

---

### Post by drubin on 2008-11-22
> **pp. said:**
> That issue has been discussed time and again. I don't know, however, if any kind of resolution has been arrived at.

clearly it hasn't if it still happening. :)

---

### Post by drubin on 2008-11-26
> **drubin said:**
> Do the admins know about this? and it not be resolved? It seems that *.ubuntuforums.org | *.ubuntuforums.com points to the same server, and same vhost. This is a valid url  I added spaces as I do not want Google re-indexing odd stuff that it shouldn't.

I would submit this as a bug. mainly because logins and preferences do not carry through with the subdomains. Can we not redirect the browser for any thing that is not ubuntuforums.org/ ?

Is there a reason why the [404 error page]("http://en.wikipedia.org/wiki/404_error") is infact the index.php?
http : // ubuntuforums. org/foo/bar/nothing loads up the forum index(Clearly with the relative css paths messed up.

The same would go for /showthread**d**.php how are people to know the url was not valid if you direct them to the main index page with no warning? Is this a config choice of the admins or default forum behavior.

---

