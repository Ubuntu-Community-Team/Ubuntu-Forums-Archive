---
title: "Newbie Font Help Needed"
date: 2009-04-15
forum: General Help
---

### Post by Wayne77 on 2009-04-15
I'm a heavy Windows user and hate font smoothing. I have font smoothing turned off in Windows and like it that way.  I've just installed Ubuntu and have disabled font smoothing and hinting. I've also installed the Microsoft font pack so that I can use Arial. 

Problem is that with the exception of one Ubuntu font, Kochi Gothic, all fonts look terrible. Arial for instance looks nothing like it does in Windows. Some letters look OK but others have bits sticking out of them that make them look terrible. All the other Ubuntu fonts with the exception of Kochi Gothic look the same ie. terrible.

Is this as good as it gets or have I missed something? Can I get my Arial font, or other fonts for that matter, to look the same in Ubuntu as they do in Windows?  I don't want to turn font smoothing on because it gives me headaches and sends me blind. :-)
Please help.

---

### Post by Camilia on 2009-04-16
Go to Assesories - Terminal and paste

sudo apt-get install msttcorefonts

This will get you similar fonts as in windows.

---

### Post by ncmncm on 2009-04-16
Details in this blog.

[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

Worked  for me.

---

### Post by blackened on 2009-04-17
> **Wayne77 said:**
> I've also installed the Microsoft font pack so that I can use Arial.

> **Camilia said:**
> Go to Assesories - Terminal and paste

sudo apt-get install msttcorefonts

This will get you similar fonts as in windows.


> **ncmncm said:**
> Details in this blog.

[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

Worked  for me.

Really? It's obvious that neither of you could be bothered to read the OP.

**Wayne**, while flailing around on the intertubez, I came across [http://www.sharpfonts.com/]("http://www.sharpfonts.com/"), which has a multi-distro tutorial on how to make Linux/BSD fonts look better. I haven't tried it personally, but I read through it, and it seems like sound advice.

---

