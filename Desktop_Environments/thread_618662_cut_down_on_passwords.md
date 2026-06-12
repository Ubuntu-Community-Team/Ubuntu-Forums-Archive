---
title: "cut down on passwords"
date: 2007-11-20
forum: Desktop Environments
---

### Post by odindio on 2007-11-20
I'd like gnome only to challenge me with a password when I login and run sudo commands from the command line.  Is that possible?  I don't want to be challenged when I go into the packet manager, services, or screen and graphics...etc.  I'm just playing around with ubuntu.  I don't use it to store anything sensitive, and I just have it on a couple of old junker PCs on my network.  Thoughts? Comments? Suggestions?

---

### Post by edd07 on 2007-11-20
The thing is, the package manager and all that other stuff **are**, as you call them, sudo comands.  They need root privileges because packages are sensitive information. If you still don't want to, you can login as root, but that is EXTREMELY discouraged. Ubuntu doesn't even enable it by default.

Oh, and you post was inaccurate. Screen stuff doen't ask for a password ;-)

---

### Post by happysmileman on 2007-11-20
You can make it so you can run "sudo" without a password by manually editing /etc/sudoers, it says how in there somewhere in a comment (small file, you can't miss it).

Not sure how to do it for graphical programs, either way I'd reccomend you don't, but I suppose for a personal computer if you have everything backed up you might just prefer ease of use than security

---

### Post by Nem1976 on 2007-11-20
> **edd07 said:**
> The thing is, the package manager and all that other stuff **are**, as you call them, sudo comands.  They need root privileges because packages are sensitive information. If you still don't want to, you can login as root, but that is EXTREMELY discouraged. Ubuntu doesn't even enable it by default.

Oh, and you post was inaccurate. Screen stuff doen't ask for a password ;-)


Actually he's correct if you go into anything under the Administrator menu like Screens and Graphics it requires the sudo password.

As for the prompt for the password ya I know it's a little different but honestly once you get used to it being there it becomes second nature.

---

### Post by odindio on 2007-11-20
Wow! What a response.  I thank everyone for there input (even you password junkies :lolflag:). Just kiddding:)

Essentially I'll just log in as root if I'm going in to play around with some serious system modifications.  Which is pretty much all I'm going to do. 

Loging out afterward is obviously wise.

I

---

