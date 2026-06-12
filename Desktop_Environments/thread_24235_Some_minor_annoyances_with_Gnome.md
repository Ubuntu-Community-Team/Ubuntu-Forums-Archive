---
title: "Some minor annoyances with Gnome"
date: 2005-04-06
forum: Desktop Environments
---

### Post by trash-can on 2005-04-06
Hi!

I just recently switched from Debian&KDE to Ubuntu Hoary. So far, no regrets :) But I'have discovered some problems which are a bit annoying.

[list]I have always been using gkrellm to keep an eye on how system behaves. It's a great little app and I have tried other tools(gdesklets & karamba & torsmo), but have always switched back to gkrellm. **The problem is:** when I press "Show Desktop" button also gkrellm is minimized and if activate or open other app window, there is no way to get back gkrellm :([/list]
[list]Reading through [Ubuntu Starter Guide](http://ubuntuguide.org/) I noticed that there was mentioned nautilus special location "applications:///", unfortunately It seems to be missing in Gnome 2.10 along with some other special locations like start-here:///, preferences:///. Well, maybe it is Gnome 2.10 feature?[/list]
[list]Nautilus randomly hangs when I try to view mp3 or ogg file properties. It happens more frequently with ogg, but so far I have not found any reason or pattern for this problem, maybe I should file a bug?
[/list]

---

### Post by Burgundavia on 2005-04-06
2. Applications:/// was removed due to a change in menu makeup in 2.10. Gnome switched over to the Freedesktop.org spec, and removed applications:/// as it was for the old spec.

3. Try and reproduce it with one ogg or mp3 file and then file a bug.

Corey

---

