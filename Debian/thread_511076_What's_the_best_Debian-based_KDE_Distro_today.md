---
title: "What's the best Debian-based KDE Distro today?"
date: 2007-07-27
forum: Debian
---

### Post by wersdaluv on 2007-07-27
I'm looking for a debian-based kde distro to replace Kubuntu since synce-kde does not work with it and it really is giving me a hard time.

I tried Knoppix, but it seems that its repositories are not being updated well.

I am currently downloading Sidux. I hope this is what I am looking for.

I am also considering Pardus, but I'm hesitating with trying it because I do not think it has a lot of support in English.

What is the best Debian-based distro today?

Edit: Oooops. It seems that Pardus is not debian-based! LOL

---

### Post by kerry_s on 2007-07-27
why not just go straight to the source> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)

---

### Post by wersdaluv on 2007-07-27
> **kerry_s said:**
> why not just go straight to the source> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)

I currently have it installed but I prefer I KDE-centered Distro and I want a bleeding edge desktop, by that, I mean, the desktop with the latest and greatest apps but is stable enough for the use of a student like me.

---

### Post by b9anders on 2007-07-28
if you want debian, kde and the bleeding edge then sidux is for you. It's basically debian sid with a few added scripts.
How they manage to make it so fast I don't know but for kde it's flying.

---

### Post by Bachstelze on 2007-07-28
Why run a copy when you can run the original ?

Go with Debian Sid.

---

### Post by wersdaluv on 2007-07-30
You mean Debian Sid is still better than Sidux? How come?

---

### Post by Pobega on 2007-07-30
Either use Debian itself or use Sidux. Sidux uses KDE by default, but the only problem is that the people of that community are pretty stubborn to support things outside of their niche (Like GNOME, for example), whereas Debian users don't have a centric desktop environment or anything. Everyone just uses what they like.

But personally if I were you I'd use Debian testing. Sid is too bleeding edge for my tastes, and testing (Lenny at the moment) has pretty up to date packages.

---

### Post by JackieBrown on 2007-08-04
> **wersdaluv said:**
> You mean Debian Sid is still better than Sidux? How come?

For the same reason that Sidux is good.  

It doesn't have all those scripts to hide things (including upgrading) from you.

But at the same time those scripts help make it better for people that want the latest and greatest but don't want the work that comes with that.

Pobega is right about the other window managers and DE's but since you want a kde distro than that should matter.

---

### Post by Bachstelze on 2007-08-05
> **wersdaluv said:**
> You mean Debian Sid is still better than Sidux? How come?

Because Debian Sid is the original and Sidux is the copy. A very good one, but not as good as the original.

---

### Post by davtaine on 2007-08-06
...yawn...

---

### Post by cleary on 2007-08-07
> **HymnToLife said:**
> Because Debian Sid is the original and Sidux is the copy. A very good one, but not as good as the original.

It's not a copy - it *is* sid. Every sidux release is a snapshot of the sid repositories at a stable point in time.
Unlike sid though, there is a community for support, there are notifications/early bugfixes for broken packages in sid, and update tools designed to remove the danger from keeping sid current.

---

### Post by GoinEasy9 on 2008-10-19
I don't understand why someone would say that sidux is a copy of Sid.  We use Debian Sid repos, every time we update, we are current with the Sid repos.  We have a blazing fast kernel (now at 2.6.27 thanks to slh) and some of the most innovative configuration routines (ceni, wpa_gui thanks to kelmo) of any distro out there.  Our IRC and forums solve problems fast and help to keep Debian Sid stable.  Running Sid instead of sidux just means you have to work on problems that the sidux devs have already solved.
Linux is all about choice. If you like solving problems on your own, then by all means, run vanilla Sid.  I like bleeding edge with minimal problems, so I run sidux.
As far as the devs aversion to Gnome, it's more due the fact that few in the sidux community care for it, and the fact that no one wants the responsibility for maintaining it.  Gnome breaks more in Sid than does KDE, that and the fact that we like KDE a whole lot more is the reason there isn't a Gnome version of sidux.  For example, there is an XFCE version of sidux, and I can see a growing group of LXDE enthusiasts.  sidux is open if you want to get involved.
Read the forums or chat in IRC, get to know sidux, resistance is futile - you will be assimilated.

---

### Post by igknighted on 2008-10-19
> **Pobega said:**
> Either use Debian itself or use Sidux. Sidux uses KDE by default, but the only problem is that the people of that community are pretty stubborn to support things outside of their niche (Like GNOME, for example), whereas Debian users don't have a centric desktop environment or anything. Everyone just uses what they like.

But personally if I were you I'd use Debian testing. Sid is too bleeding edge for my tastes, and testing (Lenny at the moment) has pretty up to date packages.

Do you know why Sidux doesn't use gnome?  It has _nothing_ to do with the Sidux devs.  The gnome packages in debian unstable are, well, unstable.  To an unusable point.  KDE, Xfce, etc. all have usable, albeit bleeding edge, packages.  This is the reason for the choice, not any personal preference.  If you don't believe me go install Sid and see for yourself.

---

### Post by basenvironment on 2008-10-20
> **cleary said:**
> It's not a copy - it *is* sid. 
Does it use the debian kernel? Does it follow debian policy regarding firmware? Does sidux have its own repos/packages? If I install sidux and change my sources to debian unstable, how much will it add/remove/replace? If I install debian sid and change my sources to sidux, how much will it add/remove/replace?

Something different is not the same - debian sid is debian sid, sidux is sidux. Sidux is based on debian sid but seems more like a subset to me. Why would I want a subset when I can have the whole superset!

If you enjoy a tv-dinner then that is great - enjoy it. I like the buffet myself...

---

### Post by basenvironment on 2008-10-20
> **igknighted said:**
>  The gnome packages in debian unstable are, well, unstable.  To an unusable point.  ... If you don't believe me go install Sid and see for yourself.
Uh, I do/did and gnome seems to work fine. Can you give me an idea of what is unstable to an unusable point? I must be overlooking it...

---

### Post by basenvironment on 2008-10-20
> **GoinEasy9 said:**
> ... solve problems fast and help to keep Debian Sid stable.  
sid is never stable....otherwise they would call him woody, sarge, etch...

---

### Post by Antman on 2008-10-20
> **davtaine said:**
> ...yawn...
+1:popcorn:

---

### Post by Vorian Grey on 2008-10-21
> **igknighted said:**
> Do you know why Sidux doesn't use gnome?  It has _nothing_ to do with the Sidux devs.  
Not true. The main reason is none of the current devs want to bother with it. I've read on their forums that if two maintainers could be found they would support Gnome. So far they've had no takers.

---

### Post by Antman on 2008-10-22
> **Vorian Grey said:**
> Not true. The main reason is none of the current devs want to bother with it. I've read on their forums that if two maintainers could be found they would support Gnome. So far they've had no takers.
+1 I have read that too.

---

### Post by dptxp on 2008-11-02
sidux is a distro where Gnome-centric users like me have accepted kde. Gnome is not officially supported as there are no maintainers for it, but some use Gnome.

sidux is not a copy of Debian sid, it is well-maintained and pretty stable.

---

### Post by xArv3nx on 2008-11-02
> **Vorian Grey said:**
> Not true. **The main reason is none of the current devs want to bother with it.** I've read on their forums that if two maintainers could be found they would support Gnome. So far they've had no takers.
Why do you think they don't want to bother with it? :)

---

