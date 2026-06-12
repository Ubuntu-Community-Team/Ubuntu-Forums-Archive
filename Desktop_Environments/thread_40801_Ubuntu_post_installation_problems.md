---
title: "Ubuntu post installation problems"
date: 2005-06-10
forum: Desktop Environments
---

### Post by Vertical on 2005-06-10
Hello

I installed Ubuntu 5.10 in expert mode. During install I set up root password & user account.

Now, when I log under regular user I can't run any program, which need root priviligies. For example, command for running Gdm Setup in GNOME menu is: 'gksudo gdmsetup'. When I type this in console just nothing happens! The same is with synaptic and any other program. When I type just program name 'gdmsetup' or 'synaptic' system says I need root privilegies. I need to swith to root user with su, but I don't really like this way.

That confuses me. Are there any way to make ubuntu ask for root password, when I'm trying to run program from GNOME menu?

Thanks

---

### Post by sethmahoney on 2005-06-10
I'm not sure if this answers your question or not, but:

-When you launch a program from the menu that requires root privileges, Ubuntu should ask for your password.  Is it not doing this?

-When you're launching a program from the terminal that requires root priviliges, you should use:
```
sudo command
```
where "command" should be replaced with whatever program you're trying to launch, for example:
```
sudo synaptic
```

gksudo is just the gui version of sudo - it should pop up a dialog box asking for your password.  sudo, on the other hand, just asks for the password in the terminal window.

---

### Post by wylfing on 2005-06-10
Vertical, this behavior is to protect you from anyone executing malicious code. Whenever you want to run programs that can affect the state of your system, like installing new software (e.g., synaptic) you will need to escalate your priveleges by typing your password. Like sethmahoney stated, preface the 'synaptic' command with 'sudo'. It will ask for your regular user password.

---

