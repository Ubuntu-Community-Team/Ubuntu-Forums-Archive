---
title: "Jaunty update manager: no icon?"
date: 2009-04-28
forum: General Help
---

### Post by vexorian on 2009-04-28
Seems update manager was changed to pop up automatically, which is probably a good idea to make sure most users update security stuff quickly.

However, some of us old ubuntu users could find it a tad annoying, is there a way to revert to the previous behavior?

---

### Post by anjilslaire on 2009-04-28
Good question. I noticed this too, and prefer an icon on the task bar.

---

### Post by Brandon Williams on 2009-04-28
There are already a few threads related to this just from the past day or two. Please search the forum for an answer before posting!

The behavior is intentional. Read the Jaunty release notes for more information and a configuration setting that reverts to the old behavior.

---

### Post by freonchill on 2009-04-28
if it is not showing up in the update manager by default, close it

ALT+F2, type in "update-manager -d"

then you will have an button to click to update to jaunty

---

### Post by anjilslaire on 2009-04-30
> **Brandon Williams said:**
> There are already a few threads related to this just from the past day or two. Please search the forum for an answer before posting!

The behavior is intentional. Read the Jaunty release notes for more information and a configuration setting that reverts to the old behavior.

Yes, we realize it's intentional. No need to be rude, or quote the "please use search before asking" to members who've been here far longer than yourself.

If you want to be helpful, please post the information rather than "RTFM", thanks.

The information is here, btw:
[http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates](http://www.ubuntu.com/getubuntu/releasenotes/904#Change%20in%20notifications%20of%20available%20updates)
> 
Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```


---

### Post by anjilslaire on 2009-04-30
> **freonchill said:**
> if it is not showing up in the update manager by default, close it

ALT+F2, type in "update-manager -d"

then you will have an button to click to update to jaunty
Appreciate the effort, but this is about the notification system itself used by Jaunty, not the upgrade from Intrepid to Jaunty.

---

### Post by SentientFluid on 2009-04-30
> **anjilslaire said:**
> Yes, we realize it's intentional. No need to...quote the "please use search before asking" to members who've been here far longer than yourself.

From Section II - Technical Support Policies of Ubuntu Forums Code of Conduct:> Searching the Ubuntu Forums is a quick way to see if someone has had your issue and if it has been answered. In a forum as large and active as this one, there's a good chance your question has been answered before, and you can get the information you want quickly. 

Not to be rude but one would think that long time members would be aware of this and realize that searching before asking is not only a faster way to find a response, but also eases the load on those who regularly respond to posts.  Consider it basi forum manners.

---

### Post by leonardo_neo on 2009-04-30
This is what I found from the Ubuntu 9.04 release notes.....

> Change in notifications of available updates

Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

gconftool -s --type bool /apps/update-notifier/auto_launch false

Hope this helps you :)

---

### Post by rajeev1204 on 2009-04-30
> **leonardo_neo said:**
> This is what I found from the Ubuntu 9.04 release notes.....



Hope this helps you :)

That fix doesnt work.For me atleast.I see the icon alright,but it doesnt pop up automatically like it used to.

---

### Post by anjilslaire on 2009-04-30
> **SentientFluid said:**
> Not to be rude but one would think that long time members would be aware of this and realize that searching before asking is not only a faster way to find a response, but also eases the load on those who regularly respond to posts.  Consider it basi forum manners.

Yes, I'm aware, and I use Search regularly :) The user simply came across as "Go find it yourself." If he was aware of multiple threads and the answer, its much more polite to say so, and also give some links.

I just happened upon the OP's comment and agreed that it was annoying as a matter of opinion. 
What we got was "You need to read and search! The answer has already been given!", to paraphrase.
Going by that standard, I'll assume that this user has read & knows everything he needs, and as such I'll refrain from responding to his threads.

Apologies to all for hijacking this topic; I'll get off my soapbox now, and leave it well enough alone.

---

### Post by vexorian on 2009-04-30
I did realize it was intentional, I was just asking if there was a way to change it. For some reason when reading the release notes I only bothered to check the hardware support parts. The 'search for similar threads' thingy did not give me any result.

After three days of use I actually like the new update manager, it only shows security updates and stops bothering you when you close it.

---

