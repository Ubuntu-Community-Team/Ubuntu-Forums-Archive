---
title: "True Combat Elite Files"
date: 2006-08-08
forum: Gaming &amp; Leisure
---

### Post by MonkeyBoy on 2006-08-08
I have just reinstalled TCE and was wondering if anyone knows if there are any good repositories of PK3 files anywhere.  

So far I have been connecting to servers at random and leaving it to download all the files but this seems a bit of a lame way of getting the files.  

I know there are some big collections of ET PK3 files online but I haven't seen the same for TCE.

---

### Post by searayman on 2006-08-08
somone was helping me with that, and uploaded them for me to his box.net account. CHeck out this link, but i dont know how long he will keep them there. It was a personall favor.

[http://www.box.net/public/y474qefpc0#main]("http://www.box.net/public/y474qefpc0#main")

---

### Post by MonkeyBoy on 2006-08-09
Fantastic!  Thank you for that.  The link is still good and it would have taken so much longer to download all 220 meg from the various game servers.  

I'm definately going to back these up!

Cheers again!  :D

---

### Post by simplyw00x on 2006-08-09
```
for link in `curl -s http://www.gamingneelix.de/index.php?action=tcemaps |\
grep -o "&lt;a href=\"[^&gt;]*&gt;" | sed -e 's/&lt;[^&gt;]*URL=/ /g' |\
sed -e 's/"&gt;$//'`; do wget -c $link; done
```

---

### Post by stickman419 on 2008-12-06
hey what files and versions do i need to be able to play true combat elite on my linux box?.do i just use v0.49 or i must download 0.45 up to 0.49 and please can u tell where to get them.thanks in advance

---

