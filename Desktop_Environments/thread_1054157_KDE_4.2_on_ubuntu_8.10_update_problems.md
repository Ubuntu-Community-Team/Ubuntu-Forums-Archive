---
title: "KDE 4.2 on ubuntu 8.10 update problems"
date: 2009-01-29
forum: Desktop Environments
---

### Post by qjmoss on 2009-01-29
I followed the guide on 'http://www.kubuntu.org/news/kde-4.2' and I added the repo. No updates are available to me for KDE. I think this is because I don't have a previous version of KDE. If anyone knows how I can get a clean install of KDE 4.2 that would be greatly appreciated.

Also, I had KDE 4.1 and didn't like all the applications it came with, is there a way to remove the apps that are not necessity (clones of Gnome apps)

Thank you for the help =)

---

### Post by pritamps on 2009-01-29
> **qjmoss said:**
> I followed the guide on 'http://www.kubuntu.org/news/kde-4.2' and I added the repo. No updates are available to me for KDE. I think this is because I don't have a previous version of KDE. If anyone knows how I can get a clean install of KDE 4.2 that would be greatly appreciated.

Also, I had KDE 4.1 and didn't like all the applications it came with, is there a way to remove the apps that are not necessity (clones of Gnome apps)

Thank you for the help =)

Run the following to get KDE 4.2 after adding the repo:

```
sudo apt-get install kubuntu-desktop
```

That will install KDE 4.2 and it will show up in your Sessions in the login screen as KDE, I think.

Hope that helps!

---

### Post by qjmoss on 2009-01-29
Well thats what i thought, but I wanted to do it through Synaptic, so it's easily removable..


How would I go about removing every package if I didnt it through terminal..

apt-get remove wouldnt take everything out

---

### Post by pritamps on 2009-01-29
> **qjmoss said:**
> Well thats what i thought, but I wanted to do it through Synaptic, so it's easily removable..


How would I go about removing every package if I didnt it through terminal..

apt-get remove wouldnt take everything out

To remove KDE 4, you could do 
```
sudo apt-get remove kdelibs5
```

(Almost?) All KDE applications depend on this, so removing this would automatically remove all your KDE 4 applications. 

In any case, installing through Synaptic or the command line would give the same result.

One thing you could do was to install through aptitude instead of apt-get, i.e.
```
sudo aptitude install kubuntu-desktop
```

and then use aptitude to remove kubuntu-desktop as well. Aptitude does this metapackage thing quite well..

---

### Post by keypox on 2009-01-30
i followed those directions but when in kde i ran a command i cannot find now that said i had 3.5.10?   

I trying again...

---

