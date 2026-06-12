---
title: "Unity + Group management"
date: 2012-07-18
forum: Desktop Environments
---

### Post by lptr on 2012-07-18
Where to find UI for group management ? User is in system control. But groups and additionally to mapping users to groups? 

Don't tell me terminal...

---

### Post by bogan on 2012-07-18
Hi!, **lptr,**

In 12.04 unity or gnome, enter 'group' in Dash or Applications Search box ans select 'Users & Groups'.

Hope that is what you are looking for.

Chao!, **bogan.**

---

### Post by lptr on 2012-07-18
> **bogan said:**
> Hi!, **lptr,**

In 12.04 unity or gnome, enter 'group' in Dash or Applications Search box ans select 'Users & Groups'.

Hope that is what you are looking for.

Chao!, **bogan.**

Thanks for reply.

If doing Super-A group, I get this: ((attchmt))

KUser would install complete KDE. That's not exactly what I want.
:confused:

---

### Post by bogan on 2012-07-18
Hi!, **lptr,**
EDIT: InSystem Settings>System there is 'User Accounts' which does the same as below.
When I enter 'group' in Dash, I get an Icon: 'Users and Groups'; selecting that opens a Window titled: "User Settings". [See Screenshot][ATTACH]221438[/ATTACH]. 

Maybe you need to install it; I do not see anything in Ubuntu Software, except Kuser, which I do not have installed.

Synaptic shows a package: 'adduser', which is installed; "add & remove Users & Groups"; maybe that is it.

 Do you have it installed.?

[Actually, adduser seems to be a Terminal only cmd, not what you wanted; 'gksu adduser' did nothing.]

Chao!, **bogan**.

---

### Post by lptr on 2012-07-18
nope. This program I could not find anywhere. 

adduser is a terminal program. Yes.

System control user program has no advanced button, no groups. :(

I forgot to mention: This is a totally new installed machine. From scrap 12.04 no update as the old machine is 10.04 and I was afraid that something will break.

---

### Post by MG&amp;TL on 2012-07-18
> **lptr said:**
> nope. This program I could not find anywhere. 

adduser is a terminal program. Yes.

System control user program has no advanced button, no groups. :(

I forgot to mention: This is a totally new installed machine. From scrap 12.04 no update as the old machine is 10.04 and I was afraid that something will break.

Unless someone can say otherwise, I think it's a terminal job. I did this a while ago and was unable to find a GUI for it, so I gave up and read the various manpages.

It's not really a common need, which I guess is why GNOME didn't include it.

---

### Post by lptr on 2012-07-18
> **MG&TL said:**
> Unless someone can say otherwise, I think it's a terminal job. I did this a while ago and was unable to find a GUI for it, so I gave up and read the various manpages.

It's not really a common need, which I guess is why GNOME didn't include it.

No common need? Maybe. But as this is an replacement for an older Linux machine here it is. Machine also runs as samba server here in the network. 

Ok. It's somewhat overblown but will help in administration things: Will now install webmin. Unity only seems to be good as desktop surface.

---

### Post by bogan on 2012-07-18
Hi!,** lptr**,

What I reported, and the screenshot, were from a directly installed 12.04 LTS v .3.2.0-26-generic-pae #41, with Gnome-session-fallback and fully updated.

I also have an updated installation - originally 9.10 - now 12.04 LTS v.3.2.0-26-generic #41, [ not -pae] also with Gnome-session-fallback and fully updated.

Interestingly, in the latter, whilst running Dash> Users & Groups shows the same User Settings Window [with Advanced settings]; running System Settings>System>User Accounts opens a 'User Settings' Window similar to your Screenshot, without the 'Advanced Settings' or 'Group Management options. [ Whereas with the former both are the same.]

I have no idea why they are different in this respect, though there are several subtle differences in behavior, mainly in the sequence of displays during start-up and shutdown, and the time they take to do so.

Both have roughly the same apps installed, and similar desktop managers and compiz tweaks.

Chao!, bogan.

---

### Post by lptr on 2012-07-18
Gnome-session-fallback is installed, too. Fully patched, yes.

Strange.

---

