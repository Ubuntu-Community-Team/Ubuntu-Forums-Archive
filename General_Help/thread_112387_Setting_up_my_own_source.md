---
title: "Setting up my own source"
date: 2006-01-04
forum: General Help
---

### Post by thessem on 2006-01-04
I've been using ubuntu for about 3 days, and I have done what I ussually do with any new distro, and that is to explore every option and push the distro as far as I can with tweaks ect.

Needless to say that Ubuntu is so very screwed at the moment. Its going to be easier to just re-install now that I know what I'm doing.

I was just wondering, because I have a very limited download limit, how would I go about not needing to re-install all these packages (Like kde and all that) that I installed using apt-get and synaptic?

I'm pretty sure they are all stored in /var/cache/apt/archives/ as .deb files. I'm just wondering how to set that up in sources.lst so that, if apt-get or synaptic download something, it will check if I have a version stored on my harddrive first?

Basicly, I'm asking, how to I set up my own reposotry (hopefully ftp, so I can do this for other computers on my network without having to re-download everything), and make it the prefered repos to download anything from.

Another solution, although I don't think it is exactly what I want, would be a command that just does sudo dpkg -i <somesortoffunkywildcard>, so it just installs all the .debs in a folder.

Any answer would be greatly appreciated.

---

### Post by thessem on 2006-01-04
Okay, after about 5 minuts RTFMing, I'm pretty sure that

```
sudo dpkg -i -R <folder where I eventually copy the archive to>
```

will work.. Or it won't, can be bothered testing it atm. the problem is, I dont want most of the packages that would be installing, and there are 100s to sort through, and I could really use my own local reposotry.

---

### Post by mcduck on 2006-01-04
Take a look at this: [https://wiki.ubuntu.com/AptMoveHowto]("https://wiki.ubuntu.com/AptMoveHowto")

and I think that 'sudo dpkg -i /path/to/your/debs/*.deb' would work too.

---

### Post by thessem on 2006-01-04
Thanks alot. That is exactly what I wanted. Now I'm going off In a journey with duel boot/ Duel OS.

Thanks again.

---

