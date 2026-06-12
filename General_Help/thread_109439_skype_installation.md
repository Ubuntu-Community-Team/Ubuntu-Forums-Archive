---
title: "skype installation"
date: 2005-12-28
forum: General Help
---

### Post by dcy on 2005-12-28
can anyone help me installing skype?

I ve downloaded the latest version of skype from the skype website. it was a .deb file.

then i ve extract it to a directory. now there is control.tar.gz data.tar.gz and debian-binary tezt file. 

what should i do next?

thanks for your help.

---

### Post by gsmith on 2005-12-28
Generally the only thing you have to do to install a .deb is type "dpkg -i filename.deb".  IIRC skype requires some GUI libraries (qt?) that aren't in the default system, so you may need to install some other stuff to get things working.  I'm sure it'll report this problem to you at some point in the process.

---

### Post by darth_vector on 2005-12-28
the deb package on the skyp website is broken :)

download the rpm package for fedora core and so the following:

```
sudo alien --to-deb packagename.rpm
```

this will create a good, working deb package. then install it with

```
sudo dpkg -i packagename.deb
```

i believe this is in the wiki.

---

### Post by dcy on 2005-12-28
thank you very much..

i got some warnings about packages but at the end i was succesful..
btw. at this moment i ve found deb file on skype webpage..

but anyway thanks for your help..

---

### Post by rpalyvoda on 2005-12-28
Hi,

in "wiki" there is a howto:

[https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29)

it worked perfectly for me!

---

### Post by dcy on 2005-12-28
[QUOTE=rpalyvoda]Hi,

in "wiki" there is a howto:

[https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29](https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29)

it worked perfectly for me![/QUOTE]


you are absolutely right rpalyvoda...
i ve missed that document on wiki...
thank you very much..

---

