---
title: "Questions about desktop environments"
date: 2014-06-01
forum: Desktop Environments
---

### Post by claes2 on 2014-06-01
Hi there.  At the moment I am running Ubuntu 14.04 LTS and I am a relatively new user that is just starting to get comfortable.  I have some questions about alternate DE's vs Unity.  I am looking for a DE that is less resource intensive than Unity, although I am unsure of my options.

1) What other DE's are there besides Unity?
2) Are there any other DE's that I would be able to install without having to re-install Ubuntu?
3) How do I go about doing such a thing?

This is a good start, and should get the ball rolling.

---

### Post by qyot27 on 2014-06-01
1) Yes there are.  GNOME (referring to the GNOME 3 desktop here, not the deeper system stuff that Unity also depends on), KDE, Xfce, and LXDE are generally the big players.  MATE and Trinity also exist as forks of previous versions of GNOME and KDE.  Various *box window managers (Openbox or Fluxbox, etc.) can be used as minimalistic environments.  There's also Enlightenment, using various tiling window managers as desktops, and other types of non-traditional-desktop options that can possibly be even lighter on resources.

2) Pretty much any of the ones I just mentioned.  You can install them by looking for the DE themselves, or in the case of KDE, Xfce, or LXDE, you can look for kubuntu-desktop, xubuntu-desktop, or lubuntu-desktop.  The biggest differences between the plain DE and the -desktop variant are in the theming or select choices of software that get pulled in at the same time.

3) Look in the Software Center, or you can use the Terminal to do it:
```
sudo apt-get install lxde
```
Unless MATE has finally gotten into the official repositories, you'll need to add the repo provided by the MATE project itself.  They have the instructions to do so on their website.  The same might also be true of Trinity, but I'm not sure.


GNOME and KDE are in the same general resource ballpark as Unity.  MATE and Xfce are lighter on resources (Xfce moreso), and LXDE uses the least resources, more or less (while still retaining a traditional desktop; you can get even lower with non-traditional window manager sessions as desktops and such, but with the steeper learning curve).

Once installing a different DE, you can select between them at the login screen - click on the Ubuntu button on the login dialog and it'll show the alternate DEs available.

---

### Post by claes2 on 2014-06-01
Thank you so much for your reply.  I installed Gnome Flashback and it runs beautifully.  I'm going to play around with this one and some others before I make an informed reply, which will probably have some more questions but I appreciate your prompt response.  It was very helpful.

---

### Post by LastDino on 2014-06-01
Although, all this has been very well described,  unless your system config is quite ancient like mine (i.e: P4 single core and less than 2GB RAM for example), you need not shy away from Unity or even KDE forms of Ubuntu, or for any other distro for that matter.

---

### Post by PJs Ronin on 2014-06-01
I'm currently having an affair with xfce.   I'm not a fan of the direction Unity is taking nor with what appear to be inconsistencies between Unity on 13.10 and on 14.04, although this may be caused by my own ham-fistedness.   Nonethless, xfce is customisable to just about any degree you wish and I now have mine looking a treat.   I started with a standard Ubuntu/Unity install and then added xfce via:```
 sudo apt-get install --no-install-recommends xfce4 xfce4-goodies
```

---

### Post by claes2 on 2014-06-01
> **PJs Ronin said:**
> I'm currently having an affair with xfce.   I'm not a fan of the direction Unity is taking nor with what appear to be inconsistencies between Unity on 13.10 and on 14.04, although this may be caused by my own ham-fistedness.   Nonethless, xfce is customisable to just about any degree you wish and I now have mine looking a treat.   I started with a standard Ubuntu/Unity install and then added xfce via:```
 sudo apt-get install --no-install-recommends xfce4 xfce4-goodies
```

Would you be amenable to posting a picture of your desktop?  Don't feel compelled to by any means but I would like to see what a nice xfce DE can look like from an average user not someone making a desktop just to post it like on deviantart.  

I appreciate aescthetics but not at the expense of functionality and performance.  My ideal DE is a marriage of both function, convenience, strong performance, and clean aesthetic design.  Since I opened this thread I have been using several variants of the Gnome DE because I like the design and because they are 2D and aren't as resource hungry as the full blown Unity 3D DE can be, which is completely unecessary to me.

