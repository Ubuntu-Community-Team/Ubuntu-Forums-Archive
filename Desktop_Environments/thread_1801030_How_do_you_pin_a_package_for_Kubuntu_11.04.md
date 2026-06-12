---
title: "How do you pin a package for Kubuntu 11.04?"
date: 2011-07-09
forum: Desktop Environments
---

### Post by MasterNetra on 2011-07-09
Yea, I was wondering how to pin/lock a package in Kubuntu 11.04, there is no preference file in /etc/apt/ dir like told in a older post. I'm trying to lock the bcmwl-kernel-source package sense I have to use maverick's version because its broke for me in Natty (Have a bcm4312 card).

---

### Post by matt_symes on 2011-07-09
Hi

Try creating the file yourself.

Kind regards

---

### Post by MasterNetra on 2011-07-09
> **matt_symes said:**
> Hi

Try creating the file yourself.

Kind regards

Try that...nothing KPackage won't obey it, I tried creating it with:

```

Package: bcmwl-kernel-source
Pin: 5.60.48.36+bdcom-0ubuntu5
Pin-Priority: 1001

```

no dice, I remember once before when I tried this I got it to work...I just can't remember what I did...

---

### Post by matt_symes on 2011-07-09
Hi

[noparse]Did you configure Dir::Etc::preferences to point to the file ? 
[/noparse]

That is mentioned in the man page apt_preferences.

> 
[noparse]FILES
       /etc/apt/preferences
           Version preferences file. This is where you would specify "pinning", i.e. a preference to get certain packages from a separate source or from a different version of a distribution.
           Configuration Item: Dir::Etc::Preferences.

       /etc/apt/preferences.d/
           File fragments for the version preferences. Configuration Item: Dir::Etc::PreferencesParts.
[/noparse]
What does this return

```
apt-config dump | grep Dir::Etc
```Kind regards

---

### Post by koleoptero on 2011-07-10
```
sudo apt-get install aptitude
sudo aptitude hold name-of-package
```

Which is one more reason to love aptitude.

---

### Post by el_koraco on 2011-07-10
> **koleoptero said:**
> ```
sudo apt-get install aptitude
sudo aptitude hold name-of-package
```

Which is one more reason to love aptitude.

It will only hold the package when aptitude is running updates (an apt-get dist-upgrade will disobey the hold). The same can be done with dpkg - [like this]("http://www.debianadmin.com/how-to-prevent-a-package-from-being-updated-in-debian.html"). I'm not sure about KPK. it should obey dpkg, but I can't be sure.

---

### Post by MasterNetra on 2011-07-10
> **matt_symes said:**
> Hi

*snip*

What does this return

```
apt-config dump | grep Dir::Etc
```Kind regards

```

*snip*@*snip*:~$ apt-config dump | grep Dir::Etc
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::netrc "auth.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Etc::preferencesparts "preferences.d";
Dir::Etc::trusted "trusted.gpg";
Dir::Etc::trustedparts "trusted.gpg.d";

```

I should of recorded what I did last time to get to it to work...but apparently I thought it was so simple that I would of been able to figure it out again...So I know I missing something very simple with this that would get it to work...

> **koleoptero said:**
> ```
sudo apt-get install aptitude
sudo aptitude hold name-of-package
```

Which is one more reason to love aptitude.

No go, Kpackage ignores the hold from aptitude, I had even installed synaptic to hold it, KPackage still don't care, its doing its own thing. It would be nice if the Kubuntu team actually put the option to lock package in KPackage...

---

### Post by MasterNetra on 2011-07-10
Apparently I found the problem... It didn't like the use of version for Pin, so instead I did this modeled off of the wiki listing:

```

Package: bcmwl-kernel-source
Pin: release n=natty
Pin-Priority: -10

Package: bcmwl-kernel-source
Pin: release n=maverick
Pin-Priority: 900

```

And it works! ... I don't think the Pin-Priority has to be specific values, as long as the version you want to be dominate is higher. When I had loaded synaptic before with the previous settings it claimed it didn't understand what I had as Pin, so I dunno maybe it can do specific versions but not sure how to set it in pin. But no matter this works too.

Thanks everyone for trying!

---

### Post by koleoptero on 2011-07-10
Thanks for posting the solution, it might come in handy.

---

### Post by matt_symes on 2011-07-10
Hi

I think you need version in the preferences file by pin. That is what i have in mine and that works for me. I missed that earlier in your post.

Yours would become..
[FONT=monospace]
[/FONT]```
Package: bcmwl-kernel-source 
Pin: **version** 5.60.48.36+bdcom-0ubuntu5 
Pin-Priority: 1001
```Kind Regards

---

### Post by MasterNetra on 2011-07-11
> **matt_symes said:**
> Hi

I think you need version in the preferences file by pin. That is what i have in mine and that works for me. I missed that earlier in your post.

Yours would become..
[FONT=monospace]
[/FONT]```
Package: bcmwl-kernel-source 
Pin: **version** 5.60.48.36+bdcom-0ubuntu5 
Pin-Priority: 1001
```Kind Regards

Ah thanks, thats probably what I did last time but forgot, oh well.

---

