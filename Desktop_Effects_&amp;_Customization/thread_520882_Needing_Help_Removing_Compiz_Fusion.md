---
title: "Needing Help Removing Compiz Fusion"
date: 2007-08-08
forum: Desktop Effects &amp; Customization
---

### Post by amyfan on 2007-08-08
i installed compiz fusion through this site [http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml]("http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml")
and now i need help to uninstall it its not my cup of tea its cool and all but i just don't like it also yes i used synaptic s but that dont remove it its still in effect any one please if u know how to totally remove all the files that site had me install please help u can reach me at aim im agememirpnort or at hot mail im battlemouse1 please someone help

---

### Post by Mr-Monkey on 2007-08-08
Use this 

```
sudo dpkg --remove --force-remove-reinstreq  NAME THE PROGRAM HERE
```

---

### Post by Hayesio on 2007-08-08
Change back to Matacity or whatever your original/defalt windows manager is.

The site you intalled compiz-fusion from lists the packages you installed.

Go through each package with:

sudo apt-get remove "package name" --purge

The terminal may also return redundent dependancy files and recommend that you use "autoremove" to remove them - do this.

Thats what I'd try anyway.

Cheers

---

