---
title: "[HOWTO] Use a proxy with authentication with Synaptic/apt-get"
date: 2006-07-07
forum: Desktop Environments
---

### Post by ajkst1 on 2006-07-07
This was a major issue that I had with using Ubuntu at work. I did a search on Google Groups and found this post that worked for me. Thanks to veehell on  the ubuntulinux newsgroup for the fix!

> From:	 	veehell - view profile
Date:		Tues, Mar 21 2006 11:05 am
Email: 		"veehell" <veeh...@gmail.com>

Hi Ming

this is usuall issue with synaptic application. How to fix it ?
go to "Settings" >> "Network" and fill it like this

<your_proxy_account>:<your_proxy_password>@<proxy_adress_or_ip>

then restart synaptic and try again. Be aware, because each proxy have
different loging (email adress vs user_id)

if you want to use with apt-get/dpkg you have to specify "http_proxy"
variable....and export it. Search ubuntuforums (original/official site)
or Wiki.ubuntu, there are severals threads related to.

shortly (c'n'p) >>
edit /etc/wgetrc find the line where "http_proxy" and "ftp_proxy",
delete the sharp (#) symbol and modify proxy connection with your
connection in this format: http://<username>:<password>@<your_proxy_url>:<your_proxy_port>

/etc/bash.bashrc file so it looks like the
following:   export http_proxy=http://<username>:<password>@<your_proxy_url>:<your_proxy_port>

read also those:
[http://ubuntuforums.org/showthread.php?t=137668&highlight=proxy+synaptic](http://ubuntuforums.org/showthread.php?t=137668&highlight=proxy+synaptic)
[http://ubuntuforums.org/showthread.php?t=136065&highlight=proxy+synaptic](http://ubuntuforums.org/showthread.php?t=136065&highlight=proxy+synaptic)

Also there is "global" GUI settings for "proxy" inside the "GNOME" so
you can specify the proxy there also....

cheers
-vh- 


---

