---
title: "ATI restricted driver &amp; Desktop Effects"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by tom1g on 2007-06-26
FIrst I tried to eneble Desktop Effects. But, strange thing happened: screen was white and only thing I could see was the cursor. About 30 sec later,  screen became normal again and Enable options was still there untouched. I thought that problem is in drivers (I have ATI Radeon Mobility Xpress 200m). I opened Restritted drivers dialog and enabled ATI Restricted driver.

I restarted my machine after that.

After restart, I tried to open Desktop Effects dialog. But there was (and still is) an error saying: The Composite extension is not available.

How can I fix it?

---

### Post by acadiansteph on 2007-06-26
I have the same ATI chipset and the same thing happened to me. As far as enabling the composite extensions, i imagine I'd have to had a comment to the Xorg file,but alas I do not know How to do it. There is the Unofficial Ati  wiki , which gives a detailed instruction on direct rendering (i.e 3d acceleration). You might find further info there.

---

### Post by tom1g on 2007-06-26
> **acadiansteph said:**
> I have the same ATI chipset and the same thing happened to me. As far as enabling the composite extensions, i imagine I'd have to had a comment to the Xorg file,but alas I do not know How to do it. There is the Unofficial Ati  wiki , which gives a detailed instruction on direct rendering (i.e 3d acceleration). You might find further info there.

I am on linux for less than 24 hours, any noob turot there? :D

---

### Post by acadiansteph on 2007-06-26
Welcome to Ubuntu. Don't be afraid of searching the forums before posting. I hope you enjoy your Ubuntu. If you are unsure of something in Ubuntu, just ask and someone will help. I'm a noob myself(with only 15 beans) and wish I could help you more. My moto in Ubuntu 7.04: If I don't know what it does (or what it's for), I'm not touching it!!!:D . Good luck and welcome to the forum!! Steph

---

### Post by tom1g on 2007-06-26
> **acadiansteph said:**
> Welcome to Ubuntu. Don't be afraid of searching the forums before posting. I hope you enjoy your Ubuntu. If you are unsure of something in Ubuntu, just ask and someone will help. I'm a noob myself(with only 15 beans) and wish I could help you more. My moto in Ubuntu 7.04: If I don't know what it does (or what it's for), I'm not touching it!!!:D . Good luck and welcome to the forum!! Steph
People help to a certain level, They aren't almighty.

Any ideas how to fix this? I really want to turn on desktop effects ...

---

### Post by akschnare on 2007-06-26
I don't think that compiz will work with the restricted drivers. For that, you have to download Beryl or the new Compiz Fusion. It's a shame that ATI doesn't support Linux better, but there's not much you can do. 

The good news is that when you install Beryl, it works great. Hope that helps.

---

### Post by kpolice on 2007-06-26
You have to install XGL to use compiz with the restricted drivers.

---

### Post by tom1g on 2007-06-26
any nooby howto?

---

### Post by acadiansteph on 2007-06-26
Hey Tom1g try this link: [http://ubuntuforums.org/showthread.php?t=272104&highlight=Official+ATI+Wiki](http://ubuntuforums.org/showthread.php?t=272104&highlight=Official+ATI+Wiki) . I am sure  you will find info on your driver and much more!!! Links about Compiz, Beryl and 3d acceleration

---

### Post by tom1g on 2007-06-26
> **acadiansteph said:**
> Hey Tom1g try this link: [http://ubuntuforums.org/showthread.php?t=272104&highlight=Official+ATI+Wiki](http://ubuntuforums.org/showthread.php?t=272104&highlight=Official+ATI+Wiki) . I am sure  you will find info on your driver and much more!!! Links about Compiz, Beryl and 3d acceleration

Thx Steph

---

### Post by acadiansteph on 2007-06-27
Another link Tom1g which is useful to get 3d acceleration (i.e.  to play 3d games, etc). Here is the URL:  [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)  . This is the guide I used to get graphics accelerations with my ATI 200m . Hope it helps, Steph

---

