---
title: "Huge Problem, Nothing but problems"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by JZeFF on 2007-07-22
I AM NEW TO ANY LINUX OS, STARTED ABOUT A WEEK AGO.  end caps to stress my virginity in linux os's

Ok i installed ubuntu 7.04 for like the 5th time this week, problem after problem....

The first thing i did this time was install envy and get my latest drivers for my 7900gtko

Then i updated restarted, turned on desktop effects, my terminal is white, compltely white,  and i dont have any close/maximize/minimize buttons on any window...

I tried metacity in terminal but i get ....

jeff@jeff-desktop:~$ metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

After doing ctrl alt f1 then typing metacity i thought it worked, but i had no cube effect, and when i manually added more desktops they were all blank and just resulted in a frozen computer.

I dont know what to do, im about to give up on ubuntu, trust me i DONT want to give up on it yet thats why i reinstalled 5 times.

---

### Post by qamelian on 2007-07-22
Try typing ```
metacity --replace
```

---

### Post by JZeFF on 2007-07-22
i tried what u just suggested and got this   

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

ATM i have desktop effects turned on, but sometimes i get wied things that happen,   if i turn them on i have one desktop, my windows are wobbly.  But after minimizing them a few times the close/minimie/maximize things go away...

Ubuntu has led me to nothing but frustration so far.

---

### Post by Deco_21 on 2007-07-22
What kind of Graphic card do you have ??
Do you want to have a cube effect ?? , With Desktop effects you will not get that cube. You need to install beryl or Compiz Fusion.

---

### Post by rocknrolf77 on 2007-07-22
Maybe you need to add ```
Option "AddARGBGLXVisuals" "True"
``` to your xorg.conf... And the defaultdepth need to be 24. 

[SIZE="5"]See the link :[/SIZE]

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29)

---

### Post by JZeFF on 2007-07-23
My video card is a 7900gt, and before i did anything i installed envy and got the latest drivers, yes i would like to have the cube, so w/e i need to do, PLEASE give me some step by step instructions. 

Like i said first post, im totally new to linux, i know the very basics...

EDIT:  After looking at your post im installing beryl... i will post when its finished

---

### Post by JZeFF on 2007-07-23
OK, i got beryl installed, but one more question i went System->Preferences->Session

Then in startup added 

Name: Beryl-Manager
Command: emerald --replace

But it diddnt start on startup

---

