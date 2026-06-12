---
title: "how to make a website with usernames and passwords?"
date: 2009-05-03
forum: General Help
---

### Post by gfunkera on 2009-05-03
how can i make a web page secure or look differnt with a user logged into it?

---

### Post by BslBryan on 2009-05-03
Can you be a little more specific please?

Your post is a little vague. :)

---

### Post by lisati on 2009-05-03
> **gfunkera said:**
> how can i make a web page secure or look differnt with a user logged into it?
The first thing that comes to mind is COOKIES which you might be able to test for.

---

### Post by gfunkera on 2009-05-03
what i mean is i have a web server set up on a computer and im going to set up the router its connected to with a DMZ so that it can be accessed from other computers by going to the IP address and a specific port... when the user gets to the site the first thing they get is two text boxes to type in their name and password.. then that username and password gets checked against a database and then the person is directed to a page where they can view stuff and edit databases, etc... 

im writing this database and site for work so that we can go paperless and be more effiecient...

eventually i dont want outsiders accessing the important page (the one after the login page) to be accessed by others by simply typing in the url in their browsers (if they somehow were to figure out)... but that capability isnt entirely important as long as i can have different users and their own passwords.. the people using this system arent very computer savvy and the site will be a local thing that wont be accessible from the internet..

---

### Post by 4Orbs on 2009-05-03
EDIT: Disregard this post. Sorry, I misinterpreted the requirements.

Create the website with a blog software like WordPress or if you want something more complex, use a CMS like Joomla or Drupal. Most of these require a database. These are a better alternative to writing your own html or php website. They install quickly and have plenty of plugins available to customize your site. Instant website, complete with user accounts, security, and easy modification.

---

### Post by bodhi.zazen on 2009-05-03
You can secure your [page with ".httaccess".

See [http://www.elated.com/articles/password-protecting-your-pages-with-htaccess/](http://www.elated.com/articles/password-protecting-your-pages-with-htaccess/)

[http://httpd.apache.org/docs/1.3/howto/htaccess.html](http://httpd.apache.org/docs/1.3/howto/htaccess.html)

If you can,  ie you have access to the apache config files, configure apache and not .htaccess. (use the same commands and set-up, but put them in your apache config file and not in .htaccess).

See also :

[http://httpd.apache.org/docs/1.3/howto/auth.html](http://httpd.apache.org/docs/1.3/howto/auth.html)

---

