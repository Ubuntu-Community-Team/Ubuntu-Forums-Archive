---
title: "How do I apt-get if I'm not connected to the net?"
date: 2005-12-28
forum: General Help
---

### Post by darrowconley on 2005-12-28
As the title says, how do I perform an apt-get if I'm not connected to the net?
I have gone to [http://archive.ubuntu.com](http://archive.ubuntu.com) and downloaded the update binary package, but I don't konw how to install it. 

Help
Thank you

---

### Post by Bachstelze on 2005-12-28
```
sudo dpkg -i packagename.deb
```

---

### Post by darrowconley on 2005-12-28
the packages are not *.deb. At least that is the error I get.

---

### Post by ts. on 2005-12-28
[QUOTE=darrowconley]the packages are not *.deb. At least that is the error I get.[/QUOTE]
They look like they're in archive formats (either .bz2 or .gz), in which case you need to use the bunzip2 or gunzip (I think) commands or an archive/unarchive utility from the GUI before you get the .deb. Then you can use dpkg.

---

### Post by darrowconley on 2005-12-28
I tried both contents amd_64 from here ([http://archive.ubuntu.com/ubuntu/dists/breezy/](http://archive.ubuntu.com/ubuntu/dists/breezy/)) and packages from here ([http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-amd64/](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-amd64/))
They are extracted using file roller 2.12.1.

the dpkg -i did not work with thoes.

the icons have little locks in the upper right side of the icons for both the .gz and extracted file.

Is there anything that I am missing?

---

### Post by 0MG on 2005-12-29
make sure to sudo the dpkg command

---

### Post by darrowconley on 2005-12-29
I did sudo them both.  
My ultimate goal with all of this is to be able to get gcc3.4.5 on my computer so I can install my network drivers. So do I need to do all of this to get gcc3.4.5 on my computer?

---

### Post by FLeiXiuS on 2005-12-29
Is this perhaps on the CD?  I know you can setup apt-get's repo's to your Breezy CDROM.

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

```

I believe thatsit, might not be I just typed it out how I assume it would be. 

Hopefully others can answer before I return home from work.

---

### Post by az on 2005-12-29
[http://packages.ubuntu.com/breezy/interpreters/cpp-3.4](http://packages.ubuntu.com/breezy/interpreters/cpp-3.4)
[http://packages.ubuntu.com/breezy/devel/gcc-3.4-base](http://packages.ubuntu.com/breezy/devel/gcc-3.4-base)
[http://packages.ubuntu.com/breezy/devel/gcc-3.4](http://packages.ubuntu.com/breezy/devel/gcc-3.4)

You can download the three packages you need from those three pages.

As for the build-essential, you can just get it from your cd.  The version of gcc included on the cd is not the one for making kernel modules.

To add the cdrom as a repository, do notedit the sources.list by hand.  Just run

sudo apt-cdrom add

or add it to your repository list using synaptic.  Pop the cd into your drive when asked.

---

### Post by az on 2005-12-29
[QUOTE=darrowconley]I did sudo them both.  
My ultimate goal with all of this is to be able to get gcc3.4.5 on my computer so I can install my network drivers. So do I need to do all of this to get gcc3.4.5 on my computer?[/QUOTE]

It is unfortunate that the version of the compiler available on the cd is not the one used to make the kernel or extra kernel modules.  To quote Matt Zimmerman (CTO for Ubuntu) when asked about that, he said:

"That will never happen again!"

---

### Post by darrowconley on 2005-12-29
Thank you azz,  I will try your suggestion when I get home from work.

---

### Post by Bachstelze on 2005-12-29
Tou can also download all the universe/multiverse packages in .deb format from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by darrowconley on 2005-12-29
Thanks HymnToLife, I'll try that.

I'm also going to try this ([http://www.ubuntuforums.org/showthread.php?t=79896)](http://www.ubuntuforums.org/showthread.php?t=79896)). I don't know why it didn't come up on my initial searches. I think I missed the (-) inbetween gcc and 3.4. 
Anyhow I will let you know if it works. Again, thank you all for your help.

---

### Post by FLeiXiuS on 2005-12-29
[QUOTE=azz]sudo apt-cdrom add[/QUOTE]

Good find :-)

---

