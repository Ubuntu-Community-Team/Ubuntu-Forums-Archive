---
title: "What Are The Right Beryl Repositories?!?!?!?"
date: 2006-12-25
forum: Desktop Environments
---

### Post by mjolinr on 2006-12-25
ok, i got beryl and it works great, but my repository is outdated or something apparantly.  so i used to have **deb [http://beryl-mirror.lupine.me.uk](http://beryl-mirror.lupine.me.uk) edgy main** but that didnt work so i got rid of it (after making a backup of the original /etc/apt/sources.list) and i put in **deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main** and that seemed to find updates for beryl but they all fail when i try to install them. what are the right ones?????

---

### Post by JamesWP on 2006-12-25
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

That's Treviño's SVN Snapshot Repo, be warned though, it's not 100% stable, so if you rely on your desktop heavily don't use it, otherwise enjoy beryl with the latest features with almost 0 hassle :-).

Oh, be sure to add the key by running this command :-)

wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

---

### Post by AgenT on 2006-12-25
You must download and install the PGP key. For more information, visit:
[http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)

---

### Post by iamhugeinjapan on 2006-12-25
> **mjolinr said:**
>  i put in **deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main** and that seemed to find updates for beryl 

Not sure why they are failing but that's the right 'stable' repository.

---

### Post by mjolinr on 2006-12-28
> You must download and install the PGP key. For more information, visit:
[http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/)
ok so I did that and the updates installed, but then i got errors and it said i had a broken package and to fix it with some filter thing.  but now the updater says my system is up-to-date.  so do i still have to filter for the broken package?

---

