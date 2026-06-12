---
title: "Help with Blubuntu"
date: 2008-02-21
forum: Desktop Environments
---

### Post by geekcliff on 2008-02-21
Can anyone help? ive just set my pc theme to blubuntu, ive changed the grub menu, the login screen and the splash screen but just cant get rid of the brown screen that shows when the splash screen is running, just before the desktop appears.

---

### Post by Alucard-sama on 2008-02-21
Oh god I know how this feels.
I've tried to find a solution for this but it seems to be built into the distro (hell even Xubuntu suffers from this problem!).
I may be wrong but this seems unsolvable, atleast not without editing some obscure file that'd probably be pretty dangerous to mess around with.
But like I said, I could be wrong.

---

### Post by geekcliff on 2008-02-21
Thanks for the reply, ive seen this too in xubuntu, maybe i should ask the question in the linux mint forum, as ive have tried that distro too and they seem to have got rid of it.

---

### Post by kevinmchapman on 2008-02-21
If I am thinking of the same screen then this will help:

[http://ubuntuforums.org/showthread.p...t=brown&page=2](http://ubuntuforums.org/showthread.p...t=brown&page=2)

Edit: got tags wrong

---

### Post by geekcliff on 2008-02-21
> **kevinmchapman said:**
> If I am thinking of the same screen then this will help:

[http://ubuntuforums.org/showthread.p...t=brown&page=2](http://ubuntuforums.org/showthread.p...t=brown&page=2)

Edit: got tags wrong
That link just takes me back to the start page of the forum, or is that what you are trying to tell me.

---

### Post by canci on 2008-02-21
It seems to be the display manager. I use SLiM (Slim login manager), which is a bit geeky to set up (requires fiddling around with text configs) but
not too hard. It doesn't have the "transitioning 1-coloured screen" as the others, but isn't as advanced and easy to use as GDM, KDM which both have
this problem.

I don't know if it's in the repos, but here's the website
[http://slim.berlios.de/](http://slim.berlios.de/)

G'luck! :D

---

### Post by geekcliff on 2008-02-21
> **canci said:**
> It seems to be the display manager. I use SLiM (Slim login manager), which is a bit geeky to set up (requires fiddling around with text configs) but
not too hard. It doesn't have the "transitioning 1-coloured screen" as the others, but isn't as advanced and easy to use as GDM, KDM which both have
this problem.

I don't know if it's in the repos, but here's the website
[http://slim.berlios.de/](http://slim.berlios.de/)

G'luck! :D

Thank you, but i dont think i want to be that ambitious, ive done a lot of reinstalls just lately.:lolflag:

---

### Post by kevinmchapman on 2008-02-22
Ooops! First attempt at a hyperlink - do you think anyone noticed? :oops:


You need to edit /etc/gdm/PreSession/Default and change BACKCOLOR. You will need to use a colour picker to translate the colour code (I used the one in GIMP to find something appropriate)

---

### Post by geekcliff on 2008-02-22
> **kevinmchapman said:**
> Ooops! First attempt at a hyperlink - do you think anyone noticed? :oops:


You need to edit /etc/gdm/PreSession/Default and change BACKCOLOR. You will need to use a colour picker to translate the colour code (I used the one in GIMP to find something appropriate)

WOW! That worked great, i just had to change the word edit to, sudo gedit, job done, you are now my hero.
 You seem to know a lot for a man of not many beans, so to speak:biggrin:

---

### Post by geekcliff on 2008-02-22
PS. If you want a good colour picker, get Gcolor2 from the repo, its a stand alone version.:guitar:

---

### Post by olzak on 2008-02-25
You can also change background color using mouse right-click at desktop and then choose 'Change Desktop Background' and there under 'Wallpapers' choose 'Colors' and then pick color you like,

---

### Post by geekcliff on 2008-02-26
> **olzak said:**
> You can also change background color using mouse right-click at desktop and then choose 'Change Desktop Background' and there under 'Wallpapers' choose 'Colors' and then pick color you like,
Thank you:)

---

