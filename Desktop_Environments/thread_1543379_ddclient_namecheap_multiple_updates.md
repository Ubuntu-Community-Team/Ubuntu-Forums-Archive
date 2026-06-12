---
title: "ddclient namecheap multiple updates"
date: 2010-08-01
forum: Desktop Environments
---

### Post by cantdrive55 on 2010-08-01
I'm trying to update my dynamic ip using ddclient and I have multiple domains I'm trying to update. However when I update, it only actually updates the last entry (host2) in my ddclient.conf file.

I found this thread about it but I cant seem to get it to work?
[http://sourceforge.net/projects/ddclient/forums/forum/399428/topic/2093302](http://sourceforge.net/projects/ddclient/forums/forum/399428/topic/2093302)

I am using version 3.8.0 btw

Below is my current config:
```
protocol=namecheap
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
server=dynamicdns.park-your-domain.com
login=host1.net
password=9800***********************
@,www

protocol=namecheap
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
server=dynamicdns.park-your-domain.com
login=host2
password=a527c**********************
@,www

```

---

### Post by ian_hawdon on 2010-09-02
I'm having the same issues, friendly bump ;)

---

### Post by ian_hawdon on 2010-09-03
I found a fix, I have blogged about it :-)

[http://www.op-ezy.co.uk/~ian/blog/2010/09/03/making-ddclient-work-with-multiple-domains-on-namecheap/](http://www.op-ezy.co.uk/~ian/blog/2010/09/03/making-ddclient-work-with-multiple-domains-on-namecheap/)

You will need to patch the ddclient script (located at /usr/sbin/ddclient) with this:

```
--- ddclient.old	2010-09-03 18:40:15.064904091 +0100
+++ ddclient	2010-09-03 18:40:14.254904011 +0100

@@ -3274,8 +3274,11 @@

my $url;
$url = "http://$config{$h}{'server'}/update";
- $url .= "?host=$h";
- $url .= "&domain=$config{$h}{'login'}";
+ my $domain = $config{$h}{'login'};
+ my $host = $h;
+ $host =~ s/(.*)\.$domain(.*)/$1$2/;
+ $url .= "?host=$host";
+ $url .= "&domain=$domain";
$url .= "&password=$config{$h}{'password'}";
$url .= "&ip=";
$url .= $ip if $ip;
```

and append your domain name to your configuration file (e.g. @.example.com, [www.example.com](www.example.com),) and restart ddclient.

EDIT: Fixed rouge HTML code that occurred when posting to Wordpress!

---

### Post by Myfathersheart on 2011-01-11
I am a huge noob with codes I have literally had Ubuntu for 3 weeks and so far the most I have successfully done in a terminal is sudo apt-get ____  .  So I am trying to set up ddclient now for opendns so I can filter the internet on Ubuntu.

I have two questions.  This may be difficult for me to explain so bear with me. I will try my best.  First, I don't know what I am supposed to do with the code. I am assuming that I should copy it and paste it into a terminal one line at a time.  I am also assuming that there are certain segments that I have to personalize (for example the part that says {'password'} ) but this personalizing part is where I get confuse.  I don't know what parts of the code need to go into the terminal and what parts are just the post's author's instruction (for example if my password is 1234 would i replace the {'password'} part with {'1234'} or lose the brackets and type '1234' or lose the brackets and quotations and just type 1234).  Like I said originally I am just trying to set up ddclient for opendns and [http://ubuntuforums.org/showthread.php?t=1264710](http://ubuntuforums.org/showthread.php?t=1264710) isn't working for me.  I posted why it isn't working for me in the last post of that thread.  

If anyone can help me with this please reply to either thread.

---

