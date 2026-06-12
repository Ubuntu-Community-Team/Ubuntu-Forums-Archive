---
title: "I have an issue with the .desktop file"
date: 2015-04-28
forum: Desktop Environments
---

### Post by Microud on 2015-04-28
Uhh...Forgive my poor English.
Today I downloaded an application and I want to and it to my Dock,so I write a .desktop file in "/usr/share/applications".
It can be draged to the dock and show the icon correctly.But when I click it,it do nothing.The icon blinks(sorry I don't know is it the right word,I mean blinblin,OMG,if you can't understand just skip this sentence:cry:) for seconds but then nothing happen.h 
I think that I write the contents blow is right and the permission is right ,too.
```
  1 [Desktop Entry]  2 Exec=/opt/shadowsocks/shadowsocks.sh
  3 Icon=/opt/shadowsocks/icon.png
  4 Type=Application
  5 Terminal=true
  6 Name=Shadowsocks
  7 Categories=Network;
  8 InitialPreference=9



```
Also,the real file "/opt/shadowsocks/shadowsocks.sh" is executable,but why can,t I exec it?
Oh,yes, I can run this script shell in folder "/opt/shadowsocks/" by "./shadowsocks.sh" without error.
I don,t konw why it doesn't work,so could someone help me? Thanks very much!:p

---

### Post by dino99 on 2015-04-28
an example : [http://askubuntu.com/questions/281293/creating-a-desktop-file-for-a-new-application](http://askubuntu.com/questions/281293/creating-a-desktop-file-for-a-new-application)

---

### Post by Microud on 2015-04-28
Thanks a lot!I have solved it.It's my fault to run the second one.

---

