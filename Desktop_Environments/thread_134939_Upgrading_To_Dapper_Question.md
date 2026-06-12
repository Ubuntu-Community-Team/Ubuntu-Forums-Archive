---
title: "Upgrading To Dapper Question"
date: 2006-02-22
forum: Desktop Environments
---

### Post by TomAnthony on 2006-02-22
I am currently running 5.10, and was wondering how to upgrade to the alpha 4 of Dapper? Can I run it from the CD, or do I need to change my sources.list to dapper instead of breezy to do it. Are there any instructions on how to upgrade?

---

### Post by Jucato on 2006-02-22
it is extremely recommended NOT to use Dapper Drake (release 6.04) as your main OS. It's is currently still in development stage and so there are still many bugs/problems. If you are interested, however, in trying it out or in helping in the development, you could install it on another separation, or use a Live CD that is available. the Flight-4 Live CD, I believe, not contains the new "Espresso" project, something that lets you install from the Live CD itself, kinda Live CD and Installer CD in one.

---

### Post by Ozitraveller on 2006-02-23
[QUOTE=TomAnthony]I am currently running 5.10, and was wondering how to upgrade to the alpha 4 of Dapper? Can I run it from the CD, or do I need to change my sources.list to dapper instead of breezy to do it. Are there any instructions on how to upgrade?[/QUOTE]

change my sources.list to dapper instead of breezy YES.

Although I prefer to do a clean install from Flight-4 and then just update from there.

The live cd of flight-4 is good too. I have it seems stable. Although I don't thinks I'd try the espresso option (install from desktop icon)  just yet.

---

### Post by Xian on 2006-02-23
Agree with Ozitraveller, stay away from expresso install method and go instead with the InstallCD ISO. It would be best to install on a separate partition and keep your 5.10 for a while. Upgrading via apt will probably work, but it is more risky and troublesome than using the CD method, plus you will be removing a working Breezy install. I'm running Dapper but it should not be used by most as their primary OS.

---

### Post by TomAnthony on 2006-02-23
So if I have the install cd, will it do an upgrade from my breezy to the dapper flight 4?

---

### Post by GTvulse on 2006-02-23
[QUOTE=TomAnthony]So if I have the install cd, will it do an upgrade from my breezy to the dapper flight 4?[/QUOTE]
Yes.

---

### Post by TomAnthony on 2006-02-24
I've installed Dapper Flight 4, and I was wondering if it will automatically update itself as the releases become available, and when the final version is released in April will it automatically update to that?

---

### Post by Jucato on 2006-02-24
Yep. I think you just need to enable the proper repositories.

---

### Post by Xian on 2006-02-24
[QUOTE=TomAnthony]I've installed Dapper Flight 4, and I was wondering if it will automatically update itself as the releases become available, and when the final version is released in April will it automatically update to that?[/QUOTE]


If you've installed DF4 the repos you need are already set, the only change would be if you desired the universe and multiverse options. The auto-update tool will check daily for version upgrades and keep you informed. It is a good idea to update each time a new Flight or eventual beta is released as those are generally more stable snapshots.

---

### Post by nrwilk on 2006-02-24
You'll have to initiate the update manually, but it won't be a difficult process.  :)

---

### Post by TomAnthony on 2006-02-24
Yeah, I've enabled all repositiories listed, and it actually has updated itself a few times since install, including Firefox. The automatic adept update checker is very nice. It seems to be relitivly bug free so far.

---

### Post by nrwilk on 2006-02-24
[QUOTE=TomAnthony]Yeah, I've enabled all repositiories listed, and it actually has updated itself a few times since install, including Firefox. The automatic adept update checker is very nice. It seems to be relitivly bug free so far.[/QUOTE]

Oh, right.  If you're running Gnome, it will tell you that there are available updates.  You'll still have to initiate the process, but it'll let you know when you can.

---

### Post by LateNighter on 2006-02-24
So let me get this Straight.

 They are working on a Setup alot like Mepis, where you stick in the CD run it Live, and if you want Install from clicking on an Icon Placed on the Desktop?:D 

 :cool: 

 I take it the Expert Install Mode will still be there for those of US who choose to Dual Boot?:KS 

 Either Way Ubuntu Still RULEZ....\\:D/

---

### Post by TomAnthony on 2006-02-24
[QUOTE=nrwilk]Oh, right.  If you're running Gnome, it will tell you that there are available updates.  You'll still have to initiate the process, but it'll let you know when you can.[/QUOTE]

 Actually KDE, but it has the update notifier in the F4 build.

---

### Post by TomAnthony on 2006-02-24
[QUOTE=LateNighter]
 Either Way Ubuntu Still RULEZ....\\:D/[/QUOTE]

Yeah it does. I've played with Liunx for years, but this is the first time I am considering staying with it for good and getting rid of XP. It is a great system!

---

### Post by Jucato on 2006-02-24
[QUOTE=LateNighter]So let me get this Straight.

 They are working on a Setup alot like Mepis, where you stick in the CD run it Live, and if you want Install from clicking on an Icon Placed on the Desktop?:D 

 :cool: 

 I take it the Expert Install Mode will still be there for those of US who choose to Dual Boot?:KS 

 Either Way Ubuntu Still RULEZ....\\:D/[/QUOTE]

Yeah, they call that "Espresso" I think. But I think that the install option won't be available on an Icon but rather as one of the options when you boot the CD. 

Also, I've been installing Ubuntu/Kubuntu 3 times now, dual booting with XP. But I have never done an expert install. I don't think it's necessary when dual booting, except perhaps for some options you would like to manually choose. But the defaults work, too.

---

### Post by nrwilk on 2006-02-24
[QUOTE=TomAnthony]Actually KDE, but it has the update notifier in the F4 build.[/QUOTE]
Best news I've heard all day. :D 

This is the SINGLE thing Gnome has that I envied.  Now, I'm absolutely happy with KDE.


Also, I finally was able to resize my XP partition, so I'm going to install Dapper right now.

EDIT:  Too bad the update notifier is through Adept.  Is the version of Adept included with Dapper much improved?  Can it be used with Synaptic instead?  I've found Adept to be terrible.

---

### Post by LateNighter on 2006-02-25
[QUOTE=Fenyx]Yeah, they call that "Espresso" I think. But I think that the install option won't be available on an Icon but rather as one of the options when you boot the CD. 

Also, I've been installing Ubuntu/Kubuntu 3 times now, dual booting with XP. But I have never done an expert install. I don't think it's necessary when dual booting, except perhaps for some options you would like to manually choose. But the defaults work, too.[/QUOTE]

 You say that it runs it all automattically if you just let it go through it's paces on it's own?
 And it doesn't bother the XP partition at all?
 Does it give you a chance of Setting up SWAP Space?

 SOUNDS GOOD I can't Wait....\\:D/ :KS

---

### Post by Jucato on 2006-02-25
yep. you can choose to manually setup the partition in a normal install (just pressing enter at the prompt). Also, the normal install reinforces the non-root user principle of Ubuntu by not letting you create a root user. I heard that expert install creates a root user? I'm not entirely sure about that though.

---

