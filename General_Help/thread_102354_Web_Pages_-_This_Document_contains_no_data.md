---
title: "Web Pages - This Document contains no data"
date: 2005-12-11
forum: General Help
---

### Post by badboyz107 on 2005-12-11
Hey all....well I have now put Ubuntu on TWO systems now and so far have been very happy now that I know how to iron out most problems on my own.  One small problem I have noted on my wife's computer, and so has she (she wants windowz back) is this::

Many times when you try to open a website (it seems random) you get the error message

"this document contains no data"

Hit refresh and you might get it 15 more times or you might get right in.  Also I have noticed that when you use google for a search it will not fill out the page completely only showing like 2 entries then a blank page...

Any ideas, thoughts, comments, help???

---

### Post by badboyz107 on 2005-12-13
Well it seems that no one has any suggestions....here is a newly discovered wrinkle...

it also seems to be effecting the ability to lookup smtp and pop3 addresses in thunderbird?

---

### Post by jvictor on 2005-12-13
1) Chk if u have disabled IPV6 system wide
2) Chk if u have disabled ipv6 for firefox.
3) What is the nameserver in ur resolv.conf ? ( I use the ISPs nameserver, ur ADSL router can misbehave sometimes :-) )

---

### Post by bb002 on 2005-12-13
I tend to get this error too but for me the entire page does load. Then after the pages finishes loading i get the "Document contains no data error".

How do I check to see if ipv6 is disabled system wide? I know i did it in firefox.

---

### Post by kaamos on 2005-12-13
Try this: [http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6](http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6)

Hope it works!

---

### Post by badboyz107 on 2006-01-06
Okay folks I think I have narrowed this down somewhat but still dont know how to fix the problem...disabling IP6 didnt do anything at all

I have tried Ubuntu or other Linux varients on this same computer and others around the house either live or full install and have the same problem at all the computers.....

The only thing that has changed in my network is my router its a Linksys RT31P2-NA

Where should I go now or what should I do now??  I'm going to attach screenshots of all the stuff I could think of to assist!

---

### Post by badboyz107 on 2006-01-06
5 more

---

### Post by badboyz107 on 2006-01-06
Anything else I can post, information or images that might give someone (ANYONE!!) the information they need just let me know!

I'm getting desperate

---

### Post by bjourne on 2006-01-06
I think it is like this: Firefox starts downloading a html page, but gets disconnected for some reason and therefore displays the "Document contains no data" alert. Something is probably wrong with your network, do you have other computers connected to the router? If you haven't already, check the cabling (there might be a glitch) and or try using the old router instead (since you changed it).

---

### Post by badboyz107 on 2006-01-06
Everything else seems to work just fine on the network, Windowz, Desktop BSD, PC BSD, even a Mac, I cant switch out the router cause I went to voIP and this is the router that I got from the cable company that has fone ports

Checked the cabling also and it seems to be fine, espcially since you can plug one of the aforementioned OS's into that same cable and it screams...

GRRR!  I love Ubuntu but what now?

---

### Post by dcstar on 2006-01-06
[QUOTE=badboyz107]Everything else seems to work just fine on the network, Windowz, Desktop BSD, PC BSD, even a Mac, I cant switch out the router cause I went to voIP and this is the router that I got from the cable company that has fone ports

Checked the cabling also and it seems to be fine, especially since you can plug one of the aforementioned OS's into that same cable and it screams...

GRRR!  I love Ubuntu but what now?[/QUOTE]
You may need to check that Ubuntu is setting up your network card correctly.

If things like flow control/duplex aren't matching what the LAN cable plugs into, you can get issues like this, it may be that the Ubuntu driver for your LAN card isn't as good as the other OSs.

I don't know exactly where you'd set these things for your network interface, but if you do a search you might find something to change these things.

---

### Post by msvr on 2006-01-07
Few months back i had Mandriva LE2005 on my box and i used to have the same error on specific webpages.
Since i changed my os to Breezy, i have no problems.

Any way** some body suggested thi**s,:
 "browser.xul.error_pages.enabled" and set it to true.
See the following link for detailed info. - [http://www.techspot.com/vb/all/windows/t-15244-the-document-contains-no-data--firefox.html](http://www.techspot.com/vb/all/windows/t-15244-the-document-contains-no-data--firefox.html)

Hope this helps. You may give a try to user agent switcher extension.

---

### Post by feathers on 2006-01-07
I sometimes get this mistake. I have always thought this to be a problem of the webserver. Many webpages check what browser and os you are using. I have encountered webpages that simply refuse to work with linux. Does this problem occur with ubuntuforums.org as well? Or other linux sites?

---

### Post by handy on 2006-01-07
Do you have any problems with synaptic?

Cheers,

handy

---

### Post by badboyz107 on 2006-01-13
Okay as weird as this seems it has NEVER choked on synaptic I assumed that this meant that the issue was on the OS somehow I have fixed the problem now in a kind of work around but the ONLY one that seemed to work.

I took my old router that I KNEW everthing worked on and plugged it into my cable modem....then took my  VOIP router and uplinked to it.....then I plugged my computers back into the old router and viola it all works....

This is the first tiem I have been able to reach the forums since the new VOIP router was installed...right now it seems to be the charm plus I have almost doubled the amount of ports available on my network (as long as they are windowz LOL)

---

