---
title: "Firefox 3 in Lenny yet?"
date: 2008-06-30
forum: Debian
---

### Post by Inxsible on 2008-06-30
I aptitude searched for firefox 3 and iceweasel 3 in lenny and didnt find anything. I have Iceweasel 2.14 installed and I would like to go 3.0

Have the packages come up in lenny yet? or are they only in sid?

---

### Post by Mizzou_Engineer on 2008-06-30
> **Inxsible said:**
> I aptitude searched for firefox 3 and iceweasel 3 in lenny and didnt find anything. I have Iceweasel 2.14 installed and I would like to go 3.0

Have the packages come up in lenny yet? or are they only in sid?

It is only in sid so far, and that's not even 3.0-final, but 3.0-alpha9 when I checked a few days ago.

---

### Post by jdhore on 2008-06-30
> **Mizzou_Engineer said:**
> It is only in sid so far, and that's not even 3.0-final, but 3.0-alpha9 when I checked a few days ago.

Currently 3.0-RC2 as of about 2 weeks ago which, for Linux and Windows users is the same as final.

---

### Post by basenvironment on 2008-07-01
> **Inxsible said:**
>  or are they only in sid?
sid....should be fine to install it in a lenny system though

---

### Post by tturrisi on 2008-07-02
I have FF3 running on Lenny by doing:
Use your browser to locate the 3.0 path at the ftp site.

cd /tmp
wget [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest-2.0/linux-i686/en-US/firefox-2.0.0.14.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/latest-2.0/linux-i686/en-US/firefox-2.0.0.14.tar.gz)
cd /opt
tar -zxvf /tmp/firefox-2.0.0.14.tar.gz
cd /opt/firefox
debian:/# ln -s /usr/lib/firefox/plugins /opt/firefox
debian:/# ln -sf /opt/firefox/firefox /usr/bin/firefox
debian:/# ln -sf /opt/firefox/firefox /usr/bin/mozilla-firefox
debian:/# ln -sf /opt/firefox/firefox /usr/bin/mozilla

I prefer FF over Iceweasel because many servers do not recogize the name "iceweasel" in browser headers and as a result some sites don't display certain multimedia content.

---

### Post by utUtu on 2008-07-03
> **tturrisi said:**
> I have FF3 running on Lenny by doing:
Use your browser to locate the 3.0 path at the ftp site.

I prefer FF over Iceweasel because many servers do not recogize the name "iceweasel" in browser headers and as a result some sites don't display certain multimedia content.

Just change the agent value to Firefox from Iceweasel
in url bar, type about:config
then search for 'agent', and then change it as below

```


general.useragent.extra.firefox;Firefox/3.0

```

---

### Post by tturrisi on 2008-07-05
I also prefer the top of the browser window to say Mozilla Firefox instead of Iceweasel.

---

### Post by odiseo77 on 2008-07-10
I guess you all have already noticed, but Iceweasel 3.0~rc2-2 is now on lenny's repos. It's retained for some reason (using the gnome update notification applet), but a simpe "aptitude upgrade" upgrades it. 

For some strange reason after having upgrading it, it starts in "No connection" mode, so I have to go to "File" and uncheck the "Work without connection" option anytime I open it (otherwise it says it's working in no connection mode and cannot find the site). Does anyone know how to solve this issue? Is it a bug or something, or is it just me who's having this problem? (It's becoming really annoying to do this anytime I start iceweasel).

Thanks in advance.

---

### Post by Inxsible on 2008-07-10
> **odiseo77 said:**
> I guess you all have already noticed, but Iceweasel 3.0~rc2-2 is now on lenny's repos. It's retained for some reason (using the gnome update notification applet), but a simpe "aptitude upgrade" upgrades it. 

For some strange reason after having upgrading it, it starts in "No connection" mode, so I have to go to "File" and uncheck the "Work without connection" option anytime I open it (otherwise it says it's working in no connection mode and cannot find the site). Does anyone know how to solve this issue? Is it a bug or something, or is it just me who's having this problem? (It's becoming really annoying to do this anytime I start iceweasel).

Thanks in advance.I have just gone ahead and removed iceweasel and installed opera in its place....its much faster IMO

---

### Post by benuski on 2008-07-10
> **odiseo77 said:**
> I guess you all have already noticed, but Iceweasel 3.0~rc2-2 is now on lenny's repos. It's retained for some reason (using the gnome update notification applet), but a simpe "aptitude upgrade" upgrades it. 

For some strange reason after having upgrading it, it starts in "No connection" mode, so I have to go to "File" and uncheck the "Work without connection" option anytime I open it (otherwise it says it's working in no connection mode and cannot find the site). Does anyone know how to solve this issue? Is it a bug or something, or is it just me who's having this problem? (It's becoming really annoying to do this anytime I start iceweasel).

Thanks in advance.

Do you have network-manager installed?

---

### Post by khelben1979 on 2008-07-10
> **odiseo77 said:**
> I guess you all have already noticed, but Iceweasel 3.0~rc2-2 is now on lenny's repos. It's retained for some reason (using the gnome update notification applet), but a simpe "aptitude upgrade" upgrades it. 

For some strange reason after having upgrading it, it starts in "No connection" mode, so I have to go to "File" and uncheck the "Work without connection" option anytime I open it (otherwise it says it's working in no connection mode and cannot find the site). Does anyone know how to solve this issue? Is it a bug or something, or is it just me who's having this problem? (It's becoming really annoying to do this anytime I start iceweasel).

Thanks in advance.

Does it exist a ppc linux build in Lenny for the ppc architecture at the present? 

I want to be able to use it on my old laptop over here, will be interesting to see the performance..

---

### Post by odiseo77 on 2008-07-10
> **Inxsible said:**
> I have just gone ahead and removed iceweasel and installed opera in its place....its much faster IMO

Yes, I'm using Opera and Iceweasel on my Debian install. I like both (and I specially like Opera since v. 9.50), but I'm more used to Iceweasel, so I'd like to solve this issue somehow (maybe it's some bug and I have to wait for the next iceweasel release).

> **benuski said:**
> Do you have network-manager installed?

Yes, it's installed but I don't use it, since I'm on a wireless connection and last time I did it (many many months ago), it couldn't connect to my router, so I got used to connect manually. But I think this is a specific Iceweasel issue, because it didn't happen before I upgraded it this morning (and doesn't happen with any other program).

> **khelben1979 said:**
> Does it exist a ppc linux build in Lenny for the ppc architecture at the present? 

I want to be able to use it on my old laptop over here, will be interesting to see the performance..

There are iceweasel packages for all the debian supported architectures (including ppc), as I can see [here]("http://packages.debian.org/testing/iceweasel"). In my opinion, Iceweasel is as fast as firefox can be, so, if you've used firefox on this laptop, I think the performance will be pretty much the same. I tried seamonkey on PuppyLinux and I found it to be very light; I think the Debian equivalent is Iceape, so I guess it must be lighter than firefox/iceweasel. 

Greetings :)

---

### Post by khelben1979 on 2008-07-11
I meant Iceweasel of course. I have never run Firefox on the ppc linux system.

---

### Post by markharding557 on 2008-07-12
iceweasel is firefox with a different logo so it's no suprise they perform the same

---

