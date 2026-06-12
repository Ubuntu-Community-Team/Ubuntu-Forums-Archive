---
title: "Forums being farmed out?"
date: 2006-06-02
forum: Forum Feedback &amp; Help
---

### Post by tonyr on 2006-06-02
It looks like something is being done to alleviate the forums bottleneck, spreading
servers around or mirroring or farming out or something.  Could sombody
amend the **Global Announcement** to that effect, please?  My access is currently
through [www.webdwelling.com;](www.webdwelling.com;) I think that's new...

...and when I tried to get to the Official Wiki from the link at the top of the page,
I was rudely informed that I was trying toi access a secure server from an
insecure server (or was it *vice versa*?)...

---

### Post by imagine on 2006-06-02
[QUOTE=tonyr]...and when I tried to get to the Official Wiki from the link at the top of the page, I was rudely informed that I was trying toi access a secure server from an insecure server[/QUOTE]
The Wiki uses a encrypted connection whereas the forum does not. And you obviously set up your browser to inform you about every switch from a secure to a not secure site and vice versa.
If youre not interested in such informations I recommend you change this setting of your browser. Since you didnt write which browser you use I cannot give more specific details how to do this, but it should be easy anyway.

---

### Post by tonyr on 2006-06-02
[QUOTE=imagine]
If youre not interested in such informations I recommend you change this setting of your browser. Since you didnt write which browser you use I cannot give more specific details how to do this, but it should be easy anyway.[/QUOTE]

I never had a problem getting to the Wiki from the Forums before my access
changed to [www.webdwelling.com](www.webdwelling.com). 

Here is the message.  I doesn't look to me like anything I can fix with my browser
settings.  I don't believe that my machine is the **proxy**, and I am pretty
sure it is not the **server**. I am ready and willing to be to be corrected. 
I use Firefox.

> 
Retrieval of secure URLs through a non-secure proxy is forbidden.

This proxy is running on a non-secure server, which means that retrieval of pages from secure servers is not permitted. The danger is that the user and the end server may believe they have a secure connection between them, while in fact the link between the user and this proxy is insecure and eavesdropping may occur. That's why we have secure servers, after all.

This proxy must run on a secure server before being allowed to retrieve pages from other secure servers. 


EDIT: Here is the **Official Wiki** link/URL from my forums page:
[URL="http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/wiki.ubuntu.com/"]
http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/wiki.ubuntu.com/[/URL]

---

### Post by ubuntu-geek on 2006-06-02
Maybe your isp runs your web traffic through a proxy. We are not "farmed" out.

---

### Post by ubuntu-geek on 2006-06-02
Maybe your isp runs your web traffic through a proxy. We are not "farmed" out.

---

### Post by kassetra on 2006-06-02
> **tonyr]It looks like something is being done to alleviate the forums bottleneck, spreading
servers around or mirroring or farming out or something.  Could sombody
amend the **Global Announcement** to that effect, please?  My access is currently
through [URL="http://www.webdwelling.com said:**
> www.webdwelling.com;[/URL] I think that's new...

...and when I tried to get to the Official Wiki from the link at the top of the page,
I was rudely informed that I was trying toi access a secure server from an
insecure server (or was it *vice versa*?)...

ummm.... I click the Official Wiki link and it's just fine.... 

something may be wrong with your access?  I'm not certain what the issue is - you changed your access and now you have problems getting to the wiki link?

---

### Post by tonyr on 2006-06-02
At this point I am assuming that my browser, Firefox, latest 1.5.0.3 ubuntu
version, is the victim of a known Mozilla security issue.  My guess is
that it is probably the one published as MFSA-33, but it may be something
else.  This problem is reported as addressed in 1.5.0.4.  The current                
/usr/share/doc/firefox does not contain a reference to this advisory.  The
suggested workaround at [http://www.mozilla.org/security/announce/2006/mfsa2006-33.html]("http://www.mozilla.org/security/announce/2006/mfsa2006-33.html")
says that the workaround is to upgrade to a fixed version.  I seem to be able to
avoid the problem by turning cookies off completely.

I have seen the two different bogus proxies, one in Firefox and one in Konqueror,
so I have to believe that there is some other agent involved.  I have contacted
my ISP, hevanet.com, to alert them to a possible security problem, but their
weekend respone time is slower than 8/5.

---

### Post by tonyr on 2006-06-03
OK, I'm pretty much convinced now that it is not a Security (with a Big S) issue.  What
I saw was the result of a CGIproxy.  Somehow the **Official Wiki** link was being
CGIproxyized to translate the address from **[http://wiki.ubuntu.com](http://wiki.ubuntu.com)** to
**[http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/wiki.ubuntu.com/](http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/wiki.ubuntu.com/)**.
How might that have happened?

Is there some policy about this? Is it a bad thing?  Do the forum adminsitrators feel like
this is an issue?  It is an inconvenience in the sense that if it becomes more
prevalent, more users will start to see the same thing I did, namely, a refusal to
link to the **Official Wiki** from the **Forums**.

---

### Post by imagine on 2006-06-03
Does only the Ubuntu wiki use that webdwelling proxy?

Did you maybe set http_proxy or https_proxy?

```
echo $http_proxy
echo $https_proxy
```

---

### Post by tonyr on 2006-06-03
No **http_proxy** or **https_proxy** defined on my session.  I don't thiink
The Problem is specific to, or even related to the forums website.  Google for
**cgiproxy** and you'll get an idea of what is going on.  

I hadn't set up my browser (Firefox) to be paranoid about cookies, and somebody
"slipped me a mickey".  I don't think it's malicious, just inconvenient and sometimes
irritating.

---

