---
title: "EJect Button Problem"
date: 2008-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jerg on 2008-12-17
Hey whats poppin?

I'm a n00b to ubuntu i rarely rely on forums for help, however this seems like an awesome one and I know some one can help me here. I'm fed up with windows so I pledge myself to be a full Ubuntu user I'll only use windows for my music production and thats through VirtualBox anywayz

I'm having a small problem I have Ubuntu 8.04 installed on my Dell XPS m1530 for sometime now and I'm currently having problems with my eject button ..I followed these instructions from this site ([http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)) when it came to configuring other hardware... But i don't know how to fix this problem...so can someone help me out thanks alot in advance

---

### Post by outlaws42 on 2008-12-18
when you push the eject button on the CD it doesn't eject? 
If so you may need to unmount  the CD drive first before physically pushing the button on the drive. maybe im misunderstanding you.

---

### Post by bigbrovar on 2008-12-18
> **jerg said:**
> Hey whats poppin?

I'm a n00b to ubuntu i rarely rely on forums for help, however this seems like an awesome one and I know some one can help me here. I'm fed up with windows so I pledge myself to be a full Ubuntu user I'll only use windows for my music production and thats through VirtualBox anywayz

I'm having a small problem I have Ubuntu 8.04 installed on my Dell XPS m1530 for sometime now and I'm currently having problems with my eject button ..I followed these instructions from this site ([http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)) when it came to configuring other hardware... But i don't know how to fix this problem...so can someone help me out thanks alot in advance

[http://bigbrovar.wordpress.com/2008/11/20/how-to-make-m1330s-eject-button-work-with-ubuntu/]("http://bigbrovar.wordpress.com/2008/11/20/how-to-make-m1330s-eject-button-work-with-ubuntu/")

---

### Post by csowm5je on 2008-12-18
Is there a way to unmount first and then eject the CD/DVD.

---

### Post by outlaws42 on 2008-12-19
If you go into nautilus to the left you should see the CD/DVD listed you have in the drive, Just right click then unmount or eject

---

### Post by thorcik on 2008-12-19
You can always open the terminal and write ```
eject /dev/cdrom
```in my case it always works :o)

---

### Post by jerg on 2008-12-19
Yo first thanks for all the support everyone..... bigbrovar link had the exact information i was looking for ....like that command thorcik

I'm hungry for more unix knowledge and everyday im being feed a different meal ....i love it

peace

---

