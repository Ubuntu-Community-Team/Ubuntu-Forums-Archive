---
title: "Broken perl packages - how do I fix?"
date: 2009-02-23
forum: General Help
---

### Post by poo706 on 2009-02-23
- Ubuntu 8.10 -  Help!  I went monkeying around with stuff that I probably shouldn’t have, and now I don’t know how to undo what I did.  I download a .deb for CheckGmail, but when I tried to install it, it complained about libgtk2-trayicon-perl, so I downloaded a .deb for that.  When I tried to install that, it complained about the version of perl.  So I got a .deb for 5.10.0-19, and when I tried to install that, it complained about the version of perl-base, so I got a .deb for 5.10.0-19.  When I installed that, it seemed to go smooth at first, but then resulted in 2 broken packages.  In my panic, I got a .deb for libperl-dev_5.10.0-19 and tried to install that.  Now I have 3 broken packages:

libperl5.10 (installed version 5.10.0-11.1ubuntu2.2)
libperl-dev (installed version 5.10.0-19)
perl (installed version 5.10.0-19)

I have tried “sudo apt-get install  –f”, but it fails.  Libperl5.10 depends on perl-base (= 5.10.0-11.1ubuntu2.2) but 5.10.0-19 is installed.  Perl depends on perl-modules (>= 5.10.0-19) but 5.10.0-11.1ubuntu2.2 is installed.  Resolve generated breaks.  

Seemingly, the only option through Synaptic is to uninstall these broken packages, but it looks at though it’s going to take a whole long list of installed software along with it.  What can I do?  Thanks!

[poo]

---

### Post by mc4man on 2009-02-23
What I'd do is this
Remove libperl-dev (or mark for removal
Search perl in synaptic and find ALL the packages you upgraded to 5.10.0-19
One at a time highlight the package and then click on the 'packages' tab -> force version. Choose the 5.10.0-11.1... version for each one. Once you have them all marked for downgrade then click the green 'apply' button (don't click apply till they are all marked for downgrade

---

### Post by poo706 on 2009-02-23
When I mark libperl-dev for removal, it also marks everything that uses perl for removal as well.  Is that really what I want to do?

[poo]

---

### Post by mc4man on 2009-02-23
> Is that really what I want to do?
no
see if you can mark the -dev to be downgraded along with the others

otherwise wait for some other idea's

---

### Post by poo706 on 2009-02-23
My x11vnc connection seems to have gone down for some reason, so I can't try anything until I get home.  By the way, I haven't rebooted since I caused this whole mess for fear that it won't boot up.  Is there any reason I should or shouldn't at this point?

[poo]

---

### Post by poo706 on 2009-02-23
None of the three broken packages will let me force a version, the option is grayed out.  Is there a terminal command that accomplishes this same thing?

[poo]

---

### Post by poo706 on 2009-02-23
BOO-YAH!  I fixed it!  I ended up tracking down the 5.10.0-11.1ubuntu2.2 versions of perl-base and perl.  Then I ran "sudo dpkg -i xxxx.deb", first on perl-base, then on perl, and that took care of it.  Learned a lot in the process, including a valuable lesson.  Thanks for the help!

[poo]

---

