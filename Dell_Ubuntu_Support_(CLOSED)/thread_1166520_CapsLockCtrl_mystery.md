---
title: "CapsLock/Ctrl mystery"
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Hoary on 2009-05-21
(Perhaps less a Dell than an 8.04 question; feel free to move/delete.)

I've just got myself a Mini 12 (8.04 HH). One of the very first things to do was to switch Ctrl and CapsLock. A bit of googling soon took me to advice given in many places (within this website, pretty close to what Unutbu writes in [this (Xubuntu) thread]("http://ubuntuforums.org/showthread.php?t=889621&highlight=Ctrl+CapsLock"), but actually from [here]("https://bugs.launchpad.net/ubuntu/hardy/+source/xorg-server/+bug/207960") ), viz:

> Put the following in a text file.

!
! Swap Caps_Lock and Control_L
!
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L

save the above as /etc/SwapCapsCtrl.kmap

[...]

To make the change permanent, do this:
edit /etc/rc.local
add the following before the last line that says 'exit 0'
sudo loadkeys /etc/SwapCapsCtrl.kmap


I rebooted the computer; it worked (keys as I wanted them). All fine and peachy so far.

Some hours later, I connected the computer to the wider world and it wanted a pile of upgrades: 300+ files totaling 400+ megabytes. Those it got. At some point I had to reboot.

Some time after that (and presumably as a result of one or more of the upgrades, though I don't know for sure), I noticed that the "CapsLock" key was ... a CapsLock key (and that the "Ctrl" key was a Ctrl key). Damn. My work was undone.

However, both /etc/SwapCapsCtrl.kmap and /etc/rc.local
were exactly as I had rewritten them.

Frankly I don't understand /etc/rc.local at all: instead, I'm just blindly following instructions. I can wildly guess that some other change somewhere has resulted in the computer no longer paying any attention to /etc/rc.local, or that something elsewhere trumping what's written there, or that loadkeys syntax has changed.....

The Xubuntu advice page has alternative ways of switching the keys around. I suppose I could try one of those. But I do like to think (or just to delude myself) that I have some idea of what's going on here so I'm reluctant to inflict on this computer the configuration equivalent of "tag soup" in a web page.

Thanks in advance for any advice.

---

### Post by coffeeaddict22 on 2009-05-22
Sorry, can't answer the question completely.  However, the input control has moved in the last wee while from X- based to using HAL- have a look [here on the Ubuntu wiki]("https://wiki.ubuntu.com/X/Config/Input") and [here on the Debian site]("http://wiki.debian.org/XStrikeForce/InputHotplugGuide") for more info.

---

### Post by Hoary on 2009-05-22
Thank you for trying to help, but I found that a little opaque.

It occurred to me that since the need for this editing came from a bug in whatever the menus did and since a lot of time had passed since then, the bug might have been fixed. So I commented out the line from /etc/rc.local and then swapped the keys as a System menu option; this worked, and it also worked after a reboot. So I suppose I'm OK.

---

