---
title: "Apache2 will not parse PHP5"
date: 2008-12-16
forum: General Help
---

### Post by thammonddoel on 2008-12-16
This seems like as a good a place as any to whimper for a little help. I did a fresh install of 8.10, set a static IP, added "ServerName localhost" into apache2.conf to quiet the FQDN squawks, then started LAMP installation.

First installed Apache2. "It Works" comes up no problem.
Next, installed PHP5 (including cgi) and modified the DirectoryIndex in apache2/mods-available/dir.conf to put index.php first (this was after trying to place a DirectoryIndex entry into apache.conf and believing from other posts I've seen it is overridden by dir.conf).

Restarted Apache.

I created a file called testphp.php with the entry < ?php phpinfo(); ?> as the only line in the file.

Used both the FireFox and Konqueror browsers (after cleaning the cache, history and EVERYTHING), and Apache2 still loads the file instead of parsing the php. This is all I see:

< ?php phpinfo(); ?>

Help getting Apache2 to actually parse PHP would be most gratefully and humbly (which is hard for me) appreciated.

BTW - PHP is running.

---

### Post by lykwydchykyn on 2008-12-16
Sounds like you need to install the libapache2-mod-php module.  Try that and see if it fixes your issue.

```

sudo apt-get install libapache2-mod-php

```

---

### Post by doobiest on 2008-12-16
You may also need to symlink php5.load and php5.conf from /etc/apache2/mods-available to /etc/apache2/mod-enabled

---

### Post by thammonddoel on 2008-12-16
Gives me this:

einstein@einstein-ubuntu:~$ sudo apt-get install libapache2-mod-php
[sudo] password for einstein: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libapache2-mod-php
einstein@einstein-ubuntu:~$ 

Is that the right package?

---

### Post by lykwydchykyn on 2008-12-16
It's libapache2-mod-php5, my bad.

---

### Post by thammonddoel on 2008-12-16
The links look like they're there...

einstein@einstein-ubuntu://etc/apache2/mods-enabled$ ls
alias.conf            autoindex.conf  include.load      setenvif.conf
alias.load            autoindex.load  mime.conf         setenvif.load
auth_basic.load       cgi.load        mime.load         ssl.conf
authn_file.load       deflate.conf    negotiation.conf  ssl.load
authz_default.load    deflate.load    negotiation.load  status.conf
authz_groupfile.load  dir.conf        php5.conf         status.load
authz_host.load       dir.load        php5.load         suexec.load
authz_user.load       env.load        rewrite.load
einstein@einstein-ubuntu://etc/apache2/mods-enabled$

---

### Post by doobiest on 2008-12-16
its libapache2-mod-php5

you can always do a more generic search in aptitude or synaptic if you're unsure of the exact package name

---

### Post by thammonddoel on 2008-12-16
Already the newest version...

---

### Post by doobiest on 2008-12-16
> **doobiest said:**
> You may also need to symlink php5.load and php5.conf from /etc/apache2/mods-available to /etc/apache2/mods-enabled

OK did you check my suggestoin to see if php5.load and .conf exist in /etc/apache2/mods-enabled?

That is required.

---

### Post by thammonddoel on 2008-12-16
Yep.  They're there.
einstein@einstein-ubuntu://etc/apache2/mods-enabled$ ls
alias.conf            autoindex.conf  include.load      setenvif.conf
alias.load            autoindex.load  mime.conf         setenvif.load
auth_basic.load       cgi.load        mime.load         ssl.conf
authn_file.load       deflate.conf    negotiation.conf  ssl.load
authz_default.load    deflate.load    negotiation.load  status.conf
authz_groupfile.load  dir.conf        php5.conf         status.load
authz_host.load       dir.load        php5.load         suexec.load
authz_user.load       env.load        rewrite.load
einstein@einstein-ubuntu://etc/apache2/mods-enabled$

Contents of the files:
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

Interesting, should that be php5 isntead of 3, and if so, where dod the 3 come from?

---

### Post by doobiest on 2008-12-16
have you restarted apache since you added it under mods-enabled? or was it already there.

also do this from the command line and the output should indicate if php is loading

apache2ctl fullstatus


even do this apache2ctl fullstatus|grep -i php

---

### Post by thammonddoel on 2008-12-16
Here's the output:
Apache Server Status for localhost

Server Version: Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch
    mod_ssl/2.2.9 OpenSSL/0.9.8g
Server Built: Sep 19 2008 13:43:21

&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;

Current Time: Tuesday, 16-Dec-2008 12:16:04 PST
Restart Time: Sunday, 14-Dec-2008 09:00:43 PST
Parent Server Generation: 0
Server uptime: 2 days 3 hours 15 minutes 20 seconds
1 requests currently being processed, 5 idle workers

_W____..........................................................
................................................................
................................................................
................................................................

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current process

PID Key:

   5076 in state: _ ,   5077 in state: W ,   5080 in state: _
   5082 in state: _ ,   5084 in state: _ ,   27810 in state: _


&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;
To obtain a full report with current status information you need to use the
ExtendedStatus On directive.
&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;
SSL/TLS Session Cache Status:
cache type: SHMCB, shared memory: 512000 bytes, current sessions: 0
sub-caches: 32, indexes per sub-cache: 133
index usage: 0%, cache usage: 0%
total sessions stored since starting: 0
total sessions expired since starting: 0
total (pre-expiry) sessions scrolled out of the cache: 0
total retrieves since starting: 0 hit, 0 miss
total removes since starting: 0 hit, 0 miss
&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;

Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch mod_ssl/2.2.9
OpenSSL/0.9.8g Server at localhost Port 80


and for the grep:

einstein@einstein-ubuntu://etc/apache2/mods-enabled$ apache2ctl fullstatus|grep -i php
Server Version: Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch
Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch mod_ssl/2.2.9
einstein@einstein-ubuntu://etc/apache2/mods-enabled$

---

### Post by doobiest on 2008-12-16
OK so it's definately loading the php module.

So you're saying when you browse to your webpage, the php file doesnt parse it just displays the raw data of that file?

and you are browsing in the sense of [http://localhost/test.php](http://localhost/test.php)  or whatever the file is?

Man, i dunno, I've tried nothing and I'm fresh out of ideas.

What if you even make a php file calles hello.php in /var/www/...

and put this in the file.

<? echo "hello"; ?>

What displays in your browser.

---

### Post by doobiest on 2008-12-16
Also, reading your first post, I'm not sure why you had to modify dir.conf that's not required, you might want to revert all of those changes.

Really you shouldnt have to modify anything in mods-available. just make sure they're symlinked to enabled

And regarding the browsing comment I wanted to doublecheck that you are trying to load this file through apache, not just in a browser through your filesystem.   The equivalent of clicking, file > open in firefox and choosing the local path of the php file vs. the http path.

---

### Post by thammonddoel on 2008-12-16
Well - that will teach me for copying and pasting something so simple.  The line in my test file was < ?php phpinfo(); ?> was copied from a posting.

Know what's wrong?  The space after the "<".  I removed that and PHP works just fine.

Thanks y'all for the help.

---

### Post by doobiest on 2008-12-16
haha that's kind of wild. enjoy.

---

