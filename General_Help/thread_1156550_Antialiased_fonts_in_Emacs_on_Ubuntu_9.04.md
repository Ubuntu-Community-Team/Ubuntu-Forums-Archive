---
title: "Antialiased fonts in Emacs on Ubuntu 9.04"
date: 2009-05-11
forum: General Help
---

### Post by metadave on 2009-05-11
Hello -

  Is there any easy way to get anti-aliased fonts to work in Emacs 22.2 w/ GTK on Ubuntu 9.04 (x86)? I've found several old articles/posts on this, but the tips don't seem to work anymore (or repositories are now missing etc).

Thanks -
Dave

---

### Post by GrouchoMarx on 2009-05-13
Here is the Emacs Wiki: [http://www.emacswiki.org/emacs/XftGnuEmacs]("http://www.emacswiki.org/emacs/XftGnuEmacs")

Note that emacs doesn't use anti-aliased fonts by default. You have to explicitly tell it to use an anti-aliased font (like Bitstream Vera Sans Mono).

---

### Post by radiocognition on 2009-05-14
I am an Emacs user myself - and this was something that always drove me crazy.  A while ago, I was compiling Emacs from the Savannah CVS tree from source in order to get decent fonts.  Nowadays its just easier to do:
```
sudo aptitude install emacs-snapshot
```

Much cleaner!  I know it's not emacs 22, but there is less hassle

---

### Post by metadave on 2009-05-14
Installing the emacs-snapshot worked perfectly!
THANK YOU!!!

---

### Post by jpkotta on 2009-05-15
emacs22-gtk also works.  You need to either uninstall emacs22 or use Debian alternatives to make the GTK emacs default.
```
sudo update-alternatives --config emacs22
```

---

