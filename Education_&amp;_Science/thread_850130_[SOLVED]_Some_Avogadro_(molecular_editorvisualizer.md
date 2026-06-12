---
title: "[SOLVED] Some Avogadro (molecular editor/visualizer) quirks"
date: 2008-07-05
forum: Education &amp; Science
---

### Post by Tharmas on 2008-07-05
Hi, everybody 

In the last months [Avogadro]("http://avogadro.openmolecules.net") has been my molecular editor of choice. I'm truly amazed because it is great software, despite being in Qt:oops:.
I'm installing it from the [Debichem repository in Launchpad]("https://launchpad.net/~debichem/+archive")

My problem:
In two of the machines where I have it installed, the "export to graphics" option in the menu is unavailable (dimmed). I can't figure out what is the problem.
Has anyone had similar troubles?

---

### Post by mj_ja55 on 2008-07-10
I installed Avogadro from the repository you linked to, but it does not run on my system.  I try to start it from the applications menu and nothing happens.  I'm running Ubuntu 8.04 Hardy Heron on a Dell Inspiron 6400 laptop.  I would like to get it working as it looks like the kind of software that would be very useful to me (I am a chemistry graduate student).  Did you have to do anything special to get it running?

---

### Post by Tharmas on 2008-07-14
If you installed it from the repository I assume you have all dependencies met.
Could you try to run it from a Terminal window and paste here the result?

---

### Post by mj_ja55 on 2008-07-14
Sorry, I went back and checked and found OpenBabel2 installed, which was preventing Avogadro from recognizing OpenBabel3.  Once I fixed that, it runs great.

Also, my option of "Export->Export Graphics" works great.  Can I give you any other information that might help you track down your problem?

Edit: I used the Export option to create the image for my avatar.

---

### Post by Tharmas on 2008-07-17
I have this problem in Gutsy in a laptop and in Hardy in a desktop pc. But I just can't figure out what is the culprit of this. Could it be some dependency on some graphics package? I just can't understand and its very annoying.
By the way, what's that molecule? 
Me, I like coffee, and it goes with the forum theme. ;)

---

### Post by mj_ja55 on 2008-07-17
I think quinine is a great molecule both for its structure and history.

Perhaps you have a problem with your 3D rendering?  I had a lot of problems with all 3D rendering until I turned off the desktop visual effects.  Perhaps you could try contacting the Avogadro dev team and ask them?  I'm starting to think we are the only two people using Avogadro on this site.

---

### Post by LaserJock on 2008-07-29
Hi,
Sorry for dragging up an older thread, but I've got a few questions. I'm the guy that packages Avogadro for Debian and Ubuntu. Are you still having problems? What versions of Ubuntu, openbabel, and Avogadro are you using? I'd like to get broader feedback on the packages as it's very new, but exciting project.

-LaserJock

---

### Post by s4nn3 on 2008-08-19
Hey,
you are not the only one using it, the whole material science and chemistry department of my university are using it, great program ;)

However I still have the same problem, the option: export graphics is greyed out and I cannot click it.

I am using Avogadro version 0.8.1, Ubuntu version 8.04 and OpenBabel version 2.2.0. 

Thanks for all tips,
btw dont know if u got something to do with this LaserJock, but the tutorial sucks :P

/S

---

### Post by jeecol on 2008-11-26
I also a new user of Avogdaro. That is super great! 

However, I have the same problem of exporting images even after some trials. 


Today, 2008-11-26 (I use Ubuntu 8.10, Avodagro 0.8.1. )
I check what I installed by synaptic. I saw libopenbabel (2.2.0-1) and some other packages' names containing the babel (I did not know when they came to my computer, apt-get handled everything). And the source.list consists some mirror-web in Taiwan

a. I removed openbabel (2.2.0-1), and restarted Avogadro--> did not work
b. removed python-babel (1.2.0.dfsg-6ubuntu-1) --> did not work
c. when I planed to remove libopenbabel3 (2.2.0-1), there came a warning, a lot of chemistry software was going to be unindtalled if I clicked YES. Sure, I did not do it. 

I really need the function of exporting image of malecules. 


By the way, I just got the permission for translating Avogadro into the official language, traditional Chinese that is mainly used in Taiwan (not in  China). However, I appreciate the authors of Avogadro. 



----------
One Dollar

---

### Post by LaserJock on 2008-11-26
OK everybody, I spent some time with the Avogadro developers today trying to figure the "Export->Export Graphics" thing out. The short story is Avogadro relies on a OpenGL feature to export directly to pngs, etc. It turns out though that not all graphics cards support the OpenGL feature and so the menu item is greyed out.

So, the good news is that you aren't doing anything wrong and everything is working as intended. The bad news is if your graphics card doesn't support writing from OpenGL (your Export Graphics menu item is greyed out) then you need to render an exported POV-Ray file to .png. 

To do that first make sure povray is installed:
```
sudo apt-get install povray
```

Then after you export to a .pov file (I called mine benzene.pov) you run the following :
```
povray -Obenzene.png -FN benzene.pov
```
notice that there is no space between -O and the output file name. The -FN tells povray to output a PNG. Read the povray man page (run man povray) to get more options.

We're looking into alternative methods for exporting to graphics that will working on a greater variety of hardware. Hopefully we can figure something out for the next Avogadro release.

-LaserJock

---

