---
title: "Unity not displaying recently opened applications"
date: 2012-05-14
forum: Desktop Environments
---

### Post by m_sharp on 2012-05-14
Hi,

I am having a bit of a strange issue with Unity, I have done a quick search on Google and come up with no solid results on what might be causing my issue.

What has happened is this. My Netbook has had a few upgrades so I'm trying to avoid a full reinstall but not going to be too surprised if that is the only option.

The problem is that on start-up I get an error message relating to lens.video (I can't remember exact error as I haven't got my Netbook beside me right now). When I go into the Unity main menu it doesn't display any items such as recently used applications. I can search for applications such as VLC and they will appear.

A bit if history on the Install path.

The netbook started with a 10.10 server install which had LXDE running for a while.
I then upgraded it to 11.04 sticking with LXDE
This was in turn upgraded to 11.10 again sticking with LXDE
I have no upgraded to 12.04 and stuck with LXDE for a while and this all seemed to work OK.
Installed ubuntu-desktop package using apt-get and everything seems to be working except the unity menu issue.

Thanks for your help guys

Sharpy

---

### Post by Krytarik on 2012-05-14
Try clearing the Zeitgeist database, either by deleting the entire file:
```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
```Or via "System Settings -> Privacy".

Regards.

---

### Post by wilee-nilee on 2012-05-14
Unity might need a reset hit alt-f2 then type in unity --reset then hit enter.

---

### Post by m_sharp on 2012-05-14
Many thanks for the responses. I will try them when I get home and let you know.

---

### Post by apollothethird on 2012-06-26
> **m_sharp said:**
> Many thanks for the responses. I will try them when I get home and let you know.

Hi, m_sharp.  I'm wondering if either of those resolved your issue?  If so, which one?

I'm having a similar problem, but not exactly that.  Before upgrading I had lots of recent used apps that would show up.  The list would survive reboots.  However, after the upgrade I only have a few recently used apps and they don't survive reboots.  The list starts over after I reboot.

I'm wondering if this is a default that can be configured different or if I'm suffering from the same issue you were having.  If the latter is the case, I'll try what worked for you.

I prefer not to completely clear my sqlite database if its not going to resolve the issue.  The recent docs lens works great.  I use it all the time.  Clearing the database will clear those items.  But if it it's the only way to go and works I'll give it a try.

Thanks again for coming back and reporting the results.  You might even consider marking the thread solved for your issue if it worked for you.  The consideration would be a great gift back to the community that always go out of the way to help.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

