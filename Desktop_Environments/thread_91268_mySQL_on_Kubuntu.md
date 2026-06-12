---
title: "mySQL on Kubuntu"
date: 2005-11-16
forum: Desktop Environments
---

### Post by PokerFacePenguin on 2005-11-16
I have attempted to install (unsuccessfully) drupal.  Over the course of time I have loaded my machine with different applications to tune it to my preferences.   Apache, Apache2, PHP4, and PHP5, myphpadmin, and mySQL have all eventually found their way onto my machine.  I have borked up my drupal install so bad that I would like to reinstall it from scratch with a new guide that I have recently found here:

[http://www.umasslug.org/index.php/Drupal_on_ubuntu_server](http://www.umasslug.org/index.php/Drupal_on_ubuntu_server)

The problem is I am wondering what is going to break when I uninstall all of the aforementioned programs.  I was poking around in the databases for mySQL and there is a database in there called "mysql" along with the other test db's that I have created and the one for the unsuccessful attempt at drupal.  Inside the mysql database there are some tables that appear to have something to do with system maintainence.  I say this because inside of one of those tables there is an account that I have not created named "debian-sys-maint".

I have said all this because I am wondering if it is safe to start removing all of these programs.....
I believe that if I remove mySQL that it will most likely break something that came with the default install and I have spent too much time tweaking this install of kubuntu out to bork it up good.

Am I correct in extrapolating that mySQL comes with the base install of Kubuntu Breezy 5.10?
What will break if I remove mySQL?

Any help with this sure would be appreciated.  Thanks.

---

### Post by HermanAB on 2005-11-16
If you delete the mysql db then you have to reinstall mysql, so don't do that...

See this:
[http://www.aerospacesoftware.com/MySQL_Howto.html](http://www.aerospacesoftware.com/MySQL_Howto.html)

Cheers,

Herman

---

### Post by PokerFacePenguin on 2005-11-17
[QUOTE=HermanAB]If you delete the mysql db then you have to reinstall mysql, so don't do that...

See this:
[http://www.aerospacesoftware.com/MySQL_Howto.html](http://www.aerospacesoftware.com/MySQL_Howto.html)

Cheers,

Herman[/QUOTE]

I had decided to try and work it out so I just did a "drop" for the drupal table I had created before and tried to reinstall drupal.  I am still getting the error from firefox wanting to download the phtml file.  It's got me stumped.

---

