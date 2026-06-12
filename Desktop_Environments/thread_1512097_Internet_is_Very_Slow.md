---
title: "Internet is Very Slow"
date: 2010-06-17
forum: Desktop Environments
---

### Post by hamzah01 on 2010-06-17
I have Ubuntu 10.04 installed on my HP laptop and every think work just fine, however i only have problem with Internet Speed. The net is very slow for some reason even though I have 7MB of download. the speed is very fast on WIN Vista but not on Ubuntu. 
I have even installed Chromium Web Browser, but the problem is same. 
any idea why is that ? 

thank you

---

### Post by wojox on 2010-06-17
You could try disabling [ipv6]("http://wojox.homelinux.org/?p=46")

Also see this tutorial [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Winston888 on 2010-06-17
Since changing over from Windows 7 to Ubuntu 10.04 a few weeks ago I seem to be having the same issue. I have tried all methods of firefox optimizations I could find but still the speed is perceptably slower than with Windows 7. 
I then tried Opera and found that it is much speedier than Firefox. Some people find the reverse to be true. I suppose it depends on a lot of factors.
Try Opera.

---

### Post by quirkification on 2010-06-18
I wouldn't say my internet is slow...but my internet is very on/off. Pages either load or they are temporarily unavailable.
I use Google Chrome with Firestarter firewall. And am pretty sure that the firewall does slow facebook...but Iam trying to break that addiction. Using the extension "stayed focused" adn I am only allowed 10 minutes a day.

But is that what you mean by slow internet...slow loads or none at all?

---

### Post by lisati on 2010-06-18
> **quirkification said:**
> I wouldn't say my internet is slow...but my internet is very on/off. Pages either load or they are temporarily unavailable.
I use Google Chrome with Firestarter firewall. And am pretty sure that the firewall does slow facebook...but Iam trying to break that addiction. Using the extension "stayed focused" adn I am only allowed 10 minutes a day.

But is that what you mean by slow internet...slow loads or none at all?

Firestarter isn't a firewall, it's a front-end to a firewll. It's also depecrated. Try (g)ufw instead.

---

### Post by quirkification on 2010-06-18
Humm, giving it a shot as we speak. We'll see in a day or two if i see any changes.

And thanks for removing that china warehouse sales ad things. wtf?

---

### Post by cybrsaylr on 2010-07-06
> **wojox said:**
> You could try disabling [ipv6]("http://wojox.homelinux.org/?p=46")

Also see this tutorial [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

Thanks wojox, that did the trick!

I was having the same problem. I just installed 32 bit Lucid on a couple year old Dell Pent 4 and Firefox and Opera were loading very s-l-o-w. After disabling ipv6 as per your instuctions above both FF and Opera are loading very speedy again. 

Have had this ipv6 issue often in the past. Just wish there was an easier way to disable ipv6 than the above.

---

### Post by cybrsaylr on 2010-07-06
> **wojox said:**
> You could try disabling [ipv6]("http://wojox.homelinux.org/?p=46")

Also see this tutorial [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

Just curious?
Will this fix in disabling ipv6, work with Karmic also?

At times Karmic slows done then speeds up and I was wondering if it could be an ipv6 issue also.

---

