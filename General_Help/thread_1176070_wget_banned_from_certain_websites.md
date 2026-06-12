---
title: "wget banned from certain websites?"
date: 2009-06-01
forum: General Help
---

### Post by Aped on 2009-06-01
I've been using wget to snag blogs, webcomics, music and just generally updates so that I can read them later (my school's wireless is pretty shoddy); noticed that on several blog places [hypem.com, most notably] I get 403 Forbiddens a lot, and when I try to recursively get posts I end up with a file called robots.txt that says something like: 

```
# See http://www.robotstxt.org/wc/norobots.html for documentation on how to use the robots.txt file
#
# To ban all spiders from the entire site uncomment the next two lines:
# User-Agent: *
# Disallow: /
```
Though this varies from site to site. 

Currently using the command like so, as you can see: 
```
wget -rnd -l2 --random-wait -U "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.10) Gecko/2009042523 Ubuntu/9.04 (jaunty) Firefox/3.0.10" www.hypem.com 
```

I realize that what I'm asking for is technically bypassing something and is not therefore 100% whitehat, but it's completely legit (in the --random-wait bit of wget's MAN pages it even says that the practice of banning wget is dumb). 

I've tried spoofing a referrer too but may be doing it wrong... 

Anyway, anyone with experience in this know a workaround?

---

### Post by schwim on 2009-06-01
It's very common to block offline browsers, usually in an effort to save bandwidth.

Your resolution is to change your user-agent string that wget uses so the server doesn't know it's a scraper.

---

### Post by Aped on 2009-06-01
> **schwim said:**
> Your resolution is to change your user-agent string that wget uses so the server doesn't know it's a scraper.

I thought I'd done that with the -U "Mozilla bla bla" bit? No?

---

### Post by schwim on 2009-06-02
Hi there Aped,

Very sorry.  I responded while tired and definitely didn't steer you in the right direction.

The robots.txt you posted of course wouldn't ban you since the user agent info is commented out.

Often, you don't get grabbed by the robots.txt, but instead by a honeypot.

On my sites, I place a hidden image at the top of the page.  For scrapers that hit any page on my site, they see that link first.  Clicking it, they immediately get added to the list of disallowed ips, via my .htaccess.

This may be what's happening to you if you're spoofing your u/a string and still getting blocked.  The only way around this is to find the offending link and adding it to your blacklist for the scraper.

You may also want to read [this link](http://linuxshellaccount.blogspot.com/2009/01/using-wgets-user-agent-option-safely-on.html) as it's very informative on the use of scrapers and the spoofing of the U/A string.

thanks,
json

---

### Post by benj1 on 2009-06-02
just be aware that mozilla doesn't like their user agent string being used on anything without their permission, so you could get sued (unlikely i know). i tend to find a blank user agent string works ie --user-agent="",
if you read the man page as it has other tricks, i think theres a --random-wait flag because some sites flag up multiple requests in quick succession.

---

### Post by schwim on 2009-06-02
> **benj1 said:**
> just be aware that mozilla doesn't like their user agent string being used on anything without their permission.....

That's why I posted the link :)

---

### Post by Aped on 2009-06-02
> **benj1 said:**
> just be aware that mozilla doesn't like their user agent string being used on anything without their permission, so you could get sued (unlikely i know). i tend to find a blank user agent string works ie --user-agent="",
if you read the man page as it has other tricks, i think theres a --random-wait flag because some sites flag up multiple requests in quick succession.

Woof, wouldn't want to offend the Mozilla corp. and I definitely wouldn't want to get sued; will discontinue that UA string ;)

I'll check that link out, thanks for the responses guys. 

For the record, I've been using random timing for a while now, and that doesn't seem to be doing the trick either; appending --erobots=off did SOMETHING but it's still not working; keep fiddling is the name of the game, I guess.

---

