---
title: "Firefox Image Display Problem"
date: 2005-04-07
forum: Desktop Environments
---

### Post by danja on 2005-04-07
Hey!

Being fairly new, and thoroughly enjoying my experience with Ubuntu, I've just set my laptop up to receive internet from my XP machine via Proxy server, but I have a problem...

Images!

They do not seem to display on websites.

I tried searching for Linux wallpapers in Goole Images, and they appeared in the search results, but to try and click & enlarge the image to save, just gave me this error:

"The requested URL: /example/example/wallpaper/index.php?img_id91" Was not found on this server"

To me, that looks like it tried to resolve it off my laptop, correct?

It seems to have lost the original path of the image, hence not finding it.

What could be the fault?

Thansk in advance, 

Dan

---

### Post by nad on 2005-04-08
What are your proxy settings in FireFox (Edit -> Preferences -> General -> Connection)?

Dan M

---

### Post by danja on 2005-04-08
Hi Nad, 

Im not actually at my laptop at the minute, Im in work, thats at home :(

I'll look as soon as I get back tonight mate!

Cheers for your reply,

Dan

---

### Post by danja on 2005-04-08
[QUOTE=nad]What are your proxy settings in FireFox (Edit -> Preferences -> General -> Connection)?

Dan M[/QUOTE]

Right, here goes:

Manual Proxy Configuration - All i.p address are 192.168.xxx.xxx

Ports are:

HTTP:6588
FTP:21
Gopher:0
SSL:0
Socks:1080

Any help to you Nad?

---

### Post by nad on 2005-04-08
Have you tried the auto-detect proxy settings script in the same toolbox? There are several proxy settings for FireFox. Manually changing your settings will also require you to manually make changes to your FireFox config file. Type in your address window 'about:config' to get an idea of what is involved!

If the auto-detect settings don't work, please post back.

Dan M

---

### Post by danja on 2005-04-09
Auto detect didn't work Nad, so I opened the config like you said, and theres a hell of alot going on lol

Which part would I have to edit?

---

### Post by nad on 2005-04-09
Hi,

Sorry I haven't gotten back to you.

What you are trying to do is pretty close to the cutting edge for FireFox. And FireFox is still a little buggy. My gut feeling is that you have to allow more connections, in both FireFox and your proxy server (I seem to remember reading about that somewhere) and that your Socks port in the manual configuration should be the same as your proxy port. Please take notes as you change settings that you may return to configurations that sort of work. Changes from the default made to the config file at about:config will be highlighted in bold.

Search these forums and the MozillaZine forums for how to tweak your FireFox network connection settings. I don't mean to leave you on your own, but this could take a while and is quite specific to your setup. Keep posting here as others have similar problems and I have not read a definitive answer yet.

Regards,

Dan M

---

### Post by shakin on 2005-04-10
[QUOTE=nad]What you are trying to do is pretty close to the cutting edge for FireFox.[/QUOTE]

Sorry, but unless I'm misunderstanding the situation, I don't agree with you. Dan is just trying to run Firefox from behind a proxy and that should work perfectly (I have done it, as have most other people who have used FF from their work).

To me it's clear that the problem is in XP's proxy server setup. I bet you could put a Windows box running any browser behind that proxy and it would have the same problem. Dan, if you have another Windows box, please try doing that.

I also suggest temporarily putting the Linux box directly onto the net by swapping the network cable from the Windows box to your laptop. Don't forget to remove the proxy settings when you do this! If Firefox can suddenly browse the web perfectly, you know where your problem lies: the proxy server config.

You will need to find a Windows forum for information about how to config the proxy server. If you want to make things simpler, I'd say grab a broadband router for under $50 and skip trying to use XP as a proxy server. By not requiring the XP box to be powered on 100% of the time you will make up for the cost of the router in lower electric bills :)

---

### Post by nad on 2005-04-10
Yeah. That makes sense. I do remember reading that the default number of ports open in an XP box isn't enough.

Dan M

---

### Post by danja on 2005-04-10
Wow, so much usefull information, cheers guys!

I've been told before that running a router would be much easier, even XP to XP network connection.

I've dual booted my laptop to run XP & Unbuntu, XP surfs perfectly with everything a normal connection would get, P2P the lot, through proxy and SOCKS.

Ubunutu however shows issues with websites, I've not even tried any P2P apps yet.  

It's a shame, would have been cool to flick between to two.

As for plugging the interent into the Ubuntu OS, AOL don't do drivers for myy broadand modem yet :(

Bout time they did I say hehe

---

### Post by danja on 2005-04-10
You'll find this weird, but I've sorted it.

I'm running two proxy servers now, Proxy+ & AnalogX Proxy.

AnalogX Proxy works for my SOCKS connections whereas Proxy+ doesn't, and Proxy+ works fine for my HTTP, i.e. my images loads now etc, whereas AnalogX Proxy threw up the problems originally mentioned.

Weird eh  :roll: 

So overall, aa combination of two proxy apps looks to sort my issue out  \\:D/

---

