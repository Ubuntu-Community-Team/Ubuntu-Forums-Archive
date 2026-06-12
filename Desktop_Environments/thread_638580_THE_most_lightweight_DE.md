---
title: "THE most lightweight DE"
date: 2007-12-12
forum: Desktop Environments
---

### Post by Warpnow on 2007-12-12
Does anyone know how the "lightweight" DEs like Enlightenment, Fluxbox, IceWM, ect, stack up?

Can someone gimme a list of some REALLY lightweight DEs that are in the repos?

I have got fluxbuntu installed and its running pretty decently but if I can find something even lighter I will use it.

---

### Post by de_valentin on 2007-12-12
I've used enlightenment for a while on my opld laptop and it was very fast but I didn't like it very much so I returned to Xubuntu which was a bit slower but very acceptable

I've seen Elive that uses enlightenment and it looks very nice, same goes for dreamlinux. 

Dreamlinux didn't recognize my usb-ports so I stopped using it, even though it really made my old laptop feel fast.

---

### Post by SupaSonic on 2007-12-12
OpenBox... Although I don't think it is much different from FluxBox in terms of performance.

---

### Post by Onyros on 2007-12-12
From my testing...

**XFCE** is heavier than **Enlightenment** (E17) which is heavier than **IceWM** which is a little heavier than **Openbox** which is a little heavier than **Fluxbox** (if you want to use a panel - Openbox doesn't have one by default, so you have to use other solutions - , otherwise they're pretty much the same).

Than you have a bunch of other, even more minimalistic which may yield even better results, but are not usable for me (personal opinion) as a user.

I boot to Fluxbox on Arch Linux to 24MB of RAM, if that means anything.

---

### Post by Warpnow on 2007-12-12
I am having problems with fluxbuntu freezing up if I run more than just 2 apps at once. I have my mud client (necessity) and web browser, but if I try to boot even a command line it freezes up.

Its an old machine, but I was hoping I could find something lighter than fluxbuntu...

Its a p2 250mhz with 128mb of ram.

---

### Post by forrestcupp on 2007-12-12
> **Warpnow said:**
> I am having problems with fluxbuntu freezing up if I run more than just 2 apps at once. I have my mud client (necessity) and web browser, but if I try to boot even a command line it freezes up.

Its an old machine, but I was hoping I could find something lighter than fluxbuntu...

Its a p2 250mhz with 128mb of ram.

The CLI?

---

### Post by Thanoulis on 2007-12-12
Maybe it is not the Fluxbox, but your web browser that takes up too many system resources...
What web browser do you have?

---

### Post by Warpnow on 2007-12-12
Kazehakase or however it is spelled, comes with fluxbuntu.

---

### Post by Onyros on 2007-12-12
You can't really expect miracles with 128MB of RAM ;)

Your problems have nothing to do with Fluxbox.

128MB is *enough* if some tweaking is done, but I suggest you try something other than the *buntus for that hardware of yours.

Something like Puppy Linux or Damn Small Linux. Maybe even Deli Linux.

Kazehakase uses Gecko as a rendering engine, so even though it is lighter than Firefox or Epiphany, if you open enough tabs you will surely be able to max out your RAM usage, let alone using with a mud client at the same time...

Either that, or try using a different browser in Fluxbuntu, something like Dillo or HV3.

---

### Post by Iceni on 2007-12-12
Why not drop the window manager and just run the CLI? Works well.

---

### Post by bonzodog on 2007-12-12
I would say Openbox is lighter than Fluxbox, as it contains very little code. It has no way of rendering backgrounds or panels by default.
You need extra apps to do that.

However, lets go Ultra light -- Gentlemen, I refer you to a Window manager with just 2000 lines of code. It's called [dwm]("http://www.suckless.org/wiki/dwm"). 
Menus? no, don't need them. 
Background? no, them neither. 
Window title bars? no, too much code. 
Theming - nope, no point, nothing to theme.

It's a tiling WM, and has a few cousins, like wmii, ratpoison, 9wm, and larswm.

