---
title: "packages.ubuntu.com"
date: 2005-04-20
forum: Desktop Environments
---

### Post by leech on 2005-04-20
Now that we have a proper package searching website, I was wondering if/when it will be possible to add the search engine to Firefox?  Since Firefox is the default browser with Ubuntu, I think this would be a good idea.  

There is already a way to set up a search for the packages for Debian (I use it all the time).  It's convenient to have, instead of having to load up synaptic everytime.  

Leech

---

### Post by heimo on 2005-04-20
I'm not sure what kind of package search you're refering to, but here's my "poor man" solution. (I have to translate these, so the actual terms may be off.)
 
Add new quick search bookmark to Firefox. For url, enter
[url="http://packages.ubuntu.com/%s"]```
[/url][http://packages.ubuntu.com/%s]("http://packages.ubuntu.com/%s")[url="http://packages.ubuntu.com/%s"] 
``` [/url]
 
And for keyword for example *u*
 
Now if you type (on the address/location field):
u build-essential
you'll get hits for that package.
 
You can add another quick search for searching on descriptions:
[url="http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=%s&searchon=all"]```
[/url][http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=%s&searchon=all]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=%s&searchon=all")[url="http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=%s&searchon=all"]
``` [/url]
 
for keyword ud, and enter *ud compiler* to find compilers.. and so on. :)
 
Maybe this wasn't what you meant, but maybe this is helpful for someone out there.
 
EDIT: Please note that on second example forum shortens the url. Hover your mouse over and look at the status bar.

---

### Post by speedman on 2005-04-20
Ask and you shall receive.  :) 

Put the attached image - ubuntusearch.png - in /usr/lib/mozilla-firefox/searchplugins.

Then create a file /usr/lib/mozilla-firefox/searchplugins/ubuntusearch.src with this content:

=====

# Mozilla Firefox plugin file
#
# Ubuntu package lookup
# by Chris Heaven based on the Debian package search plugin
# by Fergus McKenzie-Kay who utilized original code
# by Spencer Wysinger <http://wysinger.com/>
#
# Last updated: April 20th, 2005

<search
        name="Ubuntu Package Search"
        description="Perform a search for Ubuntu packages"
        action="http://packages.ubuntu.com/cgi-bin/search_packages.pl"
        searchForm="http://packages.ubuntu.com/"
        queryEncoding="utf-8"
        queryCharset="utf-8"
        method="GET"
>

<input name="searchon" value="names">
<input name="subword" value="1">
<input name="version" value="all">
<input name="release" value="all">
<input name="keywords" user="">
<input name="sourceid" value="mozilla-search">

</search>

=====

Restart Firefox and the Ubuntu package search option will be available in the menu of search engines.

HTH


Regards,

SM

---

### Post by Chris_Durham on 2005-04-20
Speedman,

I tried the code you displayed and it's not working for me. I'm very new to the whole linux world so it'svery possible I'm doing something wrong, but I don't know what.

---

### Post by speedman on 2005-04-20
This should be easier for you.  Download this file:

[http://beonix.ca/ubuntusearch.tar.gz](http://beonix.ca/ubuntusearch.tar.gz)

Extract the tarball and cd to the ubuntusearch directory.  Run the install.sh script (as per the included README), restart Firefox and the search plugin will be available to all users on your system.


Regards,

SM

---

### Post by Seth on 2005-04-20
Speedman,

I used the first method and worked great, thanks :D

---

### Post by speedman on 2005-04-20
My pleasure Seth.  :) 


Regards,

SM

---

