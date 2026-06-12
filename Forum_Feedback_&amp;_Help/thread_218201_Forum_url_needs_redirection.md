---
title: "Forum url needs redirection"
date: 2006-07-18
forum: Forum Feedback &amp; Help
---

### Post by Peter Mount on 2006-07-18
Hi

I know the actual url of the forum is:

[http://www.ubuntuforums.org](http://www.ubuntuforums.org)

Sometimes I accidently go to:

[http://www.ubuntuforum.org](http://www.ubuntuforum.org) (without the "s")

It looks the same forum but I can't login at that url. It's only after I realise my mistake that I can log in. Maybe the site at the "wrong url" needs a javascript redirection like:

function forumRedirect(){
	var urlStr1 = window.location;
	urlStr2 = urlStr1.toString();
	if(urlStr2.substring(0) == "http://www.ubuntuforum.org/"){
	  window.location="http://www.ubuntuforums.org/";
        }
}

Of course it would be simpler to do the redirection in cPanel.

Have fun

---

### Post by Biltong (Dee) on 2006-07-18
Or you could just Bookmark it. Problem solved :-)

---

### Post by Peter Mount on 2006-07-18
> **Biltong (Dee) said:**
> Or you could just Bookmark it. Problem solved :-)

You're right, of course.

I have bookmarked it but I have this awful habit of choosing the url from the list in the address bar in Firefox. Dare I say my "ID10T error"? :rolleyes: 

Seriously, this issue could explain the odd problem people may have with logging in. If the alternate url is still there and it's got a version of this forum then it could be causing some degree of confusion. People may have that alternate url bookmarked for this forum. A redirect would solve this problem. 

Just my suggestion.

---

### Post by GStubbs43 on 2006-07-18
Correct me if I am wrong, but I don't even think Ubuntu owns ubuntuforums.org, the Whois lookup lists two different registrants, ubuntuforum.org's being mostly private. You would have to talk with the owner of ubuntuforum.org, not here. The owner of ubutnuforum.org could also be trying to get personal info. I don't know, it could of course just be an error in the script for the site and it could very well be owned by Ubuntu. I really have no idea, but the best thing you could do is to click on the good ol' bookmark on your browser.;)

---

### Post by Peter Mount on 2006-07-18
Thanks GStubbs43 for explaining that to me.

It looks really peculiar that [http://www.ubuntuforum.org](http://www.ubuntuforum.org) would have the exact same design as [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)

I'll just use my bookmark from now on

Have fun

---

### Post by henriquemaia on 2006-07-18
> **GStubbs43 said:**
> Correct me if I am wrong, but I don't even think Ubuntu owns ubuntuforums.org, the Whois lookup lists two different registrants, ubuntuforum.org's being mostly private. You would have to talk with the owner of ubuntuforum.org, not here. The owner of ubutnuforum.org could also be trying to get personal info. I don't know, it could of course just be an error in the script for the site and it could very well be owned by Ubuntu. I really have no idea, but the best thing you could do is to click on the good ol' bookmark on your browser.;)

Only staff can answer this. And I think Peter Mount made a good point.

---

### Post by ubuntu-geek on 2006-07-20
ubuntuforums.org = owned by me
ubuntuforum.org = owned by canonical/ubuntu

Canonical redirects ubuntuforum.org to our site, ubuntuforums.org..

---

### Post by Peter Mount on 2006-07-20
> **ubuntu-geek said:**
> ubuntuforums.org = owned by me
ubuntuforum.org = owned by canonical/ubuntu

Canonical redirects ubuntuforum.org to our site, ubuntuforums.org..

Hi ubuntu-geek

If they've put a redirection in it isn't working. I just went to [http://www.ubuntuforum.org](http://www.ubuntuforum.org) and I didn't get redirected to [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)

I even typed in my login details at [http://www.ubuntuforum.org/](http://www.ubuntuforum.org/) and even though I got a "thank you" screen for logging in I wasn't logged in. I tried to post a comment in a forum and it said I wasn't logged in.

This is in Mozilla Firefox 1.5.0.4 on Windows 2000

I think you need to have a word with Canonical about this

Have fun

---

### Post by ubuntu-geek on 2006-07-20
Should redirect ok now.. :) mod_rewrite for the win!

---

### Post by Peter Mount on 2006-07-21
Hi

I just tried it in Firefox on Dapper and the problem is still there.

Otherwise the forum seems great.

Have a good day

---

### Post by ubuntu-geek on 2006-07-21
Ahh yeah.. suppose I should make it work with the www appended.. :)

---

