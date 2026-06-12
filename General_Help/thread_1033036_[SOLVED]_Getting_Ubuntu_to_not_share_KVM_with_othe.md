---
title: "[SOLVED] Getting Ubuntu to not share KVM with other users"
date: 2009-01-06
forum: General Help
---

### Post by Kissell on 2009-01-06
This may not be Ubuntu specific, but I was hoping someone here could help, maybe it would be possible with different X-sessions?

I have a really powerful server with a lot of RAM, and its running Ubuntu.

I have Sun's VirtualBox installed, and I have two virtual machines running.

I want to have two monitors, two keyboards, two mice, hooked up to this powerful server.

What I would like to do, is dedicate one set of KVM to one virtual machine, and dedicate another set of KVM to another virtual machine.

Currently I plugged in another keyboard and mouse and I can use either mouse to play around and use both virtual machines and the OS...  but what I'd really like to do is have each mouse controlling its own virtual machine and not have them interfere with each other.  

This way I can use the server as multiple desktops with multiple admins, and pool resources, and not have to have completely separate hardware for each admin.  We already have a really powerful server, so I shouldn't need more than a monitor, mouse, and keyboard to give each user their own environment with it.  And one user can be running a windows XP virtual machine and be oblivious to it being a virtual machine, and when they're not using the computer I can have the whole powerful system to myself, bwahhhahaah!

---

### Post by bodhi.zazen on 2009-01-07
What you are talking about is called "Multi seating"

See 

[http://www.linuxtoys.org/multiubuntu/multiubuntu.html](http://www.linuxtoys.org/multiubuntu/multiubuntu.html)

[http://www.automation.dn.ua/linux/3d-multiseat_en.html](http://www.automation.dn.ua/linux/3d-multiseat_en.html)

I am sorry I do not have a better link, but those should get you started.

---

### Post by Kissell on 2009-01-07
That'll help a lot, I didn't know the term for it, so google wasn't being much help at figuring out what I meant without the keyword.

---

### Post by Kissell on 2009-01-07
Oh, one other quick related question.

I want to not run VGA and mouse cables all over the place with long runs...  I want to use a converter that can use CAT-5 cable to send those signals and then break it back out into VGA, keyboard, mouse on the other end...  I forgot what it's called, so I can't google it either...  KVM CAT-5 switch is not bringing me the opposite of the results I wanted...  I don't want one keyboard for multiple servers, I want the other way around but using CAT-5 to get to the desktop locations.

---

### Post by bodhi.zazen on 2009-01-07
I am not sure what it is called either

KVM splitter ?

[http://www.nti1.ca/kmspltpc.html](http://www.nti1.ca/kmspltpc.html)

---

### Post by Kissell on 2009-01-07
nah, if i used that then I wouldn't be able to tell the computer how each keyboard was different, they'd all appear to be the same keyboard, so I wouldn't be able to split them into different heads.

I'll post it back here if I ever remember it...  I know I've read about doing it, but it was a long time ago.

---

