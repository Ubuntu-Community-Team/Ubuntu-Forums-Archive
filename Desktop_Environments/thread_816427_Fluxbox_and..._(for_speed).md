---
title: "Fluxbox and... (for speed)"
date: 2008-06-02
forum: Desktop Environments
---

### Post by AnLGP on 2008-06-02
I'm using fluxbox as my WM.  I found this site:

[http://users.skynet.be/six/gpure/tech/linux/apps.html](http://users.skynet.be/six/gpure/tech/linux/apps.html)

which has tons of lightweight applications.  I just downloaded cmus/ted/naim between yesterday and today.  they're taking some getting used to because I'm used to open office/pidgin/amarok (or xmms) and not quite used to working in the terminal.  but I like the fact that i can have all these things open and my computer still runs really well :).  oh I also have conky up.

what I want to know is what do you guys recommend?  can you give reviews?  that guy doesn't really.  or maybe point me in a direction?  i've looked at the DSL applications and such as well.

maybe a browser?  I'm in firefox right now.  i've got dillo/kazehakase/epiphany/konquror (however you spell it) installed as well.  which one of those would you recommend as an alternative?  i want it to be able to be somewhat modern but lightweight.  and for some reason kazehakase doesn't goes as quick as firefox for me ? *scratches head*

Thanks.

Just looking for more stuff :)

---

### Post by kerry_s on 2008-06-02
you sound like you got it all under control, the best way is to try different things. when i'm bored i'll usually browse through the repo in synaptic, see if i spot anything that sounds interesting.

anyways here my list:

jwm, i love this window manger better than all others.
clex, file manager
vim
vlc
mtpaint
epdfview
gpicview
abiword
openoffice writer and impress
grun
scrot
iceweasel
conky
rxvt

i think that's it?
i'm also running my screen at a virtual size of 1280x768, its a 1024x768 laptop lcd screen, just found out the vid card(neomagic) can do a virtual size of 1280x1024, but prefer to only scroll side to side, so 1280x768 is good enough for me.

---

### Post by Inxsible on 2008-06-02
Love all of the apps kerry mentioned except that I havent tried jwm and clex. I should though.

And I don't like AbiWord - only because it screws up the formatting of my documents that I had created in Windows. Its probably just me...but still

I just did a minimal install and added the Enlightenment DR17 from cvs. I was gonna add Thunar as the file manager - because its nice and light - but it depends on a couple other xfce packages. Good time to try clex :)

Thanks kerry.

and I am in the same boat as the op for my browser -- Firefox takes up like 108 MB with just 2 tabs open and of that 1 pointing to iGoogle. So I really need a different browser.

I am not sure about Iceweasel or Swiftweasel because they are built on Firefox itself. So the performance might not be better.

Also I am hooked onto 3 add-ons 1) No Script 2)Ad Block and 3)Speed Dial. any browser I use has to have those 3...so I am still looking. 

the new Opera browser is said to be light ...but I still have to try it out.

---

### Post by urukrama on 2008-06-02
> **Inxsible said:**
> and I am in the same boat as the op for my browser -- Firefox takes up like 108 MB with just 2 tabs open and of that 1 pointing to iGoogle. So I really need a different browser.

I use Opera and Epiphany. In the past Firefox was a dependency of Epiphany, but this has luckily changed in Hardy :D Epiphany has an add-block extension.

Other lightweight applications I use that haven't been mentioned yet:

Openbox (window manager)
Feh (to view images and to set the desktop background)
cplay (play music)
Leafpad (simple graphical text editor)
osmo (calendar, todo, contacts, tasks, etc.)
xpad (notes)
xcalc (calculator)
slim (login screen)
gmrun
rtorrent
htop (system monitor)

---

### Post by kerry_s on 2008-06-02
yeah, for firefox/iceweasl you can google for the tips to lower the resources, it just takes a couple of settings in about: config and it will behave itself.

