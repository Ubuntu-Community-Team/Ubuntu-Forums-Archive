---
title: "Ubuntu Slab Broke Stuff, Please Help"
date: 2008-12-08
forum: General Help
---

### Post by Andysan on 2008-12-08
Hi all,

I attempted to install slab earlier via the following:

```
sudo aptitude install gnome-main-menu
```

[IMG]http://bp0.blogger.com/_D6x4bhBopWc/R16CPfQrVqI/AAAAAAAAABQ/pdaofXzc3WM/s400/slab.png[/IMG]

All went well and i have a nice new menu (although not as nice as i had hoped!).

Unfortunately, in my haste i neglected to notice that installing Slab would remove three other things.  As a result, my Ubuntu rebooted to a trashed filesystem and a blue screen.

Suffice to say, everything has got significantly better since then, and i have got everything back the way it was.  I remembered one of the things that it removed was [COLOR="Blue"]linux-headers-2.6.27-7-generic[/COLOR] but i cannot think of the other two.

Does anyone:

a) Know perhaps what the other two things were - a Google search has yielded nothing.
b) Know if there is a log somewhere that lists installed & removed packages?

I just want to ensure that everything is back the way it was.

Thanks in advance.

P.S:  If anyone wants to call me an idiot, please go ahead - i know i would!

---

### Post by plucky on 2008-12-08
This might help:-

Open **Synaptic Package Manager** and go to **File > History** and that should tell you what has been installed or removed.

Good Luck

---

### Post by Andysan on 2008-12-08
Hi Plucky,

Thanks for the reply, will take a look and report back.

EDIT - I have the following for today.

This was when i reinstalled the header file:

```
Commit Log for Mon Dec  8 19:26:06 2008


Installed the following packages:
linux-headers-2.6.27-7-generic (2.6.27-7.16)

```

This was about the time it all went topsy-turvy:

```
Commit Log for Mon Dec  8 19:09:58 2008


Installed the following packages:
linux-headers-2.6.25-2-386 (2.6.25-2.3)
linux-headers-2.6.27-7 (2.6.27-7.16)
linux-headers-386 (2.6.25.2.3)
linux-ports-headers-2.6.25-2 (2.6.25-2.3)

```

This looks about right, but it is marked as "installed"?  I assume my uninstallations would definetly show up, even though they were done through the console.

Thanks. :)

---

