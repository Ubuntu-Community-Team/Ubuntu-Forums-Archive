---
title: "ICEwm uses more ram then KDE?"
date: 2008-04-05
forum: Desktop Environments
---

### Post by patrickaupperle on 2008-04-05
Look at this screenshot. I am no expert, but it looks like my ubuntu is taking more ram then my debian.
For the debian did a simple gnome install then used aptitude to get kde. 
For the ubuntu install I used a mini iso then installed a cli. I then ran
```
sudo apt-get install xorg xterm wdm icewm menu dillo
```
then 
```
sudo /etc/init.d/wdm start
```

This should have resulted in lower ram consumption, right?
Oh, I just found out that it won't let me shutdown either:(:(.

---

### Post by kerry_s on 2008-04-05
debian is smaller, faster, more stable.

if your using debian you should use slim, it's much better than wdm, wdm is really old.

oops, just noticed slim is in testing/lenny. i run etch/lenny so i forget sometimes. :)

---

### Post by patrickaupperle on 2008-04-05
Ok. So a minimal ubuntu is harder on resources then fully loaded Debian?

I am getting rid of minimal ubuntu then.

---

### Post by kerry_s on 2008-04-05
you should try a minimal debian, it's much better.

i use a custom etch/lenny on 450mhz 256mb ram. startup ram is 29mb with a background, 20mb with out a background. i have to do a lot at the same time for it to use swap. i use jwm for my wm, tweaked out of course, no icons where not needed, i use rox-filer with light icon's, there basically just the frame of the icon, so there transparent. it may look scarce but i have most of the stuff of a normal desktop, there just not in my menus, but set as actions in rox.

---

### Post by patrickaupperle on 2008-04-05
Can you give me some instructions to do that. It looks wicked cool. I have an old 250 mhz(I think) pentium 2 that I want to try this on. Think it will work?

---

### Post by kerry_s on 2008-04-06
> **patrickaupperle said:**
> Can you give me some instructions to do that. It looks wicked cool. I have an old 250 mhz(I think) pentium 2 that I want to try this on. Think it will work?

how much ram?

dsl might be your best bet-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)
iso-> [ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.3RC2.iso](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.3RC2.iso)

for debian:
grab the net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

when it comes to the package selection part, just uncheck everything, that will give you a base install, ready for building up.

log in as root
apt-get install xorg jwm menu mc rox-filer leafpad dillo iceweasel
type> update-menus
type> exit
log in as your user
type> startx

i added both really light and the standard, not sure what will run on your specs.

mc = file manager/editor, really light console based, so runs in term or tty
rox-filer = gtk2 file-manager, 1 of the lightest gui file managers, very configurable once you learn your way around.
leafpad = editor, use as the rox text editor, set as run action for text
dillo = light web browser, very fast, not full of features though
iceweasel = standard firefox web browser.

i think dsl is your best bet, my install is almost exactly like there's, but there's is special built to be as light as possible.

if you go the debian route and it works, i can talk you through setting up auto log in and startx, so you don't have to do it manually.

good luck!

---

### Post by patrickaupperle on 2008-04-06
Sweet thanks. Is JWM lighter than flux or openbox?  If so, then I am going to use it. If not I might do all this in virtual box with each wm and see which I like best.

