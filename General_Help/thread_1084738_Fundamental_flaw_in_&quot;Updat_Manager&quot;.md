---
title: "Fundamental flaw in &quot;Updat Manager&quot;?"
date: 2009-03-02
forum: General Help
---

### Post by emarkay on 2009-03-02
OK, click on it and the dialog comes up and it says: 
"Keep your system up to date" 
and then goes and looks at all the available updates.

OK so far.

Then it says, EVERY TIME:
"Your system is up to date"

However, if I click "Check" and enter my password, 90% of the time I get UPDATES!!!

Is this conceptually AFU or what?

How about if the default become:  

"Your system appears to be up to date, but click the "Check" button to confirm."

BTW, I have noticed this since Ubuntu 6-point-whatever, but have never bothered to comment till now.

Anyone???

Thanks.

---

### Post by Rallg on 2009-03-02
It has been that way for some time. You are correct: it is misleading.

---

### Post by emarkay on 2009-03-30
Filed a bug report...

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/352035](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/352035)

---

### Post by Therion on 2009-03-30
Agreed, it IS misleading.  

I've just grown accustomed to Ubuntu being that way and had quit thinking about HOW misleading it is.  Further, I don't think anything is being checked the first time you click through, since it appears you need to be "root" in order to make such changes to the system; which of course only compounds the issue.

---

### Post by Cheesehead on 2009-03-30
It's not really a bug. It's expected behavior.

update-manager (u-m) is meant to be used with update-notifier (u-n). u-n downloads all the updates and upgrades before notifying you 'Upgrades to your system are available' and sending you to u-m. The idea is that your upgrades are fast and convenient because u-n has already completed the downloading in the background.

The u-n/u-m pair is also structured that way it is so that upon u-m startup it doesn't seem to freeze or become unresponsive while immediately downloading the updates. (prevents a lot of frustration and false bug reports)

When you skip the first step, the second does seem weird.

Power-users can always use the command line apt-get, python-apt, apticron, and other fancy tools to customize their upgrade joy.

---

### Post by Hobgoblin on 2009-03-30
> **emarkay said:**
> 
Then it says, EVERY TIME:
"Your system is up to date"


It also says "The package information was last updated ..... ago".

Can't blame it for your lack of reading.:)

---

### Post by emarkay on 2009-04-03
> **Hobgoblin said:**
> It also says "The package information was last updated ..... ago".

Can't blame it for your lack of reading.:)

I don't care when I updated it, just that it MAY not be "up to date..."  sheesh.....

---

### Post by ws.venkateswaran on 2009-06-15
hi guys

have been using windows till about a month ago and have shifted to ubuntu 8.10... so just give a few guidelines on updating..

am not sure whether my update manager is functioning. everytime i run it it checks and says the system is up to date. till now i have not had a single update done by the update manager.

how is updating of apps done in ubuntu.. can anyone give a brief intro

if this question has been asked many times before can you just guide me to the posted replies

thanks

---

