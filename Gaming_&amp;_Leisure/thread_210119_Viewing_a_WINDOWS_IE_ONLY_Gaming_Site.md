---
title: "Viewing a WINDOWS IE ONLY Gaming Site"
date: 2006-07-06
forum: Gaming &amp; Leisure
---

### Post by furryfren on 2006-07-06
I'm pissed with how this site: [http://www.silkroadonline.net](http://www.silkroadonline.net) only allows a combination of WINDOWS **AND** INTERNET EXPLORER.

Does anyone know how to overcome this? I'm using Greasemonkey's IE Emulation script to emulate IE but how does one emulate Windows?

---

### Post by Mr_HeNtAi on 2006-07-06
I've never seen those requirements before, I guess the site isn't worth viewing.

---

### Post by JoshHendo on 2006-07-06
[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

This will install IE using Wine. It should work pretty well, as long as you already have Wine installed.

---

### Post by arizonagroovejet on 2006-07-06
Try installing the using the User Agent Switcher Extension and selecting the IE/Windows setting.
[https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)

Once you're in find their contact section and explain to them the concept of browsers other than Internet Explorer.

The site looks at the User Agent string of your browser to determine what browser you are running and hence whether or not your browser is capable of viewing the site. An utterly flawed method of browser detection given the UA string can be altered by the user to say anything at all.

---

### Post by RawMustard on 2006-07-06
Interesting.  With NoScript installed I can surf that site pretty well.  Maybe I'm missing stuff, but then I don't support sites that are Windows/IE only, infact I send them abusive emails telling what a buch of losers thay are :)

---

### Post by arizonagroovejet on 2006-07-06
[QUOTE=RawMustard]Interesting.  With NoScript installed I can surf that site pretty well.  [/QUOTE]

It's because the site does UA string detection using Javascript. So if you browse to the site with Javascript disabled the Javascript which locks out any browser it doen't think is IE/Win simply doesn't get run.

---

### Post by B0rsuk on 2006-07-06
Attention everyone: after you get the site fooled, please mail the webmaster and tell him his site sucks, because you had to bypass his  silly browser detection.

---

### Post by vem0m on 2006-07-06
heh b4 i switched to linux i loaded it thu firefox in windows :P

---

### Post by DirtDawg on 2006-07-06
A little while ago [I was having trouble]("http://ubuntuforums.org/showthread.php?t=201647") because Opera browser identifies itself as Internet Explorer, perportedly for just such occaions.

Really though, it sounds like NoScript is a good workaround.

---

### Post by FredB on 2006-07-06
Another great idea is too tell this webmaster that the first browser war is closed now. We are no more in 1997-1998.

---

### Post by WildTangent on 2006-07-06
I just sent an email to the webmaster (according to domaintools.com whois search) [email]sonkilmer@joymax.com[/email]

> 
Subject: Your website is not friendly

Your website, silkroadonline.net does not allow anyone to enter unless they use Windows and Internet Explorer. Quite unfortunate for those of use using Mozilla Firefox ([www.getfirefox.com)](www.getfirefox.com)), or god forbid, running Linux rather than an evil corporations product.

Not only this, but your website is heavily reliant on javascript, which is too bad for the security-conscience people who do not trust javascript and disable it. Very bad webdesign quite frankly.

Oh, by the way, I was able to easily get past your user-agent checker and view the website with the browser of my choice, on the operating system of my choice. Maybe you should rethink your ideas.

-An Upset Linux and Firefox User


-Wild

---

### Post by Lord Illidan on 2006-07-06
That e-mail will be promptly ignored and put down to belonging to a plain and simple linux zealot. Why can't you have put it across more politely? Referring to Windows as an "evil corporation's product" is the first nail in the coffin.

I would've just informed him that he should have made his site compatible for linux and firefox, and that his site's "protection" could be hijacked easily.

---

