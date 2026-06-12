---
title: "Configuring Apache2 Visually?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by atraeyu on 2006-09-13
Yesterday I installed ubuntu.  Today I installed apache2, php5, mysql.
I'm new - I've played with the configuration a little bit.

Fedora Core 5 included a graphical utility for configuring apache - I haven't seen the equivalent with ubuntu.  Anyone know if this exists?

---

### Post by SeanHodges on 2006-09-13
The best GUI for Apache that i've heard is Webmin ([http://www.webmin.com/](http://www.webmin.com/))

Unfortunately (and surprisingly!) its not in the repositories... Though they have made a deb package, that should be simply a matter of download and double-click to install.

I might try the software myself tomorrow, and if so I will post back with my success.

Heres a screenshot of webmin working with Apache: [http://www.webmin.com/screens/apache.gif](http://www.webmin.com/screens/apache.gif)

---

### Post by atraeyu on 2006-09-13
Wow, webmin actually does quite a bit more than I was looking for.
At the risk of sounding like a total idiot: It's ugly, too.
Thanks for the suggestion though, I'm just hoping for something a little more user friendly.

I really only need something that will help me configure apache2 (and perhaps proftpd) ...

---

### Post by SeanHodges on 2006-09-14
Well I've done a bit of research, and sorry to say there are no worthwhile alternatives available. The only other candidate that I found was a Java tool called Mohawk, but it was unusably flakey in Ubuntu, and looks VERY ugly.

The general concensus is that you should really configure Apache by editing the configuration files. This way you have a better idea of what is set up and more control of the service. It is quite easy to configure, you dont need to search far to get the information you want. This is strongly advised across the board, from Windows, Redhat, OSX, to Ubuntu.

Webmin is probably your best bet if you really want a user interface, I found these instructions for installing it in Ubuntu Dapper:

[http://invaleed.wordpress.com/2006/06/19/howto-install-webmin-ubuntu-dapper-drake-606/](http://invaleed.wordpress.com/2006/06/19/howto-install-webmin-ubuntu-dapper-drake-606/)

You can configure the theme of Webmin (i suppose the default one just works well on most browsers or something, but i agree, it does look ugly!) Here is a really nice looking theme i found:

[http://www.stress-free.co.nz/webmin-theme/](http://www.stress-free.co.nz/webmin-theme/)

It should also allow you to configure ProFTPd, I have seen [this]("http://www.usalug.org/CROUSE/webmin.jpg") screenshot, which indicates this. My guess is that you'll also be able to hide the stuff you dont want, its pretty versatile as it's a web-based interface.

I still havent tried it, so let me know how you get on...

---

