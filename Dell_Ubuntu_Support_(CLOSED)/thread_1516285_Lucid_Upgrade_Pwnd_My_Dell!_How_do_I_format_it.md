---
title: "Lucid Upgrade Pwnd My Dell! How do I format it???"
date: 2010-06-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nbala on 2010-06-23
[[COLOR=Blue]Latitude D610 running Karmic[/COLOR]]
Helllo- here's my Dell story:
***Every*** time in my life that I have upgraded/updated (XP,Vista, iPod Touch etc) it has _**always**_ been a disaster either disabling primary components or** turning the device into a paper-weight!**  :-?

So when the Update Manager kept offering the Lucid upgrade, of course I thought "*Oh no- you're not going to screw me this time!!*" and cancelled it.
BUT- then one day I thought: "* Hey, this is **Linux**, this is **Ubuntu**, not WindoZe or appleOS, Linux is my friend, it will be fine! *"

Yup-Nope not at all!
I lost my keyboard input and sound (probably much more but once I saw that I just stopped looking!). The keyboard worked in *bootup* but **not** within GUI, so I am using the onscreen keyboard (:confused:)
I've found that other users have had similar issues when they upgraded to Lucid!
( I don't know if they are Dell users tho)

Here comes a question for all of you:
[COLOR=Blue]**I have reinstalled Karmic Ubuntu with a partition containing my previous account**
[/COLOR][B][COLOR=Blue]I have backed up my needed stuff[/COLOR]
[SIZE=2][COLOR=Red]How do I format ( and get rid of the partition ) to reinstall Karmic from a clean-slate???[/COLOR][/SIZE][/B][SIZE=2][COLOR=Red]
[/COLOR][/SIZE]
I have **Gparted** (?) but no idea how to use it to FORMAT ](*,) or **how to format in Ubuntu** any help IS greatly appreciated as I need this laptop for my graduate studies to help disabled children! (No joke!)
[B][SIZE=2][COLOR=Red]
[/COLOR][/SIZE][/B][B]Thanks for any help you offer, and has anyone else with a Dell had upgrade problems with the keyboard & sound going offline within the Gnome/Xterm GUI?
[/B] :-D **Thank you!!! ** :-D

---

### Post by gbrainin on 2010-06-23
I'm a little confused.  You said you reinstalled Karmic, but you want to format a partition so you can install Karmic?

The short answer to your question may be this: If you're going to mess with the partitions on your primary hard drive, you probably should do it from a Live CD or USB, because you generally can't mess with a partition while it's mounted.  When you run gparted from the Live CD, you may need to unmount a partition before making changes.  Then you select the partition you want to make changes to, and make the changes (most are under the "Partition" menu).

---

