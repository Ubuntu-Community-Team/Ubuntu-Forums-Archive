---
title: "How do I get true full screen in virtualbox?"
date: 2009-02-20
forum: General Help
---

### Post by wolfen69 on 2009-02-20
when i do Host button+F, it sort of goes fullscreen, but the OS window is only about 8 inches wide, with alot of black around it. how do i get real full screen so that it takes up the whole space of the screen area?

---

### Post by Mercury_Alpha on 2009-02-20
What guest OS is running in the VM, and did you install Guest Additions?

---

### Post by DGortze380 on 2009-02-20
> **wolfen69 said:**
> when i do Host button+F, it sort of goes fullscreen, but the OS window is only about 8 inches wide, with alot of black around it. how do i get real full screen so that it takes up the whole space of the screen area?

What is your guest machine?

You need to install guest additions for it to automatically support native resolutions (Only available in Windows and Ubuntu guests to the best of my knowledge).

Otherwise you'll need to adjust your screen resolution in the guest if possible (you may need to do this regardless).

---

### Post by kellemes on 2009-02-20
> **wolfen69 said:**
> when i do Host button+F, it sort of goes fullscreen, but the OS window is only about 8 inches wide, with alot of black around it. how do i get real full screen so that it takes up the whole space of the screen area?

Guest Additions indeed.
[http://linuxandfriends.com/2009/02/12/installing-virtualbox-guest-additions-in-ubuntu-linux/]("http://linuxandfriends.com/2009/02/12/installing-virtualbox-guest-additions-in-ubuntu-linux/")

---

### Post by CrucifiedEgo on 2009-02-20
Have you set the guest resolution to the native resolution of your host OS?

---

### Post by wolfen69 on 2009-02-20
> **kellemes said:**
> Guest Additions indeed.
[http://linuxandfriends.com/2009/02/12/installing-virtualbox-guest-additions-in-ubuntu-linux/]("http://linuxandfriends.com/2009/02/12/installing-virtualbox-guest-additions-in-ubuntu-linux/")

the how to video does not work. do i install guest additions in the host, or the virtual os? and where do i get it? btw, i'm running the non-free virtualbox.

---

### Post by Mercury_Alpha on 2009-02-20
> **wolfen69 said:**
> the how to video does not work. do i install guest additions in the host, or the virtual os? and where do i get it? btw, i'm running the non-free virtualbox.

In that video, Ubuntu was running as the guest OS, inside of Vista. Just start your guest OS, and go to the Devices menu like the video shows ya.

Also, what guest OS are you running?

---

### Post by wolfen69 on 2009-02-20
i'm trying  out kubuntu.

---

### Post by wolfen69 on 2009-02-20
> **Mercury_Alpha said:**
> go to the Devices menu like the video shows ya.



what video? it won't play. all other youtube vids are fine.

---

### Post by wolfen69 on 2009-02-20
OK, the video finally played. i'll try it out later. thanks for the help.

---

### Post by Mercury_Alpha on 2009-02-20
> **wolfen69 said:**
> what video? it won't play. all other youtube vids are fine.

The one mentioned here:

> **kellemes said:**
> Guest Additions indeed.
[http://linuxandfriends.com/2009/02/12/installing-virtualbox-guest-additions-in-ubuntu-linux/]("http://linuxandfriends.com/2009/02/12/installing-virtualbox-guest-additions-in-ubuntu-linux/")

I had some glitchiness with that clip, but I thought it was on my end. You just have to scroll the time marker ahead a few seconds and hit the play button.

---

### Post by kellemes on 2009-02-21
> **wolfen69 said:**
> the how to video does not work. do i install guest additions in the host, or the virtual os? and where do i get it? btw, i'm running the non-free virtualbox.

Sorry for the bad link, didn't watch the video myself ;-)

---

