---
title: "Gmail problem with pidgin"
date: 2009-06-25
forum: General Help
---

### Post by Czarli on 2009-06-25
[SIZE=3]Hello,

I am having trouble signing in my gmail account with pidgin but I can sign in my yahoo account just alright. :(

Lately, I know that there are problems with signing in yahoo with pidgin but I have already solved this problem. It also seems that I am the only who cannot connect my gmail account here in the office.

 Can anyone suggest what I can do to solve this problem? :confused:

Thanks a lot.[/SIZE]

---

### Post by Vikhyath on 2009-06-25
which version of pidgin do you use

---

### Post by cybergalvez on 2009-06-25
gmail is working for me, are you using the latest version? the Pidgin website tells you how to install the lastest version

---

### Post by Czarli on 2009-06-29
> **Vikhyath said:**
> which version of pidgin do you use

Hi, I'm using v2.5.5...

---

### Post by ftabor on 2009-06-29
V2.5.7 is the latest version.

---

### Post by Czarli on 2009-07-27
Am using pidgin v2.5.8 now but i stll can't open my gmail... 

i've tried to put in talk.google.com in Connect Server. it still doesn't work. am i doing something wrong? :confused:

---

### Post by Czarli on 2009-08-13
Hello everyone,

Well, no one answered my latest reply so I did a little researching by myself and found out a solution for this problem.

In editing your gmail account, under the Advanced tab, I checked both 'Force old (port 5223) SSL and 'Allow plaintext auth over unencrypted streams' (although the post from where I got said that it may not matter whether or not you checked 'Allow plaintext...'). 

In Connect Port, type in either 443, 5222, or 5223 (whichever works for you, in my case, 443 worked fine).

In Connect Server, type in talk.google.com

My File transfer proxies is proxy.jabber.org and my Proxy setting is 'Use GNOME Proxy Settings'

I hope that this also works for anyone there who have the same problem.

:guitar:

---

### Post by Anxious Nut on 2009-09-01
THANK YOU, THANK YOU VERY MUCH!!!

i had this problem for over 2 weeks and couldn't find a way I WAS DESPERATE. But when i tried THIS!! man all I can say is THANK YOU

btw i did exactly like what you've done

---

### Post by squee on 2010-01-29
Worked for me too, but I'm not so happy doing it as un-securely as this. I'll look into it more, to see if I can put the security back in.

---

### Post by BinaryEnCoder on 2011-05-29
try just deleting the certificates inside pidgin and closing and re-opening it.
when it opens should ask for approval of the certificates and by just clicking accept should work.

---

