---
title: "Problem with Apache's mod_rewrite..."
date: 2005-12-23
forum: General Help
---

### Post by XtremeGamer99 on 2005-12-23
I posted this problem a couple of months ago, and I never solved it. I thought I might post it again, see if I have better luck this time. >_>

My mod_rewrite doesn't seem to be work fully. It's wierd, because some things work and som things don't. Here's my site if you need to physically experiment further: [http://xgamer.ath.cx](http://xgamer.ath.cx). Please note that the links aren't "mod_rewrite ready", meaning the links aren't making use of it. To test the module, you need to manually enter whatever you need to enter into the address bar. Also note that my site is still being tested, which is the reason why everything has a "TESTING!!!11!1" option or name on it. >_> 

Anyway, my .htaccess file looks like this:

```
RewriteEngine On

RewriteRule ^cds/?$ cds.php [L]
RewriteRule ^cds/([0-9]+)/?$ cds.php?cd=$1 [L]
RewriteRule ^cds/([0-9]+)/song/([0-9]+)/?$ cds.php?cd=$1&song=$2 [L]
RewriteRule ^cds/artist/([0-9]+)/?$ cds.php?artist=$1 [L]

RewriteRule ^news/?$ news.php [L]
RewriteRule ^news/([0-9]+)/?$ news.php?id=$1 [L]

RewriteRule ^polls/?$ past_polls.php [L]
RewriteRule ^polls/([0-9]+)/?$ results.php?id=$1 [L]

RewriteRule ^scripts/?$ scripts.php [L]
```

Now, notice how I said it's not working *fully*. For example, if I type in /cds/, it displays what /cds.php would. However, the rest of the code under that doesn't work, and just displays what /cds.php would. Ex: /cds/9 is supposed to display what cds.php?cd=9 would, but only displays /cds.php. The same is with the *news* redirects. /news/ works, but /news/2 doesn't.

To feul my confusion, both codes for the polls work. /polls/ does display /past_polls.php, and /polls/3 does display /results.php?id=3.

Also, the ever so popular test-to-see-if-it-works code, where it redirects / to [www.google.com](www.google.com), works. (I can't remember the actual code, though).

I just don't get it. I've checked everything. I know that the module is loaded, and I know that it is working (to some extent). What's wrong? Is it a bug? I noticed that with the two poll codes, the files that are being 'rewritten' are different from what is being called (ie, /past_polls.php is different than /polls/). I don't kow if it's something in my code, which I don't think is, since it worked back when I ran Windows as a development server. I just don't know what it is.

Any help will be *greatly* appreciated. Thanks.

---

### Post by XtremeGamer99 on 2005-12-23
Anyone?

---

### Post by hpn on 2006-01-02
yep, strange thing. Even with rewrite module installed and *loaded*, it ain't working :?

[http://ubuntuforums.org/showthread.php?t=73246&page=2](http://ubuntuforums.org/showthread.php?t=73246&page=2)

---

