---
title: "LXDE, GNOME, XFCE...confused..."
date: 2015-08-02
forum: Desktop Environments
---

### Post by kunitoki2 on 2015-08-02
Hey and greets from Germany!
6 months ago I made the transition from Win (95, 98, XP, 7) to Linux (Lubuntu because I am obsessed with small and lightweight and responsive and fast) - so far I love it.
I still dual boot with Grub but for weeks I haven't used Win at all - I guess I will purge it forever soon.
Linux I am still learning but it's a lot of fun.
Here's what's confusing me right now: Lubuntu has a lot of apps and they all work - but why?
The media player is GNOME MPlayer, the power manager is XFCE Power Manager...I know these are different desktop environments and I am using LXDE right now.
How come these apps work?
Aren't they part of different desktop environments?
Don't they depend on libraries only those environments provide?
I can't imagine that every DE provides all the libraries of all the other DEs so every app works in every DE - what a bloat that would be.
Or are these just labels that don't really mean anything and they work because they have been developed using toolboxes like GTK or something like that?
Maybe stupid questions but as I said before I am still in the phase where I put the pieces together and although a lot in the linux world makes sense to me, there are still things that are confusing. :)

---

### Post by grahammechanical on 2015-08-02
Your are forgetting something.

It is the word Linux. We use a Linux distribution. There are different Desktop Environments and User Interfaces and some desktop environments come with their own versions of utilities. But there is nothing to stop the developers of say, Lubuntu, from using a utility written by the Gnome developers. The utilities are still Linux software.

There is also something else to remember and that is the word Ubuntu. So, the Lubuntu developers use Ubuntu as a base. This means that there are many libraries that are common to Linux distributions. And this is also true for those distributions based upon Ubuntu.

Perhaps you should investigate how the Debian package method works. It is Debian packaging that informs the package manager which installs the software what libraries a particular package/application depends on (dependencies).

If there is any bloat it is in the repositories that the Ubuntu developers maintain. Those repositories have to contain all the libraries for all the DEs and UIs used by Ubuntu and its family of distributions.

Regards.

---

### Post by vasa1 on 2015-08-02
You could look at the output of **apt-cache show *package_name*** to find out what each application needs in order to run on *any* desktop environment.

---

