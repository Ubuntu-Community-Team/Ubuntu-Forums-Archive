---
title: "Do I really need the source repos?"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Megatog615 on 2006-09-25
I'd like to speed up my "sudo apt-get update"s, as I do it a lot. Do I really need the source repositories? I don't compile anything from source, so I don't see the need.

---

### Post by lamego on 2006-09-25
If you dont need to compile from the source you don't need them.

---

### Post by Megatog615 on 2006-09-25
Well, I was kind of skeptical. I thought since the default /etc/apt/sources.list comes with deb-src repos, maybe some packages(that I had yet to install) required that some dependencies be compiled, or something.

Thanks for the reply.

---

### Post by eeried on 2006-09-25
sources are included in the sources.list because, I think, sources should always be made available when free (= libre) software is distributed.

You can comment them out with a hash sign # at the beginning of the lines.

cheers

---

### Post by Megatog615 on 2006-09-25
Oh, right. Yea, I commented them out. I think the Ubuntu installer should ask you if you want to enable them in the installation process, instead of tying up the apt-get update of many users who won't even use the source packages.

---

