---
title: "can't log into xfce but can to gnome"
date: 2008-06-18
forum: Desktop Environments
---

### Post by fishwebby on 2008-06-18
Hello,

I'm having a problem with the Xubuntu desktop - I'm running Ubuntu 8.04 using Gnome, and all is working nicely. I thought I'd try out Xubuntu, so I did this:

sudo apt-get install xubuntu-desktop

rebooted, selected xfce as my session and all nice. I think I prefer xfce as it seems cleaner. However, the problem started when I got curious about compiz. I installed it and all my window borders disappeared. I've since uninstalled it and I've got my window borders back, and I can still go into Gnome ok, but if I try and select xfce as the session it just goes to a blue screen after the login page and doesn't do anything.

So I think that compiz has left some configuration that doesn't work somewhere, so what I want to do is completely remove compiz/xfce/xubuntu including all configuration (whilst keeping gnome) then reinstall it all as I know it works. How can I do that?

Thanks
Dave

P.S. Much as I'd like to see what compiz looks like, I'm happy to do without it if it kills my setup like that!

---

### Post by mali2297 on 2008-06-18
Delete the directories ~/.config/xfce4, ~/.config/xfce4-session and ~/.cache. It should clear most of your xfce settings.

---

### Post by fishwebby on 2008-06-19
Hello

That seems to have sorted it - I reinstalled xubuntu-desktop and now I can log in using xfce - thank you very much! :-)

Alas now I seem to be experiencing [this bug]("https://bugs.launchpad.net/ubuntu/+bug/221657"), but as it's confirmed as a bug I guess I'll just have to wait until it gets fixed...

Cheers
Dave

---

