---
title: "Starting Gnome Shell at Login"
date: 2010-11-13
forum: Desktop Environments
---

### Post by Dobbie03 on 2010-11-13
I just installed GS following the instructions here:
[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)

and the classic way  of getting GS to start at login (adding gnome-shell --replace in start up applications) doesnt work.

To start GS now we have to use the command "~/gnome-shell/source/gnome-shell/src/gnome-shell --replace" via the terminal adding that to start up doesnt work either, does anyone know how to get GS to start at login?

---

### Post by Dobbie03 on 2010-11-13
Disregard, thanks to a very helpful person at Webupd8, I created a script to start at boot.

---

### Post by cariboo on 2010-11-13
You don't need to create a script, if you are running maverick, install gnome3-session from the repositories, then you can choose your session from the login screen. BTW gnome-shell from the ricotz staging ppa is pretty up-to-date, it's currently at 2.91.2.

---

### Post by Dobbie03 on 2010-11-13
LOL I wish I had known that earlier...oh well thanks anyway :)

---

### Post by nilarimogard on 2010-11-14
> **cariboo907 said:**
> You don't need to create a script, if you are running maverick, install gnome3-session from the repositories, then you can choose your session from the login screen. BTW gnome-shell from the ricotz staging ppa is pretty up-to-date, it's currently at 2.91.2.

The Ricotz staging PPA has packages for Natty, not Maverick:

[https://launchpad.net/~ricotz/+archive/staging/+packages]("https://launchpad.net/~ricotz/+archive/staging/+packages")

And I don't think Matt is running Natty already...

---

### Post by Harry33 on 2010-11-14
If one uses Rico's PPA (named "Testing PPA" at the moment, not Staging), one must use Natty (and with all updates).
If anyone wants to stick to Maverick, he or she has to use the official repos of Maverick.

In both of those cases it is handy to use the package gnome3-session of the repos.
Then you can choose from the login screen to use either
Gnome3 session (Gnome-Shell) or
Ubuntu Desktop Environment (Gnome-Panel).

Another option is of course to build with jhbuild.

---

### Post by Dobbie03 on 2010-11-14
> **nilarimogard said:**
> The Ricotz staging PPA has packages for Natty, not Maverick:

[https://launchpad.net/~ricotz/+archive/staging/+packages]("https://launchpad.net/~ricotz/+archive/staging/+packages")

And I don't think Matt is running Natty already...

No you're right, I am still using Maverick.

---

