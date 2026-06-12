---
title: "Bare bone xUbuntu, another Desktop?"
date: 2008-01-04
forum: Desktop Environments
---

### Post by FFMG on 2008-01-04
Hi, 

I have xUbuntu on an old Acer 210 Travelmate.
The install worked as expected, (with a few little hiccups).

I had to create 512Mb of swap to compensate for the lack of actual memory. Yes I know that 512 is probably an overkill but at least the system is now usable.

I now need to trim everything down as much as possible to make the laptop as lightning fast as possible and I was wondering if the default xUbuntu desktop is the best choice for that.

Is there any even more 'lightweight' desktops that I could replace the default one with.

Coming from a Windows environment I am still tied having a desktop while I am learning the ropes with *nix.

So, what can I change/update/download to make the desktop even faster than it is currently.

Thanks

FFMG

---

### Post by mojoman on 2008-01-04
If you want lightweight I'd recommend you to go with a windowmanager instead of a desktop environment. Personally, I'd recommend fluxbox, it's fast and highly configurable but there are lots of others to choose from as well. You can use a pager with it, giving you workspace overview at very low memory cost. You can also use icons but if you're low on memory I'd stick with keybindings, which fluxbox do excellent. Fluxbox is in the repositories and here are some long-lived threads on fluxbox.

[URL="http://ubuntuforums.org/showthread.php?t=371144"]
http://ubuntuforums.org/showthread.php?t=371144[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=371144"]
http://ubuntuforums.org/showthread.php?t=483613[/URL]

Here is a screenshot of mine (I have a dual-monitor setup so my screen actually extends but that part is visible on a HD-projector. The screenshot is only on the monitor part of the screen though the pager covers the entire screen).

/mojoman

---

### Post by FFMG on 2008-01-04
> **mojoman said:**
> If you want lightweight I'd recommend you to go with a windowmanager instead of a desktop environment. Personally, I'd recommend fluxbox


Looks great indeed.

