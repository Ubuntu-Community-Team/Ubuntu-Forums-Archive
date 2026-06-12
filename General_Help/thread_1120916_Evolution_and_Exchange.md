---
title: "Evolution and Exchange"
date: 2009-04-09
forum: General Help
---

### Post by wsonar on 2009-04-09
I am running Janty but I think this may be do to the recent upgrade my company did to the OWA 

I just tried to setup my exchange setting in evolution and when I enter
my Outlook Web Access URL I get the following error

see screen shot attached.

---

### Post by wsonar on 2009-04-09
Bug # 206346
[https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/206346](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/206346)

Looks like a known issue with exchange 2007

guess I will try thunderbird

---

### Post by Wayne_V on 2009-04-09
I don't think Evolution or Thunderbird is compatible with the latest Exchange protocol.   You should be able to use imap with your Exchange server however.

---

### Post by wsonar on 2009-04-10
yea I didn't have any luck with thunderbird either and I had used the IP address for my incoming and outgoing servers

---

### Post by creolbuay on 2009-04-29
mapi

Found this: [http://bugzilla.gnome.org/show_bug.cgi?id=574784](http://bugzilla.gnome.org/show_bug.cgi?id=574784)

I tired it once at work and it worked perfectly until our Exchange admins decided to stop imap connections to the server. Now we are paying for crossover and office 2007 to get outlook so we can connect to it.  That is a mess all on it's own however.

If the server you are trying to connect to has imap active then mapi for evolution will get you connected.

Yur Administrator will be able to provide you with settings to get you connected if it's available.

---

