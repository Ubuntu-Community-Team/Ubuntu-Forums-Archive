---
title: "Thinking about trying Fluxbox? Does it work well with Ubuntu?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by kentl on 2006-08-11
Hi!

I've been thinking about trying Fluxbox for quite a while. I tried it earlier when I was even more of a Linux beginner than I am now. The minimalistic approach seems appealing to me.

I'm wondering if Ubuntu is a good distribution to try this? Or should I go for another distribution? (I know Ubuntu's main WM is Gnome.)

---

### Post by maniacmusician on 2006-08-11
yeah, KDE and Xubuntu are also very good. I've tried fluxbox, it works pretty well. Other than fluxbox, I was using Xubuntu (CFCE environment), and though minimalistic is good for intense tasks like recording and editing music, i prefer a more loaded environment for normal everyday stuff.

---

### Post by aysiu on 2006-08-11
The only distribution you'll notice a difference on is Damn Small Linux because all the plugins and such have been configured for you.

If you install Fluxbox on Ubuntu or any other major desktop distro, it'll look very bare... and pretty much the same whether you're using Ubuntu or Mandriva...

---

### Post by dusu on 2006-08-11
Go for it kentl !

I've installed Breezy server, X and blackbox on a quite old laptop and it works perfectly... no reason why fluxbox should be any different !

---

### Post by Haegin on 2006-08-11
I have done it in the past and it worked very well. I'm not on my main machine at the moment but I can send you some links about config files and fluxbox setup if you want later today. If you have problems I will be happy to help.

---

### Post by kentl on 2006-08-11
> The only distribution you'll notice a difference on is Damn Small Linux because all the plugins and such have been configured for you.
 
