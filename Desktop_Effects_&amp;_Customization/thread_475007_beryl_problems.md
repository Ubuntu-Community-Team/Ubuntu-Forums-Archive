---
title: "beryl problems"
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by Rufi0h on 2007-06-15
i installed beryl and now i tried to run beryl-manager
as soon as i did this a blank white screen came up and nothing else. i moved the mouse around franticly and when i got to the top right it seemed like a graphic game up in the middle, and when i moved it over to the right the screen rotated to another white screen in the cube affect. please someone help me with this problem. Thanks

BTW im a compleat noob at this. just installed Ubuntu yesterday. 

if it helps i have
Nvidia 6800
ASrock 939
amd 3200
200 gb wester digital

---

### Post by kidders on 2007-06-16
Hi there,

I don't mean to be discouraging, but Beryl is highly experimental, and really isn't something beginners should get tangled up in. Honestly speaking, I would recommend holding out for a few weeks, until you get your bearings, and then giving it a shot.

There's lots and lots of detailed help on Beryl floating around the web ... some of it more generic, and some specifically targeted at Ubuntu users ... but you need to know your way around your system before getting started, so you can contend with the inevitable crash or two, as you tweak it to play nice with your hardware.

---

### Post by ajmorris on 2007-06-17
can you please post you /etc/X11/xorg.conf file.

---

### Post by Rufi0h on 2007-06-17
so i screwed up in the install.. i got angry and decided since i had it only for a day i would just reinstall. did that and everything worked fine. im really kinda of afraid of touching anything, so im going to take kidders advice and wait till i become more familure with Ubuntu before doing anything else with beryl. 


one thing would be nice is if i could get my resolution to1440 x 900. it doesnt even give me the option.

---

### Post by kidders on 2007-06-18
> **Rufi0h said:**
> one thing would be nice is if i could get my resolution to1440 x 900. it doesnt even give me the option.That's the sort of fiddling that can take a few days to get used to. You can alter your /etc/X11/xorg.conf to make extra screen resolutions available to your computer's users. (By default it's probably configured to allow only a basic set that is likely to work with most hardware.)

> **Rufi0h said:**
> im really kinda of afraid of touching anythingThe things you need to be a little wary of doing virtually always require root access. As the superuser, Linux tends to assume you know what you're doing, and won't try to stop you doing something daft!

---

### Post by Rufi0h on 2007-06-21
the last time i messed with Xconf i lost the tops to my windows and had to reinstall everything. is there a way i can back up everything and resort to the working configuration if i screw it up

and dont be afraid to be very basic. im still really new at this.

---

### Post by franck3d on 2007-06-21
to back up your xorg.conf file:
 in a terminal window --

sudo cp /etc/X11/xorg.conf xorg.conf.bu

that will make a copy of your file and add ".bu" to the end of the file name.

it seems like every time I have seen this command in a post or tutorial, people use different extension to
identify the backup.   .bu   .backup   ~
It took me a while to understand that there was no difference between them all, it just a name.

welcome to ubuntu and the forums, they are both great!

P.S. if you mess up your xorg.conf to the point where you can't get X started, get to a command prompt and:

sudo cp /etc/X11/xorg.conf.bu xorg.conf

and you'll be back where you started.

---

### Post by kidders on 2007-06-21
> **Rufi0h said:**
> the last time i messed with Xconf i lost the tops to my windows and had to reinstall everythingI know this is no good to you now, but it sounds like you may just have been having window manager problems ... usually a 30-second fix.


... just in case something similar happens again.

---

### Post by franck3d on 2007-06-21
losing the tops of the windows seems to be a pretty common issue with beryl, but easy to fix.
I can usually get straightened out by using the beryl manager to switch the window manager to metacity(gnome default) and back to beryl.

---

