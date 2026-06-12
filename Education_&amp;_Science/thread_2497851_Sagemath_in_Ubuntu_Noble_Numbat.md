---
title: "Sagemath in Ubuntu Noble Numbat?"
date: 2024-05-20
forum: Education &amp; Science
---

### Post by Bakerbakura on 2024-05-20
Hello there

Does anyone know why Ubuntu 24.04 doesn't include sagemath? Strangely, a few of the Sagemath database packages are in the repository for Noble Numbat, but not the main Sagemath package.

I'm not sure if this is the right place to ask. Who are the people who decide this sort of thing?

---

### Post by deadflowr on 2024-05-20
sagemath was removed because it fails to built with python 3.12 on Ubuntu.
See: [https://bugs.launchpad.net/ubuntu/+source/sagemath/+bug/2063058](https://bugs.launchpad.net/ubuntu/+source/sagemath/+bug/2063058)

Not sure if they can or should also remove the database packages if it's pointless to have them if the main package isn't there...

> Who are the people who decide this sort of thing?
Looks like the Ubuntu Desktop team.

---

### Post by Bakerbakura on 2024-05-21
Hmm that's strange. I was able to build Sagemath from source from their latest GitHub release using Python 3.12.3 (having to jump through a few hoops, but yeah).

---

### Post by grieda on 2024-06-20
[COLOR=#000000]That's a bit strange. I've run into similar issues before where certain packages aren't included in the main repo. It could be due to dependency problems or maybe the maintainers haven't gotten around to it yet. The decision usually lies with the package maintainers and the Ubuntu release team. I'd recommend checking out the Ubuntu forums or hitting up the Sagemath mailing list for more insight. I had to do the same with another software package a while back, and the community there was pretty helpful.[/COLOR]

---

### Post by egourgoulhon on 2024-07-26
Here are some [simple instructions]("https://sagemanifolds.obspm.fr/install_ubuntu.html") to install SageMath 10.4 in Ubuntu 24.04.

---

