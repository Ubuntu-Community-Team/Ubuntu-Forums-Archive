---
title: "Login/Desktop Environment fails after trying to enable &quot;Magnify&quot; effect in Compiz"
date: 2008-12-03
forum: General Help
---

### Post by Halo_gg on 2008-12-03
I was playing around with compiz and compiz manager to find the best effect that suits me this morning.

Things always happen when you are having fun - I was trying to enable "Magnify" effect and a window pop up saying conflicts with existing effect (or something like that), I clicked the button to resolve conflict. Now bad thing happend! The whole screen went dark with "colourful" thin vertical strips.

I have tried to restart and login with different types of sessions - as soon as I login, the screen flashes and the system kicked me out to the login screen again! Apparently only the "Failsafe Terminal" works. 

Any ideas what I can do to recover to the previous working desktop environment?

Thanks,
Halo_gg

---

### Post by Wartender on 2008-12-03
dude that same exact thing happened to my mom's laptop (except i had clicked ignore conflicts.) what i did was a clean re-install. (i used the live-cd to format the ext partition and then just reinstalled it onto that partition, you can save your settings and stuff by copying your home folder somewhere i guess though)

---

### Post by Halo_gg on 2008-12-03
> **Wartender said:**
> dude that same exact thing happened to my mom's laptop (except i had clicked ignore conflicts.) what i did was a clean re-install. (i used the live-cd to format the ext partition and then just reinstalled it onto that partition, you can save your settings and stuff by copying your home folder somewhere i guess though)

Thanks for sharing, Wartender.

Re-install is probably the last thing I would do. I shall see if any linux guru here that may be able to offer some advice or even know how to solve this problem in the shell environment.

Guys and gals, my hand is still up...

---

### Post by kawaji on 2008-12-03
The issue has been reported to launchpad,
See the comments for solutions. 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311)

---

### Post by 9ico on 2008-12-03
[nfl jerseys](http://www.9ico.com/)

---

### Post by Halo_gg on 2008-12-03
> **kawaji said:**
> The issue has been reported to launchpad,
See the comments for solutions. 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311)

Thanks for the link, kawaji! I will try it out tonight! Cheers!:popcorn:

---

### Post by eternalnewbee on 2008-12-04
you could also press **ALT-F2** and enter ```
metacity --replace
``` and go to: **Main Menu > System > Preferences > CompizConfig Settings manager** and disable the plugin.
After that press **ALT-F2** again and ```
enter compiz --replace
``` and see if that solves your issue.

---

### Post by Forlong on 2008-12-04
> **eternalnewbee said:**
> you could also press **ALT-F2** 
Remember, he doesn't have access to GNOME at all.
> **Halo_gg said:**
> Apparently only the "Failsafe Terminal" works.
This would work in such a case:
```
key="gconftool-2 /apps/compiz/general/allscreens/options/active_plugins" ; $key -s -t string $($key -g | sed -e 's/,mag//g')
```
This will disable the Magnifier Plugin in Compiz.

But it's a hell of a lot to write down and type into a terminal.

So try this:
```
gconftool-2 -s -t string /desktop/gnome/session/required_components/windowmanager metacity
```
This should start GNOME without Compiz on startup.

---

### Post by eternalnewbee on 2008-12-04
My mistake:oops:

---

### Post by Halo_gg on 2008-12-05
You guys are awesome! Thanks so much!:popcorn::popcorn::popcorn:

---

### Post by rswoody2000 on 2008-12-12
> **Forlong said:**
> Remember, he doesn't have access to GNOME at all.

This would work in such a case:
```
key="gconftool-2 /apps/compiz/general/allscreens/options/active_plugins" ; $key -s -t string $($key -g | sed -e 's/,mag//g')
```
This will disable the Magnifier Plugin in Compiz.

But it's a hell of a lot to write down and type into a terminal.

So try this:
```
gconftool-2 -s -t string /desktop/gnome/session/required_components/windowmanager metacity
```
This should start GNOME without Compiz on startup.

I cant thank you enough, i thought i would not manage to get out of that problem. I really didnt want to re-install from scratch.:D

---

### Post by eternalnewbee on 2008-12-12
> You guys are awesome! Thanks so much
Remember to mark your thread as solved, under [COLOR="Red"]Thread Tools[/COLOR], at the top of this page.

---

