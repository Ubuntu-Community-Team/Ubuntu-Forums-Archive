---
title: "sudo vs gksudo"
date: 2005-11-29
forum: Desktop Environments
---

### Post by invalid on 2005-11-29
Hiya,
 
I was just curious, what exactly is the difference between using sudo and gksudo? I am aware that one is done fully through the terminal, while the other is done graphically - but really, what is the difference?

Also, why is there a difference in the way they appear? When I use gksudo, the text and images are larger than if I were to use sudo (which is my prefered method). I have attached some images so you can see what I mean - notice how the gksudo has larger objects.

[sudo image]("http://www.thedarkmere.net/~beau/images/synaptic/synaptic_sudo.jpg")
[gksudo image]("http://www.thedarkmere.net/~beau/images/synaptic/synaptic_gksudo.jpg")

Thanks,
Cb

---

### Post by Corvillus on 2005-11-29
By default, gksudo uses root's home, wheras sudo uses the calling user's home. So essentially, gksudo calls sudo -H rather than just sudo.

---

