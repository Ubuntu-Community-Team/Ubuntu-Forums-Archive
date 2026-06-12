---
title: "Evolution Hijack!! total takeover"
date: 2005-05-23
forum: Desktop Environments
---

### Post by byen on 2005-05-23
hey guys,
You must have heard this Q? many times but I dont think this query was totally dealt with... just when i thought my migration to linux was complete...BANG! here is my problem...

After using Mozilla suite in windows..I saw evolution and it looked promising and so i ditched mozilla and configured it to use my gmail account. And since then..evolution has taken over my OS. It jumps to full CPU usage (from 4% to a 100 jump) and also takes my entire RAM space too! Its really gotten buggy and turned out to be a pain... Ive deleted my account to see if it would calm down but its just not letting me use the computer at all.. Is there anyway I can disable it from booting? and running in the background? . Im suprised that after struggling so hard to get linux to this point..they would include a progam like this! what should i do? Is it true that by unustalling evolution gnome becomes unstable? is there a way out? Please help.
Byen

---

### Post by JonahRowley on 2005-05-23
I've never been happy with Evolution.  All I want is an email client, not a monstrosity.  I'm *very* happy with KMail, but you kind of have to run KDE to use it.  I see a lot more quality apps on KDE, maybe you should give Kubuntu a try?

---

### Post by art on 2005-05-23
I don't have any problems with having the Evolution installed... But I use Thunderbird and I find it excellent. As for disabling evolution, is it in the startup programs? You may check with gnome-session-properties command.

---

### Post by byen on 2005-05-23
no...i did check it out to see if i could disable it but it is not in the session panel. and I could infact uninstall it but Ive read in various other forums that the distro itself was effected after uninstall...am not sure if it is true but I just cant risk it.....

---

### Post by art on 2005-05-24
[QUOTE=byen]no...i did check it out to see if i could disable it but it is not in the session panel. and I could infact uninstall it but Ive read in various other forums that the distro itself was effected after uninstall...am not sure if it is true but I just cant risk it.....[/QUOTE]
 Yeah that's true I guess... If I do Synaptic remove Evoltion it also marks ubuntu-desktop as the one to be removed.
So whenever you start ubuntu the evolution kicks in? Why don't you edit gnome-session-properties when evolution is running, remove it from current session, kill it and log out, first checking "save current setup" icon.

---

### Post by firas on 2005-05-24
I don't seem to have any problems with evolution on my system (i'm using both gnome & mainly kde). However if u do need to uninstall evolution you can do so even if it uninstalls the ubuntu-desktop package. The ubuntu desktop package is a metapackage meaning it doesn't do anything itself it just references all the ubuntu packages you need to install. Here's it's description:

[B]The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).[/B] 

If you find that you're having problems you can just reinstall ubuntu-desktop and it'll reinstall the removed evolution packages as well.

---

### Post by byen on 2005-05-24
Yup.. will try and see if the session-kill method works. I think it will...thank you guys. GO Ubuntu!

---

### Post by ububaba on 2008-02-29
I am deleting the message

---

