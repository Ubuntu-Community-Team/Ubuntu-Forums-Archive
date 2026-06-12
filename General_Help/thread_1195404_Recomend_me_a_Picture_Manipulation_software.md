---
title: "Recomend me a Picture Manipulation software"
date: 2009-06-23
forum: General Help
---

### Post by keforex on 2009-06-23
Hello all,

Do you know any software that can manipulate pictures in batch? What I need is to resize / re-sample more than 10,000 pictures and I can't do that one by one. In windows I can do that using infranview. Any suggestions? Thanks in advance!

---

### Post by syrex314 on 2009-06-23
Check out ImageMagick; it's great for batch operations!

---

### Post by Cheesemill on 2009-06-23
If you want something with a GUI then check out [Phatch]("apt:phatch").

---

### Post by keforex on 2009-06-23
Thanks for the super quick replies. I am testing Phatch. How do I run ImageMagick after installation? It doesn't appear in the Application->Graphics menu.

Thanks!!

---

### Post by Cheesemill on 2009-06-23
I bilieve that ImageMagick is a command line only tool (useful for scripts and webservers).

Hence my > Im you want something with a GUI .......

:D

---

### Post by keforex on 2009-06-24
Oh, ok. I actually knew that but I thought there was some kind of GUI for it that I could install and use via Synaptic.

---

### Post by jdeppel on 2009-06-24
.

---

### Post by coffeecat on 2009-06-24
If you install the package nautilus-image-converter from Synaptic you can right-click on a number of images selected in a Nautilus window and batch resize them. How long it would take to resize 10,000 I really don't know.

---

### Post by Leslie Viljoen on 2009-06-24
Imagemagick has a bit of a basic graphical user interface called "display". (press alt-f2, type "display" and press enter).

I couldn't get it to perform batch operations, but I didn't play with it much.

---

### Post by kaibob on 2009-06-24
> **keforex said:**
> Oh, ok. I actually knew that but I thought there was some kind of GUI for it that I could install and use via Synaptic.
I use Imagemagick a lot, and I've never heard of a GUI for it. 

Imagemagick is actually a suite of command-line programs, which are discussed at:

[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

To batch resize, resample, and the like, use the Imagemagick convert program. You can get an idea of the many convert options at:

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

Most people use Imagemagick with shell scripts. If you decide to use a shell script, this forum's members are always happy to help should the need arise.

BTW, the purpose of the Imagemagick display utility is to display images. It won't convert anything.

---

### Post by starcannon on 2009-06-24
Might want to check out some of The Gimp's features. 
Heres a beginner tutorial on batch editing using The Gimp:
[http://www.gimp.org/tutorials/Basic_Batch/](http://www.gimp.org/tutorials/Basic_Batch/)

GLAHF

---

### Post by sedawk on 2009-06-24
Have you tested the GIMP image editor already?
Very powerful!

---

### Post by keforex on 2009-06-26
> **coffeecat said:**
> If you install the package nautilus-image-converter from Synaptic you can right-click on a number of images selected in a Nautilus window and batch resize them. How long it would take to resize 10,000 I really don't know.

Perfect! This worked fine - all pictures resized pretty quick (having a 3.61GhZ quad core helps). The only drawback is that I can't choose the quality to influence the physical file size but overall a very quick and easy solution. Thanks!!

---

### Post by stani on 2009-06-27
> **keforex said:**
> Thanks for the super quick replies. I am testing Phatch. How do I run ImageMagick after installation? It doesn't appear in the Application->Graphics menu.

Thanks!!

If you have any issues with Phatch, feel free to report here:
[http://ubuntuforums.org/showthread.php?t=1178224](http://ubuntuforums.org/showthread.php?t=1178224)

I'm the author of Phatch ;-)

---

