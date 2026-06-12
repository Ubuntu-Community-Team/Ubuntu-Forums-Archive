---
title: "Dismissing updates?"
date: 2005-04-24
forum: Desktop Environments
---

### Post by aaroniu on 2005-04-24
I'm only a low-level Linux geek, so go easy.

Is there any way to dismiss updates that the "Software Updates" window reccommends? A few days ago three updates for KDE came in and the "updates available" icon shows in my panel. I don't use KDE, and I don't particularly need to be on the cutting edge of non-critical updates, but I can't see any way to dismiss the updates. They just stay there, and the "updates available" warning stays in my panel. I do, however, want to see updates as they're coming in, particularly the security ones, and if that icon becomes a permanent part of my Desktop I won't notice it any more.

So is there a way I can dismiss individual updates but keep being notified of new ones?

---

### Post by Burgundavia on 2005-04-24
You will always be notified of all updates. And as a security principle, always apply ALL upgrades as soon as they are available. If you don't want to install the updates, then uninstall the program.

Basically, every 24 hours, the system checks for more updates and will simply add the upgrades to the queue.

Corey

---

### Post by crazybill on 2005-04-24
I agree that the update feature is very nice. I do not recommend uninstalling it.

---

### Post by aaroniu on 2005-04-25
Thanks for the replies, guys. I understand the importance of security updates. What I'm talking about is non-critical updates.

I was under the impression that an Ubuntu release is relatively stable, and I don't need to worry about non-critical security updates until the next release in six months. I would much rather have a stable system than one with up-to-the-minute patches that might not be 100% stable.

Is there no way to seperate critical security updates, from updates to packages I don't care about and am not using?

---

### Post by tread on 2005-04-25
Well, this might work:
Comment out all repositories except the cdrom in /etc/apt/sources.list

(Note: You have to be sudo to do that)

Then fire up synaptic, and reload package information.

---

### Post by tomchuk on 2005-04-25
[QUOTE=tread]Well, this might work:
Comment out all repositories except the cdrom in /etc/apt/sources.list[/QUOTE]

You definitely don't want to do that! You wouldn't get *any* updates, even important security ones.

Ubuntu doesn't release updates to the current release except to address serious bugs or security issues, they're all worth installing. You can install apt-listchanges wich will install itself in /etc/apt/apt.conf.d/ and will output the changelog for updated packages, so you can read them and decide if they're worth installing.

You can use apt pinning to pin packages to a certain version so they won't be upgraded. For instance to pin kdelibs-bin to the current version:

```

# /etc/apt/preferences

Package: kdelibs-bin
Pin: version 3.4.0-0ubuntu3
Pin-Priority: 1001

```
You can read more about pinning at the [APT howto](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

### Post by az on 2005-04-25
[QUOTE=aaroniu]Thanks for the replies, guys. I understand the importance of security updates. What I'm talking about is non-critical updates.

I was under the impression that an Ubuntu release is relatively stable, and I don't need to worry about non-critical security updates until the next release in six months. I would much rather have a stable system than one with up-to-the-minute patches that might not be 100% stable.

Is there no way to seperate critical security updates, from updates to packages I don't care about and am not using?[/QUOTE]

Unless you are running the current developmental version (breezy) you will get no new versions, just security updates and bug fixes.  Any one of them can be severe.

---

### Post by tread on 2005-04-25
You're right Tomchuk .. what I should have said was,

update the packages you want, then comment out the repositories. Then about once a week, uncomment, update selected packages and then comment again. Ad inifinitum.

Bad solution, I agree .. but it would work I think. Of course, anyone who does this must be diligent enough to check periodically for security updates.

---

### Post by aaroniu on 2005-04-26
[QUOTE=tomchuk]Ubuntu doesn't release updates to the current release except to address serious bugs or security issues, they're all worth installing.[/QUOTE]

Thanks, this answers my question. The updates in question gave no sign of being important, and I'm just skeptical of installing stuff I don't need.

---

