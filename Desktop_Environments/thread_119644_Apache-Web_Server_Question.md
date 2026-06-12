---
title: "Apache-Web Server Question"
date: 2006-01-19
forum: Desktop Environments
---

### Post by gbold on 2006-01-19
This has probably been answered before but I am trying to set up a web server using Apache and I want to use a folder/partitition I created during the install of Ubuntu 5.10 called /web (partition 2 on drive 2) to hold my /slr4l web folder with my site in it.  Question is, what should I set the permissions for the /web and /slr4l folders to so everything will be secure?  I think I can figure out how to set up Apache to use the /web/slr4l folder (lots of great info on this from the community).  Any other tips and/or ideas (like other programs to install besides Apache... FTP server, Mail server etc.) to help me along is always appreciated.
Thanks-
Linux Newbie Greg

---

### Post by darth_vector on 2006-01-19
you want the permissions to be 755. the folder must be world readable and executable for others to see the webpage.

you might want to install a firewall. i use shorewall and its quite easy to install and configure.

---

### Post by gbold on 2006-01-20
Darth-Vector
So both the root folder (/web) and the page folder (/slr4l) should be set to 755?  I'm currently behind a router that I set up with 4 subnets (the webserver will be on one with my house computers on another) and I look into the firewall program you mentioned.  Any one else? Preferred mail and ftp servers?
Thnaks to All-
Greg

---

