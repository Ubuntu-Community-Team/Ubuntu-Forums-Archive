---
title: "segfaults that are NOT specific to a single program"
date: 2009-04-07
forum: General Help
---

### Post by abben on 2009-04-07
This is all leading to a question at the end.

I use Xubuntu, but my computer is pretty old so I am extremely conscious of resource consumption, so I use awesomeWM and tend to use lightweight programs whenever possible.

Over and over again I see people report segfaults in this forum, and the response almost universally is to find the mistake in the program that must have lead to the segfault or file a bug report. But what about the case where a segfault is *not* caused by a buggy program?

Some specific things I know about this kind of segfault...

- They tend to be more likely, the more resource intensive the activity (a browser with few tabs vs that same browser with many tabs)
- In some cases, if I attempt to re-open a program that has segfaulted during the current session, it will segfault instantly, and continue to do so for the rest of my session.
- Its almost always in immediate response to some action, sometimes trivial (like right clicking)
- In some cases, I can re-open a program without it segfaulting, but performing the same action that preceded the previous segfault again leads to a segfault.
- An action that has never lead to a segfault in the past (like hitting CTRL-T to open a new tab in Opera), can lead to a segfault in the future.
- Similarly, an action that has caused a segfault in the past can be done perfectly fine without resulting in a segfault.
- For me, this experience has been **the same** across multiple installs of multiple iterations of Ubuntu, Xubuntu, and Debian.
- If I restart my computer, the segfaulting issue tends to go away.

Given these circumstances, I **do not think the problem I've encountered is specific to a given distribution of Ubuntu or given piece of software**. It probably means that my little old computer with 256mb of ram just isn't good enough, right?

I can live with this if I have to, but the problem for me is specifically the segfaults that recur whenever I try to run a program, which effectively force me to restart if I ever want to use that program again. 

So, why is this happening, and how can I cause these recurring segfaults to go away *without* restarting my computer?

And can you tell me anything more about segfaults than the fact that they involve accessing unallocated memory that might help me understand them?

(yes I've read the wiki article, and searched here and on google for similar topics; responses are universally about segfaults in particular programs)

thanks much for the help

---

### Post by abben on 2009-04-07
bump

---

### Post by 3rdalbum on 2009-04-07
Every time you get a segfault, the kernel prints "traceback" information to the kernel log. You can view it in Gnome System Log (under "messages" or "kern.log") or by typing "dmesg" into a terminal.

The traceback tells you the system calls that lead to the program crash. You might get some particular information that could help. The other thing you can try is running the program from a terminal and seeing if any error messages are output.

I have observed the behaviour you mention, so no you're not crazy :-)

---

### Post by abben on 2009-04-07
> **3rdalbum said:**
> Every time you get a segfault, the kernel prints "traceback" information to the kernel log. You can view it in Gnome System Log (under "messages" or "kern.log") or by typing "dmesg" into a terminal.

The traceback tells you the system calls that lead to the program crash. You might get some particular information that could help. The other thing you can try is running the program from a terminal and seeing if any error messages are output.

I have observed the behaviour you mention, so no you're not crazy :-)

I'll keep that in mind for when I get back home today. I wonder what I could be doing so consistently across installs that would lead to this happening.

If there are any other thoughts, do tell. I'm specifically interested in why restarting seems to fix things, and if there is some specific aspect to restarting my computer that I can emulate in a simple terminal command to stop the segfaults.

Does anyone know if, say, a memory management program might help me?

---

### Post by change_mode on 2009-04-07
> **abben said:**
> 
I use Xubuntu, but my computer is pretty old so I am extremely conscious of resource consumption

[...]

- They tend to be more likely, the more resource intensive the activity (a browser with few tabs vs that same browser with many tabs)

You're not running out of memory, right? That would cause segfaults.

---

### Post by abben on 2009-04-07
> **change_mode said:**
> You're not running out of memory, right? That would cause segfaults.

I absolutely am running out of memory (at least I think), and I am vaguely aware that this has everything to do with my segfaults.

But my segfaults are unpredictable enough that I'm sure there are at least a few cases where I've had sufficient memory but had segfaults anyway. And I am certain there are cases where I've had segfaults with one program, but then was able to open a whole bunch of other programs without problems (for example, Opera has segfaulted before, but then I would be able to use Epiphany, burn cd's, run Gimp, without problems.

So, while my answer to that is yes, I'm not sure if that in itself accounts for why things segfault so unpredictably, or if that should mean there are no workarounds.

Does anyone know if there is a memory management program for ubuntu like there are for windows? Perhaps that would help prevent segfaults?

---

### Post by change_mode on 2009-04-07
What do you mean by memory management program? You can use top / htop to see how much memory your applications use.

If you want to test if the segfaults are directly related to running out of memory, you can make your swap partition big enough that you won't run out of memory. Maybe that's enough to solve your problem.

---

### Post by Yashiro on 2009-04-07
It's not likely your crashes are caused by having only 256Mb of ram. You don't need an external memory manager.

If you are adamant it's not a software caused issue, then it's more likely you have some faulty hardware.

---

### Post by abben on 2009-04-07
> **Yashiro said:**
> If you are adamant it's not a software caused issue, then it's more likely you have some faulty hardware.
Yeah, that's what I was thinking. If that's the case there is really nothing I can do. If it was caused by software, I imagine it would be some low-level OS thing, or it would somehow related to something I always do across every install I've ever had, such as configure my sound card (but that sounds silly).

A hardware issue would make sense, though.

> What do you mean by memory management program? You can use top / htop to see how much memory your applications use.

I mean a memory management program that's capable of *clearing memory* that was previously allocated but no longer needed, like from memory leaks.

---

### Post by abben on 2009-04-08
bump again. Is it reasonable to think segfaults can be a hardware problem?

---

