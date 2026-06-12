---
title: "ati radeon 4800 drivers issues /"
date: 2009-05-16
forum: Desktop Environments
---

### Post by lalamax3d on 2009-05-16
Previous History:
2 years ago. win xp 64 bit with nvidia geforce 8 series. unable to setup maya nicely. viewport behaves strange. start flickering while orbitting aroung.
search lots of forums. out of frustration i moved to ATI. Later on  ppl mentioned that don't use latest drivers. use old ones and it will work.

any how when moved to ati with windows. it had new problem with maya. rotation (multiple axis) won't work.
searched lots of forums again. out of frustration i moved to UBUNTU. later on ppl mentioned to use catalyst 8.xx driver and it worked for sure.

Current Scanario:
ok now i am on ubuntu. 9 (32 bit). fresh install. everything works good. ati radeon 4800 driver propriateory (green light is ON) apparently works fine.
what maya does, it makes everything hang
how : when hotbox appears,
i tried removing / disabling compiz / >> even moving xfce (simple gfaphical desktop manager)
it helps improving hang version. but what is still extremly annoying is maya viewport refreshing
as soon as any other view / window open >> previous goes black. 

i tried configuring houdini apprantice. it's viewport / windows behave much better but rotation / tranlation is is issue, because i can't rotate / translate in z axis

i tried ubuntu studio with hopes that it is for artists and should work. it is showing same problemo

What i want
1- currently which version of catalyst my ubuntu is using? how to get version in terminal (i.e gcc -v)
2- is it latest? - when ati released new one, will it update?
3- ATI has ati-driver-installer-9-4-x86.x86_64 on website. if my current is not latest. can i manually update to latest. will it help? are there some easy steps ?
hope to hear some guidelines and helpful response...
thanks in advance
regards
lala

---

### Post by stilling on 2009-05-16
1)try this command in terminal 
 fglrxinfo it will show you something like this
 OpenGL vendor string: ATI Technologies Inc.
 OpenGL renderer string: ATI Mobility Radeon
 OpenGL version string:(8.37.6)<-- Version

2)ubuntu always updates the latest versions but he will select what is 
  the best driver for you. 
3)yes you can install it download the .deb package save it on your
  desktop double click to open and select install
  If no .deb package find the rpm package use alien to transform it to
  deb and install it 

Hope this Helps you

---

