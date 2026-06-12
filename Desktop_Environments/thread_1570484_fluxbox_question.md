---
title: "fluxbox question"
date: 2010-09-08
forum: Desktop Environments
---

### Post by pythonsyntax on 2010-09-08
After you install fluxbox how do i get it to start up on ubuntu 9.10?And what are the step i need to take.

---

### Post by Joe of loath on 2010-09-08
Did you install onto the desktop edition or server edition? The sever edition will start it automatically, the desktop edition you have to select it from the 'sessions' menu on the login screen.

---

### Post by pythonsyntax on 2010-09-08
i useing ubuntu 9.10

---

### Post by Joe of loath on 2010-09-08
Yes you said, but the desktop version (With gnome) or the server editon (terminal only)?

---

### Post by pythonsyntax on 2010-09-08
desktop with gnome

---

### Post by Joe of loath on 2010-09-08
Then once fluxbox in installed, log out, click the 'sessions' menu at the bottom of the screen, and fluxbox should be there.

---

### Post by sikander3786 on 2010-09-08
> **Joe of loath said:**
> Then once fluxbox in installed, log out, click the 'sessions' menu at the bottom of the screen, and fluxbox should be there.
Before clicking 'sessions' make sure you click your username first and then the options will be visible :-)

---

### Post by pythonsyntax on 2010-09-08
I don't have that on 9.10

---

### Post by pythonsyntax on 2010-09-09
anyone?

---

### Post by Joe of loath on 2010-09-09
I'm pretty sure you have something similar. Have a poke around and see what you can find.

---

### Post by pythonsyntax on 2010-09-09
I check and i don't see that up when i login in 9.10

---

### Post by sikander3786 on 2010-09-09
> **pythonsyntax said:**
> After you install fluxbox how do i get it to start up on ubuntu 9.10?And what are the step i need to take.
So fluxbox is not listed in sessions menu in GDM. I doubt if it is installed at all. How did you install it? What is the output of

```

locate fluxbox

```

and

```

which fluxbox

```

---

### Post by pythonsyntax on 2010-09-09
apt-get install fluxbox

---

### Post by sikander3786 on 2010-09-09
Can you please tell what options have you got under the sessions menu? Normally they are "failsafe gnome", "gnome" and "xterm".

---

### Post by pythonsyntax on 2010-09-09
there no 'sessions

---

### Post by Nythain on 2010-09-10
ok, when you boot your computer... before you log in, it will take you to a window where you select your username and put in your password... dont do that yet... just select your user... after selecting your user, somewhere on that screen a "sessions" menu should become available (i forgot what gdm looks like on 9.10 so i cant tell you exactly where on the screen)... in that sessions menu should have entries like GNOME, Safe Whatever, XTerm, and there should be one for Fluxbox...

select the fluxbox one, then put in your password and log in

---

### Post by sikander3786 on 2010-09-10
> **pythonsyntax said:**
> there no 'sessions
Strange. Can you somehow post a screenshot of your login screen?

There is an option in Lucid to select the default DE from System >>> Administration >>> Login Screen. It should also be present in 9.10. Try selecting fluxbox from there.

---

### Post by pythonsyntax on 2010-09-10
it not let me log in to flux box?

---

### Post by sikander3786 on 2010-09-10
> **pythonsyntax said:**
> it not let me log in to flux box?
Please be a little more specific about your problem when asking for help. It doesn't let you login? How? What happens then? Any error messages?

---

### Post by stanca on 2010-09-11
Check if you have the auto login enabled.

---

### Post by pythonsyntax on 2010-09-14
no it not

---

