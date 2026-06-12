---
title: "secure login to ubuntuforums.org...?"
date: 2006-08-28
forum: Forum Feedback &amp; Help
---

### Post by yossman on 2006-08-28
there does not appear to be a secure way to log into the ubuntuforums.org site at the moment.  i looked around for a bit on the forums, but i can't seem to find an answer to this..

most web sites these days give you a way to change to 'secure mode', usually a link placed somewhere around the 'username/password' boxes on the page. this changes the connection to use SSL (HTTPS), offering better protection against entities in the same network sphere from potentially sniffing your username and password to the ubuntu forums.

this might seem like a non-issue to some people; i suggest they start by considering how many networks are not using very good security practices to begin with. they don't need any help making it worse, they need sites to lead by example, and use better security practices.

as a simple example, imagine wanting to log into the ubuntuforums.org site from an internet cafe; personally, i'd be out of luck at the moment, since i would not want to log into any site without at least the SSL layer of protection.

thanks for reading, ttys. ;-)


yossman

---

### Post by Pumm4 on 2006-08-28
[SIZE=2]Yes, great thinking **yossman** - you have a point there. ;) Besides [/SIZE][SIZE=2]HTTPS is the secure version of HTTP, the communication protocol of the World Wide Web. It was invented by Netscape Communications Corporation to provide authentication and encrypted communication and is used in electronic commerce. Meaning that s[/SIZE][SIZE=2]ecure HTTP, indicates a web site that is using SSL to encrypt information coming in and going out so that it cannot be intercepted.[/SIZE]

---

### Post by Woei on 2006-08-29
> **yossman said:**
> there does not appear to be a secure way to log into the ubuntuforums.org site at the moment.  i looked around for a bit on the forums, but i can't seem to find an answer to this..

most web sites these days give you a way to change to 'secure mode', usually a link placed somewhere around the 'username/password' boxes on the page. this changes the connection to use SSL (HTTPS), offering better protection against entities in the same network sphere from potentially sniffing your username and password to the ubuntu forums.

this might seem like a non-issue to some people; i suggest they start by considering how many networks are not using very good security practices to begin with. they don't need any help making it worse, they need sites to lead by example, and use better security practices.

as a simple example, imagine wanting to log into the ubuntuforums.org site from an internet cafe; personally, i'd be out of luck at the moment, since i would not want to log into any site without at least the SSL layer of protection.

thanks for reading, ttys. ;-)



Extremely doubtful they'll implement this. The forum operators have enough problems as is judging from the announcement at the top of the mainpage, and enabling SSL will pummel performance. I actually don't know of a single forum where SSL is enabled. You could argue that it should be possible to sign in over https, encrypting your password, and then roam the forums over plain http, but that still won't protect you completely, as the bad guys can hijack the session by stealing your cookie.

If you're really that paranoia, consider running a proxy server on a trusted host where you have shell access, and open a tunnel to that machine. The proxy settings in your browser should point to localhost then. See man ssh, more specifically, the '-L' option.

---

### Post by ubuntu-geek on 2006-08-29
Yeah, our servers are already being taxed pretty hard. We haven't considered this an option and it has never been an issue in almost three years. So, as far as it being implemented probably not.

---

### Post by northern_sky on 2008-07-19
Time to bump this one.

It's so very easy to snoop an login thats sent in cleartext.This enough should warrant SSL for login.
Also, imagine for example a user living a closed country (china etc, wanting to post things that could be considered censorable by that goverment etc.Therefore, https for the whole site, should be the best for integrity of the users.

Regards
Northern

---

### Post by LaRoza on 2008-07-19
> **northern_sky said:**
> Time to bump this one.

It's so very easy to snoop an login thats sent in cleartext.This enough should warrant SSL for login.
Also, imagine for example a user living a closed country (china etc, wanting to post things that could be considered censorable by that goverment etc.Therefore, https for the whole site, should be the best for integrity of the users.

Regards
Northern
This thread is old and there was another one recently where the proposal was rehashed from every angle.

The only instances of accounts being used by others (2, in total) were physically used on the computer.

---

### Post by matthew on 2008-07-19
Yeah, our servers are already being taxed pretty hard, harder than they were the last time this thread was replied to by an admin. We have considered this as an option, only because people brought it up, but it has never been an issue in almost five years, and we really don't need to push our poor servers any further as they are already overworked. So, as far as it being implemented probably not.

---

