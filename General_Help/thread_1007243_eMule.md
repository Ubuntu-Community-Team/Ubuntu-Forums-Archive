---
title: "eMule ?"
date: 2008-12-10
forum: General Help
---

### Post by stans on 2008-12-10
I'd like to access eMule but see that it only supports access via an application installed on Windows. Does anyone know how I can access eMule using Linux (not with Wines) ?

---

### Post by binbash on 2008-12-10
did you try amule?

---

### Post by Hallvor on 2008-12-11
> **stans said:**
> I'd like to access eMule but see that it only supports access via an application installed on Windows. Does anyone know how I can access eMule using Linux (not with Wines) ?

Like binbash said, aMule is the native ed2k client. You can install it either through Synaptic or thorugh the terminal:

```
sudo apt-get update && apt-get install amule 
```

---

### Post by stans on 2008-12-11
Yes, I did see aMule but didn't know if it would work. Thank you both for the replies.

---

### Post by stans on 2008-12-11
OK - this is really cool: no adware.

The one challenge that I have is how slow the downloads are. I've searched a bit for an answer but there is so much to wade thru. 

I'm downloading a file now that is estimated to take two days to arrive.

---

### Post by Arup on 2008-12-11
> **stans said:**
> OK - this is really cool: no adware.

The one challenge that I have is how slow the downloads are. I've searched a bit for an answer but there is so much to wade thru. 

I'm downloading a file now that is estimated to take two days to arrive.

Have you forwarded the ports?

---

### Post by stans on 2008-12-11
I think my problem is that the server that I am uploading from is slow as there was one file from another location that arrived very quickly.

---

### Post by Arup on 2008-12-11
Yes get latest servers from [http://ed2k.2x4u.de/index.html](http://ed2k.2x4u.de/index.html)

---

### Post by stans on 2008-12-11
Thank you !

There are instructions for doing this ?

Service Temporarily Unavailable is what I got, btw...

---

### Post by Hallvor on 2008-12-12
> **stans said:**
> OK - this is really cool: no adware.

The one challenge that I have is how slow the downloads are. I've searched a bit for an answer but there is so much to wade thru. 

I'm downloading a file now that is estimated to take two days to arrive.

Servers have nothing to do with speed. The servers are only used to find sources. The data chunks are transmitted from peer to peer. You only need servers for bootstrapping anyway, since Kad will work just fine alone.

Slow speed on the ed2k network is caused by the large amount of leechers with 30 movies on their download list, uploading at 10 kB/s.

---

