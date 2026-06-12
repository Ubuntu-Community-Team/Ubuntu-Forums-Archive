---
title: "Need help with java and firefox"
date: 2006-03-29
forum: Desktop Environments
---

### Post by cooldudejz on 2006-03-29
i just updated to the newest firfox 1.5 and everything works except java. i know that i have to create a link, but i do not know how.

---

### Post by nazish on 2006-03-30
first tell me where is your JRE located
 or else i let me give you the commands to make it work
goto the directory containing JRE

the path to the plugin is
 
**JRE->plugin->i386->ns7**

in this directory you will find a file called as **libjavaplugin_oji.so**

now you should create a symbolic link to this file in your Firefox directory

open the terminal

goto firefox directory usually /usr/lib/firefox

goto plugins directory

now you are in /usr/lib/firefox/plugins

then run the following command

[B]ln -s /usr/lib/firefox/plugins/libjavaplugin_oji.so /(path to JRE)/plugin/i386/ns7/libjavaplugin_oji.so
[/B]

change your paths if they are not as above

and to test java visit 

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

