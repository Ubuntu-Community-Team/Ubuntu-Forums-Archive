---
title: "Need help using wget to download files from university page"
date: 2009-06-08
forum: General Help
---

### Post by bzm3r on 2009-06-08
I need to download a whole bunch of files (~240 - 300 pdfs) from my university's Blackboard portal page. After some sniffing, I decided to test out wget on a single url and I typed this into my terminal:

> wget 'https://some.universitypage.edu/@@some_auth_code/convoluted/path/to/content.pdf'

wget fetches: 
> --2009-06-08 00:00:00--  'https://some.universitypage.edu/@@some_auth_code/convoluted/path/to/content.pdf'
Resolving some.universitypage.edu... 707.140.120.5
Connecting to some.universitypage.edu|707.140.120.5|:777... connected.
HTTP request sent, awaiting response... 302 Found
Location: 'https://some.universitypage.edu/@@some_auth_code/convoluted/path/to/content.pdf?bsession=13371337&bsession_str=session_id=13371337,user_id_pk1=707707,user_id_sos_id_pk2=1,one_time_token=' [following]
--2009-06-08 00:00:00--  'https://some.universitypage.edu/@@some_auth_code/convoluted/path/to/content.pdf?bsession=13371337&bsession_str=session_id=13371337,user_id_pk1=707707,user_id_sos_id_pk2=1,one_time_token='
Connecting to some.universitypage.edu|707.140.120.5|:777... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `content.pdf?bsession=13371337&bsession_str=session_id=13371337,user_id_pk1=707707,user_id_sos_id_pk2=1,one_time_token='

    [ <=>                                   ] 1,116       --.-K/s   in 0s      

2009-06-08 00:00:00 (111 MB/s) - `content.pdf?bsession=13371337&bsession_str=session_id=13371337,user_id_pk1=707707,user_id_sos_id_pk2=1,one_time_token=' saved [1116]

The contents of the saved file:

> <html>
<head>
</head>
<body onLoad="document.relay.submit()">
<form method=post action="https://login.someuniversity.edu/" name=relay>
<input type=hidden name=cookiez_g_req value="sOme660cHArsW0rthOfStuff">
<input type=hidden name=post_stuff value="">
<input type=hidden name=relay_url value="https://login.someuniversity.edu/Cookiez.reply">
<noscript>
<p align=center>You do not have Javascript turned on,   please click the button to continue.
<p align=center>
<input type=submit name=go value=Continue>
</noscript>
</form>
</html>


When this file is opened with Firefox, I can download the file that I need (without the need for me to login again, because I guess the authorization is stored within the cookiez_g_req thingamajiggy). However, what I really want is content.pdf. This is would be great if there were only a couple files I needed to download, but I have approximately 40 lectures each for 6 classes...using wget to automagically download all the lectures would be speedy, while making me look very cool with all my fellow scriptkiddiez.

So, what's going on here, how can I make wget jump through the last hoop to get me the pdf, instead of stopping at just giving me a fancier link to the pdf?

P.S. I tried > wget 'https://some.universitypage.edu/@@some_auth_code/convoluted/path/to/content.pdf?bsession=13371337&bsession_str=session_id=13371337,user_id_pk1=707707,user_id_sos_id_pk2=1,one_time_token='  

I was hoping that perhaps it could download the pdf from the link that it returns (I can't say I completely understand what I'm doing) but it just returns another html file that's identical to the one I pasted above. Perhaps the auth cookie is different, never bothered to check.

---

### Post by kay-man on 2009-06-08
Have you tried passing user and password information to wget?

You can even pass a cookie file to use. Check

```
man wget
```

for details

---

### Post by bzm3r on 2009-06-08
Authorization is not the problem, it authorizes just fine as the output I pasted shows. Getting authorization was the easy part.

---

### Post by kay-man on 2009-06-08
I don't know. The reply you're getting mentions javascript. If that is indeed the issue maybe wget can't do it.

But if all the download links are on the same page you might be able to use the firefox DownThemAll extension to, well, down them all :)

---

### Post by bzm3r on 2009-06-08
Oh, update. I got this firefox plugin called DownThemAll (seems like a graphical wget), and it happens to be using pretty much the same url I passed wget, except with a referer as well.

I gave wget the same referer url too with "--referer=https://hellokitty.edu", but still no change to what it gets.

---

### Post by bzm3r on 2009-06-08
There are things wget can't do?!

"Pro" cli users make it seem like there's nothing wget can't do...

---

