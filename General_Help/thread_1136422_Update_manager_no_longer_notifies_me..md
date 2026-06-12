---
title: "Update manager no longer notifies me."
date: 2009-04-25
forum: General Help
---

### Post by DarkDancer on 2009-04-25
Hi All!

I installed 9.04 about a week before final release and all went relatively smoothly, until on release day I checked (just for grins and giggles) and there were a bunch of packages in it waiting to be updated. I noticed that there was an update to the update manager, so I thought that might fix it, but when I checked tonight, even though there was no notification, it updates. How do I make it tell me when the updates arrive?

---

### Post by conscious on 2009-04-25
See [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

### Post by DarkDancer on 2009-04-26
Thanks... ;)

---

### Post by GreyGeek on 2009-04-27
Interesting comment by Mark Shuttlesworth about this topic: 

 Bug #332945:
[Jaunty] Update Notifier icon would provide useful status information
Mark Shuttleworth wrote on 2009-03-27: (permalink)

Nothing like a healthy debate. But please let's keep it stylish, informative and pleasant. There are some comments here that are not very Ubuntu. Please take a breath, and pour some water on any flames you're about to throw. They don't help.

**Now, some folks are saying "why wasn't I consulted about this change?". But think about this. You probably weren't directly consulted on a million other changes that make up this release. Most of those came from upstream, some came from Debian, and many were made right here in Ubuntu. We have a lot of very public, open, participative forums, but nobody can be in every forum, on every thread, in every meeting, on every channel. The fact that there is a change here that surprises you isn't grounds for shouting out that the change itself was made in bad faith.**

Also, the fact that this change was driven by a team at Canonical (including me) is no reason for conspiracy theories or abuse. Canonical drives a huge amount of changes, mostly in proportion to the person-hours contributed, but we invest Ubuntu alongside the rest of the community, and we work hard at making that relationship a success. **I've personally [COLOR="Red"]spent[/COLOR] quite a lot sponsoring some of the people who are most vocally upset here, to come to UDS's, so I'm not all that sympathetic to them saying that Canonical doesn't make an effort to hear their voices.**

Now, on this specific issue.

**We have good usability information that says that notification areas are swamps. They are swamps on Windows, and swamps in all the Linux distributions.** They inevitably become dumping grounds for "things that don't fit". Users dislike them, and application vendors abuse them. Most of all, average users don't understand the majority of the information that is presented there, because it's all inconsistent and often arbitrary. We want Ubuntu to be better than that. So we have been studying the panel indicators and trying to figure out what we can do to make it better.

Now, this is highly sensitive stuff. People who DO understand something there, are often very attached to it, because it's very visible. We're going to cause a lot of disruptions, and we might get the odd thing wrong.

But, we're not afraid of making bold moves. Ubuntu itself was a bold move, and has attracted a fair amount of criticism for its very existence, but that didn't stop us. **If we want to transform the Linux desktop from where it is today, to something that Apple will feel obliged to emulate in parts, we are going to have to make bold moves and big changes, and those will cause distress.** If we're right, the result will be fantastic, and the changes will be embraced by other distributions and upstream. If we're wrong, they won't.

We are focusing our design and user experience attention on the elements of the experience that span multiple applications. Notifications, and the notification area, are two such elements. We developed a framework for "how applications engage with the user when they don't have the focus". We tested those ideas, and we think they are worth taking some risks to achieve. MPT documented that conceptual framework, it was discussed, and now we are getting down to work.

Back to the notification area. **If we're going to clean up the panel and the notification area, we should start with the system pieces. Those include the restart-required icon, and the updates-available icon. So those are gone in 9.04.** There are ways for experts to have that functionality if they want it. Most of the folks on this bug are squarely in the expert group, and I won't be offended at all if you decide to have those icons in your notification area. But I do think that the approach we are taking is better to spread the arms of the community open even wider, and draw in folks who are experts in a million things OTHER than code, translations, and open source project matters. Our friends and family.

**I'll ask you all to be excellent to each other.** This bug is no place for name-calling and slander. [COLOR="Red"]Everyone here, including those most upset, and including me and the others on the team that are driving these changes, devotes our lives to the same cause: getting free software everywhere. Treating each other poorly is a step backwards.[/COLOR]

---

### Post by jngrim on 2009-05-18
I have installed jaunty as well and now I do not get nofified of any updates at all.  IS there a way to turn this on? I have updated all the settngs but when I launch update manager after 2-3 day, I always have updates available.  How can I fix this?
thanks

---

### Post by kostkon on 2009-05-18
> **jngrim said:**
> I have installed jaunty as well and now I do not get nofified of any updates at all.  IS there a way to turn this on? I have updated all the settngs but when I launch update manager after 2-3 day, I always have updates available.  How can I fix this?
thanks
The update manager pop-ups daily only if there are security updates. In all other cases, it pop-ups only every 7 days.

---

### Post by adrianx on 2009-05-18
This worked for me:
[http://ubuntuforums.org/showpost.php?p=7182124&postcount=2](http://ubuntuforums.org/showpost.php?p=7182124&postcount=2)

---

### Post by jngrim on 2009-05-18
this does work either...I still show pulse audio update available only when I open the update manager.

---

