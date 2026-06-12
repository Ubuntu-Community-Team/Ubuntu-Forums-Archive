---
title: "Choppy video"
date: 2006-01-28
forum: Desktop Environments
---

### Post by caspar_wrede on 2006-01-28
I have a computer with 200GB of videos /music and seeing as it only has one partition, I couldn't do an upgrade from scratch when breezey came out because I had nowhere to store all that stuff. So I did an apt-get dist-upgrade which worked well.

However, videos now play choppily which they didn't use to do (using xine / kde). Going back to the old kernel doesn't solve the problem. Any idea what the problem is / what I need to check?

---

### Post by chris_andrew on 2006-01-28
Out of interest, how much RAM have you?

With regard to your one partition, you may like to look at this great guide to moving your partitions:

[http://www.gentoo.org/doc/en/articles/partitioning-p1.xml](http://www.gentoo.org/doc/en/articles/partitioning-p1.xml)

Thanks,

Chris.

---

### Post by caspar_wrede on 2006-01-28
I have 500MB of RAM. Thanks for the tip about moving paritions, but I'm hoping there is a simple a simple tweak for my problem.

---

### Post by banjobacon on 2006-01-28
[QUOTE=caspar_wrede]However, videos now play choppily which they didn't use to do (using xine / kde). [/QUOTE]

Are you still using Xine, or were you using Xine before?

---

### Post by caspar_wrede on 2006-01-29
[QUOTE=banjobacon]Are you still using Xine, or were you using Xine before?[/QUOTE]

I was using xine before and am using it now. Everything is the same other than that I upgraded to breezy!

---

### Post by akudewan on 2006-01-29
Make sure your graphics card drivers are installed and loaded in xorg.conf.

Which graphics card do you have?

---

### Post by caspar_wrede on 2006-01-29
[QUOTE=akudewan]Make sure your graphics card drivers are installed and loaded in xorg.conf.

Which graphics card do you have?[/QUOTE]

An ATI radeon 7000. 

It's small and crap but *used* to be good enough for playing videos. The problem is that the computer is used as a fileserver and is only connected to a TV, using the TV-out of the graphics card. The ati drivers always cause problems with TV-out, and as far as I can remember I just used the vesa driver. There were a few old xorg.conf's lying around which I tried but none of them solved the problem. grrrrr......

I have attached my current xorg.conf

---

### Post by akudewan on 2006-01-30
Try to find out your CPU usage when playing videos. You can use gkrellm, or use the "top" command.

I don't know much about ATI cards, but you could try installing the drivers. I had to install my nvidia drivers after upgrading to breezy. Maybe its a similar problem?
Have a look at these threads:
[http://ubuntuforums.org/showthread.php?t=122874&highlight=ati+radeon+howto](http://ubuntuforums.org/showthread.php?t=122874&highlight=ati+radeon+howto)
[http://ubuntuforums.org/showthread.php?t=24557&highlight=ati+radeon+howto](http://ubuntuforums.org/showthread.php?t=24557&highlight=ati+radeon+howto)

Best of luck

---

