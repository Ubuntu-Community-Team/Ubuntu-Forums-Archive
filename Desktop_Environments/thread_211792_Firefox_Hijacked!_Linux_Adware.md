---
title: "Firefox Hijacked??! Linux Adware??"
date: 2006-07-08
forum: Desktop Environments
---

### Post by tikihead on 2006-07-08
I've got a fairly clean install of dapper (several days old). It seems to me that I've picked up adware or a browser hijack in my firefox! When trying to resolve a dead link or url, instead of giving me the standard 404 or whatever - it starts looking at seeq.com. Arrgh! One of the reasons I wanted to switch is the lack of these issues and now they show up again! Any help is appreciated.

Tiki

---

### Post by Eversmann on 2006-07-08
Don't worry because it can be your router. Trust me, i have a 3com wifi, and sometimes it replies me with a weird address if i type an url wrong, more or less.

But, a hijack isn't attached to an operating system specific, if there's a security hole in firefox and they discovered it, someone can attach codes to run with it. Very very weird in firefox btw.

---

### Post by tikihead on 2006-07-08
Doesn't happen on any other pcs behind the router. :(

---

### Post by fragos on 2006-07-08
This is not uncommon but it's not Firefox.  It's Service providors who have hijacked the unused domains.  IMHO registering domains only to resell at a higher price to someone in actual need of the domain shouldn't be allowed.

---

### Post by tikihead on 2006-07-08
Does it with any random url such as entering in 555555555 in the address bar. This sucks, darn you seeq.com darn you to heck! But still all other machines behind the router are fine.

Tiki

---

### Post by DirtDawg on 2006-07-09
This problem doesn't seem common. There's only [one posting]("http://forums.mozillazine.org/viewtopic.php?t=317172&highlight=seeq+com") in the Mozilla forums about this and it's neither new nor useful.

To me, this sounds like a virus. That you managed to get one on Linux is impressive.
Don't get frustrated yet as it may be a minor problem.

In the meantime there's a virus scanner available in the repositories. You could try to run that just to see what happens:
[http://packages.ubuntulinux.org/dapper/x11/aegis-virus-scanner](http://packages.ubuntulinux.org/dapper/x11/aegis-virus-scanner)

---

### Post by aysiu on 2006-07-09
Can you post a link to one of these dead URLs? If we're all getting seeq.com, maybe that's just what the URL is redirecting to instead of it being adware or a virus.

99% of the time when people think they've gotten spyware, adware, or a virus in Ubuntu, it turns out to be something else.

---

### Post by tikihead on 2006-07-09
Will post a screencap or something when I get a chance. I'm at work for another 6 hrs, and sleeping hopefully for 8 after. Like I said previously, it happens anytime I enter in a non valid or non existing url like [http://55555555]("http://55555555").

Cheers,
Tik

---

### Post by srunni on 2006-07-09
Who's your ISP?

---

### Post by RawMustard on 2006-07-09
Try deleting your profile and creating a new one, and see if it still does it.  It's in .mozilla folder in your home directory, you'll need to show hidden files to see it.

Make sure firefox is not running, make a backup of .mozilla folder, then delete the .mozilla folder.  When you start firefox again, it will recreate it and make a new profile.  See if you still have the problem?

---

### Post by handy on 2006-07-09
> **fragos said:**
> This is not uncommon but it's not Firefox.  It's Service providors who have hijacked the unused domains.  IMHO registering domains only to resell at a higher price to someone in actual need of the domain shouldn't be allowed.

Yep, it is very common, & I agree: 

It's just more marketroid manipulation of the population, for personal monetary accumulation! 

Should be first in line for eradication!

---

### Post by tikihead on 2006-07-09
ISP is Mediacom. They give a cable modem/router/wireless combo device, which I'm sure is what Ubuntu is pulling DNS from. Question is why are none of the other pc's poisoned like Ubuntu is? Digg users are also suggesting other browsers on the Ubuntu machine eg. Opera and Konquerer. Also suggested are bypassing the router's DNS and putting in my own. Well at least we are narrowing it down that it's not a horrible new trend of scary linux ad/spy ware. Phew :|. Thanks for the help for now. Will post when I get a chance to work on it more.

Tik

---

### Post by ftravers on 2006-08-08
Okay, I'm having the same problem, albeit not on ubuntu but on windows XP with firefox.

If I put in the URL:

[http://spicevan.org/](http://spicevan.org/)

it gets redirected to:

[http://spicevan.seeq.com/seeq/index.jsp?portal_id=1&domain=spicevan.org&keyword=&referrer=](http://spicevan.seeq.com/seeq/index.jsp?portal_id=1&domain=spicevan.org&keyword=&referrer=)

if I put in the url:

[http://spicevan.org/index.php/](http://spicevan.org/index.php/)

it works fine.

If I put in spicevan.com

it also works fine.

Here is my apache httpd.conf ( running fedora core 4 ):

<VirtualHost *:80>
    ServerAdmin [email]fenton.travers@gmail.com[/email]1
    DocumentRoot /home/web/stellentwiki
    ServerName [www.spicevan.com](www.spicevan.com)
    ServerAlias *.spicevan.com spicevan.com
    ErrorLog logs/spicevan.com-error_log
    CustomLog logs/spicevan.com-access_log common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin [email]fenton.travers@gmail.com[/email]1
    DocumentRoot /home/web/stellentwiki
    ServerName [www.spicevan.org](www.spicevan.org)
    ServerAlias *.spicevan.org spicevan.org
    ErrorLog logs/spicevan.org-error_log
    CustomLog logs/spicevan.org-access_log common
    
    Alias /mw "/home/web/spicevan"
    Alias /naomi "/home2/naomiWiki/mediawiki-1.6.7"
    Alias /bhaktiom "/home2/houseWiki/mediawiki-1.6.7"
</VirtualHost>

I tried the exact same test in IE and it worked okay.  I think it must be some files that are cached by mozilla.  I'll try deleting some of the files as suggested in a prior post and report back. 

Question is, why did this happen in the first place?  This should never happen right?

Thanks.

ft

---

