---
title: "What's the root's password."
date: 2006-01-08
forum: Desktop Environments
---

### Post by gopherxiao on 2006-01-08
Dear all,

Nice to meet u at the Ubuntu Forum. I'm a new comer. Yestday I install Ubuntu 5.1 to a IBM T21. During the installation, no question ask me to input password for 'root'. Could anyone be kind to tell me what the password for 'root' is? Thx!

---

### Post by Thirsteh on 2006-01-08
There is none, noone knows, or rather, it's your normal user's password. It's a nifty little convention in Ubuntu that supposedly makes it more secure, and I would agree.

If you wish to do things as root, simply do 'sudo <command>' as your normal user, and enter your own password when you are prompted. Also, any 3rd party application that prompts you for your root password should work just fine when you enter your own password. 

It is possible to enable your root account and set your own password, but I wouldn't recommend it.

Good luck with and enjoy Ubuntu.

Edit: It's only your own user that can access root in this way. Any other users would have to be explicitly permitted in your sudo configuration file.

---

### Post by gopherxiao on 2006-01-08
Thanks Thirsteh very much!

I just foloowing [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to update my firefox to v1.5 and puzzled that what 'sudo' is for. Your reply give me the answer to. Thx!

---

### Post by Thirsteh on 2006-01-08
My pleasure, and once again good luck with this awesome Linux distribution.

---

