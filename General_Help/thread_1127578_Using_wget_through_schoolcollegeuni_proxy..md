---
title: "Using wget through school/college/uni proxy."
date: 2009-04-16
forum: General Help
---

### Post by J-E-N-O-V-A on 2009-04-16
I'm struggling to use wget through a proxy. 

Here is the general error that I receive

mark@mark-laptop:~$ wget [www.google.com](www.google.com)
--2009-04-16 20:59:08--  [http://www.google.com/](http://www.google.com/)
Resolving proxy-1... xxx.xxx.xxx.xxx
Connecting to proxy-1|xxx.xxx.xxx.xxx|:8080... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
2009-04-16 20:59:08 ERROR 407: Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ).

I then found a tutorial for "Using wget through a proxy" and used the commands:

$ export http_proxy="xxx.xxx.xxx.xxx:8080" 
$ export ftp_proxy="xxx.xxx.xxx.xxx:8080"
$ proxy=on
$ proxy_username="user name" –proxy_passwd="password"

(I know xxx.xxx.xxx.xxx is the real IP because I use it in firefox)

I then used:

$ wget -r -A mp3 "http://downloadmozart.com/?type=category&id=Symphonies"

which returned:

--2009-04-16 21:15:26--  [http://downloadmozart.com/?type=category&id=Symphonies](http://downloadmozart.com/?type=category&id=Symphonies)
Connecting to xxx.xxx.xxx.xxx:8080... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
2009-04-16 21:15:26 ERROR 407: Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  ).

My final attempt was this:

wget –http-user="user name" –http-password="password" -r -A mp3 "http://downloadmozart.com/?type=category&id=Symphonies"

which returned the same error.

This is also a problem for apt-getting things and the add/remove programs application. 
Downloads through firefox and general browsing works flawlessly using xxx.xxx.xxx.xxx:8080, however, I have to type "user name" and "password" before it lets me browse, this is clearly where the problem is.

Any help is greatly appreciated. Also, if you have any tips on how I could try to get unfiltered internet (which a friend of mine has managed but wont share) I'm all ears.

Thanks.

---

### Post by unutbu on 2009-04-16
Does this work?
```
wget --proxy-user="user name" --proxy-password="password" -r -A mp3 "http://downloadmozart.com/?type=category&id=Symphonies"
```

---

### Post by J-E-N-O-V-A on 2009-04-16
> **unutbu said:**
> Does this work?
```
wget --proxy-user="user name" --proxy-password="password" -r -A mp3 "http://downloadmozart.com/?type=category&id=Symphonies"
```

Nope, same error. 

The username and password has been assigned to me by the school, so I don't know why there's a problem. I tried both "user name" and "DOMAIN\user name" but still get the same error.

---

### Post by J-E-N-O-V-A on 2009-04-17
:(

---

### Post by braincookie on 2009-12-31
Maybe your network uses NTLM authentication ([http://en.wikipedia.org/wiki/NTLM](http://en.wikipedia.org/wiki/NTLM)).
This is supported by FF and IE, but not by wget.

I had problems getting through the proxy in my company, but I solved it by using
ntlmaps ([http://doc.ubuntu-fr.org/ntlmaps](http://doc.ubuntu-fr.org/ntlmaps)). Once your ntlmaps is correctly configured
and running, you just have to do the following:

$ export http_proxy="http://localhost:<_ntlmapsport_>"
$ wget [http://www.example.com/](http://www.example.com/)

(<_ntlmapsport_> has to be replaced with the 
previously configured port number)

---

### Post by shrik_kshir on 2010-01-17
Hi,
I'm also facing the same and none of the techniques indicated in this thread worked. My uni proxy uses basic authentication (not NTLM).
Please help.

---

### Post by sandeepcraig on 2010-07-13
hi....
I am also facing the same problem can anyone help plz.......

---

