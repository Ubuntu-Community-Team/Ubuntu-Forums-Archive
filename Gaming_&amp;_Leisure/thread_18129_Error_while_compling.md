---
title: "Error while compling"
date: 2005-03-04
forum: Gaming &amp; Leisure
---

### Post by orvalax on 2005-03-04
I get an error when I try to compile Wesnoth. Its a turn based strategy game. I believe there is something is wrong with the complier itself. It won't complie anything. Its gives an error with finding a gcc file and a few others. I tryed compling the exact same things on a different computer with ubuntu it worked. We have a pair of uber newbs here using ubuntu. Well heres the code, I'd appreciate anyone's input.

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

---

### Post by bored2k on 2005-03-04
apt-get install gcc build-essential cpp      [cpp justin case

---

### Post by orvalax on 2005-03-04
Awesome, It worked like magic. Thank you very much.

---

### Post by Eggbanjo on 2006-09-02
sudo apt-get install gcc build-essential cpp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc


Any ideas??

---

