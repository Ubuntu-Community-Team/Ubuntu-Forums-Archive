---
title: "Create a symlink"
date: 2009-03-24
forum: General Help
---

### Post by fruitmix23 on 2009-03-24
Hi all,

I'm a very new ubuntu or linux user and I have a question regarding symlinks.

I have downloaded and installed the colorgcc deb file to get compiler error messages in color, it works for both C and C++ but in order to compile I need to use the command colorgcc *fileName* which realy doesn't bug me but since I need to produce a typescript for college assignments my professor would like me to use gcc or g++ to compile.

After googleing a little I came across a [forum page]("http://ubuntuforums.org/archive/index.php/t-434787.html") that said that I need to symlink the g++ or gcc to colorgcc could someone please show me how to do this.

Thank You,
Fruitmix

---

### Post by kanikilu on 2009-03-24
```
sudo ln -s /usr/bin/gcc /usr/bin/colorgcc
```

Alternatively, I think you could also make an alias in your ~/.bashrc file, e.g. ```
alias colorgcc='gcc'
```

//Edit - actually I'm not sure that will work. I mean, you can create a symlink with ln -s, but I don't think it's going to do what you want it to do. I'd probably try the alias first...

---

### Post by fruitmix23 on 2009-03-24
I tried both methods but they don't seem to be working. Thanks anyways appreciate the help.

colorgcc is better that black and white text.

---

### Post by heindsight on 2009-03-24
Making colorgcc a symbolic link (or alias) for gcc won't work. gcc itself doesn't produce coloured output just because you invoke it as colorgcc.

You need to install colorgcc which is a Perl script which calls gcc and then colourises the gcc output.

You can install colorgcc by doing:
```
sudo apt-get install colorgcc
```

---

