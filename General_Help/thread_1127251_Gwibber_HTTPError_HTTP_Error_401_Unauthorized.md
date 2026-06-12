---
title: "Gwibber: HTTPError: HTTP Error 401: Unauthorized"
date: 2009-04-16
forum: General Help
---

### Post by wersdaluv on 2009-04-16
Gwibber stopped working for me. I got debug output.```
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/gwibber/microblog/__init__.py", line 49, in get_data
    for message in method(client):
  File "/usr/lib/python2.5/site-packages/gwibber/microblog/twitter.py", line 209, in receive
    for data in self.get_messages():
  File "/usr/lib/python2.5/site-packages/gwibber/microblog/twitter.py", line 159, in get_messages
    urllib.urlencode({"count": self.account["receive_count"] or "20"})))
  File "/usr/lib/python2.5/site-packages/gwibber/microblog/twitter.py", line 154, in connect
    url, data, headers = {"Authorization": self.get_auth()})).read()
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 387, in open
    response = meth(req, response)
  File "/usr/lib/python2.5/urllib2.py", line 498, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.5/urllib2.py", line 425, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.5/urllib2.py", line 360, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.5/urllib2.py", line 506, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
HTTPError: HTTP Error 401: Unauthorized

```

Any idea how to fix this? Where can I find gwibber's configuration files? I want to delete them.

Thanks in advance. :)

---

### Post by wisd0m on 2009-04-16
I had the same issue last week, I installed the latest update and it is working now.

---

### Post by wersdaluv on 2009-04-16
> **wisd0m said:**
> I had the same issue last week, I installed the latest update and it is working now.
Aw. It happened to me right after I installed an update :(

---

### Post by cIIIz on 2009-04-17
I'm having the same issue !
check this link for this bug
[https://bugs.launchpad.net/gwibber/+bug/360468](https://bugs.launchpad.net/gwibber/+bug/360468)

it didn't work for me BTW

---

### Post by wersdaluv on 2009-05-02
Works on Jaunty :)

---

### Post by silvagroup on 2009-05-05
wersdaluv does it really work or does it just give you notifications, because that's all I can get wroking on it.
Reply doesn't work, friends links, doesn't work ...
If that's the best it can do with FaceBook might as well just use rss feed on FireFox.

---

### Post by wersdaluv on 2009-05-06
Hmm. I just don't know. Everything works in my case. I have only tried twitter, identica, and ping.fm

---

### Post by silvagroup on 2009-05-06
Yeah, I think right now those are the services it fully works with.
I tried the latest PPA version and currently it's pretty much useless as a client for FaceBook. They are working on it so that may chnage.
If all my friends weren't on the FaceBook frenzy I'd be at identica anyway.

---

