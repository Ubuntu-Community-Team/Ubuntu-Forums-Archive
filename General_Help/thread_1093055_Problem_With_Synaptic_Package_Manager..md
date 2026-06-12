---
title: "Problem With Synaptic Package Manager."
date: 2009-03-11
forum: General Help
---

### Post by rajeevkr on 2009-03-11
[FONT="Georgia"]Guys Help Needed.

Im not very familiar with UBUNTU. Have started using it very recently.

I have a problem with the synaptic package manager from the past 2 days.
See everytime I open it I get this error message

"[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]"

I tried running that dpkg command from the terminal, but it says

"**dpkg: requested operation requires superuser privilege**"

What do I do? Help me out!

Thanks In Advance.
Rajeev.[/FONT]

---

### Post by jeroen.kurvers on 2009-03-11
try sudo [FONT=Georgia]dpkg --configure -a[/FONT]

---

### Post by iaculallad on 2009-03-11
Do what the message implies. Open your terminal and input the command below:

```
sudo dpkg --configure -a
```

Issuing the command above will require you to input your password. Characters you're typing will not be echoed back in your monitor. Just complete typing your password and press the Enter key.

---

### Post by MaxIBoy on 2009-03-11
Yeah, use sudo.

It will want a password, but if you type it, nothing will appear on the screen. This is normal, it's so someone can't look over your shoulder and count how many letters are in your password.

---

### Post by bearslumber on 2009-03-11
Hi RajeevKR,

Not sure why Synaptec Package manager is not working.

But I think I can help you with the running of "dpkg".

Make sure you always precede dpkg with sudo.

For example:

> sudo dpkg

**Background:** All commands considered as privileged, such as the changing of software packages, must only ever be executed by someone who has the privilege. the commands change the environment and/or system outside the scope of our private domain.

As ordinary users we are by default given ordinary privileges. i.e. to be able to execute anything that does not change the environment outside our own private domain. In order to change something that can affect the system (outside our private domain) we need to have elavated privileges.

The command "sudo" elavates you to the "super user" (hence su) but only after you have provided the password to verify that you are indeed the user who can elavate himself to a super user. There is also a level of having to verify the inention of making such a change.

Hope that helps.

Regards

Mr Bear

---

### Post by rajeevkr on 2009-03-11
[FONT="Tahoma"]Thanks a ton guys.

Its fine now. I didn't know I had to type sudo before the command.
U guys have been of great help.

Thanks a ton.

Cheers,
Rajeev[/FONT]

---