What do you think of PCMan? Its a file manager that looks pretty nice. Unfortunately, I don't think it is in the repos. Would it be too difficult for my computer to compile and install it?
[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

About the ram, I'll go check now.

---

### Post by mcduck on 2008-04-06
It's not using more RAM, you are just misinterpreting the memory usage reported by top.

Based on your screenshot, the KDE setup is using 54,4 MB of RAM.

The IceWm setup is using 33,1MB. (337444kB of total used RAM, minus 16956kB of read/write buffers minus 286596kB of disk cache = 33892kB = 33,1MB)

To get easier_to_read memory usage in a terminal, use the "free -m"-command and look at the "+/- buffers/cache"-line.

---

### Post by patrickaupperle on 2008-04-06
> **mcduck said:**
> It's not using more RAM, you are just misinterpreting the memory usage reported by top.

Based on your screenshot, the KDE setup is using 54,4 MB of RAM.

The IceWm setup is using 33,1MB. (337444kB of total used RAM, minus 16956kB of read/write buffers minus 286596kB of disk cache = 33892kB = 33,1MB)

To get easier_to_read memory usage in a terminal, use the "free -m"-command and look at the "+/- buffers/cache"-line.

Thank you for clearing that up. I already got rid of Minimal Ubuntu, though:lolflag:. Oh well. Debian is more my style anyway. So which wm do you think is best for a low mem and proc machine. Fluxbox, openbox, icewm, or JWM?

@kerry_s The computer is running Windows ME. WIndows ME says it has 64 mb of ram, though I am pretty sure I upgraded the ram at some point. Maybe it was an incompatible type?

---

### Post by chris4585 on 2008-04-06
building your own system using either ubuntu/debian minimal i'm sure you can get a system running under 64mbs of ram, i've done it before

fbpanel's and openbox work good together

---

### Post by patrickaupperle on 2008-04-06
So, you would suggest openbox?

---

### Post by chris4585 on 2008-04-06
i do because thats what i've used before but! jwm is just as good if not better, then you wouldnt even need the fbpanel's.. i'd just mess around, thats what i did, i've not really messed with jwm alot, so i cant say much

---

### Post by patrickaupperle on 2008-04-06
So you suggest openbox but think jwm is better? Should I go fbpanel or pypanel(I have seen it suggested alot) if I choose openbox?

---

### Post by kerry_s on 2008-04-06
> **patrickaupperle said:**
> Sweet thanks. Is JWM lighter than flux or openbox?  If so, then I am going to use it. If not I might do all this in virtual box with each wm and see which I like best.

What do you think of PCMan? Its a file manager that looks pretty nice. Unfortunately, I don't think it is in the repos. Would it be too difficult for my computer to compile and install it?
[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

About the ram, I'll go check now.

yes, jwm is smaller and lighter than all the *box's, most light distro's are switching to it instead of fluxbox or openbox.

pcman is in the repo's but it is way heavier than rox and you would also need to install icons. with 64mb of ram it's overload, you'll spend more time swapping than getting things done.

with 250mhz and 64mb of ram, you really should go dsl, all the work is done already, grab the new version, jwm is the default.
[ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.3RC2.iso](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.3RC2.iso)

me and robert follow almost the same path, except i could careless for dfm. i use jwm for desktop icons or swallowing programs.

i was going to suggest you swallow mc to the desktop, so your file manager will always be ready, been testing it out, it uses 30mb for the whole setup, so now i know you have 64mb it would be tight.

---

### Post by patrickaupperle on 2008-04-06
Sounds like jwm is the way to go. I am going to configure it in virtual box before I touch my old comp, though. :)

---

### Post by kerry_s on 2008-04-06
> **patrickaupperle said:**
> Sounds like jwm is the way to go. I am going to configure it in virtual box before I touch my old comp, though. :)

try dsl in virtual box to. :)

---

### Post by patrickaupperle on 2008-04-06
> **kerry_s said:**
> try dsl in virtual box to. :)

Ok. I am following your instructions from earlier - the iceweasel. I will download dsl now.

---

### Post by chris4585 on 2008-04-06
dsl is nice, i'd like to play with a comp with low specs like that, i'd put either jwm, which has been suggested or command line system, i'm using my laptop as a command line system atm, and its so far gotten most things done besides play videos, i will have to look up how to do that more extensively though...

---

### Post by patrickaupperle on 2008-04-06
> **chris4585 said:**
> dsl is nice, i'd like to play with a comp with low specs like that, i'd put either jwm, which has been suggested or command line system, i'm using my laptop as a command line system atm, and its so far gotten most things done besides play videos, i will have to look up how to do that more extensively though...

How do you browse the web from a cli system? 

Also DSL is great. I am posting from the live cd now. This is what i will be using. I am only using 36 megs of ram. I'll install now and see how much it uses.

---

### Post by kerry_s on 2008-04-06
> **patrickaupperle said:**
> How do you browse the web from a cli system? 

Also DSL is great. I am posting from the live cd now. This is what i will be using. I am only using 36 megs of ram. I'll install now and see how much it uses.

there are browsers for the cli as well, i prefer links2.

see, i told you dsl might be what your looking for. if you can master dsl, linux becomes a snap. i started out with dsl, i learned a lot from robert and the gang. i even still pop in there every now and then.

---

### Post by patrickaupperle on 2008-04-07
I might have to try a cli system sometime then :)

DSL is nice, but is there a way to add applications? it did not like apt-get or aptitude. I don't really want to install anything right now, but I want to know I can.

---

### Post by kerry_s on 2008-04-07
> **patrickaupperle said:**
> I might have to try a cli system sometime then :)

DSL is nice, but is there a way to add applications? it did not like apt-get or aptitude. I don't really want to install anything right now, but I want to know I can.

yes dsl has it's own package system should be in the second folder on your desktop. also you can enable apt, and apt-get anything from the repo, you can even install the gui front end "synaptic". you got to be careful though, some things could break if you use apt.
look through your menu's you'll find what you need.
things like office, i use google docs.
instant messaging i use meebo.com

