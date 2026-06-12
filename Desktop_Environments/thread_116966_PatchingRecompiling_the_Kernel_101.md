---
title: "Patching/Recompiling the Kernel 101"
date: 2006-01-13
forum: Desktop Environments
---

### Post by sameat on 2006-01-13
I have a problem with the processor in my laptop, so I came to these forums to find a solution.  I found the [solution]("http://www.ubuntuforums.org/showthread.php?t=75810&highlight=patch+dothan") pretty quickly , and it's author even said it was easy.  

I generally try to avoid solutions that involve patching/recompiling the kernel because I don't really understand the process, and it seems like it would be pretty easy to screw up and seriously damage a system.

However, I need to fix this problem, anf there is no better time to learn more about the process.  I am not having much luck, and thought I might turn to the forum to get some help and lear a bit. 

The best way for me to approach this is to go through the walkthrough from the above post and talk about the parts that confused me.  So here goes:

>1. Download the sources (sudo apt-get install linux-source-2.6.12)
>2. cd /usr/src
>3. tar xfj linux-source-2.6.12.tar.bz2

I understand all of these.

>4. ln -s linux-source-2.6.12 linux

I understand what this does, but I don't understand why I need to do it.  Any help?

>5. cd linux

Easy enough.

>6. cp /boot/config-2.6.12-9-686 .config

Again, why?

>7. apply [this patch]("http://localhost.ruhr.de/~stefan/acerTM292/patches/cpufreq-speedstep-dothan-3.patch") to the sources

I downloaded the .patch file to my desktop.  I assume I am supposed to issue the patch command from the linux directory and point to the file on my desktop.  Do I need any swiches to do this correctly?

>8. make-kpkg --initrd --append-to-version "-yourPostfix" --revision 1 >kernel-image

This compiles the newly patched kernel and creates a deb file for easy installation, right?

>9. sudo dpkg -i ../kernel-image-2.6.12-yourPostfix_1_i386.deb

Installs the patched kernel???

I should now have an additional kernel in my menu.lst, right?

I apologize if these are silly questions and that this post is so long.  I would really like to improve my general understanding of how these things work, and any help that anybody could give here would be appreciated.

Thanks.

---

### Post by art on 2006-01-14
I will try to answer the questions I know an answer to
 [QUOTE=sameat]
>4. ln -s linux-source-2.6.12 linux

I understand what this does, but I don't understand why I need to do it.  Any help?
[/QUOTE]
I am not sure about this one, and never done it that way
> 
>6. cp /boot/config-2.6.12-9-686 .config

This will copy your current configuration, which works, to the new directory, so that the new kernel has all the old settings, which you know work, and you can change the rest, which you know you want to change.
To apply a patch do 
patch -p0 < patch-file-name-here, or have a look at 
[http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)
After this you will need also to run make oldconfig, followed by a make menuconfig to adjust the desired settings
> 
>8. make-kpkg --initrd --append-to-version "-yourPostfix" --revision 1 >kernel-image
This compiles the newly patched kernel and creates a deb file for easy installation, right?

This creates the kernel package the easy way. It's a very handy tool for compiling kernels
> 
>9. sudo dpkg -i ../kernel-image-2.6.12-yourPostfix_1_i386.deb

Installs the patched kernel???

Yes
> 
I should now have an additional kernel in my menu.lst, right?

Yes. 
There is a howto on this at
[http://ubuntuforums.org/showthread.php?t=85064&highlight=kernel](http://ubuntuforums.org/showthread.php?t=85064&highlight=kernel)
might wanna have a look at it...
HTH

---

### Post by sameat on 2006-01-14
Where should the .deb be? (after make-kpkg...)  I can't find it!

---

### Post by art on 2006-01-14
should be in /usr/src

---

