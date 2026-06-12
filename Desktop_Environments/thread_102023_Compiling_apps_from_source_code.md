---
title: "Compiling apps from source code"
date: 2005-12-11
forum: Desktop Environments
---

### Post by dudds on 2005-12-11
Hoping someone can help. I just installed Linux this weekend and need to unrar some files. I have downloaded the unrar application, but it is a bunch of source code files which I don't know what to do with.

If anyone could shed some light on this, or point me to some information I could read that would be great.

Thanks in advance

---

### Post by Ampersand on 2005-12-11
Firstly, have a look through Synaptic to see if the program is there (you may need to enable the universe/multiverse repositories first - [http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)). If not, the instructions for installing a program from source are here:
[http://doc.gwos.org/index.php/ProgramInstallBeginners](http://doc.gwos.org/index.php/ProgramInstallBeginners).

---

### Post by M3ta7h3ad on 2005-12-11
you should already have unrar installed however.

unrar e filename :)

---

### Post by runlevel0 on 2005-12-11
Hi,
unrar is in the contrib or non-free section of Debian, so this should be in "metaverse" in Breezy (correct me, plz).

What I wonder about is: Why do so many new users thing software in Linux *must* be compiled?

What are we doing wrong? IMHO we need to enfatize on how to manage software in our distros, as I see that a great many of them doon't even know that you can install software via double click on a DEB file.

In my 10 years experience with Linux I have seen this behaviour a lot, and I also noticed that the users normally have a very possitive impression when they find out that software management is a point and click task, even easier as in the Windoze world.

---

### Post by taurus on 2005-12-11
[QUOTE=runlevel0]Hi,
unrar is in the contrib or non-free section of Debian, so this should be in "metaverse" in Breezy (correct me, plz).

What I wonder about is: Why do so many new users thing software in Linux *must* be compiled?

What are we doing wrong? IMHO we need to enfatize on how to manage software in our distros, as I see that a great many of them doon't even know that you can install software via double click on a DEB file.

In my 10 years experience with Linux I have seen this behaviour a lot, and I also noticed that the users normally have a very possitive impression when they find out that software management is a point and click task, even easier as in the Windoze world.[/QUOTE]
It's because
1.  They don't know about apt-get/synaptic (for Ubuntu or Debian in general),
2.  Maybe that app is not in the repos,
3.  Perhaps they've heard it somewhere if they build it from source, it will run much faster than the prebuild one,
4.  They have modified the source to include/remove whatever they intent,
5.  Or maybe they just want to learn more about building/compiling...

---

### Post by aysiu on 2005-12-11
[QUOTE=runlevel0]
What I wonder about is: Why do so many new users thing software in Linux *must* be compiled?

What are we doing wrong? IMHO we need to enfatize on how to manage software in our distros, as I see that a great many of them doon't even know that you can install software via double click on a DEB file.[/QUOTE] As a relatively new user myself, I can answer this question.

To new users, especially from Windows, the idea of a package manager that draws on repositories is an entirely foreign concept. No utility in Windows has a wealth of free software that it can download and install for you at the click of a button.

In Windows, you find a setup.exe file from some website, download it, and click through to some wizard thing. So, new Linux users usually think, "Okay. I want such-and-such a program. I'll go to their website and download it."

They get a .tar.gz, and instead of it opening up a wizard when they double-click it, they get a README file. What does the README file say? It says you have to compile it and ./configure and make and make install and have all these dependencies and whatnot.

So that's the answer to your question.

---

### Post by runlevel0 on 2005-12-12
[QUOTE=aysiu]As a relatively new user myself, I can answer this question. [...]
So that's the answer to your question.[/QUOTE]

Thanks a lot.

I was really wondering how new users came to the idea of compiling stuff. 

Maybe distro people should take this into consideration and place messages during the install process, or even better at the first login into the desktop, stressing the ease of use of the packaging systems. IMHO this would improve the new user's linux experience.

---