i try and use as much on line stuff as i can, it save you from installing and can be used from any computer.

just play with it, you'll get it, i promise. :)

also i forgot to tell you, there's 3 versions of dsl, the 1 linked to is the newest, but there's the older 1 that still uses fluxbox and has jwm as a option and there's also dsl-n, always been buggy the dsl-n. but you might want to play with the others to. visit the site, sign up for the forum, robert the builder is always there and can help you with anything.
 [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by chris4585 on 2008-04-07
install links2

and from the command line type: links2

and hit g and type a address to go to, pretty simple there's also a graphical view you can use

links2 -g [www.google.com](www.google.com)

---

### Post by patrickaupperle on 2008-04-07
> **chris4585 said:**
> install links2

and from the command line type: links2

and hit g and type a address to go to, pretty simple there's also a graphical view you can use

links2 -g [www.google.com](www.google.com)

Graphical view? Can  I do this with only a cli? how? 
I'll atempt on my own, but would be glad if I could get some help.

---

### Post by patrickaupperle on 2008-04-07
From what I have seen, graphics mode is not an option with cli only. If I am wrong, I really would like to know. 
I also, in debian minimal, can't get sudo to work.

---

### Post by chris4585 on 2008-04-07
> **patrickaupperle said:**
> From what I have seen, graphics mode is not an option with cli only. If I am wrong, I really would like to know. 
I also, in debian minimal, can't get sudo to work.

actually you can get graphical view to work in cli mode, it uses framebuffer

try

*you might have to become root to do this

```

links2 -g -mode 1024x768x256

```

that works for me :)

for some reason i cant get the mouse to work even with gpm installed, there's probably some configuration file i havent messed with, but still you can find the keys to download stuff, such as if there's a download link move to it and hit d it will bring up a download dialog

i hope this helps, i'm still learning how to do things in cli mode

---

### Post by kerry_s on 2008-04-08
don't use root for a web browser, the fix is in the /usr/share/doc/links2/README.Debian for links2.
**dpkg-statoverride --update --add root root 4755 /usr/bin/links2**

ps: no gpm needed

---

### Post by chris4585 on 2008-04-08
> **kerry_s said:**
> don't use root for a web browser, the fix is in the /usr/share/doc/links2/README.Debian for links2.
**dpkg-statoverride --update --add root root 4755 /usr/bin/links2**

ps: no gpm needed

ah thanks kerry_s

---

### Post by patrickaupperle on 2008-04-08
graphics mode did not work for me. 

I also tried putting openbox in a VirtualBox and It did not work

---

### Post by syms on 2008-04-08
of course kde and gnome is better than icewm or any other lightweight wm. i really hate all these *box, icewm because the applications(synaptic for example) looks ugly in these wms, and starts about 2x slower than in gnome or kde (thats because programs was not writed in icewm (or any other lightweight wm) language, they were writed in gtk or qt).

---

### Post by chris4585 on 2008-04-08
> **syms said:**
> of course kde and gnome is better than icewm or any other lightweight wm. i really hate all these *box, icewm because the applications(synaptic for example) looks ugly in these wms, and starts about 2x slower than in gnome or kde (thats because programs was not writed in icewm (or any other lightweight wm) language, they were writed in gtk or qt).

You can change the gtk theme's that make them look 'ugly' you gtk-chtheme it works quite well.. and i dont notice any difference in program start up in a lightweight enviornment

---

### Post by kerry_s on 2008-04-08
> **syms said:**
> of course kde and gnome is better than icewm or any other lightweight wm. i really hate all these *box, icewm because the applications(synaptic for example) looks ugly in these wms, and starts about 2x slower than in gnome or kde (thats because programs was not writed in icewm (or any other lightweight wm) language, they were writed in gtk or qt).

that's because you didn't ask how to change the looks. i try and only use gtk2 apps.
as far as speed go's, not sure whats wrong with yours, but mines plenty fast on 450mhz 256mb ram. see pic, i'll just do a few.

---

### Post by chris4585 on 2008-04-08
kerry_s nice setup btw :)

---

### Post by syms on 2008-04-09
well, thats great but i dont have time at any tweak. maybe you dont notice the speed difference but in my machine firefox in icewm starts in ~12 seconds but in gnome/xfce starts in ~7 seconds. i really see the difference. and i will probably never use any of ur  lightweight wm.

---

### Post by chris4585 on 2008-04-09
Every man has their own opinions :guitar:

I like lightweight systems because they just facinate me so much

---

### Post by kerry_s on 2008-04-09
> **syms said:**
> well, thats great but i dont have time at any tweak. maybe you dont notice the speed difference but in my machine firefox in icewm starts in ~12 seconds but in gnome/xfce starts in ~7 seconds. i really see the difference. and i will probably never use any of ur  lightweight wm.

