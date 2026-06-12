---
title: "WordPress Database Installation Problem"
date: 2006-09-08
forum: Desktop Environments
---

### Post by khaledaboualfa on 2006-09-08
Hi there, I've followed this particular thread:
[http://www.ubuntuforums.org/showthread.php?t=229499](http://www.ubuntuforums.org/showthread.php?t=229499)

I do have apache and mysql and php running according to this particular thread:
[http://www.ubuntuforums.org/showthread.php?t=218429](http://www.ubuntuforums.org/showthread.php?t=218429)

Everything goes smoothly except for some reason when I go to localhost/blog, wordpress gives me the following message:

[B]Error establishing a database connection

This either means that the username and password information in your wp-config.php file is incorrect or we can't contact the database server at localhost. This could mean your host's database server is down.[/B]

It seems things aren't going right with the passwords and the connections to the database? That error only comes up when the information between the two is different. Any ideas?

Another problem I am having is that I can't seem to access myphpadmin for some reason. It asks me for a username and password (I installed this from the repositories). Root and no password doesn't work.

---

### Post by az on 2006-09-08
Look here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Maybe you improperly set your mysql passwords?

Also,

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

Try that.

---

### Post by khaledaboualfa on 2006-09-08
THanks Azz, I actually sorted it out, but for some reason by python xamp control panel doesn't seem to want to install itself in the main menu for some reason but that's a different topic for a different time.

I'm talking specifically from this howto:
[http://www.ubuntuforums.org/showthread.php?t=223410](http://www.ubuntuforums.org/showthread.php?t=223410)

---

