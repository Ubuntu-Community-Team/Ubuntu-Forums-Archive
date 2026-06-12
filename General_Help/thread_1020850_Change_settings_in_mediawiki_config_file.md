---
title: "Change settings in mediawiki config file"
date: 2008-12-24
forum: General Help
---

### Post by ollebolle on 2008-12-24
Hi!

I am running a server with Ubuntu 6.06.
I use apache mostly for file hosting, and it works great! Nice software :)

I do also build amplifiers, and I wanted to make a web page with my amplfifer-projects.
The mediawiki software is great! It's very easy to create and edit pages with a nice web gui!
So now I have made some pages and it looks good :)

Now I want to restrict access! I want everyone to be able to view the pages, but I want to be the only one who can edit the pages.

This is not the mediawikiforum I know, but the mediawiki-people tells me to ask you ubuntu-people, because I use ubuntu-package!
I have version 1:1.7, or 1.7 of the ubuntupackage and it contains mediawiki version **1.4.14**.

This page tells me how to change the settings.
[http://www.mediawiki.org/wiki/Manual:Preventing_access#Restrict_editing_of_all_pages](http://www.mediawiki.org/wiki/Manual:Preventing_access#Restrict_editing_of_all_pages)

> # Disable anonymous editing
$wgWhitelistEdit = true;


> 
# Prevent new user registrations except by sysops
$wgWhitelistAccount = array ( "user" => 0, "sysop" => 1, "developer" => 1 );


As you can see I added these lines to my LocalSettings.php The bottom lines at the picture.

[img]http://vidingsjoserver.dnsalias.net/upload/mediawikiscreenshot.png[/img]

Nothing happens :(  I have rebooted, but still: all people can change the articles.

Is there a good solution? :P

---

### Post by ollebolle on 2008-12-24
By the way. This image (a little large maybe) is hosted on my server :)

---

### Post by ollebolle on 2008-12-24
By the way. This image (a little large maybe) is hosted on my server :)

---

### Post by albinootje on 2008-12-24
> **ollebolle said:**
> 
I have version 1:1.7, or 1.7 of the ubuntupackage and it contains mediawiki version **1.4.14**.

This page tells me how to change the settings.
[http://www.mediawiki.org/wiki/Manual:Preventing_access#Restrict_editing_of_all_pages](http://www.mediawiki.org/wiki/Manual:Preventing_access#Restrict_editing_of_all_pages)


According to this page [http://packages.ubuntu.com/search?keywords=mediawiki](http://packages.ubuntu.com/search?keywords=mediawiki) there's 1.7 in the dapper-backports.

Your screenshot shows a MediaWiki 1.7 reference.
Can you post the output of :
```

dpkg -l|grep -i mediawiki

```
And in case you're indeed using MediaWiki 1.7 and not 1.4.x, then you need to use the instructions from the "1.5 upwards" section of the mediawiki.org page you mentioned.

---

### Post by ollebolle on 2008-12-24
Hi albinootje!
Thank you for looking into my problem!

This is the output:

[img]http://vidingsjoserver.dnsalias.net/upload/dpkg.png[/img]

I guess you are right! :) I will try the solution for 1.7 version right away!

---

### Post by ollebolle on 2008-12-24
Thank you albinootje! You totally solved my problem! :p :p

Now when the page is safe I can show it! This is the page about my amplifiers:
[http://vidingsjoserver.dnsalias.net/mediawiki](http://vidingsjoserver.dnsalias.net/mediawiki)

Maybe I will buy a domain later ;)

Thanks again!

Olle

---

### Post by albinootje on 2008-12-24
> **ollebolle said:**
>  Now when the page is safe I can show it! This is the page about my amplifiers:
[http://vidingsjoserver.dnsalias.net/mediawiki](http://vidingsjoserver.dnsalias.net/mediawiki)

Maybe I will buy a domain later ;)


Cool! :)

By the way, I like Jazz too :)

---

### Post by ollebolle on 2008-12-24
Nice! :P

---

