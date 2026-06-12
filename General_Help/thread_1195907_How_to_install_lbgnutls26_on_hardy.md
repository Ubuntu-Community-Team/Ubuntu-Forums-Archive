---
title: "How to install lbgnutls26 on hardy ?"
date: 2009-06-24
forum: General Help
---

### Post by emshains on 2009-06-24
Hello and welcome. 
I recently downloaded alienarena2009 and when I tried to launch it, it complained about not having libgnutls26. So, I just typed ```
sudo apt-get install libgnutls26
```
Here's the output: 
```
$ sudo apt-get install libgnutls26
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Pakotne libgnutls26 nav pieejama, bet t&#257; nor&#257;da uz citu pakotni.
Tas var noz&#299;m&#275;t, ka pakotne iztr&#363;kst, t&#257; var b&#363;t novecojusi, vai 
pieejama no citiem avotiem.
E: Pakotnei libgnutls26 nav instal&#275;&#353;anas kandid&#257;tu
### And here's the translated version of the output ###
$ sudo apt-get install libgnutls26
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The package libgnutls26 is not accessible, but it refers to another package.
The package may be missing or outdated or only accessible from different sources.

E: The package libgnutls26 hasn't got any installation candidates.

```

Well, the translation is a bit freaky, but I hope it will help you to point out the problem. I know I have libgnutls13. So, I have to upgrade to 8.10 or 9.04 to get it working ?

---

### Post by michy99 on 2009-06-24
You can try downloading the intrepid .deb for libgnutls26 and installing it manually:

[http://packages.ubuntu.com/intrepid/libgnutls26](http://packages.ubuntu.com/intrepid/libgnutls26)

Be aware, though, that it may require newer versions of some other packages which then require others, and it can get into a pyramid of unsatisfiable dependencies.

On the other hand, it might work.

---

