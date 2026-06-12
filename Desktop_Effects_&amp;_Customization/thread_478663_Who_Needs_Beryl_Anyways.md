---
title: "Who Needs Beryl Anyways?"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by videocheez on 2007-06-19
Frustration overwhelms me at the moment trying to get Beryl running properly with my ATI X1900XTC video card.  I almost feel using some vacation time to play with this for a few 12 hour days back to back to try all of the suggested methods of configuration.  Perhaps I'll use my summer bonus next month and buy a top of the line nVidia card.  Anyone wanna buy my ATI card?:D

I hate to admit defeat and give up but being a complete linux nooob and trying to tackle Beryl + ATI has been mind boggling.

I would like to start all over again from scratch with respect to my video set-up.  I have made so many changes and since i'm noob and havent really understood what i was doing, that I would feel better just starting from scratch if i don't get this thing dialed in by the end of this coming weekend.

How can I restore ubuntu 7.04 video back the clean new out of the box version.  I know I could pop in the live CD and start all over but some things have been successful and I would hate to lose all of that.

Anyways, I feel better after that rant and if ya'll got any suggestions, I'm all ears.

Thx,

VC

---

### Post by phr0ze on 2007-06-19
To remove beryl, just load synaptic and uncheck the beryl stuff. To undo your video driver stuff, you can restore the original xorg.conf file you should have created before starting this. If you didn't back-up first there is a command to reconfigure x. I just can't think of it off the top of my head.

---

### Post by floke on 2007-06-19
No idea how to help get it working - but my wife's laptop has an ATI Radeon 200M piece of crap in it, and it runs OOTB with Beryl on Mandriva! (along with the Metisse desktop). You might want to try the liveCD of Mandriva. I'm not suggesting you install it or anything :shock: but if it works it could give you the inspiration to carry on your arduous journey!

---

### Post by floke on 2007-06-19
> **phr0ze said:**
> To remove beryl, just load synaptic and uncheck the beryl stuff. To undo your video driver stuff, you can restore the original xorg.conf file you should have created before starting this. If you didn't back-up first there is a command to reconfigure x. I just can't think of it off the top of my head.

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by nutz on 2007-06-19
For anyone looking to run Beryl on the cheap I highly recommend the FX5200 256mb. It is a little old by todays standards but you can pick it up just about anywhere for around $30 and it runs Beryl flawlessly...

The PNY version doesn't have any fans on it so it is really quiet too...

---

