---
title: "How to setup Ubuntu with no keyboard or mouse..."
date: 2009-01-03
forum: General Help
---

### Post by Shaelesand on 2009-01-03
I am making the big switch from Windows to Ubuntu.  I already switched my subnotebook.  Now I have server to switch over.  It has no keyboard or mouse or monitor.  If I can get it to the point where I can log on remotely and play I can finish it off.

It currently has windows XP, RDP stopped functioning a while ago (surprise surprise...) and it has only been used to store files for months.  Is there anyway I can setup a file to guide the install?  As soon as the server is done I can switch over my final computer, a laptop so I can't borrow the keyboard and mouse.

I have tried searching but everything I have found so far has not been what I am looking for.  Can you help me?  Please?

---

### Post by IllegalCharacter on 2009-01-04
You can try creating your own Ubuntu image with openssh-server installed, at that point you'll be able to SSH in with PuTTY or something. This guide here: [http://ubuntuforums.org/showthread.php?t=855849](http://ubuntuforums.org/showthread.php?t=855849) has a way to do it but it is quite involved.

If that doesn't work, you might have to try and find a keyboard/monitor (maybe at a friend/family member's house?) to plug into the machine, install openssh-server and then you won't need them anymore.

---

