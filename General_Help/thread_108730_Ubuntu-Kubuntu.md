---
title: "Ubuntu-Kubuntu"
date: 2005-12-26
forum: General Help
---

### Post by mavr on 2005-12-26
Can i move from Ubuntu to Kubuntu without format and reinstall the OS, just by getting KDE and removing Gnome?

---

### Post by exclipy on 2005-12-26
Yes.  Open synaptic and install the kubuntu-desktop meta-package.

---

### Post by briancurtin on 2005-12-26
```
sudo apt-get install kubuntu-desktop
```
that will install kubuntu (KDE) for you

```
sudo apt-get remove ubuntu-desktop
```
someone correct me if im wrong, but i think that will remove ubuntu (GNOME) for you


you could always leave GNOME as is, and just install kde (not the kubuntu-desktop meta-package) and select KDE or GNOME at login, unless you want GNOME gone completely

---

### Post by rfruth on 2005-12-26
No need to reformat @ boot time you can choose KDE or GNOME (if both are installed) :)

---

### Post by kenweill on 2005-12-26
You can use synaptic and install **kubuntu-desktop**

But of course, you can't do that with a fresh install of ubuntu. You should edit the repositories and include **universe and multiverse**.

It is not recommended but its what i did.

I just got kubuntu-desktop installed last night. Took 3 hours of download and installation.

Now I use either Ubuntu or Kubuntu. I just have to change my SESSION to start either GNOME(for Ubuntu) and KDE(for Kubuntu).

---

### Post by ren wins on 2005-12-26
wait, so i can install the kubuntu-desktop package, and then just pick btwn kde and gnome at the login?

---

### Post by kenweill on 2005-12-26
[QUOTE=ren wins]wait, so i can install the kubuntu-desktop package, and then just pick btwn kde and gnome at the login?[/QUOTE]

Yup. You can.
When I choose SESSION, and select GNOME, I will be in UBUNTU(GNOME).
When I select KDE, KUBUNTU will start.

Its that simple. I myself never thought its possible. But I have it. It really works.

---

### Post by Substance on 2005-12-26
Yea i knew this command..it was great because i didnt know if i wanted to stick with gnome or kde.. but i have a question how do your remove.. KDE .. if you dont want it?! not sure if its in plain view or if im retarded... (just got ubuntu running tooday.)

---

### Post by briancurtin on 2005-12-26
```
sudo apt-get remove kubuntu-desktop
```

---

### Post by anil_robo on 2005-12-27
After having used windows for 11 years, I simply didn't believe that one can switch between GNOME and KDE without formatting the hard drive. It's like hearing you can have both windows 98 and XP running at the same time, and you just logout from 98 and login to XP without rebooting. So I gave it a try, just typed a few words in the terminal, and it was installed in half an hour.

The story doesn't end here. I can even have XFCE, Fluxbox/blackbox, and whatever as per my liking.

SO convenient! Why didn't [anyone]("http://www.microsoft.com/windows/default.mspx") think of it before?

---

