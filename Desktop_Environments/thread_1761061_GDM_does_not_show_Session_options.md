---
title: "GDM does not show Session options"
date: 2011-05-17
forum: Desktop Environments
---

### Post by azad on 2011-05-17
I have Ubuntu 11.04 with Unity 2D running smooth on my machine.

I decided to give LXDE a run so I installed the packages from USC.

After rebooting the PC, I was expecting to have a list of options on the GDM where I could select LXDE or Lubuntu. But the Session options do not appear in GDM.

I selected Lubuntu in my Login Screen Settings but it still logs into Unity 2D after reboot (I've tried options LXDE, Lubuntu Netbook but results the same.)

Here is a screenshot of my Login Screen Settings:
[http://i.imgur.com/2IoDw.png](http://i.imgur.com/2IoDw.png)


So, here's the question: How do I log into LXDE (or any other DE for that matter)?

Why doesn't GDM show session options?


Any help is appreciated. Thanks in advance.

---

### Post by Krytarik on 2011-05-17
> **azad said:**
> 
Why doesn't GDM show session options?

To make them appear (at the bottom), you need to click at your username first.
Did you do that?

Greetings.

---

### Post by azad on 2011-05-18
When I click my username, it logs in instantly and does not ask for my password.

---

### Post by mcduck on 2011-05-18
> **azad said:**
> When I click my username, it logs in instantly and does not ask for my password.

In that case you'd probably better disable the passwordless login for your user, at least when you wish to switch to a different session.

The option for that is in Users & Groups. Just select your user and then click the "Change"-button next to the "Password"-field. You'll get a dialog for changing the password, and at the bottom is a checkbox called "Don't ask for password at login". Disable that and you'll be able to switch your session in the login screen.

---

