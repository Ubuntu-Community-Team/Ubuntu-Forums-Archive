---
title: "web client programming"
date: 2009-01-28
forum: General Help
---

### Post by wanchai on 2009-01-28
Sometime ago I wrote a Perl script that uses LWP in order to log on to my company's Outlook Web Access (OWA), download the emails and feed them into procmail. It worked fine and I was very happy with it. Now the company changed their system and we need to go through a Cisco SSL VPN Web whatever layer in order to get to OWA. The problem is that this extra layer checks whether the web client supports Javascript. Perl LWP does not. The OWA part doesn't need it, but I can't get through that extra logon step without supporting Javascript or pretending to do so.

Does anyone know about some Javascript supporting alternatives to Perl LWP? Basically I need a web browser with Javascript that has no GUI but that I can control via Perl or Python or something else.

---

### Post by Sorivenul on 2009-01-28
This may be a difficult situation to tackle. 

Most text-mode browsers have little to no JavaScript support. To the best of my knowledge, elinks and links2 are the only ones, and at best support is only partial. There are reports that elinks has the better JavaScript support of the two. It should be scriptable with Perl and a few other languages like Lua and Guile.

elinks should be available in the repositories.

The main website is here:
[http://elinks.or.cz/](http://elinks.or.cz/)

The official documentation is here:
[http://elinks.or.cz/documentation/index.html](http://elinks.or.cz/documentation/index.html)

---

### Post by mb_webguy on 2009-01-28
You might be able to spoof the user agent, but I don't know how you'd go about it since it's been years since I used Perl, and I have no experience with LWP.

---

### Post by wanchai on 2009-01-28
Thanks Sorivenul, these apps are interesting. I tried both elinks and links2 in the current Jaunty alpha and on my older Hardy machine. Hardy and Intrepid have elinks 0.11.3. This version doesn't even render the page. In the middle of the source it suddenly starts garbling everything and it looks as if I'm reading a binary file in vi. Jaunty has elinks 0.12pre2 and it loads the page properly. However, neither elinks nor links2 work properly with this particular page. After clicking the logon button, they download a very short html with only one script line that says document.location.replace plus the url of the logon page where I came from. Links2 has an option -enable-javascript, but switching this on doesn't seem to make a difference.

mb_webguy, do you mean something like $browser->agent('Mozilla/5.0')
That doesn't help, I need to spoof the java actions that are going on behind the scenes.

Currently I am using Firefox extensions Tamper Data and Firebug to check what's going on with this site...

---

