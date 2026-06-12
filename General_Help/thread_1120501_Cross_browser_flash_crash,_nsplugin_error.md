---
title: "Cross browser flash crash, nsplugin error"
date: 2009-04-09
forum: General Help
---

### Post by lascar on 2009-04-09
Any website with flash content on it crashes my browser. This is a 32bit system with a fresh install of ubuntu 8.10.

I've reinstalled the flashplugin-nonfree and have tried using swfdec-mozilla. I've tried both firefox and epiphany. They both seg fault when I run them from the terminal, both log the same error messages for instance going to youtube gives me

```
*** NSPlugin Viewer  *** ERROR: could not reconstruct XVisual from visualID
```

I've tried reinstalling nspluginwrapper to no avail.

Any ideas would be useful at this point.

---

### Post by lascar on 2009-04-11
sorta sucks how flash not working makes an OS useless :/

/bump

---

### Post by AbtZ on 2009-05-03
Sometimes it's easier reinstalling the whole OS if you have a weird problem. It takes, what? 20 minutes on a moderately new computer.

If you do that, I would suggest you try [Linux Mint]("http://www.linuxmint.com/"), it's based off Ubuntu but comes with flash (and many other) codecs pre-installed.

You could also try creating a new user profile to log in with -- I've had weird issues before that were due to corrupted .-files in my /home directory.

Lastly, have you tried Opera? 

Good luck. :)

---

### Post by zvacet on 2009-05-03
@ **AbtZ**

> Sometimes it's easier reinstalling the whole OS if you have a weird problem. It takes, what? 20 minutes on a moderately new computer.

This is not some other OS community.We don´t reinstall if we have problems.We are try to fix it.

 > Lastly, have you tried Opera?

That is good idea but it will not solve original problem.Sorry I can not help in this one.

---

### Post by AbtZ on 2009-05-03
Haha, man. Way to be a zealot. You think letting this guy hang for 3 weeks making no replies is better than offering a possible, albeit non-optimal, workaround/solution?

Allow me to respectfully disagree with your viewpoint.

If his problem isn't hardware-related Mint might work for him, all is good, and he can start enjoying using Linux, instead of cursing at the lack of flash. And as Mint is Ubuntu-based I don't see the harm in suggesting it. Oh well.

---

### Post by cariboo on 2009-05-03
For all we know the OP could have fixed his problem by now or has gone back to Windows. 

Telling someone to install/re-install a distribution is not helping either. It doesn't solve the problem, as the same problem may crop up again. If you can't help solve the problem, it is better not to do anything.

---

### Post by AbtZ on 2009-05-04
No, he hasn't. He was complaining about it in another forum yesterday , and the fact that everybody here was ignoring him. He found the community "support" quite lacking.

Something has gone wrong with his flashplugin install, and reinstalling it has not helped. If it's a software issue caused by some iffy config file, an OS reinstall is a quick way to fix it. If it's a hardware issue, he'll just have wasted less than 20 minutes. 

I at least gave him an option to try something -- you guys gave him *nothing*. The same problem may crop up, or it might not; who are you to tell if it's true or not until it's been tried?

Sheesh, I'm getting way off topic but the self-righteousness I see here annoys me. I hope this is not a reflection of the community in general. Otherwise the guy was right in his complaint. Get over yourselves.

---

### Post by zvacet on 2009-05-04
@ **lascar**

From terminal edit your source list with command

```
gksudo gedit /etc/apt/sources.list
```

and add this line 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

save and close file.

```
sudo apt-get update
```

Go to the synaptic and remove flashplugin-nonfree and install **adobe-flashplugin.**

---

