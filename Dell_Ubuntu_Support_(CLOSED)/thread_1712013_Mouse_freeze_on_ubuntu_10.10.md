---
title: "Mouse freeze on ubuntu 10.10"
date: 2011-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sam.wilder on 2011-03-22
Hi,
I have Dell Vostro 3300 running Ubuntu 10.10 for sometime. Recently I have started facing problem with the mouse freeze which happens irregularly, but atleast once in two days. The system becomes quite unresponsive. The keyboard however continues to work on the laptop.

I had seen similar reportings earlier in forum thread like  - 
[http://ubuntuforums.org/archive/index.php/t-8001.html](http://ubuntuforums.org/archive/index.php/t-8001.html)

Is this problem which others are facing as well with 10.04 or 10.10
What is the best resolution, as sometimes I do face prospect of loosing important work.

Thanks.

---

### Post by docmojo on 2011-05-09
Hi, I am a novice in these technical issues...

But faced this mouse freeze prob for a few days... Just struck me that, I had installed ClamAV prior to this glitch... So removed it from the system, and the problem seems to have disappeared... 

Do you have it installed too?

---

### Post by tealex on 2012-01-09
i have the same problem 
mouse suddenly freezes 
and in /var/log/messages 
USB disconnect, address XX

me help reinstall compiz

```

sudo apt-get purge compiz*
cd $HOME && rm -rf .compiz/ .config/compiz/

```

---

