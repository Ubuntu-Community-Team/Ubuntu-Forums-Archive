---
title: "E1505 Run/Install"
date: 2007-06-10
forum: Dell  Ubuntu Support
---

### Post by dutch1918 on 2007-06-10
Howdy folks:

I have a E1505 with the ATI Mobility Graphic card.  I am currently running openSUSE and I had to install the ATI drivers to get the proper resolution.  I would like to see what Ubuntu is all about so I download the Live 7.04 version but as expected it does not like my ATI card as X11 fails on boot.

Is there by chance another Live version that will work or maybe a work around.

Thanks for your help.

---

### Post by nachotronics on 2007-06-10
Hello, you can try this:

After you get the error on the live cd(x fails to start) do the following

```
wget http://www.mylittleubuntuguide.com/files/ati
chmod +x ati
./ati
```

as stated in [**_this howto_**]("http://ubuntuforums.org/showthread.php?t=399913&highlight=how+to+inspiron+feisty")

Hope this helps :wink:

---

### Post by danhm on 2007-06-11
That howto is great -- it worked wonders for me. I also have an e1505 and an ATI card.

---