### Post by rocknrolf77 on 2007-07-23
That's because the command is ```
beryl-manager
```

and not

```
Beryl-manager
```

You don't need emerald --replace, beryl-manager will take care of what window manager you use. You can choose window manager by right clicking the beryl icon in system tray :)

---

### Post by Espreon on 2007-07-23
To access the xorg.conf mentioned do this:

Fire up a terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

and add the stuff rocknrolf77 mentioned in the file and save.

Then hit CTRL-ALT-Backspace and login and see if that worked.

---

### Post by JZeFF on 2007-07-23
OK, well heres more stuff i need to figure out...

I did have beryl-manager as the code, but when i told you what i had, i accidentally capitalized the B

Still doesnt work on startup, But when i start up ubuntu i go to Applications->System Tools ->Beryl Manager

And my cube works and the wobbly windows work,     so what do i need to do to get it to start up, here is exactly what i added to startup

Name: beryl-manager
Command: emerald --replace

Do i not even need to put emerald --replace in the command?
Im confused....

---

### Post by rocknrolf77 on 2007-07-23
Name : whatever you want to call it ;)

Command : beryl-manager

No need for emerald --replace. You can choose emerald from the menu in the beryl icon :)


Edit : Have a read at [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu) and [www.ubuntuguide.org](www.ubuntuguide.org)  and you will learn things as you go along ;)

---

### Post by JZeFF on 2007-07-23
Well.    Now it starts up, but i only have 2 desktops and the cube doesn't appear, but i checked the settings in the beryl manager and the cube is activated.
Also tab+alt doesn't show me the fancy swapping things, just a little picture.  AND i no longer have wobbly windows......   this is really confusing.

Any ideas for what to do now?

All that i have done was installed wine, installed steam, got automatix, did the fat32 thing so i can access my other hard drive, and got tahoma.ttf font.

How could any of that have messed it up? and if it did what can i do to fix it?

---

### Post by rocknrolf77 on 2007-07-23
Beryl settings is confusing at first. But if you just play around with it for a while I'm sure you will find out how.

If you open nautilus/file manager and press Ctrl - H you will see the hidden files. Try deleting the file called ```
.beryl-managerrc
```  and I think the beryl settings is going to reset itself.

Or you can open your beryl settings and go to : General options > settings, profiles and Desktop integration and make a new profile :)

---

### Post by JZeFF on 2007-07-24
Somehow window manager got set to Metacity, as soon as i set it back to beryl it fixed it.

I think this problem is fixed,    but thats what i thought earlier today.

Now my next problem is trying to figure out why i get half the fps in CS:S using wine than i do in windows.
And i cant use AA
I have newest nvidia drivers using envy, and newest wine, but rly bad fps, who knows....

I guess thats a whole nother story tho, if anyone could throw me some useful thread links to that, that would be great.

Thanks for all the help here, hopefully the community will be this helpful the whole time so i can say bye bye to windows for good.

---

### Post by euxneks on 2007-07-24
> **JZeFF said:**
> Somehow window manager got set to Metacity, as soon as i set it back to beryl it fixed it.

I think this problem is fixed,    but thats what i thought earlier today.

Now my next problem is trying to figure out why i get half the fps in CS:S using wine than i do in windows.
And i cant use AA
I have newest nvidia drivers using envy, and newest wine, but rly bad fps, who knows....

I guess thats a whole nother story tho, if anyone could throw me some useful thread links to that, that would be great.

Thanks for all the help here, hopefully the community will be this helpful the whole time so i can say bye bye to windows for good.

Well, hopefully this information will be helpful:
Wine is a windows emulator and as such it is probably not going to be 100% perfect with games.  Unfortunately, Linux is not very good at working with games and usually the best solution is to use wine - which can sometimes be extremely buggy, especially with new software...
However, having said that i don't play windows games at all except Starcraft a little, and that's on wine =)

Check out this site for CS:S ( I assume that's counter strike source?)
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)
There are some howtos near the middle of that page.

Also, you might want to check out the Compiz Fusion, it's really easy to use once you get it installed and it's newer than beryl (Basically it's the newer version of beryl and it seems to work a lot better). =)
Check out the thread here to get it installed: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

Also, welcome to Linux.:)

---

### Post by JZeFF on 2007-07-24
I'm literally sick of this,  i typed sudo nvidia-settings into terminal so i could let the nvidia control panel have root privileges so i could change the settings without them reverting back to default.  AND THAT DIDN'T EVEN WORK,,,, like it was supposed to according to the forums.

However now i still have the spinning cube, no wobbly windows, and a white terminal. Also no close minimize or maximize buttons, sometimes i dont even have the top bar.
I have tried creating a new beryl profile, that doesnt fix it, i tried reloading the windows manager, i made sure beryl was set as windows manager, i keep learning stuff, but then im always forced to take 2 steps back.

I am soo sick of things going wrong,  u have no idea......

AND i went away came back, and tried to edit this and realized my keyboard wasnt working, so i had to switch over to windows to write this.
I even tried typing in a new web address and it diddnt work, i know the browser wasnt frozen because i kept changing websites with no problem at all.

---

### Post by JZeFF on 2007-07-24
Any ideas?  i dont want to start a new topic for something that relates this closely.

---

### Post by psyopper on 2007-07-24
Take a deep breath. Now take another one.

One more, slowly, in through the nose and out through the mouth.

Feel better yet?

OK, now that we have you calmed down a little lets suss this thing out.

You have installed Ubuntu several times because each time you install it you get some sort of apparent failure and you feel that the bes tthing to do is wipe it out and start over. Contrary to poular beliefe, this may be a good thing - you are learning really well through practice how to install a modern Linux distribution.

So your installation went good and now you want your video card to work at top speed so you decided to use Envy to get the latest (beta) drivers. Beta drivers may speed up your card but they don't always help your overall system stability. I would recommend installing the Nvidia drivers from the Canonical/Ubuntu repository. These are the latest nvidia certified production drivers (non-beta) precompiled and preconfigured to run properly on Ubuntu, straight from the people who brought you Ubuntu.

I'm not going to give you command line instructions because I am afriad you will panic if things aren't absolutely perfect. 

First, run Envy and tell it to remove the drivers it installed.
Next, open Synaptic Package Manager (System - Administration - Synaptic Package Manager)
Do a search (click on the magnifying glass icon) for "nvidia" without the quotes
Check the items (Mark for installation) named:
  nvidia-glx-new
  nvidia-settings
  nvidia-xconfig
Click Apply (the big green check mark) and Apply again.
When you are notified that your system update is complete, restart your computer.

After your computer restarts open a command line (ALT-F2) and type nvidia-xconfig. After that you will need to sudo gedit /etc/X11/xorg.conf and make sure you have the following lines in the "Module" section:

Load  "glx"

Go to the device section (for your video card) and make sure the following lines are there:

    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "TripleBuffer" "True"

Good luck, and remember to remain calm. In the words of a great author,[FONT="Verdana"]*** "Don't Panic"***[/FONT]

The reality is that theres a good chance that Envy bunked your system. They easy way to fix this for a new Linux user, unfortunately, is to reinstall Ubuntu. Fortunately you have lots of experience with that. On a clean installation all you need to do is open the Restricted Drivers Manager and tell it to use the drivers for your video card. While you're in that fresh installation take the advice from above - forget about Beryl and install Compiz Fusion instead.

---

### Post by JZeFF on 2007-07-24
Ok before i go to bed i will do this, it helps because when something goes wrong its just time to go to sleep =)

But!! How can i uninstall Beryl so i can Get Compiz Fusion going?  Like what would the code be for the terminal to remove beryl? or is there an easier way?

And would i be better off Reinstalling again? then just enabling the restricted drivers, and then installing compiz fusion?
Or can i just follow what you told me to do? and if that fails reinstall?

I cant stress how great this forum support has been for me, i think its all thats keeping me sane.
And i gotta be honest, i don't know if its because i have had allot of troubles, or if its because i have always kept windows running extremely stable, but so far Ubuntu has crashed at least 2x per hour since i got it...
I'm hoping thats because i have had so many problems and haven't got thing running correctly, and will eventually stop happening.

---

### Post by rocknrolf77 on 2007-07-24
If you don't appreciate all the help we give you, please read this : [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

We are just regular people trying to help you, because we believe in the spirit of the linux community.And we hope you can feel the same way one day. Then you can also become the power of the community helping others because we wan tot sincerely help others.

Just think about all the years you needed to learn windows the way you know it. It didn't come over night. Did it?

I know the the frustration. Been there. But now I know what to do. It din not come to over night.

Edit : [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu)
       : [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by JZeFF on 2007-07-24
i NEVER even hinted at not respecting the help, i said it was all that was keeping me sane...

please don't give me a bad reputation....  

Without the help i would be screwed,


Really dont understand the "scolding" i just got, but i still need some help with my above question.
Maybe i read your post wrong, maybe you read mine wrong, who knows.

---

### Post by psyopper on 2007-07-24
> **JZeFF said:**
> Ok before i go to bed i will do this, it helps because when something goes wrong its just time to go to sleep =)

But!! How can i uninstall Beryl so i can Get Compiz Fusion going?  Like what would the code be for the terminal to remove beryl? or is there an easier way?

And would i be better off Reinstalling again? then just enabling the restricted drivers, and then installing compiz fusion?
Or can i just follow what you told me to do? and if that fails reinstall?

I cant stress how great this forum support has been for me, i think its all thats keeping me sane.
And i gotta be honest, i don't know if its because i have had allot of troubles, or if its because i have always kept windows running extremely stable, but so far Ubuntu has crashed at least 2x per hour since i got it...
I'm hoping thats because i have had so many problems and haven't got thing running correctly, and will eventually stop happening.

You don't need to uninstall Beryl to run Compiz. Much like in Windows, you don't need to uninstall Internet Explorer (if you ever could...) to run Firefox or uninstall Outlook to run Thunderbird.

The reinstall is the "cleaner" option and may net better results. I think the real question is if you want to LEARN Linux or just USE Linux. If you want to learn, don't do the reinstall, work with what you have and figure out the short comings when you hit them. If you just want to use Linux (which is OK by me...) do your clean reinstall and enable the restricted drivers.

Some will tell you that you MUST learn Linux to use Linux. I don't necessarily agree with that statement. Simply using it and being satisfied with the result is all we really need because you will be a happy customer and spread the good word about your experience to your friends and relatives.

Sometimes a particular distribution doesn't meet your needs. There are 359 different distributions of Linux available. I heard on this forum once that if you run a LiveCD and have more than 3 significant things wrong or not working (no video, no network and no sound are three good examples) then you should try a different distribution.

Have you tried Kubuntu? The KDE interface is much more like Windows and may make your transition easier.

---

### Post by psyopper on 2007-07-25
> **JZeFF said:**
> i NEVER even hinted at not respecting the help, i said it was all that was keeping me sane...

please don't give me a bad reputation....  

Without the help i would be screwed,


Really dont understand the "scolding" i just got, but i still need some help with my above question.
Maybe i read your post wrong, maybe you read mine wrong, who knows.

I don't think he was scolding you. You didn't read his post wrong either. The first line he posted felt a little confusing to me too, but I think he is trying to convey a feeling of "we all have felt the very same pain you are feeling right now".

Stick with it and you will be rewarded with great things!

---

