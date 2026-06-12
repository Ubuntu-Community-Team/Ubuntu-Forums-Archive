---
title: "Problem with loading some Web Pages."
date: 2009-04-11
forum: General Help
---

### Post by DaveHi on 2009-04-11
Hi All ):P

Fairly new to Linux and enjoying the experience, but......

I am having problems loading some pages in Firefox 3.0.8, a prime example is this forum. I can log in and view everything without problems but if I try to change something, say my Sig, the page hangs when I try to load the changes. Another site that I have problems with is Facebook where I can see my main page, but, am unable to view, say, my profile page.

Have tried disabling Add-ons, reinstalling firefox and even tried an alternative browser with no effect. Strange thing is everything works fine from firefox in Vista, on my laptop and from a boot disk (that's how I'm logged in now). Unfortunately, unable to say if this problem is new or has been in existance from Ubuntu installation.

Computer spec as Sig.

Hope someone can offer me some guidance, as, although when learning a new system I know the odd re-installation is to be expected (yes I fiddle), doing so now feels like giving in!

Thanks for reading this. 

DaveHi

---

### Post by cmnorton on 2009-04-11
Your logs under /var/log might contain some information that could point to a problem. It sounds like you have a bad installation or perhaps a graphics problem. 

Can you try another browser?

Are you using any graphics-heavy applications, and, if so, how do those work?

You might consider running in recovery mode dpkg-reconfigure xserver-xorg

but before resorting to that, narrowing down your problem would be the best first step.

---

### Post by DaveHi on 2009-04-11
Now that's what I call a quick reply!

Have tried an alternative browser, sorry cannot remember name, but, did download from repository. Think it was gecko based.

Don't seem to be having any graphics problems and am not running any progs with a high demands. Have tried disabling all none essential progs, that I know about, with no effect.

Will boot back in and have a sniff around my logs as suggested.

Thanks for pointers.

---

### Post by DaveHi on 2009-04-13
Hi

Just to let you know that I failed miserably to find problem, so carried out re-installation. ](*,)

Keeping an eye out for the old problem as I put system back together, as well as keeping notes this time!

Not a complete waste of time as it gave me opportunity to install home directory on a separate partition. Don't know why that isn't the recommended installation set up in the first place?

Anyway problem has gone so I'm one happy little newbie......until the next time I stick my fingers in where they shouldn't be! 

Thanks for your suggestions cmnorton.

DaveHi

---

### Post by meho_r on 2009-04-13
Well, the best way to learn something is to break something ;) Keep going :)

---

### Post by wolfen69 on 2009-04-13
glad you got it fixed, but next time firefox starts acting up, close firefox, go to your home folder and do Ctrl + H to show the hidden files. then delete your .mozilla file. then restart firefox. a new config file will be made and hopefully the problem will be fixed. worked for me a couple times.

---

### Post by DaveHi on 2009-04-14
Hi All

Thanks for the encouragement meho_r.......I think! 

wolfen69, your suggestion has gone into my handy tips file, however, I'm afraid my fiddling had caused more damage than just to Firefox. I had tried a complete re-install as well as the epiphany, all to no effect.

Still the harder the lesson the better learnt! Just wish I knew what the lesson was! :lolflag:

Thanks all.

DaveHi

---

