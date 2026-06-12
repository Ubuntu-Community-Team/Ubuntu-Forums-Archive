---
title: "website hit counter"
date: 2009-02-25
forum: General Help
---

### Post by jdcnosse on 2009-02-25
Okay, I'm sure I made a post before, but if it did get deleted then just let me know.

Basically I want to know if there's any program for my ubuntu 8.04 server that does what this site would do?

[http://www.statcounter.com/](http://www.statcounter.com/)

---

### Post by mb_webguy on 2009-02-25
Assuming you're running your own webserver, you can use [PHPCounter]("http://phpcounter.sourceforge.net/").

---

### Post by jdcnosse on 2009-02-26
Yes, that's exactly I what I was looking for.  Just something local that would keep track of how many visitors I get and who they are.

---

### Post by bodhi.zazen on 2009-02-26
I was looking for this as well a while ago and highly advise webalizer

It is a command line tool but generates great reports

You run it with :

```
sudo webalizer
```

It then generates a directory in 

/var/www/usage

Browse to [http://your_site/usage](http://your_site/usage) to see a report

Includes hits, traffic, referrals, etc.

Nice graphs

Nice "how to" here :

[http://bobbyallen.wordpress.com/2007/01/16/install-and-configure-webalizer-on-ubuntu/](http://bobbyallen.wordpress.com/2007/01/16/install-and-configure-webalizer-on-ubuntu/)

---

### Post by fragos on 2009-02-26
I high recommend Google Analytics -- free and lots of data. Google uses cookies on visiters PC's which eliminates all the web crawler traffic that skews visit results. Google won't provide the identity of visiters but will provide where they came from whic is to me much more useful. Check it out [http://www.google.com/analytics/](http://www.google.com/analytics/)

---

### Post by CrucifiedEgo on 2009-02-26
> **fragos said:**
> I high recommend Google Analytics -- free and lots of data. Google uses cookies on visiters PC's which eliminates all the web crawler traffic that skews visit results. Google won't provide the identity of visiters but will provide where they came from whic is to me much more useful. Check it out [http://www.google.com/analytics/](http://www.google.com/analytics/)

Bingo.  No extra software, and more info than you could ever possibly want.

---

### Post by mb_webguy on 2009-02-26
> **CrucifiedEgo said:**
> Bingo.  No extra software, and more info than you could ever possibly want.

True, but you're relying on an external source to track your web site activity.  I know that Google's official unofficial motto is "Don't be evil", but I don't like giving information to corporations except when absolutely necessary, especially when it involves an 8-page TOS agreement.

> 6. INFORMATION RIGHTS AND PUBLICITY . Google and its wholly owned subsidiaries may retain and use, subject to the terms of its Privacy Policy (located at [http://www.google.com/privacy.html](http://www.google.com/privacy.html) , or such other URL as Google may provide from time to time), information collected in Your use of the Service. Google will not share information associated with You or your Site with any third parties unless Google (i) has Your consent; (ii) concludes that it is required by law or has a good faith belief that access, preservation or disclosure of such information is reasonably necessary to protect the rights, property or safety of Google, its users or the public; or (iii) provides such information in certain limited circumstances to third parties to carry out tasks on Google's behalf (e.g., billing or data storage) with strict restrictions that prevent the data from being used or shared except as directed by Google . When this is done, it is subject to agreements that oblige those parties to process such information only on Google's instructions and in compliance with this Agreement and appropriate confidentiality and security measures.
Clause ii basically means that Google can use or publish your information however and whenever it wants -- i.e. if it has "good faith belief" that it needs to do so to "protect the rights, property or safety of Google".  Maybe I'm just cynical and paranoid, but it seems to me that Google has the *right* to make a profit, and any information collected by that service is technically the *property* of Google, and it's fairly *safe* to assume that they might have the *good faith belief* that it's ok for them to sell it to earn some extra revenue.

---

### Post by bodhi.zazen on 2009-02-26
What mb_webguy said with a little less paranoia :lolflag:.

The information is available in your logs, you do not need an external source such as google (although I understand why some may choose to use any number of external trackers).

webalizer FTW !!!

---

### Post by mb_webguy on 2009-02-26
> **bodhi.zazen said:**
> What mb_webguy said with a little less paranoia.

Hey, I *did* say that I might be just a little cynical and paranoid about these things...  :D

---

### Post by bodhi.zazen on 2009-02-26
It's OK, google has been awesome and, no matter how we may feel, they have contributed to both the web and open source.

But IMO a little google paranoia is healthy, especially with their terms of use. I do not mind as much if they index my site, I probably get more traffic because of it. But that does not mean I want to give away my rights to my site :rolleyes:

---

### Post by CrucifiedEgo on 2009-02-27
> **mb_webguy said:**
> True, but you're relying on an external source to track your web site activity.  I know that Google's official unofficial motto is "Don't be evil", but I don't like giving information to corporations except when absolutely necessary, especially when it involves an 8-page TOS agreement.


Clause ii basically means that Google can use or publish your information however and whenever it wants -- i.e. if it has "good faith belief" that it needs to do so to "protect the rights, property or safety of Google".  Maybe I'm just cynical and paranoid, but it seems to me that Google has the *right* to make a profit, and any information collected by that service is technically the *property* of Google, and it's fairly *safe* to assume that they might have the *good faith belief* that it's ok for them to sell it to earn some extra revenue.

I completely understand and normally am equally paranoid.  However, this is web statistics.  Unless it's a major business endeavor in which your stats somehow are an integral part of your business plan (can't think of a good example) it's hardly data that I would be sad to see shared.

---

### Post by jdcnosse on 2009-03-01
I've decided to use webalizer only because of the fact that the logs are on my own computer, not for security but just so it works lol

I have my webserver set up special so I can get past the port 80 blocking that my ISP or my cable modem (given to me by my ISP) is doing.

---

### Post by bodhi.zazen on 2009-03-01
Glad you liked webalizer, it is an awesome tool and it likely give you all the information you need, and then some.

---

