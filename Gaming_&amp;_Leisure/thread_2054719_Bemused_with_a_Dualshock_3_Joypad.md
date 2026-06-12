---
title: "Bemused with a Dualshock 3 Joypad"
date: 2012-09-07
forum: Gaming &amp; Leisure
---

### Post by tuppe666 on 2012-09-07
I'm not using my joystick right...In fact I'm not using it at all. Its a dualshock 3. I'm trying to get it working with Native Linux games and failing with all of them, whether it be Supertux [I can move the menu a bit] or oolite [I can turn but nothing else]. A quick test with jstest-gtk and everything seems to be working. I just can't seem to play games with it [I don't mean map X.org events or map keys]

---

### Post by tuppe666 on 2012-11-22
I tried again as I have Super Meat Boy...and Dustforce both games I think are worthless without a controller. I can't even find a basic Keymapper. Any help would be appreciated.

---

### Post by xREDEMPTIONx on 2012-11-23
Hi, I've been successfully using the dualshock3 in ubuntu for awhile now and I've noticed that- 
1.) not all games even support the use of a gamepad and in this case you will have to emulate mouse and keys (i use qtsixa which allows custom profiles)
2.) the default layout for the dualshock3 as it shows in jstest-gtk is not usually correct, if the game supports gamepads but doesn't let you map the buttons in the game itself you will have to go to the mapping option in jstest-gtk and change the order of the axis and keys so they match with the game

hope this was some help

---

### Post by tuppe666 on 2012-12-01
> **xREDEMPTIONx said:**
> Hi, I've been successfully using the dualshock3 in ubuntu for awhile now and I've noticed that- 
1.) not all games even support the use of a gamepad and in this case you will have to emulate mouse and keys (i use qtsixa which allows custom profiles)
2.) the default layout for the dualshock3 as it shows in jstest-gtk is not usually correct, if the game supports gamepads but doesn't let you map the buttons in the game itself you will have to go to the mapping option in jstest-gtk and change the order of the axis and keys so they match with the game

hope this was some help

Its been some help I have installed QtsixA I seem to be able to create a profile...just not use one.

I know about moving the mapping around in jstest-gtk...I'm just not sure how I would move any of them too :)

---

### Post by xREDEMPTIONx on 2012-12-01
For qtsixa- go up to the menu bar and click Settings, Manage Devices/Profiles, then you'll get a window with devices. Click on the Default entry and click edit, follow the wizard to apply your profile to the controller.

It took me a while before I realized how to map in j-test, on the mapping window you have two sides, axis on left and buttons on right. They are displayed in a list. To remap just click and hold one of the list entries and drag it into the position you want. i.e. you have a racing game where the square button is the gas, and you want it R2 instead. In j-test the square button is the number 4 entry in the list, and R2 is 9. drag the entry for R2 from the no 9 slot to the number 4 position. It will now be the gas. There is a command to let you permanently save your remapping the joystick for j-test-gtk, it is
  sudo jscal-store js0

---

### Post by tuppe666 on 2012-12-02
Thank you that was very useful

---

### Post by xREDEMPTIONx on 2012-12-02
Your welcome:)

---

### Post by gotgenes on 2012-12-16
I'm struggling to use my PS3 controller with Super Meat Boy. Would you guys be willing to share a little more information on how you fixed the mapping using jstest-gtk and/or QtSixA?

---

