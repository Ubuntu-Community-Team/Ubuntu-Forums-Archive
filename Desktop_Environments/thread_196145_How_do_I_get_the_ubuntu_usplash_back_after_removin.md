---
title: "How do I get the ubuntu usplash back after removing xubuntu"
date: 2006-06-13
forum: Desktop Environments
---

### Post by kelean on 2006-06-13
I recently  tried xubuntu for a while ans have decided to remove it and go back to gnome.  I have removed everything except for thunar which i want to keep and the xubuntu splash screen which I would like to get rid of and back to the ubuntu splash screen.

Any help would be very aprieated.

Thanks kelean

---

### Post by ????? on 2006-06-13
I have a similar problem but with kubuntu..

---

### Post by kelean on 2006-06-14
strange thing when i started the computer today i had the xububtu startup splash screen and when i shut down i had the ubuntu shutdown splash screen.

please a little help or a push in the right direction.

Thanks Kelean

---

### Post by kickstar on 2006-06-14
howdy people,

same thing happened to me after removing kubunutu, open up synaptic and search for "usplash". This should list the usplash for each variant, mark removal of the one you dont want i.e. xubuntu - kubuntu and mark a reinstallation of the ubuntu one. Apply the changes and reboot to see if it worked. it did for me... 

good luck.

---

### Post by Ramses de Norre on 2006-06-14
```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by az on 2006-06-14
Just a shot in the dark...


If you remove the xubuntu-artwork-usplash packages, then the only usplash artwork left is the default one
usr/lib/usplash/usplash-default.so
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=usplash&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=usplash&version=dapper&arch=i386)

so then maybe try reinstalling the linux-image-2.6.15-(whatever you are running) package (the package that is the actual linux-kernel image and not a metapackage) using synaptic.

That will rerun the install scripts and rebuild your initrd with the default spash.

---

### Post by kelean on 2006-06-14
ok i had tried 
       sudo update-alternatives --config usplash-artwork.so
with no help.

i had removed the xubuntu-artwork-usplash packages and reinstalled ubuntu usplash and all is working well now.  

Thanks for the help everyone.

---

### Post by dstein on 2006-06-15
How did you reinstall Ubuntu usplash?

---

### Post by kelean on 2006-07-04
[QUOTE=dstein]How did you reinstall Ubuntu usplash?[/QUOTE]

I used synapic and installed ubuntu usplash

---

