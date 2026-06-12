---
title: "PHP Not working"
date: 2006-03-30
forum: Desktop Environments
---

### Post by rocarm on 2006-03-30
I followed [http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)
on how to install php4 apache. Apache is working fine but php4 isn't, do i have to type in a command to make it auto load? I'm still new, can anyone lend an idea?

---

### Post by dermotti on 2006-03-30
If PHP is configured properly it will load up when you start apache. Have you tried restarting apache?

What happens when you load up a php page?

You may have missed this step:
"To ensure your PHP files are properly interpreted, open httpd.conf , remove the # at the beginning of the lines which read:
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps

If the AddType lines above don't exist, manually enter them (without the leading # of course) after the line

AddType application/x-tar .tgz"

Then restart apache.

---

### Post by rocarm on 2006-03-30
Yea i've restarted apache, i even restarted the pc to make sure it was restarted, and when i try to view a php file it comes up with the promp to open or save the file, so apache isn't handling the .php request.

---

### Post by dermotti on 2006-03-30
Then you didnt to the step above i just edited in :-)

Another funky thing is, once you get it working, that page is going to be cached in your browser, so everytime you visit that page, its gonna prompt you to download it (even if php is properly working now). So keep renaming hte .php file you are trying to open to ensure you arent view a cached page.

---

