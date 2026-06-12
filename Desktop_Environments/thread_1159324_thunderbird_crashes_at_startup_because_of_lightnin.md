---
title: "thunderbird crashes at startup because of lightning extension"
date: 2009-05-14
forum: Desktop Environments
---

### Post by pureblood on 2009-05-14
I started experiencing very weird problems today with thunderbird. As I tried to start the program, the window would open, but before it would display any email the program would seg fault and close, with no debugging options. I couldn't figure out what was going on but this was very annoying. In the end, I had the idea to remove the lightning extension and now everything works out again.

This problem is tricky though, since not only you have to remove the extension with the command
sudo apt-get --purge remove lightning-extension
but also you have to remove the extension from the .mozilla-thunderbird directory. The name depends on your account, and it will be something like
~/.mozilla-thunderbird/xxxxxxxx.default/extensions/{xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}
After doing that, I don't have lightning installed with thunderbird anymore, but at least I can read my email!

Did anybody experience the same problem?

---

### Post by detl_ on 2009-05-15
Hello,
I also encountered problems with Thunderbird since upgrading to 9.04.
When I start thunderbird in the morning, leave it open for some hours, it eventually dies. When I then try to restart it, The program appears but at the same moment disappears again. After a while I am able to restart it again without problems. But I havent figured out whether this is also because of the lightning plugin or because of something else.
How can I trace down what causes this program crash ?

detlef

---

### Post by detl_ on 2009-05-15
I have one more thing to mention here:

It seems that it has got todo with the calendar plugin.
I have imported zimbra calendars to the email client - and it seems that this causes all the trouble.

I tried evolution email client and it also crashed with this error in syslog:

evolution[5532]: segfault at c ip b5ac4cfe sp bfebb060 error 4 in libevolution-calendar.so[b5a20000+113000]

maybe somebody can help me with this.?

thanks

---

### Post by pirog on 2009-08-30
Hi guys,

I am having the same problem and after removing Lightning plugin my T-bird starts with no probs. Yet, installing Sunbird standalone causes the same behaviour - it constantly crashes. *I noticed that this only happens when I have a reminder set for an event.*
Usually, restarting Sunbird or Thunderbird three times in a sequence gives no errors and reminder pops up. Hardly a good user experience.

---

### Post by kimo9909 on 2009-09-03
> **pirog said:**
> Hi guys,

I am having the same problem and after removing Lightning plugin my T-bird starts with no probs. Yet, installing Sunbird standalone causes the same behaviour - it constantly crashes. *I noticed that this only happens when I have a reminder set for an event.*
Usually, restarting Sunbird or Thunderbird three times in a sequence gives no errors and reminder pops up. Hardly a good user experience.

You might want to consider using either Zimbra Desktop >> [http://h.yimg.com/lo/downloads/zdesktop/1691/zdesktop_1_0_3_build_1691_linux_i686.sh]("http://h.yimg.com/lo/downloads/zdesktop/1691/zdesktop_1_0_3_build_1691_linux_i686.sh") or the Zimbra Collaboration Suite >> [http://www.zimbra.com/community/downloads.html]("http://www.zimbra.com/community/downloads.html").  My University uses it and now so do I.  It is very robust and easy to use!  :)

---

### Post by pirog on 2009-09-04
Cheers mate, but I am not looking to replace my suite. All I really need is for the Sunbird/Lightning not to crash :)

I might give Zimbra a try in the future.

---

