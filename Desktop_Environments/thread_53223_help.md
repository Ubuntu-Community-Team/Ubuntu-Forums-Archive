---
title: "help"
date: 2005-07-30
forum: Desktop Environments
---

### Post by PKing1977 on 2005-07-30
I just started Kubuntu in text mode at start up. When I rebooted I go right into text mode. How do I get back to my gui mode ;(

---

### Post by Feanor on 2005-07-30
try to do 

```
startx
```

or

```
startkde
```

---

### Post by PKing1977 on 2005-07-30
it tells me that I do not have the proper nvidia drives.. 
when I try to apt-get nvidia-glx it wont let me. is there anyway to get the nvidia drivers back on?

---

### Post by Feanor on 2005-07-30
I think it's better for you to search in the forum because I've read a lot of topics about nvidia driver. All that can I suggest you is to set temporarly the driver to "nv" to get access to graphic interface. So edit your xorg.conf file and replace the driver string in your "device section" with "nv".

To install nvidia drivers try to install kernel restricted modules. But I repeat that I think there are better answers in the forum  ;-)

---

### Post by PKing1977 on 2005-07-30
I got it!!! ya.. I forgot to put the install before nvidia-glx.. now I am back in kde.. However is there away to get the latest Nvidia driver to install? I am not having much luck with it.

PKing

---

### Post by Feanor on 2005-07-30
I think the best way is to download them from nvidia website  ;-) 

However the drivers on the repository should work well  :|

---

### Post by PKing1977 on 2005-07-30
I have the drivers from the website, but I can not install them. They talk about having them installed already, I need the latest drivers to get the 7800 support :(

---

### Post by Feanor on 2005-07-30
It's over for my knowledge  :?

---

### Post by Mishura on 2005-07-31
I don't recommend the newer nvidia drivers, especially if you play games in Cedega or wine.  I had some SERIOUS graphical glitches (models rendering in ALL directions or something.. ) while playing Knights of the Old republic.   Its a known problem here:  [http://digital-conquest.ath.cx/wiki/index.php/Knights_of_the_Old_Republic](http://digital-conquest.ath.cx/wiki/index.php/Knights_of_the_Old_Republic)

Of course, if you don't plan on playing emulated games, then I guess its ok.  I didn't notice a difference in performance with various Native and Emulated games between driver versions...  just that KoToR bug.

---

