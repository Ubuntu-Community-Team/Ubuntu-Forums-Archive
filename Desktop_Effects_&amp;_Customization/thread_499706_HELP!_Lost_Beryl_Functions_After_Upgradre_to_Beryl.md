---
title: "HELP! Lost Beryl Functions After Upgradre to Beryl 0.3.0"
date: 2007-07-12
forum: Desktop Effects &amp; Customization
---

### Post by Chewytwux on 2007-07-12
Hey sorry to bother any of you guys, i've been using beryl for around 2 weeks now and it's been wonderful.
Today morning i was prompted to do some updates, for a few programs that i had and beryl was one of them.
After installing the updates and restarting my computer, beryl was still there yet it's functions weren't. when i first examined the problem, it turned out that the metacity window manager was activated, but when i chose beryl as my window manager, it would accept my choice but quickly go back to metacity.
i've tried forcing beryl as my window manager but that didn't work..also i've tried to reinstall beryl with older versions but to no avail and still choses metacity as my window manager!!!!

If anybody out there could help me i would be very grateful!

Here are my settings
Toshiba satilite pro laptop
Intel Centrino 1.5 ghz
1GB ram
nvidia geforce FX 5200

Oh n ps i already have the latest nvidia drviers

---

### Post by Waappu on 2007-07-13
Hi

You cold try reset all beryl settings.
type in terminal ```
mv ~/.beryl ~/beryl_old_settings
mv ~/.emerald ~/emerald_old_settings
mv ~/.beryl-managerrc ~/beryl-managerrc_old
```and then try to enable Beryl.

---

### Post by Chewytwux on 2007-07-13
Waappu YOUR ARE MY SAVIOR!!

It worked great, thanls alot for your help, owe you one dude !! :)

BTW I WAS JUST FONDELING AROUND WITH EVERY SETTING IN BERYL TO SEE WHAT MADE IT CRASH, TURNS OUT IT WAS THE SKYDOME AND THE CUBE CAPS.
EVERYTIME I TRY TO TURN ON THE SKYDOME, BERYLW OULD CRASH AND REFUSE TO LOAD AGAIN, ALSO WHEN I TRY TO CHANGE THE CUBE CAPS PICTURE BERYL WOULD DO THE SAME THING!! 

ANYBODY KNOW A FIX FOR THAT?

AGAIN WAAPPU THX ALOT MAN !

---

### Post by Waappu on 2007-07-13
Hi

Do you see original cube caps ??

---

### Post by Chewytwux on 2007-07-13
Hey there,

Yes the original cube caps are there, but as soon as i remove them beryl would break and switch to metacity instantaneously. I used jpg and png images neither one worked. For the skydome, i still didn't encounter any picture porblems yet and that's because as soon as i activate skydome beryl would break and swtich to metacity.

They were working fine before the update.

Thanks again :)

---

### Post by Waappu on 2007-07-13
Hi

I don't know what is wrong.

You might try add Treviño&#8217;s Ubuntu Repository to sources.list and run update.
Packages from there has always worked for me.
[http://download.tuxfamily.org/3v1deb/index.html](http://download.tuxfamily.org/3v1deb/index.html)

---

### Post by Chewytwux on 2007-07-13
It's alright you've been very helpful it's enough that you got it working for me again eheh

anyways take care n cheers :)

---

