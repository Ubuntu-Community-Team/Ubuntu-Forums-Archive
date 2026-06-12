---
title: "Custom Ubuntu Development"
date: 2014-02-19
forum: Desktop Environments
---

### Post by sagar5 on 2014-02-19
Dear Guys , 

       I am looking ahead to develop a custom distro from ubuntu iso . I am half way done. Now I need to change the Ubuntu logo from the OS and need to give my own logo for my custom os. More over , I would like to create a custom credit app like " About Us " just like say "About xfce " or  " About Mint " in their respective DE or dervivative. I would like to use a custom word instead of sudo in ubuntu- How to accomplish that , I dont want to set alias in bash for sudo , Instead I need to use custom word in distro . 

Please help me accomplish the above task dear geeks.

---

### Post by Tristan_Williams on 2014-03-01
You would not be able to use a "custom word" without an alias.

This is because "sudo" is a program, just like htop or links.
You theoretically could change it, but that would require changing /usr/bin/sudo to /usr/bin/[whatever-you-want]

You would also have to change "/usr/bin/sudo" to the new name at every place which has a reference to /usr/bin/sudo
because (since you changed it to something else), /usr/bin/sudo does not exist anymore.

But i seriously doubt you want to do all that, so no, you can't do it without an alias (easily)

---

### Post by ian-weisser on 2014-03-02
> **sagar5 said:**
> I am looking ahead to develop a custom distro from ubuntu iso

Seems like you merely want to rebrand an Ubuntu release as something else.
The changes you propose seem minor and entirely cosmetic.

Be sure to read: [http://www.ubuntu.com/intellectual-property-policy](http://www.ubuntu.com/intellectual-property-policy)
You can de-brand or rebrand Ubuntu all you wish, but Canonical won't support it with software package repositories, security updates, nor support infrastructure when you do so. If you intend to distribute your new distro, must create your own infrastructure.
Debian has no such limitation on rebranding. It might be a better candidate for your proposed distro.

Is there a difference between your proposed distro and Ubuntu that makes all that work worthwhile?

---

