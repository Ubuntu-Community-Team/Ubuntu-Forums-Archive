---
title: "&quot;Ultimate&quot; &lt;Alt&gt;&lt;Shift&gt;Tab problem"
date: 2010-09-16
forum: Desktop Environments
---

### Post by Fintican on 2010-09-16
Hi everyone,

the basic problem here is that <Alt><Shift>Tab combination is not working for shifting windows in reverse direction while <Alt>Tab for normal direction works.

There are already few threads about this. But I am starting this new one because none of them helped me.

I have Compiz installed and using Application Switcher.
I have <Alt><Shift>Tab set under Prew_window in preferences of Application Switcher.
I have searched through all shortcuts in Compiz using its build in search with "Settings value" checked and there is no other binding to this shortcut.
I have the combination set in gconf-editor -> apps -> metacity -> global_keybindings -> switch_windows_backward
I tried to restart after each new setting (even probably not necessary)

This is all other threads were advising to cure the issue but still not working. One more thing which seems important to me:

I am using two different keyboard layouts and <Alt><Shift> to switch between them.

I am running fresh install of 10.04 ubuntu and I'd like to get this feature run since I miss it from winXP (Sorry, I had to use this word :) )

Pls help or advise where to look for it, thnks

---

### Post by Fintican on 2010-09-17
I have spotted where is the problem. What happens when I press <Alt><Shift>Tab is not only shifting to the next_window but also layout is switched. So this combination is decomposed to <Alt><Shift> to change layout and <Alt>Tab to shift next_window.

I have the same in win so I tried it there and I found out this difference. Shortcut <Alt><Shift> for layout switch in ubuntu does its job immediately after combination is pushed down (OnKeyDown). In Win on the other hand it has to be pushed down and released up without interupting by other key (OnKeyPressed). Therefore in Win these two shortcut don't interfere each other while in Ubuntu they do.

So it looks like end of the story. This is neither a bug nor configuration problem. It's just "unsuitable" implementation of <Alt><Shift> shortcut. I wrote unsuitable in "" because maybe there is a reason why it is so.

Thus a solution is to choose another shortcut for layout switching.

---

### Post by kroiz on 2010-10-17
Thanks Fintican,
If so then anybody with more then one keyboard layout (most of the world) would suffer from this issue.
That is a lot of people :)
I see no reason this could be handled the way windows handle it...
Does someone knows how this could be fixed?

---

### Post by ashnur on 2010-12-03
why the SOLVED in the title? it isn't solved, we just find out that why it is broken. do anyone know any solution?

---

### Post by kroiz on 2010-12-03
> **ashnur said:**
> why the SOLVED in the title? it isn't solved, we just find out that why it is broken. do anyone know any solution?
Sorry, I did not find a solution...
and I agree about the solved status ... on the other hand it probably attract more ppl to the thread :)

---

### Post by hasenj on 2011-01-28
Thanks for posting this, I've been struggling with this for a while and it was driving me crazy.

The work around is easy though, I just set the previous window short cut to "alt-capslock"

Now, one important note, my capslock is disabled.

[IMG]http://i.imgur.com/fxiJi.png[/IMG]

---

