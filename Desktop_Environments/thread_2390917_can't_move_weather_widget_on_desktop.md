---
title: "can't move weather widget on desktop"
date: 2018-05-03
forum: Desktop Environments
---

### Post by vbdanl-yahoo on 2018-05-03
Hi.  Been searching for awhile and can't find solution to what seems like a very easy problem.  Just installed 18.04 and my-weather-indicator.  When I select the option to display a widget, it appears in the upper right hand corner over the top of the taskbar that displays on the left border.  I have tried to move it with mouse, also used alt key and mouse, nothing seems to be working.. i know this is probably UE, but i will appreciate someone setting me straight.. thanks.

---

### Post by Xian on 2018-05-03
I checked my widget .... 

When I left click anywhere in the widget the cursor becomes a hand that can be used to move to another location. 

That is unless another of the program's dialogue boxes is open, i.e. preferences.

Such as:

[[IMG]http://i.imgur.com/fJeVqngm.png[/IMG]]("https://imgur.com/fJeVqng")

If nothing else works you may just rename your $HOME/.config/my-weather-indicator folder. 

See if a default config will knock it right.

---

### Post by vbdanl-yahoo on 2018-05-03
Are you using ubuntu 18.04 ?  I have tried left click and right click mouse..nothing works.
Attached is a pic of my desktop.  I even tried moving the taskbar from the left to the right side of screen.
The Activities "button" or "drop down" keeps me from seeing the upper left corner of the widget.
I thought maybe there was supposed to be a pin in the upper left corner, but i can't get to it.
Any style widget I try does the same thing..
It works fine on another computer that has 16.04 on it.
Will try your suggestion..

---

### Post by Xian on 2018-05-03
Yes .... on 18.04. Just upgraded via apt-get. 

I'm using the all-in-one widget - you can see in bottom left corner. 

[IMG]https://imgur.com/X62pLlChttps://i.imgur.com/X62pLlC.png[/IMG]
[[IMG]http://i.imgur.com/X62pLlCm.png[/IMG]]("https://imgur.com/X62pLlC")

---

### Post by vbdanl-yahoo on 2018-05-04
strange.. still does not work for me.. i changed to the allinone widget and you can see it in upper left.  still can't move it with right or left click.
i moved taskbar to bottom to look more like yours.  looks like your applications icon is in different location (upper left) instead of Activities like I have.
i installed via usb drive after downloading iso image.  not sure why that would be different than what you did.
also tried to autohide taskbar but that didn't make any difference on moving widget.
tried to attach latest desktop image but it won't let me (maybe i can only do one attachment per time limit or thread?)
it says waiting for ubuntu, then msg goes away and file is not uploaded.
I see you are running budgie? instead of gnome shell.. could that be the difference ?

---

### Post by vbdanl-yahoo on 2018-05-04
not really sure why the config file starts with x,y coordinates as 0,0 but after comparing this config with the one on another computer that was the difference.
I used vi to update the x,y from 0,0 to 1200,30 and now my weather icon appears on the right side of desktop where i wanted it.
Now i can see the red pin and left click changes it to a red dot but not a hand, so i can't manually move the widget.
Not sure if there is another parameter (maybe true,false) that controls allowing us to move the widget or not..
thanks for your help, and i will mark this as solved !!

---

### Post by vbdanl-yahoo on 2018-05-04
attached is new desktop image..

---

### Post by scarboni888 on 2018-05-06
I just upgraded from 17.10 to 18.04 and have the same problem: the widget is stuck in the same place it basically got moved to during the upgrade which in my case is top right area of the screen which is better than what vbdanl-yahoo had however I usually drag it onto a secondary monitor for normal use.  Since this is now two of us there's definitely something going on with not being able to move the thing around after installing or updating to 18.04

---

### Post by livtin on 2018-05-27
This has been affecting me since I updated to 18.04

---

### Post by raymondsirois on 2018-10-14
I'm experiencing the same issue.  Has there been a fix posted?

---

### Post by clearlex on 2019-06-28
Edit ~/.config/my-weather-indicator/my-weather-indicator.conf file.
Modify the values for "wp1-x" and "wp1-y". These are the coordinates of the widget.


Default Values
"wp1-x": 0,
"wp1-y": 0,


My settings
"wp1-x": 1053,
"wp1-y": 24,

---

### Post by lisati on 2019-06-28
Back to sleep, old thread.

Thread closed.

---

