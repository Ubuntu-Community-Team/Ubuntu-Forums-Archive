---
title: "auto internet"
date: 2009-04-11
forum: General Help
---

### Post by tony12 on 2009-04-11
Hi!

IU have installed ubuntu 9.04 and love it. I would just like to know is there are way I can set to log onto internet auto without putting in my password every time I turn the computer on?

Thank You

---

### Post by blazemore on 2009-04-11
Do you mean to connect to a wireless network?

---

### Post by tony12 on 2009-04-13
Hi!

I mean in windows  when you turn on the computer u are automaticly on the net,you just open internet explore. In ubuntu when I open firefox it asks me the password for the system.

---

### Post by leonardo_neo on 2009-04-13
Well, by default it should do it in the way you are asking for...

When you first time connect to your wireless, it asks you to save the wireless configuration login name and password in keyring manager, and to access that information, it asks you to set up a password. That's it, once you are done with this, you don't have to enter your network keys again. 

Do you have to enter your network keys again every time you wish to connect to internet??

---

### Post by tony12 on 2009-04-13
Hi!

 First I would like to thank you all in the ubuntu world. I have find this forum very helpfull so far and I know I will in the future.

Its asking for a default keyring to access the network manager. Could that be when I installed the OS keyring? Maybe should have left it blank?

Thank you

---

### Post by leonardo_neo on 2009-04-13
> **tony12 said:**
> Hi!

 First I would like to thank you all in the ubuntu world. I have find this forum very helpfull so far and I know I will in the future.

Its asking for a default keyring to access the network manager. Could that be when I installed the OS keyring? Maybe should have left it blank?

Thank you

This keyring password is different from your 'root' password. You can choose whatever password you like. But for convenience, it is better to give it the root password, so that you can recall that easily in case you need that some time.

Just fill it in, and start using your internet.

---

### Post by tony12 on 2009-04-13
Hi!

Yes I know that but if I would just like to get in without fill anything that would be great. So, can I or not?

Thank you

---

### Post by benerivo on 2009-04-13
You could try replacing the default network manager (the one that is asking you for a password every time), with the wicd network manager from the repositories. I think installing it will cause the default manager to be automatically removed and replaced wih wicd, which won't ask you for a keyring password every time.

I think there is a way to set up the default one so that it doesn't request a password but i haven't used it in a while so i can't remember.

---

