---
title: "What does &quot;Triaged&quot; mean in Launchpad?"
date: 2011-05-31
forum: Forum Feedback &amp; Help
---

### Post by nrundy on 2011-05-31
When a bug gets labeled "Triaged" on Launchpad what exactly is this telling people?

---

### Post by iclestu on 2011-05-31
> **nrundy said:**
> When a bug gets labeled "Triaged" on Launchpad what exactly is this telling people?

guessing it just means 'prioritised'

---

### Post by uRock on 2011-05-31
It means the bug has been triaged, which means the bug squad has assigned an importance value.

---

### Post by nrundy on 2011-05-31
Well the bug used to say "High". Doesn't High communicate the importance value? Why would one labeled HIGH be changed to Triaged?

---

### Post by uRock on 2011-05-31
High falls under importance. Triaged falls under Status. If you can provide a link to said bug, then I can help you distinguish what is happening.

---

### Post by nrundy on 2011-05-31
Thanks uRock :)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

---

### Post by uRock on 2011-05-31
The bugs were already assigned to a team back in April, so maybe this means someone from that team is actually working on the issue. It is hard to tell.

---

### Post by nrundy on 2011-05-31
> **uRock said:**
> The bugs were already assigned to a team back in April, so maybe this means someone from that team is actually working on the issue. It is hard to tell.

I know its hard to tell. That's why I posted. What the heck does triaged mean? does this mean it's been set aside because there's too many other bugs to deal with? Does it mean it has been given more attention than other bugs?

---

### Post by uRock on 2011-05-31
> **nrundy said:**
> I know its hard to tell. That's why I posted. What the heck does triaged mean? does this mean it's been set aside because there's too many other bugs to deal with? Does it mean it has been given more attention than other bugs?

You should post in the bug report asking the fella who changed it what he meant by it. In my mind's eye, triage would mean that a priority has been set and someone will get to it in it proper turn. With its importance is set to high, I would say that someone already is or will soon be working on it.

---

### Post by tgm4883 on 2011-05-31
Triaged can mean different things in different projects, but generally means there is enough information for a developer to work on the bug. This differs from Confirmed, since confirmed can mean someone reproduced the bug, but there isn't enough data (logs, dumps, etc) to work on.

---

### Post by tgm4883 on 2011-05-31
Found what I was looking for

[https://wiki.ubuntu.com/Bugs/Status](https://wiki.ubuntu.com/Bugs/Status)
> Triaged:

A member of UbuntuBugControl believes that the report describes a genuine bug in enough detail that a developer could start working on a fix. (also see tip below)

Use this when you are confident that it should be looked at by a developer and has enough information

While not a requirement a bug's Ubuntu task status will be Triaged before any upstream forwarding occurs

---

### Post by nrundy on 2011-05-31
> **uRock said:**
> You should post in the bug report asking the fella who changed it what he meant by it. In my mind's eye, triage would mean that a priority has been set and someone will get to it in it proper turn. With its importance is set to high, I would say that someone already is or will soon be working on it.

I didn't want to "pollute" the bug comments with something not really related to the bug.

---

### Post by nrundy on 2011-05-31
> **tgm4883 said:**
> Found what I was looking for

[https://wiki.ubuntu.com/Bugs/Status](https://wiki.ubuntu.com/Bugs/Status)

great stuff. thanks a lot for this.

Does this indicate at all that the bug has been identified? Or not necessarily?

---

### Post by tgm4883 on 2011-05-31
> **nrundy said:**
> great stuff. thanks a lot for this.

Does this indicate at all that the bug has been identified? Or not necessarily?

Not necessarily. It means someone on the bug team thinks that it has enough information for the Developer to start looking at it. That doesn't mean that the developer won't need more information to fix it. It doesn't even mean that a developer has looked at it yet.

For example take a basic error from some program that someone created a bug report for. The bug won't reach 'triaged' status until it has the _**minimum**_ amount of data needed for that. (likely program logs, system logs, trace, etc)

---

### Post by cariboo on 2011-05-31
Just to add to the discussion, this is from the [Launchpad blog:]("http://blog.launchpad.net/general/of-bugs-and-statuses")

> Triaged (Keep This Bug On The Radar)
This is an intermediate status that can be used to distinguish community-confirmed bugs from bugs that the official QA team has acknowledged and plans on working on. Many projects don’t need a separate stepping stone and developers can pick bugs directly from Confirmed into In Progress. At this point, we are sure that a) the bug has been reproduced and established b) developers have acknowledged.

---

