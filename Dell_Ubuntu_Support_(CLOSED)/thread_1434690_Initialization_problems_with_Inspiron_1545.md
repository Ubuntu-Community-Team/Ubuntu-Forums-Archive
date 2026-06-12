---
title: "Initialization problems with Inspiron 1545"
date: 2010-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by galvao on 2010-03-20
Greetings.

I'm using a Dell Inspiron 1545 and Kubuntu Desktop 9.10 64 bits. I've been having some problems when turning the notebook on.

The most frequent issue is that KDE doesn't show the login splash screen, but seems to "try" to initialize as if the notebook wasn't turned off last time it was used (which, in each and every case it was). So it loads that splash where disk, settings, network, etc... icons fade in, but the only one which actually appears is the first (Disk). After that KDE just "freezes" (although I've recently found out that I can hit CTRL+ALT+DEL, to turn it off and try again).

Antecipating the question, it's not every time that this "turn off -> turn on again" works. On several occasions tha same issue happen, making me turning my notebook off and on a few times.

Today a "new" issue appeared: first, the login splash screen showed up, with the cursor active on the password field, as it should, but somehow the "focus" wasn't really there: I've had to click the field and then type so it would accept the keyboard input. After that, KDE seemed to load OK (all icons on the initialization splash screen appeared as usual) but it froze on the last icon (the "K" one), making me, once again, turn my notebook off, wait a few seconds and turn it back on.

Please notice that I have everything in it's latest version, including the Kernel.

Can anyone please shed some light on this? It's really nerve wrecking.

TIA,

---

### Post by bobcollard on 2010-03-21
> **galvao said:**
> Greetings.

I'm using a Dell Inspiron 1545 and Kubuntu Desktop 9.10 64 bits. I've been having some problems when turning the notebook on.

Please notice that I have everything in it's latest version, including the Kernel.

Can anyone please shed some light on this? It's really nerve wrecking.

TIA,
The first question that comes to mind is how are you turning this computer off?  If you are using the power button or any other method than a software shutdown, then, that is your problem.  Even with it set to shutdown with the lid closing it gives the software time to shut itself down properly.  There is some maintenance even on these fast computers that need to be done before everything quits.  You may notice, I have the same model.  I prefer xfce to gnome or kde but it is still ubuntu based.

---

### Post by galvao on 2010-03-21
But that's the thing: I *always* use software shutdown. I even tried waiting for Kubuntu's 30 seconds timer and let it shutdown after that. Nothing seems t work...

---

### Post by bobcollard on 2010-03-21
> **galvao said:**
> But that's the thing: I *always* use software shutdown. I even tried waiting for Kubuntu's 30 seconds timer and let it shutdown after that. Nothing seems t work...
Are you using auto-login?  I've seen some problems in the forums about that lately.

---

### Post by galvao on 2010-03-21
No, I don't. I always enter my password on the login splash.

---

### Post by bobcollard on 2010-03-21
> **galvao said:**
> No, I don't. I always enter my password on the login splash.
Have you changed your login and splash?  I know you can easily enough in KDE.  I'm shooting in the dark here.

---

### Post by galvao on 2010-03-21
> **bobcollard said:**
> Have you changed your login and splash?  I know you can easily enough in KDE.  I'm shooting in the dark here.

And I really appreciate that.
I've once changed the initialization (the one that loads those disk, network, etc... icons), but after I've noticed these issues I chenged back to the default Kubuntu initialization splash.

Antecipating the question: I'm not 100% sure if the problem emerged only after I've changed the initialization screen, but it's possible. But even so, shouldn't the problem be fixed, since I went back to Kubuntu's default?

Once again, thank you for your effort. It's good to have someone trying to figure this out with me =)

---

### Post by bobcollard on 2010-03-21
> **galvao said:**
> And I really appreciate that.
I've once changed the initialization (the one that loads those disk, network, etc... icons), but after I've noticed these issues I chenged back to the default Kubuntu initialization splash.

Antecipating the question: I'm not 100% sure if the problem emerged only after I've changed the initialization screen, but it's possible. But even so, shouldn't the problem be fixed, since I went back to Kubuntu's default?

Once again, thank you for your effort. It's good to have someone trying to figure this out with me =)
How hard would it be to back up your home directory and reinstall it?

---

### Post by galvao on 2010-03-21
This is quite impossible, at least for two weeks or so... I'd really like to avoid this option, if possible :(

---

### Post by bobcollard on 2010-03-21
> **galvao said:**
> This is quite impossible, at least for two weeks or so... I'd really like to avoid this option, if possible :(
Sorry I mentioned it, I don't know what your situation is.

---

### Post by galvao on 2010-03-21
No, please don't be sorry, it's OK. I just wish there was a solution for this and on top of that it's kinda worrying to think that a simple theme could do this kind of damage (IF it is the real cause).

---

