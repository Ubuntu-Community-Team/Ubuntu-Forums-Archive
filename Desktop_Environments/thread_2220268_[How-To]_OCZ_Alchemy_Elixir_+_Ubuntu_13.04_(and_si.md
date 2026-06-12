---
title: "[How-To] OCZ Alchemy Elixir + Ubuntu 13.04 (and similar)"
date: 2014-04-27
forum: Desktop Environments
---

### Post by Yep_Yepyep on 2014-04-27
EDIT: Sorry, it should say Ubuntu 14.04 in the title, but this works for any distro.
Could an admin change the title? If you want you can also merge this thread with the old closed one, so users find the soltuion when they google it ;-)

Hi everyone!

I have an Alchemy Elixir keyboard, and the multimedia keys (play, stop, skip etc.) dont work out of the box.
Theres only one thread I found regarding this issue, it doesnt contain a solution and is closed already:
[http://ubuntuforums.org/showthread.php?t=1260381&highlight=ocz+elixir](http://ubuntuforums.org/showthread.php?t=1260381&highlight=ocz+elixir)

To solve this, follow the steps in the first answer in this thread:
[http://askubuntu.com/questions/232564/sharkoon-drakonia-gaming-mouse-doesnt-work-at-all](http://askubuntu.com/questions/232564/sharkoon-drakonia-gaming-mouse-doesnt-work-at-all)
When asked if you want to set up kexec boot. select no.
Dont follow the cleanup steps, this will break your system. However, you can remove the ~/source folder.

Funny thing: this tutorial is for an sharkoon drakonia gaming mouse. this mouse (and many other) works out of the box on any distro above 12.04, while this keyboard still doesnt ;-)
Also, I heard changing max_hid_usage as advised would be not a good thing to do, but did not find any info why it isnt, maybe someone knows more about this?

Hope I could help someone!

---

