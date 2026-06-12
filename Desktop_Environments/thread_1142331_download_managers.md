---
title: "download managers"
date: 2009-04-29
forum: Desktop Environments
---

### Post by neill on 2009-04-29
Hi

Sorry if this is a dim question ...

Because of a very poor (read rural) line connection I have lots of dropouts when downloading large files via HTTP

Is there a 'download manager' that I can can use that will 'auto resume' in some way ?

I use FlashGot for Firefox with wget and it will restart a broken download, but from the beginning !

What I'm after is something that will pick up where it left off - or am I completely wrong and that's a server side capability that's either there or not ?

/neill :confused:

---

### Post by kpkeerthi on 2009-04-29
You can try [DownThemAll]("http://www.downthemall.net/"). No matter which download manager you use, they can resume only if the website you are downloading from supports the feature. Most websites do. But not all.

---

### Post by mister_p_1998 on 2009-04-29
I think Kget resumes from where you left off, it doesnt do multiple connections to the same file for download axceleration (Like Axcel), but that wont be a problem on a slow connection.
Steve

---

### Post by neill on 2009-04-29
thanks i'll have a go with those options

/neill

---

### Post by m_duck on 2009-04-29
You can continue downloads with wget when your download is interuptted. Once you get your connection back try:```
wget -c http://file/you/were/downloading
```
Though I think you can only use it to resume downloads that were started with wget in the first place.

---

### Post by kpkeerthi on 2009-04-29
> **m_duck said:**
> 
Though I think you can only use it to resume downloads that were started with wget in the first place.

No. I have successfully resumed the partial download left over by downthemall with 'wget -c' :)

---

### Post by m_duck on 2009-04-29
> **kpkeerthi said:**
> No. I have successfully resumed the partial download left over by downthemall with 'wget -c' :)
Cool! I shall remember that for next time, cheers!

---

