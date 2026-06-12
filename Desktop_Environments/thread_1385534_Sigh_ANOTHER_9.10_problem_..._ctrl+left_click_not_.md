---
title: "*Sigh* ANOTHER 9.10 problem ... ctrl+left click not working"
date: 2010-01-19
forum: Desktop Environments
---

### Post by Jethro_uk on 2010-01-19
trying to select multiple files in Nautilus ... ctrl+left click doesn't work.

Shift+left click (all files between two points) does.

Anyone suggest a fix, or further diagnostics ?

How the hell did 9,10 make it out of the door ?

---

### Post by coldraven on 2010-01-19
It works for me in 9.10 64bit, maybe you spilt some spleen on your keyboard ;)

---

### Post by beany1 on 2010-01-19
works for me also, dunno if it will affect it but do you have conflicting shortcuts? like in compiz or keyboard shortcuts? you tried both ctrl keys? to find if it is a hardware prob?

---

### Post by simonmoon42 on 2010-01-19
I know you probably checked already... but I had a similar problem. I selected the wrong keyboard on install.

---

### Post by Jethro_uk on 2010-01-19
> **beany1 said:**
> works for me also, dunno if it will affect it but do you have conflicting shortcuts? like in compiz or keyboard shortcuts? you tried both ctrl keys? to find if it is a hardware prob?

not hardware prob, as dual boot machine works 100% in XP.

Have checked keyboard shortcuts, can't find anything that is overwriting it.

When I try and ctrl-click the second selection, the previously highlighted selection "blinks", so the machine is definitely getting the click.

If you read my recent postings since upgrading *and* installing 9.10 you will know there is a show-stopping mouse bug somewhere very deep in linux. Many people have reported it with all combinations of window manager, window decorator, mouse hardware. 

Luckily, my brother told me about Webmin, which helps a bit ... I can administer my Linux box from windows - but I can't help but feel that's not how it's supposed to be :(

---

### Post by Jethro_uk on 2010-01-19
> **simonmoon42 said:**
> I know you probably checked already... but I had a similar problem. I selected the wrong keyboard on install.

well ... it's not installed as the *exact* keyboard it is (it's a Labtec ultra thin wireless), it's in as a "Generic super power media" keyboard. But on the basis all the media and web keys work great, I don't believe it's a keyboard problem, per se ...

---

### Post by rbscairns on 2010-01-19
I have Ubuntu 9.10 in a clean install and both the Ctrl+leftclick and Shift+leftclick work as expected.

Is your Ubuntu 9.10 a clean install or an upgrade (from what)?

---

### Post by lanierbrian on 2010-01-19
I have similar mouse problems that are driving me nuts.  Mouse click works intermittently, and I get "Could not grab your mouse..." when trying to use GUI upgrade manager.

Clean 9.10 install without a lot of stuff done since, machine us used as file/print server.  Updates/upgrades using apt-get as late as today.  I'm using a Logitech wireless mouse shared with XP machine through KVM, mouse and keyboard work fine on XP machine, worked fine on Ubuntu machine at first.  Same issues with mouse/keyboard connected directly to Ubuntu machine.

---

### Post by beany1 on 2010-01-20
i did a google an found some ppl with same problem, they all seem to have had it after installing compiz or changing/activating plugins, you could try reset compiz in compiz settings manager back to default? cant promise, but thats what id do

---

### Post by Jethro_uk on 2010-01-20
> **lanierbrian said:**
> I have similar mouse problems that are driving me nuts.  Mouse click works intermittently, and I get "Could not grab your mouse..." when trying to use GUI upgrade manager.

Clean 9.10 install without a lot of stuff done since, machine us used as file/print server.  Updates/upgrades using apt-get as late as today.  I'm using a Logitech wireless mouse shared with XP machine through KVM, mouse and keyboard work fine on XP machine, worked fine on Ubuntu machine at first.  Same issues with mouse/keyboard connected directly to Ubuntu machine.

Best of luck ... some folk have had this bug since 8.10:(

---

### Post by Jethro_uk on 2010-01-20
> **beany1 said:**
> i did a google an found some ppl with same problem, they all seem to have had it after installing compiz or changing/activating plugins, you could try reset compiz in compiz settings manager back to default? cant promise, but thats what id do

Nope, I have completely disabled Compiz. This is a rarely logged into box - no need for fancy stuff.

---

### Post by beany1 on 2010-01-20
you know when you select the files, does it show up in the status bar along the bottom that you have selected more than one file??

---

### Post by firefeather on 2010-01-20
Worth trying just in case; if you have a touchpad, check to make sure your touchpad isn't disabled while typing. I don't use that setting anymore but it caused a similar problem for me a while back.

---

### Post by Jethro_uk on 2010-01-21
> **beany1 said:**
> you know when you select the files, does it show up in the status bar along the bottom that you have selected more than one file??

No

---

### Post by beany1 on 2010-01-21
orrrite, does ctrl work in anything else? like ctrl c, maybe something to do with your xmodmap? could try > xmodmap -pmto see if ctrl is linked

---

### Post by lanierbrian on 2010-01-22
UPDATE:

My issue is resolved **at the moment**, but several things changed at once so I don't know which affected the issue:

(1) I took the Logitech wireless mouse receiver out of the KVM switch and plugged another wireless mouse (an older Microsoft) directly into the PC.  I had previously tried using the Logitech with the receiver plugged directly into the PC with same behavior, so I don't think the KVM was the issue.

(2) I installed a bunch of updates using apt-get update and apt-get upgrade (this was yesterday, 1/21/10 about 3pm EST).  I had previously downloaded upadates 24-48 hours earlier.

I'm not sure if this is the end of this or if I'm being lulled a feeling of relief only to have my hopes crushed tomorrow, but we'll see!

bl

---

### Post by Jethro_uk on 2010-01-25
> **beany1 said:**
> orrrite, does ctrl work in anything else? like ctrl c, maybe something to do with your xmodmap? could try to see if ctrl is linked

```
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

to be honest I gave up using ctrl+C on Ubuntu in 8.10 ... it seems to work depending on the app ... i tend to right-click and "cut/copy <-> paste" ....

---

### Post by sirishk on 2010-02-22
Try  ctrl+alt+left_click .... it works for me

---

### Post by Jethro_uk on 2010-03-01
> **sirishk said:**
> Try  ctrl+alt+left_click .... it works for me

nope ... not for me :-(

---

