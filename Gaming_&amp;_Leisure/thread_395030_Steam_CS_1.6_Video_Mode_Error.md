---
title: "Steam CS 1.6 Video Mode Error"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by joshbax on 2007-03-27
Hey all!

So I installed steam correctly it seems, using wine steaminstall.exe etc

and i have downloaded counter-strike, but when I try to open it, i get the following error screen.

[[IMG]http://img462.imageshack.us/img462/4025/screenshot6uu1.th.png[/IMG]](http://img462.imageshack.us/my.php?image=screenshot6uu1.png)

I think i have to append the command with something in the steam window maybe? But what is that? 

Thanks for help.

And will this be the same for all steam games like cs source?

And I dont use kubunto 6.06 anymore, i can find where in my usercp to change it, I am on Ubuntu 6.10 x86 on a dell inspiron 6000 laptop with a ati mobility x300, and gfx drivers appear to be correctly installed.

---

### Post by Flying George on 2007-03-27
Earlier today I heard someone talking about 'steam4linux' I don't know much about it since I have no steam games, but I think you should do some reserach, hope this helps.

---

### Post by joshbax on 2007-03-27
yes i saw that too, but no viable results i have found.

thanks 4 reply tho!

---

### Post by Flying George on 2007-03-27
Oh, sorry I couldn't be of more help :/ But, I don't use steam.

---

### Post by joshbax on 2007-03-28
any more ideas anyone?

---

### Post by Brynster on 2007-03-28
3 suggestions

1. Run winecfg in terminal window, make sure that wine is running as win2k or XP mode.

2. Disable beryl and use nautilus as the windows management program as beryl although excellent, isn't great with gaming yet.

3. (least likely since beryl icon is there) Check you drivers for the 3d card your running are installed correctly.

---

### Post by joshbax on 2007-03-28
yup wine was in 2000 mode, now in xp.

beryl isnt actually working properly though, and yeh. that could be the problem.

when i ran the flgrxinfo (correct command?) it came back with my gfx info, which the site said meant drivers were installed correctly.

---

### Post by Brynster on 2007-03-28
Then i would suggest that its Beryl causing the issue. Try disabling it either at login or by the beryls setting manager to see which improves things

---

### Post by joshbax on 2007-03-31
ok thanks guys, i have done a fresh install, i will let u know when i finish dling cs.

---

### Post by joshbax on 2007-03-31
works on fresh ubuntu install, with no beryl running.

although this time i used envy to install the drivers - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

so that might have been it. maybe beryl will work too now.

---

