---
title: "Integrating the Forums with Launchpad"
date: 2007-03-14
forum: Forum Feedback &amp; Help
---

### Post by beuno on 2007-03-14
I'm trying to follow up on an email I sent to the launchpad-users mailing list on integrating the forums and launchpad: [https://lists.ubuntu.com/archives/launchpad-users/2007-March/001184.html](https://lists.ubuntu.com/archives/launchpad-users/2007-March/001184.html)

The main idea would be to show "related bugs" in forum threads.
I think this can be accomplished without any major changes using "tags".
Users can add bug numbers as a "tag" which is easy enough, and then a small script can grab that bugs information from launchpad.

Launchpad currently has a "text-mode" method to retrieve bug information ([https://launchpad.net/bugs/8242/+text)](https://launchpad.net/bugs/8242/+text)), which could be easily parsed in any scripting language.

Then users could see what bugs are related to that specific thread, and what status it has, as it might have been fixed when they land on the thread. 

This would save the users the time of scrolling through 8 pages to find out what that it has been fixed.

Some thought has to be given on caching information so launchpad doesn't get flooded.

Note that this can be extended to launchpad specifications, answers, etc.

---

### Post by mac.ryan on 2007-03-14
i am a rather recent user of ubuntuforums and launchpad. I like the idea, and I have some additional comments:
[LIST]
[*]I would find important, then, to have an additional flag for forum threads, signaling if a workaround has been found to the problem. This would be helpful when browsing launchpad, as the users might be interested in those threads, rather than in those where the problem is simply debated but a solution has not been found...
[*]I would find equally important that when in launchpad a bug get the status of "fixed" a message would be automatically appended to all the threads concerned. I believe this would be user-friendly for those new users who might even ignore the existence of launchpad...
[*]The only doubt I have about the idea of integrating the two platform is that this integration might be too "subtle" for new users, who might simply overlook to this feature. In this case the integration would miss the goal of limiting the "has it been fixed yet?" messages.
[*]The manual linking (via tags) sounds a bit time-consuming, little user friendly, and badly susceptible of typos...[/LIST]

---

### Post by beuno on 2007-03-14
> **mac.ryan said:**
> [*]I would find important, then, to have an additional flag for forum threads, signaling if a workaround has been found to the problem. This would be helpful when browsing launchpad, as the users might be interested in those threads, rather than in those where the problem is simply debated but a solution has not been found...

This has been proposed to launchpad lists as you can see in the mailing list, it really depends on whether they have time to implement it, and if they find it useful enough.

> **mac.ryan said:**
> [*]I would find equally important that when in launchpad a bug get the status of "fixed" a message would be automatically appended to all the threads concerned. I believe this would be user-friendly for those new users who might even ignore the existence of launchpad...

The proposal includes marking the status of a bug.

> **mac.ryan said:**
> [*]The manual linking (via tags) sounds a bit time-consuming, little user friendly, and badly susceptible of typos...

I don't see any other way. Do you have any better ideas to do this?

---

### Post by mac.ryan on 2007-03-15
> **beuno said:**
> I don't see any other way. Do you have any better ideas to do this?

Not straightforward (i.e. might be too complicated and demanding in terms of computational power, to be implemented).

However, if I can dream with my eyes open, I can see - beside the forum editing window - a list of "related bugs" that narrows down while I am typing. This could be done with tagging the bugs in launchpad, and confronting those tags with recurrent words in the post being edited. In the most perfect of the worlds, tags within launchpad would also have a vocabulary of synonims/close words, so that for example, if in a post somebody writes insistently "sound", the system will also considers bugs tagged as "alsa" or "alsa mixer".

The possibility to manually enter the related bug should be still there, though.

---

