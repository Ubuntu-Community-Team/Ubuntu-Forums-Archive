---
title: "Any known good way to save X application state between X sessions?"
date: 2008-08-30
forum: Desktop Environments
---

### Post by adamantivm on 2008-08-30
Hi,

I think I misunderstood this but I heard a while ago someone said: "Aren't yo usung <some-tool> to keep your applications running when you restart X??", like it was a very known and common thing to do.

I find myself now with the need to have something like that working, but I can't find anything like that mentioned anywhere, aside from very specific user tricks via script hacking. Is there something of the sort that already exists?

The particular reason I'm trying to get applications to outlive X sessions is because I'm about to set into configuring my laptop to work with in a dual-monitor configuration, and I want to be able to switch between 2 monitors and 1 monitor without having to close all my applications in the process! In my previous attempts to do this, the only way I had found to be able to do this was by swapping the xorg.conf file and restarting X - which would kill all my applications if I don't have a solution like the one asked for.

Ok, enough ranting about. I hope I can get some guidance from the community.

Thanks in advance!

Julian

---

### Post by adamantivm on 2008-09-06
So, I had mis-understood my colleague of course. As I had suspected, she was talking about 'screen' - which is a great idea, only for console sessions.

Regarding my need, turns out xrandr 1.2 is out. This allows switching resolution and enabling/disabling screens without stoppping any X applications.

---

