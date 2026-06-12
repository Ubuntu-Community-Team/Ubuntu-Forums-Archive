---
title: "Problem entering a forum"
date: 2008-12-10
forum: General Help
---

### Post by panosss on 2008-12-10
I have ubuntu 8.04.
I tried to enter the the forum at [www.cnchobby.gr](www.cnchobby.gr) but I can't.
With Opera:   Error: server not found
With Firefox:  site not found
With Internet Explorer: Error opening page.

The forum is working normally, so the problem is with my PC.
It's the first time something like that is happening to me.
What could the problem be? Do you have any ideas?

---

### Post by Elfy on 2008-12-10
If that's the only site you have a problem with I would try clearing private data - but backup your bookmarks etc first

It certainly works ok - I just can't read it :)

---

### Post by panosss on 2008-12-10
> **forestpixie said:**
> I just can't read it :)
Sounds 'greek' to you? It's because it is!:lolflag:
I deleted personal data (AND cookies), restarted FireFox but nothing...

---

### Post by Elfy on 2008-12-10
aah I thought it was Dutch :)
I'd be thinking it was something to do with the site and your location tbh - if you can't reach it with anything at all.

You could try to start firefox in a terminal in safe mode first - disable extensions and themes

```
firefox -safe-mode
```

You could make a new profile as well

```
firefox -ProfileManager
```

---

### Post by panosss on 2008-12-10
I tried both, but no success.
It doesn't want me...

---

### Post by Elfy on 2008-12-10
You say you tried it with IE - is that from in windows?

If that's the case then I would suggest that it's a problem with the site itself from where you are.

See if you can get [http://www.cnchobby.gr/images/r1.jpg](http://www.cnchobby.gr/images/r1.jpg)

Possibly you could see if the site works from a different pc

---

### Post by panosss on 2008-12-10
I use WINE (Windows Emulator) with wich I can run Windows applications (like IE) in Linux,
In other PCs(connected to other line, not to mine, I can't try to mine) I can enter normally in the site. Only my PC has the problem!!! I think I am in the twilight zone...
I can't open the link you gave me.
I was thinking, maybe it's something that's got to do with the router I'm using to connect to the internet...But if it was the router, wouldn't I have problems with other sites too?

---

### Post by Elfy on 2008-12-10
Yea - logically that would I guess be the case.

The only other thing I can think of - not being much good with the internet - is to try with ipv6 off. Open firefox - in the address bar put about:config once you've got past the dragons, put ipv6 in the filter.

You should have one entry - network.dns.disableIPv6 - double clici to make the value true. Close and restart firefox see if that makes a difference. Otherwise I don't know...

---

### Post by panosss on 2008-12-10
No, neither ipv6-->true worked..I 'm desperate
I 'll play some sad tone with my violin :-({|=

---

### Post by panosss on 2008-12-10
I'm now writing this with ubuntu live-cd running in my PC.
NOT even now, with live-cd, I cannot open the link ([www.cnchobby.gr](www.cnchobby.gr))!!!
Isn't that incredible??1!

---

### Post by Elfy on 2008-12-10
well if that's the case I would say it's external, but could be wrong.

---

### Post by panosss on 2008-12-10
I can't believe it. I can surf the entire internet, except for the site I want mostly!:cry:

---

### Post by mkvnmtr on 2008-12-10
Is it possible that you are blocked by a government? You don't say where you are but some governments block some sites. In that case there is proxy software in the repositories.

---

### Post by panosss on 2008-12-10
But everybody can enter this site but me.
Is it possible to be blocked only for me?
I'm in Greece.

---

### Post by panosss on 2008-12-11
I can get in with anonymous surfing!!!
[http://anonymouse.org/cgi-bin/anon-www.cgi/http://www.cnchobby.gr](http://anonymouse.org/cgi-bin/anon-www.cgi/http://www.cnchobby.gr)

Any idea what is happening? How can I fix it permanently?

---

### Post by karlr42 on 2008-12-11
Did you ever get banned from that forum? The admins may have blocked your IP address

---

### Post by panosss on 2008-12-11
But, till today, I had not managed to enter the forum. How could I be banned?:roll:
And if I had been banned, would I make a topic about enetering a site, or I would register my self with a new username??...
Anyway, I have a dynamic IP, which means it changes...so...

---

