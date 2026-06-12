---
title: "Looking for Advice on Desktop Environments"
date: 2007-01-07
forum: Desktop Environments
---

### Post by matt_risi on 2007-01-07
Hey folks,

I was recently given a semi-old HP desktop that's become my main computer, dual booting XP and Xubuntu. The thing is great, really versatile and fun. Specs are in my signature. It replaced my previous desktop which is an eMachine with the following specs:

566mHz Celeron
160 mb RAM
6.9 gb HD

I did a clean command-line install of Ubuntu 6.10 on it. Now's where you guys come in. What desktop environment would best suit this computer? K.Mandla, your guidance especially would be appreciated, but I wanna hear from anyone who's a lightweight machine enthusiast. :) 

Thanks!

---

### Post by 23meg on 2007-01-07
> What desktop environment would best suit this computer?Performance-wise, XFCE would be logical.

---

### Post by meng on 2007-01-07
Xfce. Good luck.

---

### Post by matt_risi on 2007-01-07
Been there, too sluggish. Remember that this is a kinda project computer, so it can be a frankenstein window manager for all I care.

---

### Post by 23meg on 2007-01-07
Try Fluxbox, Openbox, IceWM or even ratpoison if you like your keyboard more than your mouse.

---

### Post by maxamillion on 2007-01-07
I really don't think it is a matter of "what desktop environment best suits this computer" but one of "what desktop environment best suits you?" ....

I run Xubuntu on an Athlon64 X2 4600+ w/ 2gb of ram just because I personally prefer xfce to gnome or kde.

