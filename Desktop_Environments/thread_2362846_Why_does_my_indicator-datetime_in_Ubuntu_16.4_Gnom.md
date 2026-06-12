---
title: "Why does my indicator-datetime in Ubuntu 16.4 Gnome shell show no numbers?"
date: 2017-06-02
forum: Desktop Environments
---

### Post by werner-habel on 2017-06-02
as seen in screenshots, my indicator-datetime in Ubuntu 16.4 Gnome shell shows no numbers? Any ideas why and how I can fix this?

---

### Post by Frogs Hair on 2017-06-03
Hello and Welcome

Is this the default shell theme or third party ?

---

### Post by werner-habel on 2017-06-04
thanks Frogs Hair,

to your question, gnome-tweak-tool gives me the output in added screenshot.

hope this helps?

regards,
Werner

[ATTACH=CONFIG]275455[/ATTACH]

---

### Post by Frogs Hair on 2017-06-04
Looks like a third party theme and in that case you have to make sure it's compatible with the Gnome version in use. Just to be sure try the default theme and see if the problem persists.

---

### Post by werner-habel on 2017-06-04
unfortunately, switching to default Adwaita theme (german "Vorgabe" in added screenshot means default) problem persists.

I use the Zukitwo 3.18 branch as recommended for Ubuntu 16.04 LTS here
[https://github.com/lassekongo83/zuki-themes](https://github.com/lassekongo83/zuki-themes)

thanks again,
Werner
[ATTACH=CONFIG]275463[/ATTACH]

---

### Post by werner-habel on 2017-06-04
just noticed that issue extends to other (possibly all) numerical indicators in the upper panel.

see again added screenshot, look for number of eth connection.

[ATTACH=CONFIG]275464[/ATTACH]

---

### Post by Frogs Hair on 2017-06-04
What are you computer specs ?  Graphics / hardware.

---

### Post by werner-habel on 2017-06-07
please excuse my late reply.

life happened.

to answer your last question:

Intel® Core&#8482; i7-5500U CPU @ 2.40GHz × 4 
Intel® HD Graphics 5500 (Broadwell GT2) 
Ubuntu 16.04.2 LTS 64-Bit

meanwhile, I found out, that other user accounts did not show the described symptoms.

So I backed up my data, deleted my user account and recreated it with a fresh home directory.

Lo and behold, the issue is gone now.

Of course, this is in no way a solution, not even awork around.

It is a brute force quick and dirty hack.

I am still very interested in the root cause of this and if there is a more sensible and elegant way to solve it.


[ATTACH=CONFIG]275524[/ATTACH] [ATTACH=CONFIG]275525[/ATTACH]

cheers,
Werner

---

### Post by Frogs Hair on 2017-06-07
You shouldn't have any problems with that hardware and I wouldn't have guessed a corrupt user profile.   ;)

---

### Post by werner-habel on 2017-06-08
Thanks Frogs Hair,

still I hope someone can point to what exactly got corrupted in the old profile and how to fix it in a rational sensible way.

a little bit of background here:

I am migrating from Unity to Gnome Shell in anticipation of Ubuntu 18.04.

There is still one other user on this machine who is experiencing the same issues that I did.

I would be happy to spare her deleting her profile.

Cheers,
Werner

---

### Post by jbicha on 2017-06-10
I noticed in an earlier comment you changed your theme to Adwaita but you still had a different Shell theme. I suspect the Shell theme you were using might be the problem.

---

### Post by 2011spook on 2017-06-10
> **werner-habel said:**
> as seen in screenshots, my indicator-datetime in Ubuntu 16.4 Gnome shell shows no numbers? Any ideas why and how I can fix this?

you exist outside of time my friend,
free from the burdens of cause and effect.

---

### Post by 2011spook on 2017-06-10
> **jbicha said:**
> I noticed in an earlier comment you changed your theme to Adwaita but you still had a different Shell theme. I suspect the Shell theme you were using might be the problem.

my last comment was a joke really though...
this guy may be on to something, does it do this with other themes?

---

