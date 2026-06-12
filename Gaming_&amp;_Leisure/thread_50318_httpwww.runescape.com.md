---
title: "http://www.runescape.com/"
date: 2005-07-19
forum: Gaming &amp; Leisure
---

### Post by cledus on 2005-07-19
I started working with PCs in DOS. (anyone remember?)....
Anyway, worked my way up to XP.
I found myself with a spare computer a few years back and started to experimented with Linux.
I was using mandrake, ending up with Mandriva 2005
Then I found Ubuntu. Nice ...until...

I am using my backup system for my kids.
My plan was working well until, my son wanted to play on [http://www.runescape.com/](http://www.runescape.com/)
Nothing shows up in the window. I checked the java console and found the following:

XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:

I searched but could not find anything to help.



My specs:
Intel P4 1.8
1 GB RAM
Hoary 5.04 (updated)
Firefox - Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050524 Firefox/1.04 (Ubuntu package 1.0.2 MFSA2005-44)

---

### Post by thechitowncubs on 2005-07-20
[QUOTE=cledus]I started working with PCs in DOS. (anyone remember?)....
Anyway, worked my way up to XP.
I found myself with a spare computer a few years back and started to experimented with Linux.
I was using mandrake, ending up with Mandriva 2005
Then I found Ubuntu. Nice ...until...

I am using my backup system for my kids.
My plan was working well until, my son wanted to play on [http://www.runescape.com/](http://www.runescape.com/)
Nothing shows up in the window. I checked the java console and found the following:

XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:

I searched but could not find anything to help.



My specs:
Intel P4 1.8
1 GB RAM
Hoary 5.04 (updated)
Firefox - Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050524 Firefox/1.04 (Ubuntu package 1.0.2 MFSA2005-44)[/QUOTE]
 do you have java installed? try re installing firefox

---

### Post by Omnios on 2005-07-20
If I remember correctly "Its been a long time since I installed Java" you have to create a link in firefox's plug in directory pointing to java. I dont remember If I read it here or on the java web site. The unoficial guide has an apt-get so not shure if that link was when I used synaptic to get java or the time I downloaded it from the Java website. Anyways check the forefox plugins directory and check if there is a link there.


 Edit: I just checked something, I recently updated my firefox and I guess my link to java is borked. Anyways it came back with you need to install a plug in, java plugin. Needless to say there was no error message which possibly points to a problem with the java install. Ill check again when I relink java.

---

### Post by bored2k on 2005-07-20
[QUOTE=Omnios]If I remember correctly "Its been a long time since I installed Java" you have to create a link in firefox's plug in directory pointing to java. I dont remember If I read it here or on the java web site. The unoficial guide has an apt-get so not shure if that link was when I used synaptic to get java or the time I downloaded it from the Java website. Anyways check the forefox plugins directory and check if there is a link there.[/QUOTE]
 The java package found on the backports automatically makes this web link for you.
It's installed with a simple
sudo apt-get install sun-j2re1.5

---

### Post by RastaMahata on 2005-07-20
get java from the backports, and issue the following command```
sudo ln -sf /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /etc/alternatives/firefox-javaplugin.so
```

---

### Post by cledus on 2005-07-20
Thanks for your quick replies.
Re-installed java and firefox.
Applied the steps above.
Works good, for me.
Will have my son test some more.

Thanks to all for the great support.

---