and that further tells me you know nothing, you make 1 file, with 1 line, it's all that's needed to set a theme, took me a second. if you can't take a second to pretty up your setup, than you are just lazy.

i'm sure because the bigger desktop's start alot of things, some parts that firefox needs might already be loaded, thus saving the load time, but that's just a guess. personally, i've tried just about everything and don't really notice a difference from 1 setup to the next, firefox is always slow at the first start.

i don't think light is for you and i think you have already made the right choice. linux on my friend, linux on.

---

### Post by syms on 2008-04-10
> **kerry_s said:**
> and that further tells me you know nothing, you make 1 file, with 1 line, it's all that's needed to set a theme, took me a second. if you can't take a second to pretty up your setup, than you are just lazy.

i'm sure because the bigger desktop's start alot of things, some parts that firefox needs might already be loaded, thus saving the load time, but that's just a guess. personally, i've tried just about everything and don't really notice a difference from 1 setup to the next, firefox is always slow at the first start.

i don't think light is for you and i think you have already made the right choice. linux on my friend, linux on.

Yes you are right, i don't know about how you can make gtk2 programs look good in lightweight wm, and yes i can be sometimes lazy at these things.

But at these things im really experienced, yes it starts a lot of things, but firefox is not already loaded. I tested that not one time, i tested that many times with different config, but all tests for me showed the same results. Yes, lightweight wms are not for me. I prefer the biggest ease of use and most powerful linux desktops (KDE 3.5 is best example). That's my opinion, thanks for reading :).

---

### Post by chris4585 on 2008-04-10
> **syms said:**
> Yes you are right, i don't know about how you can make gtk2 programs look good in lightweight wm, and yes i can be sometimes lazy at these things.

But at these things im really experienced, yes it starts a lot of things, but firefox is not already loaded. I tested that not one time, i tested that many times with different config, but all tests for me showed the same results. Yes, lightweight wms are not for me. I prefer the biggest ease of use and most powerful linux desktops (KDE 3.5 is best example). That's my opinion, thanks for reading :).

of course, i favor gnome myself for a heavy DE

---

### Post by supergrapeman on 2008-05-02
> **kerry_s said:**
> how much ram?

dsl might be your best bet-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)
iso-> [ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.3RC2.iso](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/release_candidate/dsl-4.3RC2.iso)

for debian:
grab the net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

when it comes to the package selection part, just uncheck everything, that will give you a base install, ready for building up.

log in as root
apt-get install xorg jwm menu mc rox-filer leafpad dillo iceweasel
type> update-menus
type> exit
log in as your user
type> startx

i added both really light and the standard, not sure what will run on your specs.

mc = file manager/editor, really light console based, so runs in term or tty
rox-filer = gtk2 file-manager, 1 of the lightest gui file managers, very configurable once you learn your way around.
leafpad = editor, use as the rox text editor, set as run action for text
dillo = light web browser, very fast, not full of features though
iceweasel = standard firefox web browser.

i think dsl is your best bet, my install is almost exactly like there's, but there's is special built to be as light as possible.

if you go the debian route and it works, i can talk you through setting up auto log in and startx, so you don't have to do it manually.

good luck!

ah, just spotted this thread, hope it's ok to hop in and ask about the auto login and startx.. what's the easiest way to sort this out in this nice little lightweight environment?

---

### Post by kerry_s on 2008-05-02
are you using debian? it doesn't work in ubuntu because of upstart.
for debian autologin:
as root:
apt-get install rungetty

xedit /etc/inittab

change
1:2345:/sbin/getty 38400 tty1
to
1:2345:respawn:rungetty tty1 --autologin user

change "user" to your log in name
(click save 2x in xedit to save)

as user:
xedit ~/.bash_profile

put> startx <at the bottom

you don't have to use xedit, use what ever editor you prefer. a default install of debian has nano and vi, xedit comes with xorg.

---

### Post by supergrapeman on 2008-05-05
> **kerry_s said:**
> are you using debian? it doesn't work in ubuntu because of upstart.
for debian autologin:
as root:
apt-get install rungetty

xedit /etc/inittab

change
1:2345:/sbin/getty 38400 tty1
to
1:2345:respawn:rungetty tty1 --autologin user

change "user" to your log in name
(click save 2x in xedit to save)

as user:
xedit ~/.bash_profile

put> startx <at the bottom

you don't have to use xedit, use what ever editor you prefer. a default install of debian has nano and vi, xedit comes with xorg.

That's great. I am using debian, and I'm trying to create a really light install which will run a web-browser (with up to date plugins), and almost nothing else.

---

