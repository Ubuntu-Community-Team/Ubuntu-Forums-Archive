---
title: "Questions on Synaptic Package Manager"
date: 2008-12-24
forum: General Help
---

### Post by jikki on 2008-12-24
Hi, first of all I switched to linux from vista yesterday and I love it! :) I consider myself fairly advanced in computing on windows..now that I take a step back, I find a whole another world of linux! I especially appreciate the Synaptic Package Manager, keeping me up to date on basically everything.

  So here's my question. I noticed some files on the Synaptic Package Manager were a little out-dated. (ex. Battle for Wesnoth) How long does it generally take for Synaptic's 'default' servers to release a version when that version comes out? And also, I found a wonderful site "getdeb.net" which has the newer versions, and was wondering if it was possible to add the site as one of the servers that Synaptic automatically checks for updates from.

 Thanks a lot for your help and please tell me any more important, slightly-advanced things I need to be aware of while using linux! :)

---

### Post by binbash on 2008-12-24
you cant add getdeb to synaptic because it does not offer a repository.If it offers a repository you can add.Ubuntu is not a rolling release distro so NEW packages comes every 6 months with new releases.

---

### Post by hyper_ch on 2008-12-24
well, normally during a release there are no versioning updates on software - only security updates.

If you are still using 8.04 you can add playdeb - it has more games in it. You could even try to add it as repository to 8.10 BUT it is NOT RECOMMENDED! If you just wanna try it and if you are ok that you might be required to reinstall everything then you can surely try.

[http://www.playdeb.net](http://www.playdeb.net)

For additional repos, see my signature.

---

### Post by druellan on 2008-12-24
Yeah, I also thought on first sight that Ubuntu's repos will maintain my OS and all my apps up-to-date, and that's true but only when a new Ubuntu version comes out. Meantime, you only get security updates.

You can get recommended but not supported updates for applications and libraries enabling the "backports" on software sources.

To get updates of all your apps via getdeb, you can try this unofficial repo: deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/ It works and is reasonably up to date.

---

### Post by jikki on 2008-12-24
Oh ok, thank you all for your help. And thanks for the link, it would be very useful! :)

---

### Post by Nepherte on 2008-12-24
Here's some more information:
You have basically two types of linux distributions. Either with an update release cycle or so called rolling release distributions. The first one means you'll get new versions of software after every new release cycle. An example of this system is Ubuntu. They generally only include bug and security fixes and every 6 months (the release cycle) they update every piece of software. The second type is a rolling release distribution. They continously update their software to the most recent version and don't have a release cycle. They mostly don't really have a distribution version like ubuntu has (8.04, 8.10, ...). They only have one version, the most current one. An example of this second type is Arch Linux.

---

### Post by snova on 2008-12-24
You can try enabling Backports if you want more frequent updates. It probably won't have the absolute latest version, but it'll be closer at least.

Open System -> Administration -> Software Sources, Updates, and tick the fourth box. Reload from Synaptic.

(Keep in mind this'll update a lot more than just Wesnoth, probably a sizeable chunk of the system. In that case, only update the ones you want and disable Backports afterwards; it shouldn't harm anything.)

---

### Post by jikki on 2008-12-24
Wow, thank you again! :) This will surely quicken my process of getting out of the beginner zone!

---