If you want lightweight (more so than xfce), you might want to look into fluxbox, icewm, enlightenment, windowmaker, fvwm, or go here and pick one ... [http://xwinman.org/](http://xwinman.org/)

---

### Post by ynnhoj on 2007-01-07
i'm a big fan of openbox, so i guess that's what i'd suggest, as far as the light-weight window managers go (though i do think that xfce is awesome too).  at first, you might be a little underwhelmed with openbox.. because the first time you load it up, there's really nothing there (but right click and you've got yer menu--don't assume it's broken :P).  but once you learn you're way around, it's quite simple to customize.

if you're interested, here are a couple links to help you figure it all out:
openbox how-to: [http://www.ubuntuforums.org/showthread.php?t=192106](http://www.ubuntuforums.org/showthread.php?t=192106)
openbox how-to on the gentoo wiki: [http://gentoo-wiki.com/HOWTO_Openbox](http://gentoo-wiki.com/HOWTO_Openbox)

---

### Post by kerry_s on 2007-01-07
How about a little more info, like what is it's purpose going to be. Is it going to just be a web machine. Will you be using it for small office?

If you leave it up to us we'll just tell you to do this->

server/comand-line install

login

sudo su

nano /etc/apt/sources.list  <-comment out cdrom, uncomment all repos, ctrl + x + y & enter to save

apt-get update

apt-get install x-window-system-core gdm fluxbox emelfm leafpad dillo

type-> reboot

select fluxbox in session & log in

Done

Fluxbox = Window manager
emelfm = file manager
leafpad = editor
dillo = web browser

---

### Post by matt_risi on 2007-01-07
> **kerry_s said:**
> How about a little more info, like what is it's purpose going to be. 

Fair enough. I basically would like this computer to be able to run abiword and gnumeric for office apps, and in terms of net usage firefox is a must, although I've heard good things about SeaMonkey. However aside from those basic needs, I really want this computer to be a learning experience, as I'm relatively new (since August '06). 

**Overall snappiness in operation is the biggest aim here, but a desktop environment must be in place.**

Thanks for the replies!

---

### Post by kerry_s on 2007-01-07
> **matt_risi said:**
> Fair enough. I basically would like this computer to be able to run abiword and gnumeric for office apps, and in terms of net usage firefox is a must, although I've heard good things about SeaMonkey. However aside from those basic needs, I really want this computer to be a learning experience, as I'm relatively new (since August '06). 

**Overall snappiness in operation is the biggest aim here, but a desktop environment must be in place.**

Thanks for the replies!

So small office. Abiword should be quick no matter what you run. Firefox is the main problem It always is slow on first start there's nothing i found can be done about that.

So it would be this then->

apt-get install x-window-system-core gdm fluxbox emelfm leafpad dillo firefox abiword gnumeric 

I left dillo because it's a great alternative for just simple web browsing. Also if emelfm is not your cup of tea try pcmanfm( [http://pcmanfm.sourceforge.net/intro.html](http://pcmanfm.sourceforge.net/intro.html) ) just add the repo to the sources.list ( deb [http://cle.linux.org.tw/candyz/Ubuntu/edgy](http://cle.linux.org.tw/candyz/Ubuntu/edgy) i386/ ) & sudo apt-get install pcmanfm

---

### Post by matt_risi on 2007-01-07
Alright I'll give 'er a whirl. Thanks. :)

---

### Post by russellc on 2007-01-07
enlightenment dr17, aka e17, is fun to try. back when i tried it, there were new features (was compiling from cvs) left and right. a bit of compiling to do, but it was worth it. i'm not sure if its easier to install now or whatever. come to think about it, i'm somewhat tempted to try it out again tonight. it would also be interesting to see how that desktop environment runs on a computer like that.

---

### Post by matt_risi on 2007-01-07
Just tried fluxbox, xorg wouldn't start, with error 11. Any ideas?

---

### Post by maddog39 on 2007-01-07
Definetly XFCE for that. I use XFCE all the time, even on a really fast machine, its just fantastic. Although, I wouldn't recommend installing XFCE from th developers website, because it doesnt really have a true desktop yet. So use Xubuntu which has everything all setup, stable, and nice for you. :D

---

### Post by kerry_s on 2007-01-07
> **matt_risi said:**
> Just tried fluxbox, xorg wouldn't start, with error 11. Any ideas?

Sounds like a bad install, did you do the cd check? I'm about to do the exact same install, so i'll get back to you in about an hour. :)

---

### Post by matt_risi on 2007-01-08
How'd it go? Perhaps I should do a killdisk before anything else.

---

### Post by kerry_s on 2007-01-08
It went fine, but i wiped it already. My friend needed help with fvwm-crystal setup, so i mirrored his install and we're still trying to figure stuff out. I hate fvwm-crystal it just makes things harder than it should be.

---

### Post by matt_risi on 2007-01-09
Awful pretty though, you gotta admit.

---

### Post by tcrroadie on 2007-01-09
We are talking about the Gateway machine, am I correct?  If you are looking at playing around with different environments for your Gateway machine then it really doesn't matter what desktop environment or window manager you choose because that machine has 768mb of ram.  The only thing holding it back is the cpu.  If you where to open a terminal and run the command "top" to show your system resources you will have a better understanding of what I am talking about.  With top running, launch firefox and watch your cpu usage screem and hang between 50 and 80%.  

Now if you did the same experiment on your emachie 566mHz Celeron, 160mb, 6.9gb hd, you would see your cpu usage hang around 100% until Firefox is up.  

When it comes to a limited amount of ram, then you would need to look at light window mangagers.

My suggestions for each machine.

566mhz Emachine - Fluxbox

866mhz Hp - XFCE

1.4Ghz Gateway - Gnome or anything that suites you best.

Enlightenment E17 is also a great deal of fun, fairly light and gorgeous.  You can easily install E17 following my guide found here.  

[http://ubuntuforums.org/showthread.php?t=319336]("http://ubuntuforums.org/showthread.php?t=319336")

---

### Post by matt_risi on 2007-01-10
How can I implement Thunar as the default file manager in fluxbox? As well, why is it that I have to use command line to simply change the desktop background? I'm not afraid of command line stuff, I find it really useful actually, but that's just really archaic.

I'll have a look at more guides on customization that're floating around on here.

Thanks for the replies!

---

### Post by K.Mandla on 2007-01-11
Correct me if I'm wrong, but you should be able to install Thunar with *sudo aptitude install -y thunar*, and add it to the Fluxbox menu in ~/.fluxbox/menu with a *thunar* command.

Check out PCManFM too; it's a lot like Thunar, but much lighter and can do tabbed explorer windows (kewl!). 

P.S.: +1 for Openbox; +1 for FVWM-Crystal so long as you don't want to customize it. ;)

---

### Post by matt_risi on 2007-01-11
Sounds like a good option, I'll check it out. This computer's shaping up to be pretty cool!

---

### Post by tcrroadie on 2007-01-11
> **matt_risi said:**
> How can I implement Thunar as the default file manager in fluxbox? As well, why is it that I have to use command line to simply change the desktop background? I'm not afraid of command line stuff, I find it really useful actually, but that's just really archaic.

I'll have a look at more guides on customization that're floating around on here.

Thanks for the replies!

Have a look at the links below.  Both have great documentation on Fluxbox.  

Fluxbox Documentation
[http://fluxbox.sourceforge.net/docbook/en/html/]("http://fluxbox.sourceforge.net/docbook/en/html/")

How to edit the Fluxbox menu.  Also includes how to set your backgound path in your menu so that you can change your background wallpaper from the menu.
[http://fluxbox.sourceforge.net/docbook/en/html/x750.html]("http://fluxbox.sourceforge.net/docbook/en/html/x750.html")

Fluxbox Wiki
[http://fluxbox-wiki.org/index.php/Fluxbox-wiki]("http://fluxbox-wiki.org/index.php/Fluxbox-wiki")

You may also want to take a look at the Fluxbuntu project.  I have run it in Vmware back in Octomber and it is really nice.  It may save you some time configurating Fluxbox.  It is a live cd with install option. 

[http://fluxbuntu.org]("http://fluxbuntu.org")

---