clex is really, command line oriented, it's like a step up from straight command line. the short cut keys are just like mc and you can do a couple of your own if you want. just press esc & c to get to the settings. also works great if you lose gui.

yes, abiword is kind of screwy sometimes, that's why i have openoffice as a backup, but abiword is fast and can do at least 90% of the doc's i open. i need ppt so might as well have writer to.

---

### Post by AnLGP on 2008-06-02
Thanks for the suggestions. 

Why do you like jwm over fluxbox?  I may make the switch.  Although I'm getting used to my fluxbox configuration and desktop:

[IMG]http://i297.photobucket.com/albums/mm213/musicauniversalis/fluxdesk-1.jpg[/IMG]

---

### Post by RedSquirrel on 2008-06-02
More:

mplayer
abcde
xpdf
imagemagick

... and for a panel: fbpanel

window managers: I've been jumping around a fair bit lately. openbox, fluxbox, ratpoison, enlightenment 0.16.8.13,...

Edit: There are several threads on these forums listing lightweight applications. You might be able to find them with a quick search.

---

### Post by AnLGP on 2008-06-02
what are those other window managers like?

---

### Post by RedSquirrel on 2008-06-02
> **AnLGP said:**
> what are those other window managers like?
It's probably best for you to judge them for yourself. ;)

Just have a look at the website for each one, see what you think, and install if any one of them looks like something you want to try. They're all quite light.

---

### Post by Inxsible on 2008-06-02
I just installed Enlightenment DR17. I haven't explored much yet...but from what I have seen until now...I must say that I like it quite a bit.

It has a little more eye candy than your regular OpenBox, Fluxbox or BlackBox installs. A lot more than PekWM and IceWM :)

The only problem with it is that I had to install a DM (gdm) to be able to get into it. I cannot simply login at the command line and then issue a command to start enlightenment....or at least I don't know about it yet.

---

### Post by kerry_s on 2008-06-02
> Why do you like jwm over fluxbox? 

it's just simple, i used fluxbox for years, but jwm is getting to that stage where it just rocks. jwm is still young compared to other wm's and finding how to's for it is rare, if you do find how to's there basic at best.
i've learned the in's and out's through trial & error and can make it do so much more than all other wm's.

---

### Post by kerry_s on 2008-06-02
> **Inxsible said:**
> 
The only problem with it is that I had to install a DM (gdm) to be able to get into it. I cannot simply login at the command line and then issue a command to start enlightenment....or at least I don't know about it yet.

editor ~/.bash_profile

put> startx
at the bottom

make a xinitrc->

editor ~/.xinitrc

put> enlightenment_start

