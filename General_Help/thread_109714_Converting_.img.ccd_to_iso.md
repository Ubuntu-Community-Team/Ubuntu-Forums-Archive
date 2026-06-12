---
title: "Converting .img/.ccd to iso?"
date: 2005-12-29
forum: General Help
---

### Post by Jeff Eklund on 2005-12-29
Hi! Could someone explain to me how in the world I am supposed to convert this .img/.ccd into a nice, beautiful .iso?
Thanks!

---

### Post by kaamos on 2005-12-29
I don't know if there is any difference between an img and an iso. At least an .img file can be mounted just like an iso..
```
sudo mount a_file.img /a/location/ -o loop
```

---

### Post by limit223 on 2005-12-29
...and format .img you may write on the disk with k3b without converting

PS. Though, I've got a converting tool but it is for KDE desktop and is called:  [mountiso]("http://www.kde-apps.org/content/show.php?content=11577")

---

### Post by limit223 on 2005-12-29
Ups...mountiso uses ccd2iso to convert .ccd/.img in .iso file.
That's the right tool for you: [ccd2iso ]("http://sourceforge.net/projects/ccd2iso/")

Install it and then:

ccd2iso <myimage.img> <myimage.iso>
ccd2iso <myimage.ccd> <myimage.iso>

---

### Post by rizzyc on 2006-01-02
I need to burn a .img dvd movie image to dvd? Gnome baker isnt supporting it.. is there a way to make it accept the .img format??

---

### Post by kingsidy on 2006-01-02
use k3b or nerolinux which i use to burn dvds. if you want to watch the image without mounting it you can just right click the image and open with vlc (if you have vlc installed) or you can mount the image.

---

### Post by rizzyc on 2006-01-02
how do i install this k3b thing does it work on breezy?? is it a GUI program?? I wish Gnome Baker supported .img's :(

EDIT: i got it to install and work and it is burning but its only burning at like 0.9kb/s :S thats strange

---

### Post by kingsidy on 2006-01-02
u can install k3b through synaptic, or you can install from the terminal by typing > sudo apt-get install k3b

i think that there is free 30 day trial for nerolinux. just google for nerolinux and install the deb package.

---

### Post by rizzyc on 2006-01-02
:( the K3B is only burning at 0.9x or less and it says the estimated speed is 4.0x

both buffers are showing no info's

the burning speed is like (0.70x) but the estimaed was 4.10x

---

### Post by rizzyc on 2006-01-02
My dvd finished burning but it took an hour and fifteen minutes.. another thing i noticed is that it said that MD5 Failed but the dvd burned sucessfully

---

### Post by yanik on 2006-01-02
you can simply use the cli with this command:
```

growisofs -Z /dev/dvdrw=/path/to/file.img
```

---

### Post by matva on 2006-01-02
had the same problem. Really kind of pathetic that gnomebaker doesn't burn .imgs. I had to resort to renaming the .img to .iso to burn. Worked though..i guess that is all that matters.

---

### Post by rizzyc on 2006-01-02
[QUOTE=matva]had the same problem. Really kind of pathetic that gnomebaker doesn't burn .imgs. I had to resort to renaming the .img to .iso to burn. Worked though..i guess that is all that matters.[/QUOTE]

so just changing the extension worked fine?? KEWL i'll try that but what speed did it burn at. I used k3b and it burned under 1.00x even though it said supported write speed was 4.01x

---

### Post by Piraat Bill on 2006-11-01
> **limit223 said:**
> Ups...mountiso uses ccd2iso to convert .ccd/.img in .iso file.
That's the right tool for you: [ccd2iso ]("http://sourceforge.net/projects/ccd2iso/")

Install it and then:

ccd2iso <myimage.img> <myimage.iso>
ccd2iso <myimage.ccd> <myimage.iso>

I'm having trouble figuring out how to install this file, new at Ubuntu here. The install help with it says to type ./configure in console when in the folder holding the source, but it says no such command, and when i try typing it in just the /ccd2iso/ folder, it starts doing something but says no C compiler or something. Am I just doing this all wrong?
Sometimes I miss Windows, but then I come to my senses.

---

### Post by cvmostert on 2006-12-13
renaming the .img to .iso also worked for me... copying now! 

Thanks

---

