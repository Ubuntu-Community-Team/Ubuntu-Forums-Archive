---
title: "Serious Problems with Sudo and other Root stuff"
date: 2005-06-23
forum: Desktop Environments
---

### Post by semilemon on 2005-06-23
Hello. I'm a newbie and I have installed Ubuntu alongside XP today, and since have had many troubles.

First of all, the installer had me set up the root account, which some people say they have never heard of. When I first log in, I get an error telling me it couldn't connect to an IP address, and so Gnome may not work properly. Once I'm in linux, I get errors each time I use 'sudo' or anything under the "Administration" menu, such as networking or User Accounts and Groups, Have any ideas?

---

### Post by semilemon on 2005-06-23
When I first log on, It says the internet address for ubuntu couldnt be aquired. It also said adding ubuntu to the /etc/hosts file may resolve the problem, but I'm not sure what this means. Could this be the reason I have had so many problems (ie. cannot open 'Networking' or 'User Groups and Accounts', or can't use sudo?

---

### Post by fares on 2005-06-23
Hi there and welcome to Ubuntu.

[QUOTE=semilemon]
First of all, the installer had me set up the root account, which some people say they have never heard of. [/QUOTE]

- Probably the people you're talking about aren't really familiar with Linux, by the way a root account is an all-access/no-limits account. Root is the account owned by the system administrator (in this case you) and it's a necessary account on a Linux system, so in this case it's a 'standard' account.

[QUOTE=semilemon]
When I first log in, I get an error telling me it couldn't connect to an IP address, and so Gnome may not work properly. Once I'm in linux, I get errors each time I use 'sudo' or anything under the "Administration" menu, such as networking or User Accounts and Groups, Have any ideas?[/QUOTE]

I'm  not really sure about what your problem is, so if you could give me a more specific description of the problems/errors my answer would be more accurate... anyway I'll give it a go:

Are you referring to the password related to the use of the root account? i.e. when you click on, say, 'networking' a little window appears asking you to fill a password in (the password of the root account). If so and if you are using Ubuntu, try to type in the same password you use for your account, it should work.

Regards,

fares

---

### Post by semilemon on 2005-06-23
I'll get you the exact error message right away (I'll need to switch back to Ubuntu from windows), but when I click on networking, the "circle thing" (I'm assuming it means linux is doing something) appears for about 10 seconds and disappears, and no windows pop up. And it is not just networking, basically all the items under "Administration" and in "System Tools" (under Applications) behave in the same way.

---

### Post by semilemon on 2005-06-23
I just though of something else.

During the install, after creating the root account, I believe (though I'm not 100% sure) I had the option to create a regular user account, for obvious security reasons. However, if I did not do it then, I would have to be the the root account when I start ubuntu, so then I could create accounts from there, and maybe eliminate these problems all together (this isn't the only problem I'm having)? Just a thought, but what do you think?

---

### Post by debian_n00b on 2005-06-23
Hey there. I had the exact same issue with sudo/root the first time I installed ubuntu. I reinstaled and all is well.
The only thing I did differently the second time around was to specify a unique hostname when asked. The default was Ubuntu.

---

### Post by fares on 2005-06-26
Hi there, and sorry for the late reply.

@semilemon: yep, Ubuntu asks you to create a regular user account, and basically the password you choose is the same password you'll use for superuser(=root) tasks.
I think that the problem you have comes from sudo - I had something similiar during one of the latest updates. You could try to open a terminal (Applications -> System Tools -> Terminal) and type something like this:

sudo synaptic

It should prompt for the root password, use the same password you used to log in your standard user account. If it says something like "Sorry, try again" or that some child process failed, the problems come from a file named /etc/sudoers.

To solve the problem reboot your Ubuntu system choosing 'recovery mode' from the bootloader menu, it will load some things and you'll find yourself in front of a black & white screen with a prompt.

At the prompt write:
```

nano /etc/sudoers

```

It should show you some code, look for this section:
```

# User privilege specification
root ALL=(ALL) ALL

```
In my case, I have a second line under it, precisely:
fares ALL=(ALL) ALL
Your username should be there too, if not just add it - for ex.:
```

# User privilege specification
root ALL=(ALL) ALL
semilemon ALL=(ALL) ALL

```
Look at the bottom of the screen and you'll find that CTRL+O is needed to save the file, and then CTRL+X to exit the nano editor.
Your problem should be solved, at the prompt type:
```

shutdown -r now

```
This will restart your PC and you can load Ubuntu Linux in the usual way.

Hope it'll work!

@debian_n00b
When I first installed Ubuntu I left the hostname 'Ubuntu' too. This didn't cause any problem with my system, I eventually changed it via the Administration menu - Network Settings.

Bye,

Fabio

---

### Post by Curlydave on 2005-06-26
Do you have a DHCP internet connection? No? Then good luck getting Ubuntu configed right out of the box. It needs one on install or it will mess up some of your files and you have to fix them, and many things won't be set up right. Basically you need a router or a T1 lined etc; basically a connection that works automatically. You can set up other types later, but you'll still get a messed-up install.

---

