---
title: "Desktop/Compiz freezes after 5-10 mins if desktop effects turned on"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by khooke on 2007-12-09
I've been playing with Compiz Fusion on Ubuntu 7.10. I have a ATI Radeon Mobility 9000 in my laptop and I'm currently using the opensource ATI drivers - the ATI proprietary drivers I couldn't get to install.

After about 5-10 mins with the default install, not sure what drivers I had then, it would hang after about 5 mins of moving windows around. I tried the ATI drivers, and couldn't get them to work, now I'm with the opensourcedrivers. Not sure what I changed along the way, but with the effects maxed out it will last 30mins or more and then hang.

Seems like if I dial back the setting to only one or two effects it is more stable.

When it hangs, I get no mouse or keyboard response, but the hardrive light occasionally flickers so I know I still have life. I can ssh from another machine into my laptop ok, and sudo /etc/init.d/gdm restart brought back a logon and then everything is ok.

Any advice?

---

### Post by khooke on 2007-12-16
No one has any ideas how to troubleshoot this? I'm getting close to the point of installing something other than Ubuntu at this point.

---

### Post by MONODA on 2008-02-29
turn off compiz, i had the same problem.

---

### Post by bixejo on 2008-02-29
I guess it's "a bit" late for this to be helpful to you, but anyhow there it goes.

a) I uninstalled xserver-xgl and it solved the problem, I don't know whether you got this installed.

b) Since you may login remotely, try to see how many compiz processes are running in your computer:

```
$ ps -Af | grep -i compiz
```

Due to some kind of error that I've been unable to identify yet, sometimes I get about one hundred or more twin compiz processes, each one parent of the following. Looks like for some reason compiz forks forever and this may collapse the system (you shouldn't either be able to ssh your system, though...)

--Bixejo

---

### Post by bixejo on 2008-02-29
Ok, you may disregard the b) choice of my former post. I identified the problem and has nothing to do with yours. Sorry for the confusion, I was just trying to help.

--Bixejo

---