Also go look here for a list (not entirely up to date...): [http://xwinman.org/others](http://xwinman.org/others)

---

### Post by Warpnow on 2007-12-12
I am going to try DWM, thanks.

Now, as to the suggestion to move to DSL or puppy. I may try puppy. I've used DSL alot. Ran it when I didn't have a hard drive for a couple months...not an experience I want to repeat. That OS is so weird it annoys the **** out of me. Things just don't seem to work right or at all.

When I downloaded fluxbuntu I also downloaded Zenwalk and Absolute...are either of them lighter than Fluxbuntu?

---

### Post by fuscia on 2007-12-12
9wm, flwm and jwm are the lightest i've ever used. in each case, you can use feh to set the background. 

> It's a tiling WM, and has a few cousins, like wmii, ratpoison, 9wm, and larswm.

i don't see how 9wm is related to the others.

---

### Post by John.Michael.Kane on 2007-12-12
> **bonzodog said:**
> I would say Openbox is lighter than Fluxbox, as it contains very little code. It has no way of rendering backgrounds or panels by default.
You need extra apps to do that.

However, lets go Ultra light -- Gentlemen, I refer you to a Window manager with just 2000 lines of code. It's called [dwm]("http://www.suckless.org/wiki/dwm"). 
Menus? no, don't need them. 
Background? no, them neither. 
Window title bars? no, too much code. 
Theming - nope, no point, nothing to theme.

It's a tiling WM, and has a few cousins, like wmii, ratpoison, 9wm, and larswm.

Also go look here for a list (not entirely up to date...): [http://xwinman.org/others](http://xwinman.org/others)


Can't forget about. [awesome]("http://awesome.naquadah.org/")

---

### Post by Warpnow on 2007-12-12
> **John.Michael.Kane said:**
> Can't forget about. [awesome]("http://awesome.naquadah.org/")

That is so fricking awesome looking...

Is there a distro that has it by default?

I have installed alot of DEs on my main laptop which is very new and up-to-date, but that's because the session manager at the ubuntu login screen makes it very easy to switch between them. I still dont  know how to change the DE on most lightwight distros.Still relatively new to linux.

---

### Post by Dragonbite on 2007-12-12
> **Warpnow said:**
> I am having problems with fluxbuntu freezing up if I run more than just 2 apps at once. I have my mud client (necessity) and web browser, but if I try to boot even a command line it freezes up.

Its an old machine, but I was hoping I could find something lighter than fluxbuntu...

Its a p2 250mhz with 128mb of ram.

I have Fluxbuntu  running on my PI w/MMX @233Mhz and 128MB Ram and even with Conky or the gkrellim(?) running it is responsive and works. I'm just not too fond of Rox but it works.

What is a "mud client"?

Kazehakase (I just copy-pasted that from Fluxbuntu's site ;) ) sucks. It takes forever for it to not only come up, but to render each web page.

I have installed Firefox but usually don't use it (I keep it for website compatibility) and I primarily use Opera which is adequate for browsing.  Don't open more than a couple tabs and you're good.

Dillo is an option, but it doesn't like CSS or something so I'm not even giving it the time of day.

I do not like Claws for email.  It is like refreshing / redownloading every time I open a single email or something.  Since my email is Google, I'm just using Opera and it is running just fine for me.

Also, look to see if there is anyting in the #dmesg (something that the system keeps polling for that isn't there or working?) and what services you have running.

So far, Da*n Small Linux (DSL) is the fastest I have seen, even runs pretty good via live-cd on my the same laptop I have fluxbuntu installed.

Fluxbuntu, if you choose to go this route, includes a nice feature to allow you to install a minimal system (no window manager or anything). I think you boot the CD and start the installation with "Server" as a boot option (don't quote me).

---

### Post by Warpnow on 2007-12-12
Wow. I use opera on my powerful machine. I just assumed it used higher resources than Kazahakase (sp?)..is that not true?

I tried installing it...its not in the repos on fluxbuntu but is on my normal ubuntu, is there a reason for that?

---

### Post by Dragonbite on 2007-12-12
> **Warpnow said:**
> Wow. I use opera on my powerful machine. I just assumed it used higher resources than Kazahakase (sp?)..is that not true?

I tried installing it...its not in the repos on fluxbuntu but is on my normal ubuntu, is there a reason for that?
I don't know. I downloaded it from the Opera site (wanted to get the latest version) and installed it using ```
sudo dpkg -i *[COLOR="DimGray"]opera_package_file[/COLOR]*
```

Both Opera and Firefox are slow to open, but once it's open it works fine.

In Opera I did try using the GMail's new IMAP feature (over dial-up)... I'm not bothering with that again (it was very slow and typing a message it seemed it was sending every keystroke back, just wasn't worth it).

I have a blog entry about setting up Fluxbuntu [[COLOR="Blue"]here[/COLOR]]("http://my.opera.com/dragonbite/blog/2007/11/27/fluxbuntu-on-my-low-end-laptop").

---

### Post by phibxr on 2007-12-12
Ion3 has been my favorite for ages, and it's in the repos. It will take some time to get used to it, but you'll never look back again. :)

---

### Post by LaRoza on 2007-12-12
The lightest? RatPoison I think.

[http://linux.softpedia.com/get/Desktop-Environment/Window-Managers/Ratpoison-3960.shtml](http://linux.softpedia.com/get/Desktop-Environment/Window-Managers/Ratpoison-3960.shtml)

It is in Synaptic, don't install from that site.

---

### Post by jviscosi on 2007-12-12
I haven't done any benchmarking but in my experience, running exactly the same apps, OpenBox seems faster and more responsive than Fluxbox.  (I'm back to using OpenBox again.)

---

### Post by bobbocanfly on 2007-12-12
> **fuscia said:**
> 9wm, flwm and jwm are the lightest i've ever used. in each case, you can use feh to set the background. 



i don't see how 9wm is related to the others.

9wm FTW. Fuscia = legend for poiting us towards that. Run it on my server in order to run uTorrent (I know i should be using rTorrent but i cant be bothered adding 100 odd torrents back in to seed) and has virtually no system overhead. Love it.

Dont think i could stand it for a standard DE. I think the lightest i could go would be Open/Fluxbox but at the moment im fat and use GNOME

---

### Post by Onyros on 2007-12-12
> **jviscosi said:**
> I haven't done any benchmarking but in my experience, running exactly the same apps, OpenBox seems faster and more responsive than Fluxbox.  (I'm back to using OpenBox again.)If there is really a difference, I don't think it should be noticeable.

Even IF Openbox were marginally faster, I'd still prefer Fluxbox. I like the default panel, I love the tabs, I've grown fond of the menu and its editing, I find theming easy, keybinding is easy and powerful... Yep, I'm a fanboy :)

---

### Post by LaRoza on 2007-12-12
Why not BlackBox?

---

### Post by phibxr on 2007-12-12
Actually, I'm currently falling for "awesome", mentioned earlier in this topic. I found a .deb for Debian since I couldn't get it to compile, and then made an awesome.desktop (pun not intended) out of my ion3.desktop. It sure does have some functionality that ion3 is missing, but it took a good hour or two to get used to it. :)

---

### Post by jviscosi on 2007-12-12
> **Onyros said:**
> If there is really a difference, I don't think it should be noticeable.


It's actually quite noticeable on my machine.  For instance, launching Terminal (XFCE's) is almost instantaneous in OpenBox, but in Fluxbox it's a second or two before the text inside the terminal renders.

> **Onyros said:**
> 
Even IF Openbox were marginally faster, I'd still prefer Fluxbox. I like the default panel, I love the tabs, I've grown fond of the menu and its editing, I find theming easy, keybinding is easy and powerful... Yep, I'm a fanboy :)

Oh, don't get me wrong, I love Fluxbox.  There's an excellent chance I'll be using it again in a week or two.  Even though I don't use the default panel anymore and I don't really use the tabs, and on principle prefer OpenBox's use of XML in the config files, and miss the Alt-Tab switching dialog, and actually hacked some code in Screen.cc to keep KDE tray icons out of the slit (I did file a bug report about the issue), I still always seem to end up in Fluxbox again.  I can't explain it!

Anyway I think I'm getting the thread off topic so I'll stop now ...

---

### Post by D-EJ915 on 2007-12-12
> **bobbocanfly said:**
> 9wm FTW. Fuscia = legend for poiting us towards that. Run it on my server in order to run uTorrent (I know i should be using rTorrent but i cant be bothered adding 100 odd torrents back in to seed) and has virtually no system overhead. Love it.

Dont think i could stand it for a standard DE. I think the lightest i could go would be Open/Fluxbox but at the moment im fat and use GNOME
if you're just running 1 window you don't need a window manager, just start up X "startx &" and run the program from the command line "foo -display :0"

---

### Post by Onyros on 2007-12-13
> **jviscosi said:**
> It's actually quite noticeable on my machine.  For instance, launching Terminal (XFCE's) is almost instantaneous in OpenBox, but in Fluxbox it's a second or two before the text inside the terminal renders.

Oh, don't get me wrong, I love Fluxbox.  There's an excellent chance I'll be using it again in a week or two.  Even though I don't use the default panel anymore and I don't really use the tabs, and on principle prefer OpenBox's use of XML in the config files, and miss the Alt-Tab switching dialog, and actually hacked some code in Screen.cc to keep KDE tray icons out of the slit (I did file a bug report about the issue), I still always seem to end up in Fluxbox again.  I can't explain it!

Anyway I think I'm getting the thread off topic so I'll stop now ...I understand you perfectly, don't worry! Fluxbox has that effect on us.

Last time I tried Openbox was when they launched 3.4.4 back in September (?), and I really didn't notice much difference in terms of speed compared to Fluxbox, so I was only talking from experience. In theory, Openbox's code should be faster, as it's C against Fluxbox's C++ (and even that is debatable, because some state that's only a perpetuated myth in "Codeland").

Even so, you just prompted me to give Openbox another try. Who knows? Maybe I'll be singing Openbox's praise in a few days, hehe!

Also tried Awesome due to this thread, and while I acknowledge its "awesomeness" I can't fathom using it on a daily basis. :)

---

### Post by malaprohibita on 2007-12-13
So, which of these super lightweight DEs has the most usable browser?  I realize that opinions will vary, but I'm still interested to hear about preferences.

---

### Post by regomodo on 2007-12-13
LXDE?
However, as far as i can tell the project is dead

---

### Post by sirdilznik on 2007-12-13
The most lightweight DE?  That's simple, it's Xfce.  Fluxbox, Openbox, Fvwm, Dwm, etc...  are not DEs but WMs.

---

### Post by molom on 2007-12-13
e17 is probably the best balance of being lightweight and functional and as a sidedish it has a lot of eye candy. But there aren't many good distros yet that have e17 as it's default DE/WM. Geubuntu would be the best for the moment, there will be better ones soon.

---

### Post by fuscia on 2007-12-13
> **sirdilznik said:**
> The most lightweight DE?  That's simple, it's Xfce.  Fluxbox, Openbox, Fvwm, Dwm, etc...  are not DEs but WMs.

right, and linux is just a kernel, etc. etc...

---

### Post by johnraff on 2007-12-14
> **Onyros said:**
> You can't really expect miracles with 128MB of RAM ;)

Your problems have nothing to do with Fluxbox.

128MB is *enough* if some tweaking is done, but I suggest you try something other than the *buntus for that hardware of yours.

Something like Puppy Linux or Damn Small Linux. Maybe even Deli Linux.

Kazehakase uses Gecko as a rendering engine, so even though it is lighter than Firefox or Epiphany, if you open enough tabs you will surely be able to max out your RAM usage, let alone using with a mud client at the same time...

Either that, or try using a different browser in Fluxbuntu, something like Dillo or HV3.You don't necessarily have to give up on Ubuntu with only 128MB RAM. I'm using Xubuntu (Ubuntu server install + "Xubuntu desktop" package, upgraded step by step Breezy > Feisty) and it's never crashed or frozen on me. I often have 4 or 5 apps open at once, or a dozen tabs in Firefox (though now I use Swiftweasel which is a bit faster with all the same functions, and certainly echo the plug for Dillo for browsing html docs etc - lightning fast!). 

Generally it's quite usable- the biggest problem is that after a couple of hours of use a lot of data gets swapped out to disk so it can take a *long* time to reopen a window I haven't looked at for a while.

---

### Post by Onyros on 2007-12-14
> **johnraff said:**
> You don't necessarily have to give up on Ubuntu with only 128MB RAM. I'm using Xubuntu (Ubuntu server install + "Xubuntu desktop" package, upgraded step by step Breezy > Feisty) and it's never crashed or frozen on me. I often have 4 or 5 apps open at once, or a dozen tabs in Firefox (though now I use Swiftweasel which is a bit faster with all the same functions, and certainly echo the plug for Dillo for browsing html docs etc - lightning fast!). 

Generally it's quite usable- the biggest problem is that after a couple of hours of use a lot of data gets swapped out to disk so it can take a *long* time to reopen a window I haven't looked at for a while.Don't get me wrong, you can obviously use any of the *buntus with just 128MB of RAM (if the alternate cd supports that, that is). You just need tweaking to do so a little better than without it.

And then there are a whole lotta distros better suited to low RAM usage, that's all I meant.

I use Fluxbox mainly, and for daily usage, trivial stuff I rarely get to see my memory usage above ~250MB of RAM. And then with something like Arch, my memory usage is even lower.

BTW, did anyone get Awesome (WM) to always start applications on a given tag? I know how to move apps from one tag to another, but I just can't seem to make them be launched in a specific tag.

Edit: OK, for those interested. I just bound Alt+F2 to open gmrun (in the config file, .awesomerc), and I launch my apps that way. So, let's say I always want to start Opera in tag #3. I just added the following rule to .awesomerc:

```

rule
    {
        name = "opera"
	tags = "3"
    }

```

So when I press Alt+F2, and gmrun pops up I just type "opera" and it opens up on tag #3. Then I just Mod4 + 3 to move to that tag, and there it is, to my delight :P

BTW, the keybinding to launch gmrun is

```

   key
    {
        modkey = {"Mod1"}
        key = "F2"
        command = "spawn"
	arg = "exec gmrun"
    }

```

Jeez. I'm getting addicted.

---

### Post by phibxr on 2007-12-15
> **Onyros said:**
> Don't get me wrong, you can obviously use any of the *buntus with just 128MB of RAM (if the alternate cd supports that, that is). You just need tweaking to do so a little better than without it.

And then there are a whole lotta distros better suited to low RAM usage, that's all I meant.

I use Fluxbox mainly, and for daily usage, trivial stuff I rarely get to see my memory usage above ~250MB of RAM. And then with something like Arch, my memory usage is even lower.

BTW, did anyone get Awesome (WM) to always start applications on a given tag? I know how to move apps from one tag to another, but I just can't seem to make them be launched in a specific tag.

Edit: OK, for those interested. I just bound Alt+F2 to open gmrun (in the config file, .awesomerc), and I launch my apps that way. So, let's say I always want to start Opera in tag #3. I just added the following rule to .awesomerc:

```

rule
    {
        name = "opera"
	tags = "3"
    }

```

So when I press Alt+F2, and gmrun pops up I just type "opera" and it opens up on tag #3. Then I just Mod4 + 3 to move to that tag, and there it is, to my delight :P

BTW, the keybinding to launch gmrun is

```

   key
    {
        modkey = {"Mod1"}
        key = "F2"
        command = "spawn"
	arg = "exec gmrun"
    }

```

Jeez. I'm getting addicted.

Thanks for the tip for binding gmrun to a key combination! :)

---

### Post by gejr on 2007-12-24
I can't believe noone mentions [tinywm/]("http://freshmeat.net/projects/tinywm/") :D

dwm is pure bloatware with its 2000 lines compared to this. 50 lines of pure window management. Features? Nothing but, resizing and moving windows :D

Enjoy!

---

### Post by LookTJ on 2007-12-24
DEs: GNOME, KDE, XFCE, E16/E17

WMs: OpenBox, FluxBox, Metalicy, BlackBox Compiz's WM, etc else.

In my opinion, there is no lightest DE, it's based on the WM you use.

---

### Post by init1 on 2007-12-25
lwm is one of my favorites, and it's very small too.
```

sudo apt-get install lwm

```
Another favorite is wm2. It's not as small as lwm but it's close (and it looks really cool)
```

sudo apt-get install wm2

```
These aren't really DE's, but they get the job done, for me at least :D.

9wm and flwm should be mentioned too.

---

### Post by fuscia on 2007-12-25
> **init1 said:**
> flwm should be mentioned too.

it's a shame dillo hasn't ever gotten to the conversion to fltk. it would have been fun to use it in flwm.

---

### Post by K.Mandla on 2007-12-25
Moved to Desktop Environments because the question is about ... desktop environments.

---

