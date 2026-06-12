---
title: "beryl and gtk+ themes"
date: 2006-12-14
forum: Desktop Environments
---

### Post by Circus-Killer on 2006-12-14
alright, before i begin, let me just say i have searched the forum for an answer. i've found posts that deal with a similar problem, but not quite the same.

currently, i am running beryl. now, i know that for application control theme-ing is handled by gtk+. however, when i install a gtk+ theme, they only tend to half work.

now here is how my problem differs from the common problem. the common problem is to have the plain ugly gtk theme gui. my problem is that some of the gui does change. however, the change is limited, mainly only to color change. no fancy buttons (like if i use a theme with bubble buttons), no fancy sidebars, nothing. they just change color, but nothing like its supposed to.

is there something i'm missing? someone please help. ](*,)

---

### Post by raul_ on 2006-12-14
Try starting "gnome-settings-daemon" in the terminal

---

### Post by Circus-Killer on 2006-12-14
as i said, thats not the problem, i've found all those threads. but thats a different problem.

---

### Post by mcduck on 2006-12-14
> **Circus-Killer said:**
> as i said, thats not the problem, i've found all those threads. but thats a different problem.

do you have the 'gtk2-engines-pixbuf' package installed? Many GTK themes use that to allow pixmaps as parts of themes..

---

### Post by Circus-Killer on 2006-12-14
thats what i was looking for! thanks man :D

is there any other gtk2 packages i need to get most themes up and running?

---

### Post by mcduck on 2006-12-14
> **Circus-Killer said:**
> thats what i was looking for! thanks man :D

is there any other gtk2 packages i need to get most themes up and running?

that should be the only one.. Of course there's the Murrine and Rezlooks engines but they're not in the repositories. All the other important ones should be installed by default (I don't understand why pixbuf isn't).

---

### Post by Circus-Killer on 2006-12-14
thanks again. this problem has been irritating me for months now.

you have no idea how happy i am. :D

---

### Post by mcduck on 2006-12-14
No problem, I'm glad I could help. :)

---

