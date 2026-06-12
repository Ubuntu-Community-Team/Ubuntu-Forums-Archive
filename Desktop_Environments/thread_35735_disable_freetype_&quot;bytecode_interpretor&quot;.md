---
title: "disable freetype &quot;bytecode interpretor&quot;"
date: 2005-05-20
forum: Desktop Environments
---

### Post by bmgz on 2005-05-20
Ive just switched to Ubuntu after 2 years of slacking. Installation was mostly a breeze -except for couple of hiccups (thankfully the thorough documentation was very helpfull)

The font configuration is giving me headaches. I know exactly what is needed to be done: The BYTECODE_INTERPRETOR in freetype needs to be DISABLED. I would normally just recompile freetype in slack, but I am extremely hesitant to risk braking the system. I do not know much about Apt and how it will deal with custom compiled apps.. I their a "buildfile" / "Makefile" for the sources?

Basically I need Freetype without the BYTECODE_INTEREPRETOR, How would I go about this?

---

### Post by JonahRowley on 2005-05-20
If you need to recompile apt pacakges, take a look at the **apt-build** command.  It's very handy for adding a compile-time config to an already-installed package.

---

### Post by bmgz on 2005-05-20
mmmm. thanks for the pointer. looks like I'll be spending the day understanding apt-build...

---

### Post by shof2k on 2005-05-20
Forgive me if I haven't understood, but I thought freetype was installed with the BCI switched off by default for licencing reasons.  Instead freetype comes with 'autohint' (an open equivalent to BCI) enabled.

In either case, there are forums threads explaining how to do this.  I can dig them out if you really want them.

---

### Post by kiddyfurby on 2005-05-20
perhaps a dpkg-reconfigure will do?

---

### Post by bmgz on 2005-05-20
OK, i used "apt-get source <package name>" instead of apt-build.
Now I am pretty confused. The BYTECODE_INTERPRETOR option is NOT defined in the source? Isn't the source package the exact one that is compiled and included as a binary in the distro?

---

### Post by bmgz on 2005-05-20
Forget it, I can't be certain BCI is enabled. My AA fonts look really terrible. They are all blurry and/or blotchy. I really don't have a freekin clue about Apt either, but I suppose it's a bit futile trying to avoid compiling something from source..

I resign for the day, Ill just have to reside with sore eyes..

---

### Post by jcooper on 2005-05-20
Have you had a look at the usual Gnome font settings? They may be different to what you have used in slack. I had to tweak mine a bit when I installed Hoary.

---

### Post by bmgz on 2005-05-20
no, it's nothing to do with gnome settings. 
Ive gone around this bush (font rendering problems) umpteen times (every time install any distro).

heres a screenshot from firefix, displaying blurry fonts:
[http://www14a.your-server.co.za/gleeso/tmp/Screenshot.png](http://www14a.your-server.co.za/gleeso/tmp/Screenshot.png)

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=bmgz]Basically I need Freetype without the BYTECODE_INTEREPRETOR, How would I go about this?[/QUOTE]

Try **sudo dpkg-reconfigure fontconfig**.

---

### Post by bmgz on 2005-05-20
MILLIONS!!!!  :)  :)  Hail to Ubuntu, the new chief of my harddrive!!  :-P

---

### Post by bmgz on 2005-05-20
Just to clarify things for other Ubuntu newbies:

This is what my anti-aliased fonts looked like after installation  (BYTECODE INTERPRETOR enabled -yuck!  :mad: ):
[http://www14a.your-server.co.za/gleeso/tmp/Screenshot.png](http://www14a.your-server.co.za/gleeso/tmp/Screenshot.png)

 .. and after running "sudo dpkg-reconfigure fontconfig" and selecting Auto Hinter instead (Yum! \\:D/ )

[http://www14a.your-server.co.za/gleeso/tmp/Screenshot_new.png](http://www14a.your-server.co.za/gleeso/tmp/Screenshot_new.png)

--(thanks Stormy Eyes)

---

### Post by Stormy Eyes on 2005-05-20
[QUOTE=bmgz]--(thanks Stormy Eyes)[/QUOTE]

No problem.

---

### Post by JonahRowley on 2005-05-20
Does anyone know which is faster?  Which method takes less cycles?  I've noticed that on slower machines, AA fonts really slow things down, anyone know if one would be notably faster than the other?

---

### Post by bmgz on 2005-05-21
[QUOTE=JonahRowley]Does anyone know which is faster?  Which method takes less cycles?  I've noticed that on slower machines, AA fonts really slow things down, anyone know if one would be notably faster than the other?[/QUOTE]

I don't know about "noticeably" faster, but AA definately take up more resources than non-AA fonts.

---