*****

I've noticed so far that there are apps and applets that run ONLY in the Gnome DE and not in Unity.  Is xfce the same where it uses its own apps and applets?  I'd like to know more about this.  Thank you for your reply.

---

### Post by claes2 on 2014-06-01
> **LastDino said:**
> Although, all this has been very well described,  unless your system config is quite ancient like mine (i.e: P4 single core and less than 2GB RAM for example), you need not shy away from Unity or even KDE forms of Ubuntu, or for any other distro for that matter.

I'm running Ubuntu 14.04 from a Acer C720 Chromebook which has a snappy Haswell processor but only 2Gb of RAM which makes it choke when trying to do too many things at once in an OS not specifically coded for it like ChromeOS is.  When I have the ChromeOS partition loaded I can have literally 20 tabs open with no slowdown but I can't even use Chrome at all in the Ubuntu partition; it's too bogged down.  Hence my quest for lighter weight everything.  Less RAM expenditure per application, less space, and fewer processes.  Figuring out how to do it has been the most fun I've had with a computer in a long, long time.  And the Ubuntu community is very helpful and kind.  Although I have run into a few people that are die-hard this or that distro for the most part everyone has been very inviting and amenable to helping in any way they can.  It is a heady experience.

When you say KDE forms of Ubuntu to what exactly are you referring? Is it a seperate distro or a DE that I can try out wihout a full-on reinstall?  Note that I am not against talling a new distro; I would have to find one that I can install from the Chrubuntu script - but I can learn about them all regardless.  Thank you for your reply.

---

### Post by LastDino on 2014-06-01
I usually recommend Xubuntu for that config. When I say KDE I mean Kubuntu in this case, it is just like Xubuntu, an DE of Ubuntu. Although, it is known to be heavy-weight DE unlike Xubuntu. Anyway, for the config you've posted, Xubu or equivalent desktops XFCE on other ditros are the right way to go.

---

### Post by PJs Ronin on 2014-06-02
> **claes2 said:**
> Would you be amenable to posting a picture of your desktop?
[ATTACH=CONFIG]253667[/ATTACH]

Happy to oblige.   My requirement for desktop is to be as clean as I can make it and only display things when I want to see them.   The conky on the right hand side is fixed and provides all I need to know about my system and what's happening outside in the real world.   On the left side is a single panel that is only as tall as the number of icons in it, unlike unity's fixed height launcher.   This panel only appears during mouseover.   The panel also has a 100% transparent background; something I could not achieve in unity.   You will also note there is no top panel, or menu bar as unity calls it.   I think unity's top panel is the most useless/annoying/insertsuitableinvictive thing I have ever seen.

And yeah, I'm a cat guy.

---

### Post by PJs Ronin on 2014-06-02
> **claes2 said:**
> I'm running Ubuntu 14.04 from a Acer C720 Chromebook which has a snappy Haswell processor...
I didn't realise you were running a notebook.   My desktop described above is from my main desktop computer which has more grunt than a polecat in heat.   I've recently come into posession of an old Toshiba lappie (celeron based) and installed the full Xubuntu 14.04.   Go ahead, ask me if I'm happy with the results :).

---

### Post by mastablasta on 2014-06-02
XFCE is kind of light Gnome. it still looks verty nice and is really easy to setup the way you want it. most things are changed by right clicking on them and selecting "preferences" or something like that. you will see various styles of XFCE over the net. i think the default found in xubuntu is quite good. 


it is much faster (or ratrher less resource intensive) than the heavier two KDE and GNOME. eventhoough if you turn off effects in KDE it can get quite fast as well.  LXDE is the youngest of them all and stll has some rought edges. it is soon to become LXQT as RazorQT (kind of light KDE) and LXDE joined forces. since i like to use GUI to get things done i like KDE a lot. it has a lot of good GUI apps. i also like XFCE since it is light and very easy for a newb like me to modify it the way i like it (i use it in virtualbox when i test things).