If you install Fluxbox on Ubuntu or any other major desktop distro, it'll look very bare... and pretty much the same whether you're using Ubuntu or Mandriva...
But that isn't a problem, or? I hope that I can add the things I need and want myself. What's the advantage of using Fluxbox with Damn Small Linux instead of Ubuntu?
> I have done it in the past and it worked very well. I'm not on my main machine at the moment but I can send you some links about config files and fluxbox setup if you want later today. If you have problems I will be happy to help.
Some more information would be great! I also found this article inspiring: [http://www.tuxmagazine.com/node/1000191]("http://www.tuxmagazine.com/node/1000191")

---

### Post by kentl on 2006-08-11
Does it make any difference if I choose to install Ubuntu 6.06 Dapper och Kubuntu 6.06 Dapper when I'm going to use Fluxbox anyway?

Are there any things I should think of when installing Fluxbox? (Or is it just **apt-get install fluxbox** and I'm finished?)

Is it possible to switch between Fluxbox and Gnome without messing up any configuration files? And also. Is it possible to un-install Fluxbox in case I find out that it isn't for me?

---

### Post by aysiu on 2006-08-11
> **kentl said:**
> Does it make any difference if I choose to install Ubuntu 6.06 Dapper och Kubuntu 6.06 Dapper when I'm going to use Fluxbox anyway? No. It doesn't matter.

> 
Are there any things I should think of when installing Fluxbox? (Or is it just **apt-get install fluxbox** and I'm finished?) ```
sudo aptitude update
sudo aptitude install fluxbox
``` Log out, pick *Fluxbox* from the session. Log in.

Keep in mind *fluxbox* alone is *very* bare. You may want to install some extra plugins, too: ```
sudo aptitude update
sudo aptitude install fluxbox bbrun fbdesk fluxconf
``` You'll need [extra repositories](http://www.psychocats.net/ubuntu/sources) for all of this, by the way.

> 
Is it possible to switch between Fluxbox and Gnome without messing up any configuration files? Yes. Their configuration files are stored in separate hidden folders in your /home/kent directory. > And also. Is it possible to un-install Fluxbox in case I find out that it isn't for me? Yes--install with *aptitude* instead of *apt-get* and then ```
sudo aptitude remove fluxbox
```

---

### Post by Ramses de Norre on 2006-08-11
Fluxbox is very good, I've used it for several months (but today I installed XGL/Compiz and I think I'm going to use that for a while).
The only thing is that it looks difficult and hard in the beginning, but once you're used to editing some files in ~/.fluxbox/ you'll like it very much!

---

### Post by Haegin on 2006-08-11
Ok. Most stuff you will be interested in for config is in the ~/.fluxbox folder. The main file is the menu file which (iirc) takes the format as follows:
```

[begin] (MenuTitle)
[submenu]  (SubMenuName) {SubMenuTitle}
[exec] (ApplicationName) {/path/to/program}
[include] (/path/to/meufile)
[end]
[nop] (--------)
[workspaces] (SubMenuName)
[stylesdir] (/path/to/stylesdir)
[config] (FluxboxConfiguration)
[reconfigure] (Reconfigure)
[restart] (Restart)
[exit] (Exit)

```
The bit in [] is the type of command, the bit in () is the name that appears in the menu and the bit in {} is the comand itself.
Linkage: [http://fluxbox.sourceforge.net/docs/en/newdoc.menuedit.php](http://fluxbox.sourceforge.net/docs/en/newdoc.menuedit.php)

The way I installed fluxbox was by doing a server install of ubuntu (so no desktop manager or graphical login) and then installing xorg and fluxbox (and other stuff like gtk2, xterm, gvim, mpd, feh (image thingy), xplanet (cool backgrounds), and PCMan File Manager ([http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/) - like nautlius but no gnome ties).

Also the exec file will run when fluxbox starts so you can run programs from this (add a " &" to the end of each command so the next one runs - its a bash script basically). Also the ~.xinitrc file can be used to start fluxbox when you login so its automatic.

All in all fluxbox is a v cool desktop manager if you want speed. I never really used more than 200mb of memory and never touched the swap (I had conky open on the desktop) and that 200mb was when running firefox, mpd (music), open office, sylpheed claws (email), gvim and poss some other stuff.

Sorry I don't have more links - they were lost when I reformatted my PC for the umpteenth time.

If you need help then feel free to ask me and I will try my hardest.

---

### Post by kentl on 2006-08-14
Thanks to all! And especially you Human Prototype! I'm impressed by this community! When I get more knowledgable I'll contribue as well, to keep the good momentum alive. :D

---

### Post by Thulemanden on 2006-08-14
> **kentl said:**
> Hi!

I've been thinking about trying Fluxbox for quite a while

I prefer Icewm because it's so easy to configure.

---

### Post by bodhi.zazen on 2006-08-24
Fluxbox is great. I do a server install and run Fluxbox without installing gnome, KDE, or XFCE.

I disagree with some of the previous comments in that I feel Fluxbox is very full featured. It is highly configurable and uses transparency, both with menu and panel. It also handles dual monitors "out of box" better then any of the other 5 I mentioned here in my post. 

IceWM is also outstanding. More popular on Debian sites then Ubuntu.

See this site for a VERY nice overview of IceWM:

[http://forums.debian.net/viewtopic.p...6446ed4225d6b8](http://forums.debian.net/viewtopic.p...6446ed4225d6b8)

Lately I have been looking into Openbox. Very light weight. No panel. This is about as light as I go.

Try perlpanel, fbpanel (fbpanel is not related to Fluxbox), or pypanel.

---

### Post by gThree on 2006-08-24
I tried Fluxbox and Openbox and prefer Openbox.  They're easy to install, just allow some time for configuration.  Not hard to configure once you get the hang of it.  You'll probably want to change the GTK theme too.

I really like the concept of minimalistic window managers.  Once you get your key bindings set and apps sorted out, everything works very efficiently and I find the lack of graphic clutter makes it easier to focus.

I don't use a panel or a desktop, and use key bindings to launch gmrun or open/navigate the main menu.  In general, I don't think you have to be using old hardware to improve your computing experience with a *box wm.  Definitely give one (or all of them) a shot.

---

### Post by bodhi.zazen on 2006-08-24
> **aysiu said:**
> No. It doesn't matter.

 ```
sudo aptitude update
sudo aptitude install fluxbox
``` Log out, pick *Fluxbox* from the session. Log in.

Keep in mind *fluxbox* alone is *very* bare. You may want to install some extra plugins, too: ```
sudo aptitude update
sudo aptitude install fluxbox bbrun fbdesk fluxconf
``` You'll need [extra repositories](http://www.psychocats.net/ubuntu/sources) for all of this, by the way.

 Yes. Their configuration files are stored in separate hidden folders in your /home/kent directory.  Yes--install with *aptitude* instead of *apt-get* and then ```
sudo aptitude remove fluxbox
```

Thanks aysiu for this very nice how to.

In my opinion, however, this is making Fluxbox more complicated then it has to be. I would not call fluxbox a "bare" window manager, but that is me. Fluxbox is, of course, bare as a desktop manager.

I run Fluxbox without all this and would suggest you start with just fluxbox. It does take a while to learn the configuration files, but once you do many people configure the file directly rather then via a GUI tool.

gThree: I agree, but I am addicted to some eye candy. Specifically the transparency in fluxbox and at least some kind of panel. I like to see the date/clock in the corner. I know it is a lame excuse. I could do without the clock, but neither Icewm or Openbox do transparency (menu/panel). I will run openbox with a panel (fbpanel).

---

### Post by Haegin on 2006-08-24
> **bodhi.zazen said:**
> I disagree with some of the previous comments in that I feel Fluxbox is very full featured.

I must disagree in turn with this. Some people will come here expecting fluxbox to be a drop in replacement for gnome. It isn't. Gnome comes with a file manager and loads of programs (all in the gnome project even if Ubuntu doesn't include them) where as fluxbox is exactly what it claims to be, a window manager.
Remember, a window manager and a desktop environment are very different.

---

### Post by bodhi.zazen on 2006-08-24
which is why I said
> I would not call fluxbox a "bare" window manager, but that is me. Fluxbox is, of course, bare as a desktop manager.

perhaps I should have said
> I would not call fluxbox a "bare" window manager, but that is me. Fluxbox is, of course, bare as a desktop **environment**.

But the terminology is inconsistent.

---

### Post by kentl on 2007-06-13
Now a lot of time has passed, but I'm still going to do it.

Some of you in this thread have talked about installing the server edition of Ubuntu 7.04, if I'm not mistaken? I have heard the the kernel of the server edition is different from the desktop edition. And I am going to use my laptop as a desktop system in combination with me wanting a clean (as little "junk" as possible, I want to install my own stuff) install which uses Fluxbox. Which installation media and method do you recommend?

---

### Post by NeoLithium on 2007-06-13
Well, for something that is a smaller sized install without a great deal of stuff that you didn't pick, the server edition would be a good idea, then just use that to install Fluxbox as the Window Manager.   It won't give you a great deal of things off the bat that are installed, however it gives you a bit more freedom to simply have only what you want, and nothing else.  It's basically a matter of personal preference though, and how you would like to do things.

Just my 2 cents.
Have fun with it, above all :)

---

### Post by kentl on 2007-06-13
Thanks. And that's exactly what I think I would like. To start out without much and install what I need myself. Instead of the other route where you uninstall stuff you don't wan't. But what about the difference I've heard of regarding the kernels?

---

### Post by smartboyathome on 2007-06-14
You can easily upgrade the kernel after the install. That is what I did with my FVWM-Crystal install. After you get Fluxbox and a network manager installed, use:
```
sudo apt-get update && sudo apt-get upgrade
```
and you should have the latest kernel.

---

### Post by kentl on 2007-06-14
Thanks for your reply. Well I wasn't talking about upgrading the kernel to the latest version. What I heard is that the kernel in the Ubuntu Server edition is differently configured to the one in the Ubuntu Desktop edition. Exactly what these differences would consist of, I do not know.

Anyway. If it's the case, that a Server Edition uses some kind of special non-Desktop-optimal kernel, wouldn't an upgrade just get me the new version of the "wrong" kernel? ("wrong" in the context of me using the system as a desktop system, even though I installed using the Server Edition downloadable media.)

---

### Post by kentl on 2007-06-14
Thanks for your reply. Well I wasn't talking about upgrading the kernel to the latest version. What I heard is that the kernel in the Ubuntu Server edition is differently configured to the one in the Ubuntu Desktop edition. Exactly what these differences would consist of, I do not know.

Anyway. If it's the case, that a Server Edition uses some kind of special non-Desktop-optimal kernel, wouldn't an upgrade just get me the new version of the "wrong" kernel? ("wrong" in the context of me using the system as a desktop system, even though I installed using the Server Edition downloadable media.)

I haven't found a place which tells me the exact differences between the Desktop and Server edition, as well as the "alternate" install media. Just a lot of "buzz words" (non technical information which might very well be valuable from a business perspective) on the Server Edition information page.

---

### Post by smartboyathome on 2007-06-14
The kernel on my FVWM-Crystal is a "-server" kernel. But it should work fine for stuff like fluxbox, as they are very light on ram. ;)

---

### Post by kentl on 2007-11-03
Does anyone know where can I read about the differences of the kernals in the desktop and server releases?

What I've done so far is:
[LIST=1]
[*]Installed a "command-line system" using the alternate desktop image.
[/LIST]

---

### Post by deserthowler on 2007-11-03
I got a Dell with Ubuntu preinstalled.  I added FVWM and started working with it.  I used mostly Gnome at the start but am now using my custom FVWM most of the time.

I added several programs not in the original install.

Using key and mouse bindings I have several menus and mouse buttons configured for moving windows, moving between desktops, general menus, and  a specific menu for Administration.  If there is something that I haven't set-up in FVWM, I can switch to Gnome.

Using Gnome pre-configured menus.  I check the properties of a menu item and use it to call the program with FVWM by copying the call to my FVWM configuration file.  I can edit my configuration file while using Gnome.  Usually this works without any problems but YMMV.

There are 2 major problems though.  1> it is addictive and I spend a lot of time playing with configurations.  2> I have trouble remembering what is where on my menu system because I added so many features.

It's helpful is having an extra user or 2 for experimenting with FVWM so I don't screw up my working configuration while experimenting..

Although not Fluxbox related directly, these ideas might help.

Earl

---

### Post by kentl on 2007-11-03
Having extra users was a nice idea. I'll use it as well. I guess I'll be neck deep in configuration files in a while, but it's probably worth the hassle. :-)

---

### Post by RedSquirrel on 2007-11-05
If you've installed a command-line system using the alternate CD, that should give you the generic kernel. That's the one to use for what you plan to do.

You might find this link helpful:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

The howto in my signature might be of some use to you as well.

Have fun! :)

---

### Post by kentl on 2007-11-06
Thanks! :-) I got stuck by [some problems]("http://ubuntuforums.org/showthread.php?t=601828"), so I have only installed x.org and my graphics driver as of now.  But hopefully I'll be able to continue in a while. If I can't I might install Feisty and try to run that instead.

---

