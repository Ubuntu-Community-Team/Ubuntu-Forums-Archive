---
title: "Firefox mad!!!"
date: 2008-09-27
forum: Desktop Environments
---

### Post by eAi-T0ky0 on 2008-09-27
[B][CENTER]hey all...

  I have some problems here with my ubuntu [COLOR="Red"]Firefox/3.0.3[/COLOR] ... 1st I have searching on the forum for my problem about "Firefox crash when open flash" and found that thread [here]("http://ubuntuforums.org/showthread.php?t=213878&page=3") >>> I do what makadam write in [#25]("http://ubuntuforums.org/showpost.php?p=1632666&postcount=25") and When I paste that line on terminal "sudo mv /usr/bin/firefox /usr/bin/firefox.org" Firefox don't want to open from my up panel!!! :(

I don't know what i have done!!! but I know that's make my Firefox sad and won't open from my up panel again. :confused: Please help me to make it open from my panel again :(

And if any one have any idea about that problem on firefox when it crashing on flash webs like myspace and have that fixed it up please tell me about it bec I don't know!!! :confused:

Thanks[/CENTER][/B]

---

### Post by melojo on 2008-09-27
Open up a terminal and type or copy and paste this below

/usr/bin/firefox

If firefox starts goto a flash site and let it crash then post the info from the terminal.

let me know what happens

---

### Post by eAi-T0ky0 on 2008-09-27
[CENTER]Hi melojo ... thanks for replay... the terminal tell me this "bash: /usr/bin/firefox: No such file or directory" :confused:

I tell you again I do what makadam write in #25 replay from my last post, and When I paste that line on terminal "sudo mv /usr/bin/firefox /usr/bin/firefox.org" Firefox don't want to open from my up panel again!!! :(

Thanks [/CENTER]

---

### Post by melojo on 2008-09-27
ok
type this and do the same thing

/usr/bin/firefox.org

---

### Post by Bakon Jarser on 2008-09-27
Right click on the panel launcher and click properties.  Change firefox %u to firefox.org %u.  Then follow this guide (ignore the $ at the beginning of his commands)

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by eAi-T0ky0 on 2008-09-27
melojo
This command open my firefox. Thanks :)

Bakon Jarser
Thanks man ... you the best :guitar:

Thanks

---

### Post by melojo on 2008-09-27
> **eAi-T0ky0 said:**
> melojo
This command open my firefox. Thanks :)

Bakon Jarser
Thanks man ... you the best :guitar:

Thanks

You can change it back to the way it was before you entered
sudo mv /usr/bin/firefox /usr/bin/firefox.org

to

sudo mv /usr/bin/firefox.org /usr/bin/firefox

The only thing the command is doing is renaming the script that executes firefox

It should launch from the aplications menu then if you change it back.
If you have any questions don't hesitate to post. Someone can help you.

---

