---
title: "Blank,Black desktop"
date: 2008-11-11
forum: Desktop Environments
---

### Post by gulmer on 2008-11-11
This is for my KDE desktop, gnome is OK.Whenever I login to my KDE desktop, I get this error message:A Fatal Error Occurred
The application Plasma Workspace (plasma) crashed and caused the signal 11 (SIGSEGV).

I can alt-F2 and get a command line up to run applications and firefox opens automatically. The desktop is black and blank, no panel loads.How do I fix the Plasma Workspace to load so I can see my desktop. I tried to run Plasma through a command line, it tries,I see the panel try to load, then fail and the error message pops up. Any program that's running that has a pop up message is visible, including Firefox and Konqueror.
 
I would like to be able to use my KDE desktop, Gnome is OK, but I prefer to use KDE. Compiz works, I can rotate the cube.

---

### Post by linuxownsu on 2008-11-11
Man you should not use both KDE and GNOME on the same partition as thay MAY conflict with each others and make your apps run as ****. You should back up all your stuff before it's too late. Do you got KDE as a release candidate or as final version ?

---

### Post by linuxownsu on 2008-11-11
Anyway got' something for you 

[http://top-web-solutions.com/kde4-plasma-workspace-bug/](http://top-web-solutions.com/kde4-plasma-workspace-bug/)

---

### Post by gulmer on 2008-11-12
> **linuxownsu said:**
> Man you should not use both KDE and GNOME on the same partition as thay MAY conflict with each others and make your apps run as ****. You should back up all your stuff before it's too late. Do you got KDE as a release candidate or as final version ?

I installed ubuntu first with the gnome desktop, then installed the kde desktop from   snaptic package manager and I've used both for years without problems, until the 8.10 upgrade.

---

### Post by icanfly0307 on 2008-11-12
Hey There,
                    I noticed that you said that you upgraded to 8.10. I think I know what the problem is. Your KDE 4.0 packages have most probably been upgraded to KDE 4.1. This is a bug so you can either try the link that Linuxownsu posted or try my suggestion...

I fixed this problem by logging in to KDE 4.1 as root. My root account would load the desktop fine so I made a new test account just to see if the issue was with my existing user account. Guess what? My test account would work fine too! So I deleted my normal account and remade it. Yeah, I know this sounds all messy, but again, you could try the link posted by Linuxownsu. Haven't tried it  myself 'cause I downgraded my KDE 4.1 immediately down to KDE 4.0 which was a lot more stable for me...

Hope this helps... :)

---

