---
title: "Please help me!"
date: 2009-05-28
forum: General Help
---

### Post by DawnieMewMew on 2009-05-28
Hello, I'm new to this so bare with me....

I recently got my Dell computer reformatted, and it still seems to be missing a couple drivers, ie, things for the graphics card, and sound. I've tried looking up my model number on dell.com, and since I'm sucha n00b when it comes to this part of computers....so now, I have no sound on my computer, and there is a weird lag when I move windows and such, which has never happened on my computer before. My computer is a Dell XPS 400...I wish I knew the other specs of it, but I hope someone can get me in a ballpark area in where I need to be in fixing this thing.... :(

---

### Post by Legace on 2009-05-28
You seem to have a **NVidia GeForce 6800** graphics controller.
So you need to install the nvidia drivers:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
or
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Bender2k14 on 2009-05-28
Here is a link to the Dell XPS 400 specs:
[http://support.dell.com/support/edocs/systems/xps400/sm/specs.htm#wp1053343]("http://support.dell.com/support/edocs/systems/xps400/sm/specs.htm#wp1053343")

---

### Post by Bender2k14 on 2009-05-28
Also, you would probably get more responses with a more informative title.  I would recommend "Need Drives for new Dell".  (You can change the title by editing your first post.  Click Edit -> Go Advanced)

---

### Post by Bender2k14 on 2009-05-28
Type
```
lspci
```
into a terminal and paste the output here.  The output will tell us what graphics card you have for sure.

---

### Post by b@sh_n3rd on 2009-05-28
Just a note, In a dell, you could find a "Service Tag" on your computer which could help you find your PC on [www.dell.com/support]("http://www.dell.com/support") You can also find it in your system BIOS...(I have two reliable dell's that are the best in my *fleet* :D) and, welcome to the community!

---

