---
title: "Clearing your repositories."
date: 2009-04-19
forum: General Help
---

### Post by CodyK46 on 2009-04-19
I've accumulated several repositories. Most of them don't work anymore and is getting to be a pain to see the message pop-up saying they don't work. Since I don't feel like going 1 by 1 to delete the software sources, is there an easy way to erase your repositories besides the ones that came with Ubuntu?

---

### Post by Yashiro on 2009-04-19
Open Synaptic. Settings Menu > Repositories.
Click the Third Party Software tab. 
Select a repository and click the huge remove button at the bottom of the window. 
Repeat till the list is empty.

Or

Browse to /etc/apt.
Delete all the files within* sources.list.d* folder.
Edit the file sources.list and remove all the repositories you don't need.

Something like:
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) *hardy* main universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) *hardy*-security universe main multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) *hardy*-updates universe main multiverse*Replacing hardy with the name of your version, of course.*

Is all you need. If you use the gui tool after this you can add any extra official repositories that I didn't include.

---