What package do you suggest?
[http://fluxbox.sourceforge.net/download.php](http://fluxbox.sourceforge.net/download.php), it looks like Debian is the one I should get.

Do you know where I can get some install instruction?
I had a brief look at the links you gave and on the site but they only seem to mention after installation.
As a total unix newbie I am not 100% how to even run the install.

Thanks

FFMG

---

### Post by FFMG on 2008-01-04
Actually the Debian link is broken.
So I am not sure what I should get.

[http://logicvortex.net/debian/fluxbox/](http://logicvortex.net/debian/fluxbox/)

FFMG

---

### Post by growingtedium on 2008-01-04
As far as I know, everything else is technically a window manager rather than a desktop environment.  But that's more of a technicality than anything.  The only environment I know of that is relativly polished and light is enlightenment (e17).  I don't know exactly how it stacks up next to XFCE with regards to memory usage - I would guess it's pretty similar.  

There are several other light ones in the ubuntu repos, and If you're adventureous, you could install a few of them for a test run.  They're more like Windows 3.1.

Another idea is just to strip out the components from XFCE that you don't use - printer drivers, sound drivers...

---

### Post by zipperback on 2008-01-04
> **FFMG said:**
> 
Is there any even more 'lightweight' desktops that I could replace the default one with.


You might be interested in [http://fluxbuntu.org](http://fluxbuntu.org)

- zipperback
:popcorn:

---

### Post by Tyke91 on 2008-01-04
e17 is lighter than gnome, but if you wanted something lighter than xfce, then definitely go for fluxbox or maybe e16. gotta warn you tho, fluxbox is alot trickier than xfce, gnome, or KDE, and his desktop did not come that way out of the box.

mojo, what version of ubuntu did you use, and can you direct me to a good place to learn how to setup/install conky?

EDIT: i see now that you use feisty. anyway, I'd still like to know how you did it ;)

---

### Post by mojoman on 2008-01-04
I compiled fluxbox from source but the version in the repository is good too. Conky is from the repository. I'll attach my .conkyrc but a good thread is this one (the mother of all show-off-your-conky-thread ;-) )

[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

/mojoman

EDIT: also good one

[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)[http://conky.sourceforge.net/docs.html]("http://conky.sourceforge.net/docs.html")

---

### Post by mojoman on 2008-01-04
> **Tyke91 said:**
> EDIT: i see now that you use feisty. anyway, I'd still like to know how you did it ;)

Actually, I'm using Debian Lenny but I've used that setup for feisty as well so ot should be good (I tri-boot for the moment and sometimes I forget what I'm logged into...)

I've actually done very little twisting with my fluxbox. With fluxbox, a little goes a long way. :)

---

### Post by mojoman on 2008-01-04
> **FFMG said:**
> Looks great indeed.

What package do you suggest?
[http://fluxbox.sourceforge.net/download.php](http://fluxbox.sourceforge.net/download.php), it looks like Debian is the one I should get.

Do you know where I can get some install instruction?
I had a brief look at the links you gave and on the site but they only seem to mention after installation.
As a total unix newbie I am not 100% how to even run the install.

Thanks

FFMG

Some good links:

[http://fluxbox.sourceforge.net/]("http://fluxbox.sourceforge.net/")

[http://fluxbox-wiki.org/index.php/Fluxbox-wiki]("http://fluxbox-wiki.org/index.php/Fluxbox-wiki")

pull it from the repo's

```
sudo apt-get install fluxbox fbpager menu fluxconf feh
```
(that installs fluxbox,the pager, debian menu, a configuration tool and feh, a program handy to fix your desktop background)

I've done some editing, configuration and tweaking but really no rocket science. Find a theme you like, modify it if you need. I use twice (a standard theme but I modified it to use smaller fonts and don't have a clock in my toolbar), fbpager (that I modified to blend nicely with the theme), a picture from the web as a background and conky to keep my informed about what is going on (that's the pimp-looking stuff on the right side of the screen :wink: ). The menu is manually edited and I got key-bindings to enable hotkeys. All in all, a couple of hours work which is well worth the effort. I'd be happy to share any configuration files you might be interested in.

/mojoman

---

### Post by FFMG on 2008-01-04
> **mojoman said:**
> If you want lightweight I'd recommend you to go with a windowmanager instead of a desktop environment. Personally, I'd recommend fluxbox,

Thanks for that, 

Fluxbox seems to be a winner, a bit of a learning curve, but not that hard in the end.
My old machine is now running as it should.

I just need to learn how to add items to the desktop like you did, as I said, Fluxbox is not the most user friendly when it comes to newbies.

I am also missing a few menu items, (such as my system menu for example).
Do you know how I can get those back?

FFMG

---

### Post by mojoman on 2008-01-04
> **FFMG said:**
> Thanks for that, 

Fluxbox seems to be a winner, a bit of a learning curve, but not that hard in the end.
My old machine is now running as it should.

I just need to learn how to add items to the desktop like you did, as I said, Fluxbox is not the most user friendly when it comes to newbies.

I am also missing a few menu items, (such as my system menu for example).
Do you know how I can get those back?

FFMG

For your menu, this is the _[thread]("http://ubuntuforums.org/showthread.php?t=371144")_ you want to have a look at. Anything you might need, you'll find there. 

Adding items to the desktop, do you mean icons? I think _[idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page")_ is a good option but I don't use icons myself, I find that it clutters the desktop to much for my taste. If you want quick and light, I suggest you use keybindings instead. I got my multmedia keys configured as well as various alternatives using the CTRL/ALT1/ALT4 + function-keys to open stuff, move windows around or to other workspaces or whatever I like. I recommend it, It saves time and your wrist.

Like you said, fluxbox is a winner and it got a very steep learning curve but it's also a very short one, and once you're on top, it's a great view.

/mojoman

---

### Post by FFMG on 2008-01-04
> **mojoman said:**
> For your menu, this is the _[thread]("http://ubuntuforums.org/showthread.php?t=371144")_ you want to have a look at. Anything you might need, you'll find there. 


LOL, I did not see the attached file so I could not download the menu, I will have another look at it.

> **mojoman said:**
> 
Adding items to the desktop, do you mean icons? I think _[idesk]("http://idesk.sourceforge.net/wiki/index.php/Main_Page")_ is a good option but I don't use icons myself, I find that it clutters the desktop to much for my taste.

Icons are nice, (and I might use them), but I was more talking about the other extras you have on your screen.
Such as clock, cpu usage,  and so on, as in the example you gave.

They might slow my system right back down but they might be worth a try.

FFMG

---

### Post by mojoman on 2008-01-04
> **FFMG said:**
> 
Icons are nice, (and I might use them), but I was more talking about the other extras you have on your screen.
Such as clock, cpu usage,  and so on, as in the example you gave.

They might slow my system right back down but they might be worth a try.

FFMG

That's conky. You can use that with any desktop environment or window manager. It's in the repositories and it uses very little resources (at least the setup I have). My configuration file, (.conkyrc) is attached in post #8 in this thread (renamed to conky.txt). Use that as a base and edit it to fit your own preference and have a look at the conky-thread I linked to for some excellent tips on the subject.

Fluxbox menu can require a little bit more work than your run-of-the-mill menu but you can have it *any* way you like it. If you want quick-and-easy you can autogenerate too but I think that the menu, being so central, is far too important not to configure just the way I like it.

/mojoman

---

### Post by FFMG on 2008-01-04
> **mojoman said:**
> That's conky. You can use that with any desktop environment or window manager. It's in the repositories and it uses very little resources (at least the setup I have). My configuration file, (.conkyrc) is attached in post #8 in this thread (renamed to conky.txt). Use that as a base and edit it to fit your own preference and have a look at the conky-thread I linked to for some excellent tips on the subject.

I see, it is all starting to make sense now.

Thanks for the info, I learned quite a bit today.

Thanks

FFMG

---

### Post by RedSquirrel on 2008-01-04
You might want to check out fbpanel as well. It's in the repositories.

fluxconf is not especially worthwhile. At the very least, the "fluxkeys" part of it is buggy and will introduce errors into your ~/.fluxbox/keys file, so don't use fluxkeys. ;)

I can recommend the Fluxbox wiki. Lots of good info there...

[http://fluxbox-wiki.org](http://fluxbox-wiki.org)

Have fun! :)

---

### Post by FFMG on 2008-01-07
> **mojoman said:**
> That's conky. You can use that with any desktop environment or window manager. It's in the repositories and it uses very little resources (at least the setup I have). My configuration file, (.conkyrc) is attached in post #8 in this thread (renamed to conky.txt). Use that as a base and edit it to fit your own preference and have a look at the conky-thread I linked to for some excellent tips on the subject.

Fluxbox menu can require a little bit more work than your run-of-the-mill menu but you can have it *any* way you like it. If you want quick-and-easy you can autogenerate too but I think that the menu, being so central, is far too important not to configure just the way I like it.

/mojoman

Everything is working fine and as expected.
And now that I am playing with conky and fluxbox I am coming across some interesting configurations that I would like to try.
But, been new to Unix, I am not sure how I can copy and paste between my browser, (firefox), and the conkyrc file.

I use 

```
sudo nano ~/.conkyrc
```

But I don't seem to be able to copy examples I find on the net, from the browser to the editor.
How could I do that?

FFMG

---

### Post by mali2297 on 2008-01-07
> **FFMG said:**
> 
```
sudo nano ~/.conkyrc
```

But I don't seem to be able to copy examples I find on the net, from the browser to the editor.
How could I do that?


First of all, you should not need to use sudo to edit the files in your own home folder, just type
```

cd
nano .conkyrc

```
If you get an error about permissions, change the ownership with
```

sudo chown yourusername:yourusername .conkyrc

```

To copy text from one application to another, the easiest method is to mark the text with the mouse (left-click and drag), then move to the application and the place where you want to copy and just middle-click.

---

### Post by mojoman on 2008-01-07
> **mali2297 said:**
> To copy text from one application to another, the easiest method is to mark the text with the mouse (left-click and drag), then move to the application and the place where you want to copy and just middle-click.

Sure, unless you're using aterm, xterm or any other of the really lightweight terminals which doesn't support 'click-and-paste'. Instead, you need to use key shortcut for paste (ctrl+v or something but I think it depends on whether you're using emacs or vi mode but I might be wrong here). Me, I normally use the xfce-terminal. Fairly lightweight but still supports 'click-and-paste' and some other luxury stuff. :)

EDIT: FFMG. An easy way around this. Use mousepad to open the file instead. It opens up in a separate window and supports 'click-and-paste' So, ```
mousepad ~/.conkyrc
```

---

### Post by RedSquirrel on 2008-01-07
> **mojoman said:**
> Sure, unless you're using aterm, xterm or any other of the really lightweight terminals which doesn't support 'click-and-paste'. 

"**middle-click** to paste" is part of the X Window System.

Pressing "Shift+Insert" also works. ;)

---

### Post by mojoman on 2008-01-08
> **RedSquirrel said:**
> "**middle-click** to paste" is part of the X Window System.

Pressing "Shift+Insert" also works. ;)

Ok. I'm still clinging on to my two-button mouse so I wouldn't know :) 

The Xfce-terminal supports its own right-click (just like a lot of other applications does) and using that, you'll get 'paste' as an alternative. As a lot of the lightweight terminals don't support this feature I thought this might be the problem.

---

### Post by RedSquirrel on 2008-01-08
> **mojoman said:**
> Ok. I'm still clinging on to my two-button mouse so I wouldn't know :) 

You can probably click both buttons at the same time to achieve "middle-click".

Try adding the following to your xorg.conf (in the section for your mouse):

```
Option          "Emulate3Buttons"       "true"
```I haven't used that for a while (I have four buttons), but it used to work just fine. It may even be in your xorg.conf already (?).

(Mind you, clicking those two buttons at the same time may wear out your wrist/fingers/hand after a while.)


> **mojoman said:**
>  The Xfce-terminal supports its own right-click (just like a lot of other applications does) and using that, you'll get 'paste' as an alternative.

Yeah, I remember that. I find those right-click context menus for pasting rather annoying. :grin:

---

