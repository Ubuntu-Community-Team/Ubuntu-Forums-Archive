---
title: "Differences between KDE and GNOME?"
date: 2007-03-11
forum: Desktop Environments
---

### Post by Lisa Hayes on 2007-03-11
Hello to all!

This is a new experience to me, seeing that my earlier experiences with operating systems is mainly concentrated on MS windows. I am very pleased that Ubuntu (edgy eft) has worked with a few hitches here and there, though sadly, it still has no support for my printer. The most important part is internet access, and i am pleased that it worked without a hitch.

But enough about my experiences, i am here to ask a couple of questions to the more experienced users here in Ubuntuforums. I am aware that there are 3 versions of Ubuntu, but there are two distinct versions of Ubuntu. One uses GNOME (what i am using now), the other is KDE (kUbuntu distro).

I am curious to find out, on firsthand experiences on other members, if there is any significant differences between the two. I've visited the Wiki entry of both GNOME and KDE, and sadly, i did not understand the main differences between the two. 

1] As for the applications, are programs designed for KDE only work for KDE? And for GNOME applications for GNOME only? I've seen plenty of apps with labels "for KDE". Or can the applications compatible with both KDE and GNOME?
2] If i install kUbuntu, is it pretty much the same as installing as Ubuntu (edgy eft) sans the desktop environment?
3] As personal preference, will i be able to change the GNOME environment into KDE? I am curious since i want to try out other alternatives.
4] Which is currently more stable? KDE or GNOME?
5] and lastly, what is your personal preference between the two? Do you like GNOME or KDE instead?

Some veteran members might say that these are foolish questions, so please bear with me since i am a new user.

Thanks for reading!

\p/

---

### Post by bernied on 2007-03-11
1) You can use both sets of packages on both desktops, though you might need to first install some extra packages when you install kde applications in gnome, and the gnome and kde themes can sometimes not match up (apparently it works better when you install the same themes in gnome and in kde, but I don't know much about this)
2) I believe this is true, the basis is the same, even the X-Windows server is the same, it is just the desktop and associated applications that are different.
3) 'sudo apt-get install kubuntu-desktop'. You will then be able to choose which one you want to start when you login (your login screen may change as well). Your gnome desktop and all your settings will be preserved
4) hmmmm, not sure if there is an answer to this, both have stable and unstable versions available 
5) I like kde. Many gnome-lovers will say that kde is windowsish, I think that gnome is applish. In reality both can be configured pretty much how you want them.

Not foolish questions, but you will find very similar threads if you search. It's all been said before.

---

### Post by 23meg on 2007-03-11
This may help:

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by aa.ivanov on 2007-03-11
> **Lisa Hayes said:**
> ****

But enough about my experiences, i am here to ask a couple of questions to the more experienced users here in Ubuntuforums. I am aware that there are 3 versions of Ubuntu, but there are two distinct versions of Ubuntu. One uses GNOME (what i am using now), the other is KDE (kUbuntu distro).

I am curious to find out, on firsthand experiences on other members, if there is any significant differences between the two. I've visited the Wiki entry of both GNOME and KDE, and sadly, i did not understand the main differences between the two. 

Well... UNIX/Linux world used to have no consistent Graphical User Interface (GUI). At least not of the type seen in Windows/MacOS. This has changed with the release of the K Desktop Environment (KDE). It was a great innovation for the Linux world. There was a minor issue that caused major concerns though - in order to work KDE used a toolkit that was not a free software. Purists refused to use/distribute KDE because it needed the Qt toolkit to draw the Graphical Interface. Others deployed KDE and in such way they became dependant on the company that owned Qt - Throlltech. That was the main reason for the creation of GNOME. 

At present the issues around KDE are solved. Comparing the both environments, I should say that KDE is closely following the mimics of Windows, it has better integration (something called Kparts that comes very handy for deploying already created components in new programs) and is more shiny. GNOME used to mimic windows, but the new versions leave me with the impression that the team has found new source of inspiration in MacOS... I might be wrong. GNOME is more minimalistic - the default configuration utilities do not overwhelm user with tons of options. Some users find this frustrating.

> **Lisa Hayes said:**
> 1] As for the applications, are programs designed for KDE only work for KDE? And for GNOME applications for GNOME only? I've seen plenty of apps with labels "for KDE". Or can the applications compatible with both KDE and GNOME?
No. You can use KDE programs under GNOME and vice versa. The only provision is that all program libraries that are required by the program are present. The packet management system will ensure this provision is met. 
The point is that KDE programs are *designed* to work under KDE and follow the concepts behind this desktop environment. The annoyance of using KDE programs under GNOME is that it won't fit in the the selected theme and will stick out.
Creating programs having dual nature is not impossible, but it makes the programs a bit 'heavier'. OpenOffice.org for example can be made to behave as GNOME as well as KDE app. 

> **Lisa Hayes said:**
> 2] If i install kUbuntu, is it pretty much the same as installing as Ubuntu (edgy eft) sans the desktop environment?
The base system is the same, but the Desktop environment is different. In Kubuntu there won't be gedit (text editor) ot rhytmbox (musical player and organizer). Instead the KDE equivalents will be installed (Kate and Amarok). Some applications like Firefox and OpenOffice.org are usually installed both under GNOME and under KDE.

> **Lisa Hayes said:**
> 3] As personal preference, will i be able to change the GNOME environment into KDE? I am curious since i want to try out other alternatives.

Yes. In the software manager there are two packs - ubuntu-desktop and kubuntu-desktop. They are what is called meta-package - it simply lists the applications specific for ubuntu and kubuntu respectively. Switching between them shouldn't be a tough task. Making them coexist should be possible, but I have no experience. I expect some configuration to be needed. May be it's best to try live cds of both GNOME and KDE and decide which you'll use as your primary desktop.

> **Lisa Hayes said:**
> 4] Which is currently more stable? KDE or GNOME?

Both are stable enough for daily work.

> **Lisa Hayes said:**
> 5] and lastly, what is your personal preference between the two? Do you like GNOME or KDE instead?

I first started with GNOME, then had a look at Enlightenment, moved to KDE, and then back to GNOME. KDE usually is a good choice for users migrating from Windows environment. I personally dislike it (a bit) 'cause it reminds me of Windows, and more important GNOME's minimalistic approach to settings makes me to focus on the applications (which means my work) instead of playing with the desktop. Well, I sometimes miss some features form KDE.

---

### Post by Lisa Hayes on 2007-03-11
thanks bernied.

as for the link presented, t'was greatly appreciated.

I am still exploring the flexibilities in Ubuntu, and so far so good.

and thanks ivanov. You've hit some of the questions i've presented head-on.

---

