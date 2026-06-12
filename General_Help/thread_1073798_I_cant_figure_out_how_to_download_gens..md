---
title: "I cant figure out how to download gens."
date: 2009-02-18
forum: General Help
---

### Post by fbjoey on 2009-02-18
Can anyone help me out?

I cant find it in add/remove applications.
I just need pointing in the right direction and maybie some more help after that.

---

### Post by cosine352 on 2009-02-18
[http://ubuntuforums.org/showthread.php?t=290008](http://ubuntuforums.org/showthread.php?t=290008)

---

### Post by fbjoey on 2009-02-18
When I type

> sudo dpkg -i gens_*.deb

it comes up with 

> fbjoey@Fr3d:~$ sudo dpkg -i gens_*.deb
[sudo] password for fbjoey: 
dpkg: error processing gens_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gens_*.deb
fbjoey@Fr3d:~$ 


any ideas?

---

### Post by cosine352 on 2009-02-18
may be > cd Desktop

make sure you are in the right directory

---

### Post by Dougie187 on 2009-02-18
Are you in the correct directory? are you sure you have the file downloaded? Try typing (and posting) the results of
```
ls 
```
and
```
pwd
```

Actually, pwd is not needed since it is obvious you were in your home directory.

---

### Post by theozzlives on 2009-02-18
You got to download the file first.

---

### Post by fbjoey on 2009-02-18
That would explain it, I tryed downloading Gens/GS 2.15.5 M5 and it led to a page full of a strange code like this

>  !<arch>
debian-binary   1225007462  0     0     100644  4         `
2.0
control.tar.gz  1225007462  0     0     100644  1458      `
‹&#65533;&#65533;&#65533;&#65533;&#65533;íWÛŽÜÆÝçù
>:°vÔ]}_8F¯ ±%Á+ÛÉ“PÝUÍ%vf8 ¹ÒJÈÇ§–³2Ï(~’&#65533;<Ào]Åêºœ*®Ÿ}v(Apn>
~}œÏµÖJ+PÎz¹|g;ûp;N84ÍÙÐ÷Ó[÷[ÏÿO±~¼%7ÞnÇÏoí§âoµ…ÿŒ¿Ö&#65533;ê¬QKü?;P%>#iªUÇÊ¾0Å	Èx‹µinÇáqîv[Þ+2²–
æPŒó.P"XtÑéaùxÏóß›Üµë¼Ý¯R
>†ä DWPÙ‚DšAîðáHú™üÁº+ýŠl-Y—ÉI–&#65533;³Ó¾ˆ‰.‚‹|$ºÇrƒ-¿iqËãz¿kWk5¶Öh«‹Õd¦¯˜Š)É©xìo‡Â³4¨š*;y—V©údÏFJ†<°:6ànÝnšeÉû*›vÉÆœ|*+Çâ X".DG²Ûžx;‹Zä”,ˆãT¸$å|¬52aTâÄc‡ßl»»YR””MÍ
bI£´“`öN»ˆ'<6ŽïúfédªO[¤\jE•1‘äŠó5W•¼>èq‹›Í,¯(˜êªP2J “
EA-ÚxÖÇ[¾îÆ©ÞÏÂ•\ÖÊ² ‰•Î.aŒ6 ÙÐ'ƒ=ò4u»v|ˆršµÓ‘-g

and the other leads to a download page that tells me to wait 50 seconds before my download starts and then never downloads it.

---

### Post by cosine352 on 2009-02-18
right click the link and do 'save link as' or 'save target as'

---

### Post by fbjoey on 2009-02-18
Right ok its downloaded and on my desktop. How do I get  > sudo dpkg -i gens_*.deb to pick it up from my desktop instead of where ever it looking for stuff.

---

### Post by cosine352 on 2009-02-18
just double click on the downloded file

---

### Post by fbjoey on 2009-02-18
Thanks :D works a treat :D

---

### Post by doas777 on 2009-02-18
or if doubleclicking doesn;t work,
open a terminal and enter 
```

cd ~/Desktop

```

then your working directory will be '~/Desktop/'. you can confirm this with ```
pwd
``` (Print Working Directory).

once you are in the desktop folder, your command should have no problem finding your .deb

good luck

---

