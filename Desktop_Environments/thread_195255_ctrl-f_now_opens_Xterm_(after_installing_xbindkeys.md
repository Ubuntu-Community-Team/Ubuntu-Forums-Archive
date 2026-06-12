---
title: "ctrl-f now opens Xterm (after installing xbindkeys)"
date: 2006-06-12
forum: Desktop Environments
---

### Post by DeShark on 2006-06-12
Hello there... I recently decided that it'd be useful to start assigning keyboard shortcuts to various programs (such as firefox). I heard that xbindkeys could do the job so I decided to install it. So it was the usual apt-get job and I managed to install xbindkeys and xbindkeys-config. The good news is that I was able to setup my shortcuts... However, every time I press ctrl-f an xterm window pops up. I'm not sure if this is anything to do with xbindkeys, it could be to do with one of its dependencies, either way, it's blinkin' annoying. I go to use the find-as-you-type feature in firefox and now an xterm window pops up. Anyway... I was wondering if any of you clever chaps had any ideas about what might have caused this. Or, more importantly, if there's any way to undo it.

Cheers, Dan.

---

### Post by DeShark on 2006-06-13
Anyone?

---

### Post by Gravecat on 2006-06-13
I had the same problem, but thankfully the solution seems pretty simple.

If you check "sudo xbindkeys-config", there should be three default entries in the list, as well as any other ones you've set up. If you just delete the default entries then save it, that should work -- fixed it for me, at least. :)

---

### Post by DeShark on 2006-06-13
I'd already done that... and I'd uninstalled xbindkeys. But anyway, I reinstalled it and fiddled around. I've no idea what I did but it works now. There was lots of deletion and re-saving and applying changes... The problem's solved, but I wouldn't know how to help anyone else I'm afraid. Thanks for your help though. It was beginning to Reeeeally annoy me.

---

### Post by Ryzzen on 2007-02-21
I'm having this same problem now, except uninstalling and re-installing didn't help. :|

---

### Post by orawax on 2007-03-26
gedit ~/.xbindkeysrc

# set directly keycode (here control + f with my keyboard)
# "xterm"
#  c:41 + m:0x4

---

### Post by pavel989 on 2007-12-30
yea i have this same issue and its really annoying, has anyone found a solution?

---

### Post by danthesk8er on 2007-12-31
Well I had the same problem after installing xbindkeys, I tried removing it and that didn't help, so I reinstalled it. I then used xbindkeys-config and saw that 2 things were bound to the xterm. I simply deleted those entries and now my ctrl-f works fine again. Brings up searches like it is suppose to. xbindkeys is still installed and running and I have no problems. I am using Gusty Gibbon 7,10

---

### Post by pavel989 on 2008-01-01
actually i removed xterm, being tha ti dont use it and nothing i use depends on it, restarted, and it atopped  doing that

---

