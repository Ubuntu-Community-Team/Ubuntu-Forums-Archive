---
title: "Gnome 3.10 desktop not showing correctly"
date: 2014-05-03
forum: Desktop Environments
---

### Post by silajim on 2014-05-03
Hello, i am new here because of a problem that i can not find a solution, i installed gnome 3.10 on ubuntu 13.10, and this is the result:

 [[IMG]http://s28.postimg.org/785sugzah/ubutnu_problemn.jpg[/IMG]]("http://postimg.org/image/785sugzah/")

Any ideas what is happening here?

---

### Post by cmcanulty on 2014-05-03
I would try the display resolution setting in system settings

---

### Post by ibjsb4 on 2014-05-03
How did you install gnome? 

Also please post your computer specs.  CPU, ram and your video card.

And welcome to the forums :)

---

### Post by silajim on 2014-05-03
It's a VM on some cloud servers, with 2 cores and 6GB of ram, unity shows OK, but I don't want unity. I installed gnome with some online tutorials, you know... google, Ubuntu 13.10 gnome 3.10, or something like this.

---

### Post by ibjsb4 on 2014-05-03
> [COLOR=#000000]VM on some cloud servers[/COLOR]

Don't know how that works, but to get a gnome flashback session on the regular ubuntu/unity install, enter:

```
sudo apt-get install gnome-session-flashback
```

And its done.  Choose your desktop at login.

---

### Post by cmcanulty on 2014-05-03
consider trying xubuntu I just tried the 14.04 and can't believe how much nicer xfce has gotten. It was getting more and more difficult to keep the ubuntu classic version going without endless tweaks.

---

### Post by silajim on 2014-05-03
the flashback just crashes on logout, and shows a black desktop, and the full gnome has no desktop icons, but in the system menus has the same problem show above. I dont want xfce i am more comfortable with gnome, and i want gnome for vino.

---

### Post by ibjsb4 on 2014-05-03
Again, I do not know how this cloud thing works, it could for all I know be the problem. So sorry but I cannot help you, maybe other will come along that can.

Good luck

---

### Post by silajim on 2014-05-03
This cloud thing it easy how it works, it's like running a vm on vmware, all the graphics rendering is done buy the cpu and the output (the visual) instead of showing it locally is redirected to a vnc server. I will try to clean all gnome and do it again later,any ideas how to do that, cleaning all gnome from the system.

---

### Post by ibjsb4 on 2014-05-03
And VM's themselves cannot be a problem?  Again Good luck

---

### Post by cmcanulty on 2014-05-03
Vino works in xfce too

---

### Post by cmcanulty on 2014-05-03
Vino works in xfce too

---

