---
title: "can't switch user after installing vga driver"
date: 2008-05-13
forum: Desktop Environments
---

### Post by benquick on 2008-05-13
dear ubuntu masters, anyone know why?, after I installing vga driver, I can't switch user.
usually I making 2 user, one for administration, and the other one, use for standard user, i do this for securing only, i had a five computer for client, and one for server. for client user, computer specification not so good, only use cheap computer with spec mb: pcchip (onboard: vga "via technology", lan sound,)proc: intel cel 3Ghz, mem: 512. everyting can work correctly on hardy, I only can't swich user, thats all.

I was posting this thread before i don't know why this happen on my client computers
this is my thread before:
> 
[http://ubuntuforums.org/showthread.php?t=779752&highlight=can%27t+switch+user](http://ubuntuforums.org/showthread.php?t=779752&highlight=can%27t+switch+user)


---

### Post by lemming465 on 2008-05-19
No real idea; switch user is OK for me on Hardy (using an archaic nvidia graphics chip).  I believe the graphical switch user brings up a second Xserver, so if the display driver is locking some hardware video resource, that could account for the problem.

Some possible alternatives:
* Use a standard VESA video driver, if that has OK performance.  That might allow user switching again.
* Use the [Ctrl]+[Alt]+[F1] key chord to switch to a text console, and log in at the terminal as a different user.  [Alt]+[F7] will usually switch back to the graphical session.
* Use*sudo* or *su -* or *gksu* to run a command (or a whole series of commands) as a different user without logging out the original user

---

