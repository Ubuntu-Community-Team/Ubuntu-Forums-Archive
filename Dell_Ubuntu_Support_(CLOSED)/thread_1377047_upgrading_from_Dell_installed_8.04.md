---
title: "upgrading from Dell installed 8.04"
date: 2010-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by winjeel on 2010-01-09
I'll be going on a trip in a few weeks, and I'll be taking my Dell Mini 10. It runs the Dell supplied 8.04LTS. My main computer is running 9.10 and I've started to use UbuntuOne. I really, really don't want to lose any data, and it's a long trip, so I would love to take full advantage of the Contacts synchronising ability, too. However, UbuntuOne does not work with 8.04 (unless of course you use if via web browser). So, I want to upgrade the mini laptop from 8.04 through to 9.10. However, since it's Dell supplied, there is not way for me to go to appropriate menu options in System > Administration > Software Sources to apply as these have been hidden by Dell (I think). So, what do I do? Use the web browser for UbuntuOne and wait for the next LTS or is there a work around?

Many thanks for your help.

---

### Post by HTML-insane on 2010-01-10
Ah. Well, in your case, I suppose it might work (but also might be a bit dangerous) to back up your current /etc/apt/sources.list somewhere, take an existing sources.list from your other computer, change the, "intrepid" bits to, "hardy" and stick that in /etc/apt. Then you can (theoretically) upgrade to the next version of Ubuntu.

Still, that's kinda ugly and I can't guarantee that it'll work flawlessly. In fact, it most likely won't work flawlessly, and since I'm not keen on trying it...

---

### Post by snowpine on 2010-01-10
Hi Winjeel, you will need to do a fresh install if you want a newer release. ("Dellbuntu" 8.04 was a one-time collaboration between Dell and Ubuntu, with no upgrade path.) Easy tutorials on this website: [http://www.ubuntumini.com/](http://www.ubuntumini.com/) I've personally installed both 9.04 and 9.10 on my Mini 9 with no major problems.

It's worth noting however that your Mini 10 (unless you have the Mini 10v) uses the Intel GMA500 "Poulsbo" graphics, which are not well supported by most versions of Linux. You should do some Poulsbo-specific research (there are great threads on these forums) before upgrading. You might choose to stick with 8.04 (which will be fully supported through April 2011) for this reason.

---

### Post by winjeel on 2010-01-10
Thanks for the responses.

---

### Post by winjeel on 2010-01-11
Are there any commands that I can use in Terminal to do an upgrade? I'm worried that I'll be stuck in 8.04 (I really don't want to do a clean install and lose all the drivers Dell provided).

---

### Post by winjeel on 2010-01-14
Am I asking the impossible?

---

### Post by snowpine on 2010-01-14
> **winjeel said:**
> Am I asking the impossible?

8.04 will be supported through April 2011. You can do a fresh reinstall if you want a newer release. I don't have a Mini 10 (my Mini 9 has a different graphics card) so I'm afraid I can't help you with the GMA500/Poulsbo issue. The Search feature will turn up many threads on the topic, good luck! :)

---

### Post by winjeel on 2010-01-15
Thanks.

---

