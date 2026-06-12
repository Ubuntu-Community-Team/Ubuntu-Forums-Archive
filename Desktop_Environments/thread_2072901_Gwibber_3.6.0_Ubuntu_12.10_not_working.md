---
title: "Gwibber 3.6.0 Ubuntu 12.10 not working"
date: 2012-10-18
forum: Desktop Environments
---

### Post by Divan Santana on 2012-10-18
Hi All,

Trying to debug/fix gwibber.
Install 12.04.1 1 month ago and gwibber+twitter worked and not facebook see [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1058672](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/1058672) .

Upgraded to 12.10 yesterday and now when I launch gwibber I just see a a grey screen with no info.

I've tried the following to "reset" it with absolutely no results.

Remove my twitter and facebook "online accounts" then
```
sudo apt-get remove --purge gwibber gwibber-service gwibber-service-facebook gwibber-service-flickr gwibber-service-foursquare gwibber-service-identica gwibber-service-statusnet gwibber-service-twitter libgwibber-gtk3 libgwibber3 unity-lens-gwibber
sudo aapt-get autoremove --purge -y
rm -rf .cache/gwibber .config/gwibber .gconf/apps/gwibber 
gconftool-2 --recursive-unset /apps/gwibber

```

Reinstall
```

sudo apt-get install -V gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter unity-lens-gwibber gwibber-service-statusneta

```
Launch online accounts and add Facebook and Twiter accounts.
Launch gwibber, and the exact same grey screen appears.

If anyone could help would be greatly appreciated.

When running in debug mode, see attached output. My proxy is currently set to none and internet works fine.

---

### Post by Divan Santana on 2012-10-18
Typical as I post I seem to have fixed it.
My proxy settings weren't completely off.
$ env|grep http revealed some was still exporting and gwibber seemed to not like that.

Will test further but already it's looking much better and working.
Progress and learnings for ex KDE+Arch fanboy.

---

### Post by jlbotto on 2012-10-21
Hi, I've not understood what you dit to make it work. I ahve the same issue of facebook not working on Gwibber.

Could you explain a little more.

Thank You.

---

### Post by Divan Santana on 2012-10-21
Well my issue was my proxy. Therefore in ubuntu settings ensure your network proxy method is set to 'none'.

Also ensure on a your terminal that if you run the below command it will return nothing indicating that no proxy is being exported. If you did change your proxy from something to none then log out and log in.
You possibly don't have a proxy issue and perhaps its another reason why your gwibber is not working.

$ env|grep proxy

---

### Post by taglio on 2012-10-22
Hi there, i'm Riccardo Giuntoli writing from Spain, this is my first POST here in the ubuntu forums. Nice to meet you guys.

Sorry but online-accounts and gwibber on 12.10 doesn't work with proxy enabled. So the thread shouldn't be "SOLVED". Are there any planning to resolve this annoying bug?

Nice Regards,

RG

---

### Post by Divan Santana on 2012-10-22
The thread should be marked as resolved as my problem is resolved which is what the thread was about.

I haven't tested further regarding gwibber+proxies but likely there is an issue and it needs to be detailed and filed a bug report on launchpad.

If someone does that, please post it here. When I get round to it I'll do the same.

---

### Post by netgooroo on 2012-12-22
> **jlbotto said:**
> Hi, I've not understood what you dit to make it work. I ahve the same issue of facebook not working on Gwibber.

Could you explain a little more.

Thank You.



I have this same issue. My install is 12.04 and, Gwibber works fine with Twitter and, when I do posts via gwibber, it posts to facebook but, I do not see my FB account on my gwibber list at all. 

Any help on this at all or, is there another thread for this bug? 

Thanks
netgooroo

---

### Post by bernalaurelio on 2013-01-22
Hi I did the same to you and this solution did not work.

After searching for a while on Google I found the solution to this failure on the next page:

[http://www.webupd8.org/2013/01/fix-facebook-not-working-with-gwibber.html](http://www.webupd8.org/2013/01/fix-facebook-not-working-with-gwibber.html)

Just to follow step by step guide (pretty simple by the way) in which they are everything to indicate that gwibber working again.

Really works are not left without testing.

salu2

---

### Post by ckicken-ck on 2013-10-20
Thanks, I will try this. But first I purged Gwibber completely. I will keep updated.

---

### Post by ckicken-ck on 2013-10-20
...sorry, but it did not work, Gwibber always crashes immediately at the start.

---

### Post by ckicken-ck on 2013-11-10
...okay, I updated the whole system to 13.10 now it works.  :D

---

