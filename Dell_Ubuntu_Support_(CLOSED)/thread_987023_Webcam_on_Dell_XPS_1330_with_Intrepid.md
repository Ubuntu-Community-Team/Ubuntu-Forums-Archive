---
title: "Webcam on Dell XPS 1330 with Intrepid"
date: 2008-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rafanto on 2008-11-19
Hello,
I have a DELL XPS 1330 with Ubuntu 8.10 Intrepid Ibex. With Hardy (8.04.1)  my webcam worked but after installing intrepid (exnovo) the webcam it detects , the LED turns on but I can not see my image.

I test the webcam with skype & cheese 

thanks !:(

---

### Post by PsychedelicReaction on 2008-11-19
unfortunately the new intrepid ibex is shipped with some annoying bugs in the uvc video driver. i had the same problem with cheese (not with skype but maybe are related) and i solved it compiling by myself the updated uvcvideo drivers that you can find [here]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6209706").

---

### Post by rafanto on 2008-11-19
you please indicate where can I download the driver UVC to be compiled

---

### Post by llamakc on 2008-11-19
> **PsychedelicReaction said:**
> unfortunately the new intrepid ibex is shipped with some annoying bugs in the uvc video driver. i had the same problem with cheese (not with skype but maybe are related) and i solved it compiling by myself the updated uvcvideo drivers that you can find [here]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6209706").

Please clarify the link where you found the thread concerning the uvcvideo drivers. Your link is busted.

---

### Post by youthforlinux on 2008-11-19
[http://ubuntuforums.org/showthread.php?t=966398]("http://ubuntuforums.org/showthread.php?t=966398")

This worked for me.  I used the deprecated solution.

```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make uvcvideo &&
sudo install uvcvideo.ko -v -m644 /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko &&
sudo make install &&
sudo cp -av /lib/modules/$(uname -r)/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules &&
sudo depmod -ae $(uname -r)

```

Install the backports modules first.

---

### Post by PsychedelicReaction on 2008-11-20
my fault, i linked the wrong page. here it is the page [http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

and then

```

make
sudo install uvcvideo.ko -v -m644 /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
sudo make install
sudo cp -av /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules
sudo depmod -ae 2.6.27-7-generic
```

---

### Post by Teamgeist on 2008-11-20
Copy this all at once into a Terminal and hit 'Enter'. **Not** line by line but **all at once**.

```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)
```

Restart your computer and cheese should work just fine.

---

### Post by bigbrovar on 2008-11-21
i wrote a small guide on how i got everything working including webcam  with Intrepid. on my m1330 ,, [http://bigbrovar.wordpress.com/2008/11/20/ubuntu-intrepid-ibex-on-dell-xps-m1330/]("http://bigbrovar.wordpress.com/2008/11/20/ubuntu-intrepid-ibex-on-dell-xps-m1330/")

---

### Post by Darrell Lawrence on 2008-11-22
Teamgeist,

Thank you very much for your webcam solution. This resolved the webcam for me on my Dell XPS M1530. I'm in awe of your knowledge. Hope to get there myself as I work towards Ubuntu Certified Professional. 

What a great forum.

Darrell

---

### Post by Leoncio on 2008-12-23
> **Teamgeist said:**
> Copy this all at once into a Terminal and hit 'Enter'. **Not** line by line but **all at once**.

```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)
```

Restart your computer and cheese should work just fine.

Man, you made my day!  Thanks a lot for the help!

BTW, I still have a folder named gspca-ab0e29c9d7c4 and a file named tip.tar.bz2 on my ome folder.  Is it safe to remove them?

---

### Post by keptang on 2008-12-26
> **Leoncio said:**
> Man, you made my day!  Thanks a lot for the help!

BTW, I still have a folder named gspca-ab0e29c9d7c4 and a file named tip.tar.bz2 on my ome folder.  Is it safe to remove them?


yes

---

### Post by kubug on 2009-03-24
> **PsychedelicReaction said:**
> my fault, i linked the wrong page. here it is the page [http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

and then

```

make
sudo install uvcvideo.ko -v -m644 /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
sudo make install
sudo cp -av /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/uvc/uvcvideo.ko /lib/modules
sudo depmod -ae 2.6.27-7-generic
```

Hey PsychedelicReaction,

I am just wondering what that second line does ("sudo install uvcvideo.ko ....")?? I gives me an error if I run it:

```
install: cannot stat `uvcvideo.ko': No such file or directory

```

What I did was download the .bz2, unextracted it on the desktop, took a terminal and went in it and pasted your lines.

I also changed the "2.6.27-7-generic" to the current kernel.

Any ideas?

---

### Post by mcci6 on 2009-07-21
> **Teamgeist said:**
> Copy this all at once into a Terminal and hit 'Enter'. **Not** line by line but **all at once**.

```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 &&
tar xf tip.tar.bz2 &&
cd gspca-* &&
make &&
sudo make install &&
sudo depmod -ae $(uname -r)
```

Restart your computer and cheese should work just fine.

I just wanted to thank Teamgeist for his solution here. I requested help for my own problem on a separate thread ([http://ubuntuforums.org/showthread.php?p=7650907#post7650907](http://ubuntuforums.org/showthread.php?p=7650907#post7650907)) but no solutions or suggestions was offered. After researching on the internet for ages, I finally decided to try out Teamgeist's solution and it worked for me! I'm delighted!

Thanks Teamgeist! :D

---