### Post by Nezing on 2007-06-19
No wonder I cannot get "Cube" to work with my Nvidia GeForce4 MX 4000 AGP 8x card.Guess I will have to wait till xmas to get a top of the range Radeon,or something.:(

---

### Post by hardyn on 2007-06-19
> **nutz said:**
> For anyone looking to run Beryl on the cheap I highly recommend the FX5200 256mb. It is a little old by todays standards but you can pick it up just about anywhere for around $30 and it runs Beryl flawlessly...

The PNY version doesn't have any fans on it so it is really quiet too...

I just bought a BFG 6200-128 for 45$ CDN, and it also runs compiz well; but does not run compiz and openGL games simultaneously well; they kinda drag. disabling the effects brings the speed back to the games however.

for reference, is an athlon 2.4ghz with 1gb ram, and the 6200

---

### Post by lazyart on 2007-06-19
> **Nezing said:**
> No wonder I cannot get "Cube" to work with my Nvidia GeForce4 MX 4000 AGP 8x card.Guess I will have to wait till xmas to get a top of the range Radeon,or something.:(

No, no.. get Nvidia.... much better for Linux!

---

### Post by swoll1980 on 2007-06-19
I can't get it to work either

---

### Post by overdrank on 2007-06-19
Well I guess I will throw in my 2 cents worth. I have installed beryl on several ati and nvidia cards and the easiest was the intel on this new laptop. It can be installed on ati card I haven't tried it on something newer that a x300 and I believe its the xgl part. But when it runs it is great!:popcorn:

---

### Post by nutz on 2007-06-19
> **hardyn said:**
> I just bought a BFG 6200-128 for 45$ CDN, and it also runs compiz well; but does not run compiz and openGL games simultaneously well; they kinda drag. disabling the effects brings the speed back to the games however.

for reference, is an athlon 2.4ghz with 1gb ram, and the 6200

The problem here is memory. The desktop effects do not unload from your video cards memory when you fire up a game. So the game has to make due with whatever texture memory the OS isn't using. When you disable desktop effects it makes the video card use a lot less memory for the OS so more is available to the games you play. This isn't a speed issue; it is memory...

And yes 256mb is enough for Beryl or Compiz but you will want to unload them before you fire up a game. The FX5200 is just a tad slow for todays latest games but if you don't play game then it should be more than enough. It has s-video out and dual VGA out too...

I haven't gotten it to work in TwinView yet but I don't see the card having any issues with it.

---

### Post by Nezing on 2007-06-19
UPDATE:

i had a rethink about beryl,and maybe I had not set it up correctly.So I went back to Synaptic,and 
"ticked" on all these settings:

beryl-manager,
beryl-plugins,
beryl-plugins-data,
beryl-settings,
beryl-settings-bindings,
beryl-ubuntu

:popcorn:

I am now listening to Snakes and Arrows by Rush,whilst also watching Jericho "around the corner" :)

I'm also viewing some documents,on a third corner.My top and bottom "cube" are the red diamond!!

Woohoo.And all with my crap AGP card as well.

---

### Post by orb9220 on 2007-06-19
Yep had the nvidia FX-5200 128mb and it was running beryl on dual monitors great. Could get it to open black windows tho with too many apps open then open like google earth. It will run out of video ram and start to generate black windows.

But with a 256mb version should do everything well.

---

### Post by xpod on 2007-06-19
> No wonder I cannot get "Cube" to work with my Nvidia GeForce4 MX 4000 AGP 8x card.Guess I will have to wait till xmas to get a top of the range Radeon,or something.
__________________

I use the same card although mines is a pci card but beryl works fine bar the water effects:D

---

### Post by ryanVickers on 2007-06-19
*I* need it!  Reallllyyy, reallllyyy, badlyyy!! :p

Luckily it works for me - but it didn't just a few months ago, and when I decided to give it another shot, it worked properly, and was MUCH faster than before, or compiz!

---

### Post by steveneddy on 2007-06-19
> **videocheez said:**
> Anyone wanna buy my ATI card?:D



no

---

### Post by starscalling on 2007-11-04
> **steveneddy said:**
> no

seconded :P
just gave my old fx 6200 agp to roomate... using onboard intel myself.. i think im gonna get myself an 8500 for xmass but i'm holding out a lil bit to see what other 8xxx offerings nvidia has for me .. ooo 8500+512MB+45nanometer process *drools*

---

### Post by vincentvee on 2007-11-18
> **videocheez said:**
> Frustration overwhelms me at the moment trying to get Beryl running properly with my ATI X1900XTC video card.  I almost feel using some vacation time to play with this for a few 12 hour days back to back to try all of the suggeste blah blah blah
VC


first go to system>administration>restricted drivers manager
 and enable the driver for your ati card, if you haven't already.
reboot the thing


install xgl:
[COLOR=Navy]sudo apt-get install xserver-xgl[/COLOR]

make a start XGL script:
[COLOR=Navy]gksudo gedit /usr/bin/startxgl.sh[/COLOR]

if you are using gnome, paste this into the file:
[COLOR=Navy] #!/bin/sh 
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session[/COLOR]

if you are using kde put this in the file instead:
[COLOR=Navy] #!/bin/sh 
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec startkde
[/COLOR]
save it and close it.

run this command:
[COLOR=Navy]sudo chmod +x /usr/bin/startxgl.sh[/COLOR]

then this command:
[COLOR=Navy]sudo apt-get install dbus-x11[/COLOR]

if you are using gnome then do this:
[COLOR=Navy]gksudo gedit /usr/share/xsessions/xgl.desktop[/COLOR]

if you are using KDE do this instead:
[COLOR=Navy]kdesu kate /usr/share/xsessions/xgl.desktop[/COLOR]

paste this into the file:
[COLOR=Navy][Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application[/COLOR]save the file and close it

now log out or reboot whatever you prefer, and before logging back in click the options button and click on select session, choose XGL or gnome with XGL whichever there is an option for, now log in, ubuntu will ask you if you want XGL to be your default Xserver, make it default if you want.

thats it for xgl now onto the beryl, just because i have so so much trubble with compiz

start like this:
[COLOR=Navy]wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -[/COLOR]



run this command:
[COLOR=Navy]sudo gedit /etc/apt/sources.list[/COLOR]

add this line to the file:
[COLOR=Navy]deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main[/COLOR]


also while ya there add the compiz ones too:
[COLOR=Navy]deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main 
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
[/COLOR] 

then save the file and close it.

do this:
[COLOR=Navy]gksudo gedit /etc/apt/preferences[/COLOR]

paste this in the file that opens:
[COLOR=Navy]Package: beryl-core
Pin: release o=lupine
Pin-Priority: 1000[/COLOR]

save it and close it



run this command:
[COLOR=Navy]sudo apt-get update[/COLOR]

then this one:
[COLOR=Navy]sudo apt-get install beryl beryl-manager emerald emerald-themes[/COLOR]


anyways this worked for me, so it might be worth a go
let me know how it shakes out
the only reason i even  keep this info hanging around is because i think compiz has a limited future, considering i have installed about 15 times and only got it working once, and when i installed gutsy it wasn't so gutsy....

---

