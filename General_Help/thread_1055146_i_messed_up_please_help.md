---
title: "i messed up please help"
date: 2009-01-30
forum: General Help
---

### Post by jblinuser on 2009-01-30
i did a google search for cool things to do with linux and one of the sites that came up was this one.

[http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html](http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html)

so at the beginning of the site it talks about updating the repositories. so i copied and pasted the CLI comands into my terminal and after i did that i could no longer get into my  synaptic pkg mgr.

this is the error message it gives me.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i looked in the /etc/apt/sources.list.d and i can see the medibuntu.list file but i am unable to do anything with it. when i click on it it tries to take me to a site that is no longer in use. can anyone help my undo what i did with the CLI commands?

---

### Post by khedron on 2009-01-30
Try removing that file:
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by taurus on 2009-01-30
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And if you want to edit it, you have to use sudo/gksudo.  However, I think your /etc/apt/sources.list.d/medibuntu.list is all screwed up from the look at it.

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by khedron on 2009-01-30
What probably happened is that the server couldn't find the file you wanted, so gave you an html page instead explaining the error. The problem with wget is that it doesn't read html! So you just put an invalid file into your configuration directory.

Also, always be careful when following instructions for an Ubuntu version that's not the current one (Feisty vs Intrepid).

---

### Post by jblinuser on 2009-01-30
> **khedron said:**
> Try removing that file:
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

this did it thanks i knew it would be something easy like that i just didn't know the specific commands to use. thank you again.

---

