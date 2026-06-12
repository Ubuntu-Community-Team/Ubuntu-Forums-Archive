---
title: "UbuntuForums site vs useragent -"
date: 2008-10-06
forum: Forum Feedback &amp; Help
---

### Post by nowshining on 2008-10-06
this is odd, i went thru limiting what my browser sent as headers and changed the useragent, well well yes I know java crashes the browser if one choose to  change the useragent but I found ways to get around that while still having a useragent i like - either minimal or made to look like FF is on windows..anywhooo

A certain useragent sequence makes it where I am unavailable to get a page up on the UF, other sites work fine...

Mozilla Gecko/00000000

or basically that minus all the zeros - they are suppose to be a date that I zeroed out due to a bank site not working without numbers there...

Moving back on Topic what it does is my computers when using a useragent like that - sends a syn or whatever package to get a connection started - nothing - it tries and tries and all i see in the status bar is transferring from ubuntuforums.com, etc.. :/


Again i think is is a bug on ur end due to other sites work just fine, I also tried 
Mozilla Gecko\/00000000 and such and it would only load 3/4 of the page or half of it...

How was I able to get on the UF and type this up, i changed Mozilla to Firefox - a bit slow to start but connects fine, so why does changing Mozilla to Firefox make such a huge Diff.?? Again other sites work just fine when I had my UA at 
Mozilla Gecko/00000000.

So for now My UA looks like this: 
Firefox Gecko/00000000

:)

Alas yes..

[http://www.lagado.com/proxy-test](http://www.lagado.com/proxy-test)

I got it down to something similiar to this on the headers sent..Again Other sites loading just fine the way I had it and the way I have it even with the Mozilla part used..

Host	[www.lagado.com](www.lagado.com)
User-Agent	Firefox Gecko/00000000
Accept-Charset	utf-8,*
Connection	close
Referer	[http://www.lagado.com/](http://www.lagado.com/)


edit: Update

On long threads it freezes without something in the following:

network.http.accept-encoding
network.http.accept.default


However if I put a space in there ie: equiv of a blank the site continues to operate smoothly, again with leaving them blank other sites worked fine...It's just the UF I know of having problems, google worked fine, ubuntu.org kind of worked fine altho I think it was slow too, yahoo worked fine, live worked fine, etc..

---

