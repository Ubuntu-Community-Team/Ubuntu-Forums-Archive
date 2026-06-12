---
title: "Root????? (Solved)"
date: 2005-11-04
forum: Desktop Environments
---

### Post by americymru on 2005-11-04
Hi

Ive been using Linux for three years and I recently decided to try Ubuntu. I am very pleased with it and  it will almost certainly be my distro of choice in the future. I have just one problem. Whenever I su I am asked , quite properly , for a password. The only password I have is the one I assigned to the admin user during installation. This password does not work. I am sure I have overlooked something simple and I was hoping someone could tell me what it was. At the moment when I am online as an unprivileged user I cannot run my firewall ( firestarter ) or at least I cannot have access to the gui. What have I missed ? Where is my root password?

Best Regards CS  :confused:

---

### Post by rwh on 2005-11-04
Ubuntu uses sudo for most administrative stuff.  So, you can type "sudo aptitude" and be asked for your (normal user) password, and be running aptitude as root.  You could also run "sudo su" if that's what you want to do ;)

---

### Post by HermanAB on 2005-11-04
Here is the full explanation:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Cheers,

H.

---

### Post by etlgfx on 2005-11-04
there are probably a bunch of other threads about this, but here's your answer.

Ubuntu doesn't assign a root password at all at install time, instead it sets up sudo, so you can do a single su(peruser) command. It asks you for your normal user password once (with a timeout).

so if you wanna run apt-get install whatever-package, it won't let you because you don't have root privileges, instead:

$ sudo apt-get install whatever-package

if you really need the su command (like me) because you don't wanna type sudo 309345098 times you can try:

$ sudo passwd root

this will ask to create a root password.

---

### Post by americymru on 2005-11-04
Hi

Thanks for the speedy responses.  I just went out for a cigarette and by the time I got back I already had three replies!!!!

I think since im used to ye olde Linux ways i'll use the "sudo passwd" approach.

Thanks for saving me a lot of head scratching.

Best Regards CS   :smile:

---