(if that's not the right command, look what the enlightenment uses in /usr/share/menu)

---

### Post by Inxsible on 2008-06-02
> **kerry_s said:**
> editor ~/.bash_profile

put> startx
at the bottom

make a xinitrc->

editor ~/.xinitrc

put> enlightenment_start

(if that's not the right command, look what the enlightenment uses in /usr/share/menu)
all I had to do was issue this command```
startx /opt/e17/bin/enlightenment_start
``` Thanks to kellemes for suggesting that. But I guess I can also try out your suggestion.

hold on...will be back with results....

EDIT:  Nice...now I dont have to explicitly issue the command. Thanks kerry.

---

### Post by kerry_s on 2008-06-03
> **Inxsible said:**
> all I had to do was issue this command```
startx /opt/e17/bin/enlightenment_start
``` Thanks to kellemes for suggesting that. But I guess I can also try out your suggestion.

hold on...will be back with results....

EDIT:  Nice...now I dont have to explicitly issue the command. Thanks kerry.

yeah, to bad your not using using debian though, in debian you can set up auto log in with rungetty, when you power on or reboot it goes straight to the desktop, no need to log in manually.
in ubuntu that upstart gives to many problems for auto log in.

---

### Post by Inxsible on 2008-06-03
> **kerry_s said:**
> yeah, to bad your not using using debian though, in debian you can set up auto log in with rungetty, when you power on or reboot it goes straight to the desktop, no need to log in manually.
in ubuntu that upstart gives to many problems for auto log in.True...but even if I had debian - I think i would still keep the login. I don't know..its just the way I am :)

 I am not much into DM themes - be those GDM or KDM.

I think once I login -- its my desktop that should be functional...and a little eye candy here and there would be nice - but it should not hinder my work.

BTW -- I did download the debian xfce CD 1  - but I still have to install it. I would have loved it if it were a Live CD and I would have got a feel for it before installing. Do you know if Debian has a minimal installation like Ubuntu?

I know they have a netinst - but is that the same as minimal? What I mean is that I almost always hate the default apps that a distro provides (Soundjuicer, Serpent - yuck!). So I am looking for just a base install and then I can choose what I want to install. That way I have a very streamlined machine built to my specification.

And finally, given that they will both be minimal installs - what would be the performance gain on using one over the other?

---

### Post by Anzan on 2008-06-03
Yes, the Debian netinst is the minimal install.

I don't know about the differences in performance between Debian Xfce and Xubuntu.

---

### Post by bingoUV on 2008-06-03
Terminal emulator : mrxvt.

No toolkit dependencies, just depends on xorg. Full featured, multi-tabbed. You can find it in repositories. Good configuration scripts can be had on the internet, and then you can build on them to customize them according to your preferences.

---

### Post by kerry_s on 2008-06-03
> BTW -- I did download the debian xfce CD 1 - but I still have to install it. I would have loved it if it were a Live CD and I would have got a feel for it before installing. Do you know if Debian has a minimal installation like Ubuntu?

I know they have a netinst - but is that the same as minimal? What I mean is that I almost always hate the default apps that a distro provides (Soundjuicer, Serpent - yuck!). So I am looking for just a base install and then I can choose what I want to install. That way I have a very streamlined machine built to my specification.

live cd:
[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

yes, with the net installer, when it gets to the package selection part you just uncheck everything, then it will skip to install grub and you will have a base.

then you just log in as root
apt-get install xorg (wm) (etc)
type> exit <to leave root
log in as user
startx

i always use the net installer to build mine.
lenny net installer:
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

etch net installer:
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

---

### Post by Inxsible on 2008-06-03
Thanks for the live CD link... The screenshots look a lot like Ubuntu..so I guess not much will be different except for maybe the apps that are installed by default.


In any case, I plan to go the netinst way -- because I have more control of what I want to install. 

Can you tell me what and how the performance gain will be as opposed to using  Ubuntu minimal and Debian netinst - if any?

Also...sorry to the op AnLGP...for hijacking his thread :)

---

### Post by Pogeymanz on 2008-06-03
Debian netinst will be faster. There's almost no doubt in my mind.

---

### Post by Inxsible on 2008-06-03
> **EmosSuck777 said:**
> Debian netinst will be faster. There's almost no doubt in my mind.
Ok. Do you have anything to substantiate that with ??

---

### Post by kerry_s on 2008-06-03
> **Inxsible said:**
> Thanks for the live CD link... The screenshots look a lot like Ubuntu..so I guess not much will be different except for maybe the apps that are installed by default.


In any case, I plan to go the netinst way -- because I have more control of what I want to install. 

Can you tell me what and how the performance gain will be as opposed to using  Ubuntu minimal and Debian netinst - if any?

Also...sorry to the op AnLGP...for hijacking his thread :)


debian is smaller, faster, more stable. ubuntu ties alot of stuff together even in the base, with debian if you want you can further strip the base down.
i've taken out a lot of things in debian that just would break a ubuntu install or just make it cry and wine. :) if i wanted to i could easily have all the programs i have now and be around 500mb, maybe less, i'm at almost a gig now.

it's a win win all the way around.

---

