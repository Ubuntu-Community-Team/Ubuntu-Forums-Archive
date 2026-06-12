---
title: "Conky is autostarting - don't think it should be"
date: 2009-06-10
forum: Desktop Environments
---

### Post by vrothdar on 2009-06-10
Background:
[LIST]
[*]I'm running the CLI install from the alternate CD which I'm building up to a full system to suit my needs.
[*]I'm using XFCE for my desktop.
[*]I had conky autostarting and displaying correctly without any problems until last night.
[/LIST]

After some tinkering last night conky has started displaying behind the wallpaper. I know about the workarounds using sleep but would like to try and figure out why the behavior has changed to improve my understanding of conky.

Firstly I tried changing own_window_type from desktop to normal (without any hints set) to ensure conky was definitely working and that I hadn't borked my conkyrc file. That all worked fine.

Next I wanted to stop it from autostarting so that I could start it manually with own_window_type desktop to check conky displays correctly when started after the rest of the desktop has loaded. I went to session and startup to remove it from the autostart list but found that it wasn't there.

[LIST]
[*]If it's not in that list of applications why is it autostarting?
[*]Might this be related to conky starting to display behind the wallpaper?
[/LIST]

Thanks in advance for any help.

---

### Post by ushimitsudoki on 2009-06-10
I had some autostarting issues.

I cleared ~/.cache/sessions and that handled that (assuming you check the "standard" spots as well)

I also had some problems with conky opening up wrong. I wish I would remember what I did, but I didn't document it. I remember fiddling with own_window_type, and I ended up with it on "normal" (it was originally override *I THINK*)

---

### Post by vrothdar on 2009-06-10
Clearing the sessions cache stopped conky autostarting.

I tried using own_window normal and own_window_hints to make it look like own_window desktop and that worked fine and seems like a much more elegant solution than scripts to delay conky starting that I've seen recommended elsewhere.

Thanks for the help.

---

