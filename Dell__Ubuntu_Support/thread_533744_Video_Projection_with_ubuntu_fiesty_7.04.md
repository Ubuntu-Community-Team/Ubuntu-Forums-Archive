---
title: "Video Projection with ubuntu fiesty 7.04"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by ewmiller13 on 2007-08-24
First of all I have a dell inspiron 2650 laptop

What I am trying to do is get it to work with a projector.

To my knowleged and minimal experience it isn't just going to work.

I dont know if anyone has heard of Lyricue becuase I don't think that it is the most popular application in use, but that is what im trying to get set up.

If anyone could give me some nice step by step info it would be greatly appriciated.

---

### Post by ewmiller13 on 2007-08-24
If anyone wants to know what lyricue is go here[http://www.adebenham.com/lyricue/]("http://www.adebenham.com/lyricue/")

---

### Post by dulbirakan on 2007-08-24
I wonder how is it coming along? Have you managed it?

---

### Post by ewmiller13 on 2007-08-24
If your just posting to post dont im trying to get anwers, please dont waste your time posting "nothing"

---

### Post by saru411 on 2007-08-24
1st question is your video card an nvidia go card? if so do you have the nvidia drivers installed? if so have you gone to nvidia-settings and tried changing xserver display configuration>configuration>configure>seperate x screen?

hope this helps. oh if you want to save this file you will have to start by doing this as root....

> sudo nvidia-settings

---

### Post by ewmiller13 on 2007-08-24
My video card is a Geforce2 Go I have been unsuccessful at getting the nvidia drivers to work because I have problems with the driver and am unable to find some solid information to get it working. If I dont need the drivers or if you can give me some seriously detailed info Sweet but if now I dont care to have them working I just want it to work with a projector.

---

### Post by ewmiller13 on 2007-08-24
The only thing I thought might help was to get the nvtvout application and/or the Xorg-edit GUI to edit xorg.

---

### Post by saru411 on 2007-08-25
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

install and run this and it will set up your nvidia drivers for you.

---

### Post by ewmiller13 on 2007-08-25
I have already used Envy before and sadly It doesnt exactly work like it is supposed to. I install the drivers with Envy but when I restart my laptop I get a blank screen at login or a half black half cream login screen but nothing else I do however here the ubuntu drums and I can "Blindly Login" and then restart x(ctrl+alt+backspace) then I get Nvidia splash and a login screen again. I have also played around with the 3d effects after insalling envy and the wobbly windows and cube effect both work only with wobbly windows avtive when i open my home folder Its just a blank window. If you have a detailed workaround for this problem(difficult I know) I would greatly appriciate it As of now I have pretty much exhausted my resources on this one. I have acctually posted about that problem here, tried the IRC chat and google searched my brains out to end with the same result or worse(completely screwing up x and having to use the backup to fix it) so right now it is a mess. I wonder though do you know about that programming application NvTvout it said it is to set resoulution for crt monitors/tv I dnt know if it is the same for a projector If your not sure what im taliking about go to add remove applications and search NvTvout it doesnt have very detailed info about it but it has somewhat of a description. Thanks for the quick replies I have confidence you will find an answer soon.

---

### Post by ewmiller13 on 2007-08-25
Oh and if you still dont have a good Idea of what lyricue is it is much like media shout if you even know what that is (not many people do nor use it) What happens is its kind of like a dual monitor thing but what it does is you control what is on the projector with kind of like a control panel or console while only the slide is seen on the screen. the beauty of it is you can edit slides during the presentation without turning the projector off or killing the slide show.( much more advanced than powerpoint) Like I said earlier not many people understand why I would even want to use a program like this but, really and truly you wont really understand until you are in the situation i am in. this software is primarily used for church services that is why it isnt the most popular app to every body else

---

### Post by saru411 on 2007-08-25
it sounds as if you are new to ubuntu/linux. it also sounds as if you have muddled up the xorg.conf file. i would reccomend a fresh install if at all possible. after the install update your system, then reboot, then install envy, then reboot. after this you should install your other apps as needed. i hope this is possible. if not you will have to do alot of configuring and file edits that wouldnt be needed on a fresh install. this has been my experience anyway. good luck

---

### Post by ewmiller13 on 2007-08-25
Yes I am new to ubuntu but when I said I exhausted my resources that is what I ment. I have already installed envy on a fresh install and it doesnt work!!!

---

### Post by saru411 on 2007-08-26
my question to you is....did you install ubuntu. reboot. install updates. reboot. install envy. restart x? if not thats your problem

---

### Post by ewmiller13 on 2007-08-26
If I get the nvidia drivers working can you tell me how to set up for a projector?

---

### Post by saru411 on 2007-08-26
i already did

> sudo nvidia-settings

x screen display configuration> configuration>configure>seprate x screen

this will allow you to pick the correct resolution and set the screen. you will have to then save your xconfig file and then restart x. cntrl+alt+backspace

---

