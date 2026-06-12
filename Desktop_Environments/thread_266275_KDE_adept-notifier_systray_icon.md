---
title: "KDE adept-notifier systray icon"
date: 2006-09-27
forum: Desktop Environments
---

### Post by smjor on 2006-09-27
Hello all.

I need some clarification on a (for me) very annoying issue.

I run Kubuntu 6.06, and it's all working just the way I want it to, except for one thing; the adept-notifier systray icon.

On my computer it behaves like this:

1. When I log in, the green circle indicating that no updates are needed, pops up the systray, and stays there, until I log off. This is typically the case when I log in for the first time after a reboot._Sometimes_ it disappears when I do a manual "apt-get update && apt-get upgrade".

OR

2. When I log in, the green circle indicating that no updates are needed, pops up in the systray, and stays there for approximately 10 seconds, then disappears.

OR

3. When I log in, the green circle indicating that no updates are needed, pops up in the systray, and stays there for approximately 1 second, then disappears.

OR

4. When I log in, I can not see the icon at all.

Let me specify a few things. The adept-notifier process is _always_ running (I an see the process in the system guard, or by executing htop etc.), regardless of whether the icon is visible. Furthermore, the icon indicating that there are updates available always pops up as it should, so this whole issue is purely cosmetic, AFAIK.

I log in locally, and sometimes remotely via freenx, behavior is the same.

What I want to know, is how the "no updates needed"-icon is _supposed_ to work. Why does it behave differently all the time. I HATE this inconsistent behaviour.

Has anyone experienced something similar? Is there a fix for this?

---

### Post by smjor on 2006-09-29
Bump!

---

### Post by asimon on 2006-09-29
I thought the notifier icon will only show up (i.e. stay there longer then a couple of seconds) if there are updates waiting.

When I log in it always pops up. But if there are no updates, it vanishes after a couple of seconds.

---