in short XFCE - for it's flexibility & light on resources, KDE for default qt based apps.

if you need something super light try only a window manager. e.g. IceWM or JWM. or if you want something hardcore but very easy to use i3 ;-)

---

### Post by claes2 on 2014-06-02
> **PJs Ronin said:**
> [ATTACH=CONFIG]253667[/ATTACH]

Happy to oblige.   My requirement for desktop is to be as clean as I can make it and only display things when I want to see them.   The conky on the right hand side is fixed and provides all I need to know about my system and what's happening outside in the real world.   On the left side is a single panel that is only as tall as the number of icons in it, unlike unity's fixed height launcher.   This panel only appears during mouseover.   The panel also has a 100% transparent background; something I could not achieve in unity.   You will also note there is no top panel, or menu bar as unity calls it.   I think unity's top panel is the most useless/annoying/insertsuitableinvictive thing I have ever seen.

And yeah, I'm a cat guy.

Yes, the background wallpaper is irrelevant to me in desktop discussons, but I like yours because the conky is on the right and the launcher is on the left;  you tailored it to specifically fit around the picture which is nice.

I have installed the xfce DE via the command mentioned above and already I can tell that it is reacting faster and more responsively than the previous desktops that I have installed.  However the default xfce desktop is quite Spartan and it looks like it would take quite a bit of work to get it even near something as refined as you have made yours to be.  Could I ask you some questions about changing the xfce desktop into something a little more cleaner on the eyes and yet still useful and accessable for me?  If I work on that slowly while continuing my discussion about other DE's I can finish this thread with quite a bit of knowledge gained as well as a functional and aesthetically pleasing desktop.  Thank you for your reply.

First round of questions: I used Docky on my last desktop for my launcher but it looks like xfce has one already.  I'd like to remove the icons from the desktop, remove the top bar including the Applications Menu either completely or just so that I don't have to see it, increase the resolution of the entire desktop, and start working on the launcher by adding my most used applications.  Is there a theme that I can download or am I going to do this all manually?  I'm fine either way...

---

### Post by oldos2er on 2014-06-02
Moved to Desktop Environments.

There is a non-exhaustive list and descriptions of the more popular DEs and window managers [here]("http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available").

---

### Post by PJs Ronin on 2014-06-02
I'll give you a lead in on how to address these issues, but half the fun of setting things up your own way is by experimentation.   So, in no particular order:

Preliminary.   Much of what you want to do requires that the xfce display compositor be turned on.   To do this, click the Applications Start icon (the rat with an X),  select Settings > Settings Manager > Window Manager Tweaks, select the compositor tab and ensure 'Enable display compositing' is selected.

Themes.   Installing the full Xubuntu package brings in a raft of themes.   Otherwise, I'd suggest looking around [here]("http://www.noobslab.com").

Panels/Docks/Docky.   You are correct, xfce comes with its own panel system.   You can have as many as you want and position them where you want.   Again, select the Aplications Start Menu icon > Settings > Panel and you can add/delete/modify to your heart's content.

Desktop icons.   The other part of xfce's settings system is accessed by the mouse right click.   Select anything you want (an application icon, a panel, the desktop et al) right click and you'll find a settings menu for that item.   So, right click somewhere on the dektop and you'll find how to remove the desktop icons... and a bunch of other usefull stuff.

Some xfce theme/setting combinations are outstanding, some not so hot.   But, unlike unity where you need gnome-tweak-tool, unity-tweak-tool, ubuntu-tweak-tool, CCSM and probably Unsettings to get 90% of what you want, with xfce all settings are wrapped up in one location... and they work.

Have at it, have fun.

---

### Post by Jay_E on 2014-06-04
If you are a fan of xfce ( I am) you can try to download Ubuntu Studo onto a usb-stick or CD and then boot it in the "try it" mode that does not install.
xfce is the default in Ubuntu Studio. It is leaner on the apps as well.
Using a usb-stick allows you to make 'persistent' changes - and you'll always have something if your disk fails.
I tried several Ubuntu versions (over a few weeks) and looked around until I found what I liked.
Have fun,
Jay

---

