---
title: "I use the amule to download, but the filename is a mess?"
date: 2008-09-11
forum: Desktop Environments
---

### Post by Daniel_wang on 2008-09-11
I use chinese version, some body say it is because the character code conversion between utf and gb failed, can only solve it manually.

but, other say we can write a script

but i really do not how to write it

extract the ed2k links and then save it in a list file

iconv -f gkb -t utf8 -o listnew list
then convert the gbk to utf8 

then  copy listnew to  $HOME/.aMule/&#19979;&#30340;ED2KLinks
cp listnew ~/.aMule/ED2kLinks
then when amule launches it can get the right chinese name of the link

---

### Post by LRKSFAG on 2008-09-11
[size=2]&#25105;&#39030;&#20320;&#20804;&#24351;[/size][IJK&#36724;&#25215;](http://www.nsk2008.cn/see/249.html)[THK&#36724;&#25215;](http://www.nsk2008.cn/see/248.html)[KOYO&#36724;&#25215;](http://www.nsk2008.cn/see/246.html)[ASAHI&#36724;&#25215;](http://www.nsk2008.cn/see/247.html)

---

### Post by Daniel_wang on 2008-09-13
any idea?

---

