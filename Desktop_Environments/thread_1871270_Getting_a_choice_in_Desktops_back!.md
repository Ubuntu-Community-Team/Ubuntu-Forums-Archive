---
title: "Getting a choice in Desktops back!"
date: 2011-10-28
forum: Desktop Environments
---

### Post by shanta on 2011-10-28
I have been attempting to get the choice of desk top onto my system. Due to Font and colour changes making the screen unreadable. I have now found that this is caused by 11.10 trashing my Nvidia video driver setup. Reinitialization of the drivers only got the laptop monitor working which was not earlier. Due to unity demand on the system things are VARY slow. The Toshiba external monitor works for low end graphics such as the desktop but not the unity panel. My wine programs such as sketup also crash now. 

Unities display dose not see the laptop display calls it unknown. nvidia used to show me the Toshiba monitor but know calls it unknown. Prior to 11.10 it worked fine.

software centre is a joke.

I can find and install the DTM in synaptic or at the command line with apt-get. I get them installed into the system which I have done for 

KDE
a Mac clone
Gnome shell 
Gnome Fall back

All install just fine but the list of desktops on start up is fixed with the default 8.

gnome Works no menu now way to add a menu In fact no way to run a program at all
gnome classic ditto
gnome classic without ditto
rescue not tried
Ubuntu  video drivers trashed with fount colours almost unreadable. with now apparent way to change
Ubuntu 2d ditto
another unity ditto
user defined goes to the last used

So from this there are three basic

First 

How dose one get the other desktops into the list for use? Why are they not added automatically in the first place.

two
What is gnomes menu and how do we get it to show? Gnome-panel dose not work (now known to be a video driver problem.)

When the current video driver was installed which took 5 + attempts to get it working, the gnome menu now appeasers, It still consumes a lot of resources but at least it works and is now readable.

three
How dose one change the appearance of the desktop? system tools applet dose not provide this option. Help also shows nothing.
gnome-tweek is an improvement of the unity system settings but stills falls far short of  useful  tool.

We know Unity suck so lets not talk about it in this thread and work on the solutions to the problems. It seems that there will be no going back to what works by the creators of Unity. They obviously are not listening.

thanks 
Shanta

---

### Post by shanta on 2011-10-28
installed gnome-tweek and it allowed me to change the theme and fonts so I got read ability back.

Not a great tool but it did do what I needed as the gonome-system tool is far from adequate.

Still looking to be able to switch to other desktops.

---

### Post by TBABill on 2011-10-28
Assuming you are using 11.10, simple. Click logout. At the login prompt, enter your password but don't hit enter. Click the little icon in the upper right where you enter your password. Select the DE you want, then click enter. That should take you to whatever you have chosen.

---

### Post by shanta on 2011-10-31
> **TBABill said:**
> Assuming you are using 11.10, simple. Click logout. At the login prompt, enter your password but don't hit enter. Click the little icon in the upper right where you enter your password. Select the DE you want, then click enter. That should take you to whatever you have chosen.

The fact that this is how it is supposed to work. It dose not. Only the "chosen" ones show up. The one you chose to install don't show in the list such as KDE.


Of these that do show they are not vary friendly unity the worst. Mostly demanding a high end video card.

---

### Post by Frogs Hair on 2011-10-31
Gnome Classic has an applications menu in my installation . The Gnome Shell includes ways to run applications but there is a little learning involved if you are used to classic menus . [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

It is possible to add extensions to the Gnome and activate them using the Gnome Tweek Tool > extensions . Among the extensions is an applications menu extension . [http://www.webupd8.org/2011/10/official-gnome-shellextensions.html](http://www.webupd8.org/2011/10/official-gnome-shellextensions.html)
 

I don't use KDE and don't know why you it doesn't appear in the login selection if installed . ( Mac Clone ? )  . Both Unity and the Gnome shell work very well for me. The only way to get Gnome 2 back is with an earlier version of Ubuntu or another Linux distribution.

I use the method posted for choosing the different desktops from the login screen menu next to the user name .

---

### Post by randywilharm on 2011-10-31
NVIDIA drivers are notorious for falling back to the old version when a new kernel is installed.

Don't forget that you must log into the terminal as **root** in order to install the driver properly.

It is wise to do this before you implement other remedies.

---

### Post by lokutus25 on 2011-10-31
The fact is that we don't have a choice. And that's sad. I agree Unity sucks. I'd like to give a try at Gnome 3. But seems it has some issue with ATI Proprietary drivers so I need to change to radeon. If I find out how. Gnome Classic it's a joke too. Sincerely for the first time in years I'm considering other distro. Sad.

---

### Post by shanta on 2011-10-31
:popcorn:> **Frogs Hair said:**
> Gnome Classic has an applications menu in my installation . The Gnome Shell includes ways to run applications but there is a little learning involved if you are used to classic menus . [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)


Only if the video driver is high enough. I can get it on the laptop monitor post nvidia driver install but not on  the external monitor.

It is possible to add extensions to the Gnome and activate them using the Gnome Tweek Tool > extensions . Among the extensions is an applications menu extension . [http://www.webupd8.org/2011/10/official-gnome-shellextensions.html](http://www.webupd8.org/2011/10/official-gnome-shellextensions.html)
 
used that but vary limited in what it will actuly change though far grater then Unities system editing.

I don't use KDE and don't know why you it doesn't appear in the login selection if installed . ( Mac Clone ? )  . Both Unity and the Gnome shell work very well for me. The only way to get Gnome 2 back is with an earlier version of Ubuntu or another Linux distribution.

I use the method posted for choosing the different desktops from the login screen menu next to the user name .

It seems that unity will not place your choices in the list. I know of no way yet to get them on the list.

---

### Post by shanta on 2011-10-31
> **lokutus25 said:**
> The fact is that we don't have a choice. And that's sad. I agree Unity sucks. I'd like to give a try at Gnome 3. But seems it has some issue with ATI Proprietary drivers so I need to change to radeon. If I find out how. Gnome Classic it's a joke too. Sincerely for the first time in years I'm considering other distro. Sad.

yes it is sad the Unity creators and it seems gnome want to give us the Msoft approach. 

As I figure out how to do it I will post the progress here. If I cannot get choice back into my desktop I too may bite the bullet and move to a new distro.

---

### Post by RhubarbnCustard on 2011-10-31
Wow - did I get a shock when I decided to clean install Ubuntu 11.10 in place of 10.04! After a day of trying Fedora (I liked the 'look' more than Ubuntu but it was a pain to shutdown). Went back to a copy of 10.10 and realized how dated it felt and that it was hefted to the dead Open Office, so I'm back with 11.10 now, and with an open mind I'm going to give it a go.

I already love the way windows can be docked/undocked to the top bar just by grabbing with the mouse. I'm not so keen on the lack of built-in customization ability, or the limited capacity of the side bar. I'm sure these niggles will evolve away over time.

Finding stuff in Dash is a revelation - but fancy not including Synaptic?

After a few hours of use I can see that this is probably the start of a whole new way of interfacing with our technology.

---

### Post by shanta on 2011-10-31
> **randywilharm said:**
> NVIDIA drivers are notorious for falling back to the old version when a new kernel is installed.

Don't forget that you must log into the terminal as **root** in order to install the driver properly.

It is wise to do this before you implement other remedies.

They indeed do fall back. 

i would however not recommenced attempting to install from root. as the nvidia install fails to update the kernel though it dose get the miss drivers on after you uninstall from the command line then install them again from the gui.

The process though did get the right drivers installed eventually.

---

### Post by wstreet on 2011-10-31
Imagine my surprise after 11.10 install and no way to get to 'Classic' desktop.  As a developer, Unity just doesn't work for me - it's just in the way.  I've loved Ubuntu in the past because I can install and go to work and still have the option to configure as I please.

Unity may be fine for the average user but at least give us developers the option of easily selecting the environment that we prefer.

Reminds me too much of Windows 7.  I guess I'll be looking to a different distribution soon.

---

### Post by Frogs Hair on 2011-10-31
> **shanta said:**
> :popcorn:

It seems that unity will not place your choices in the list. I know of no way yet to get them on the list.

I don't know what the problem is because I have been switching between the Gnome Shell , Unity 3D and installed E17 for few days The Gnome shell is not installed by default and must be added from the software center .

If the shell is not installed the Gnome session will not work unless you install the fall-back session .```
sudo apt-get install gnome-session-fallback
```

---

### Post by shanta on 2011-11-01
> **Frogs Hair said:**
> I don't know what the problem is because I have been switching between the Gnome Shell , Unity 3D and installed E17 for few days The Gnome shell is not installed by default and must be added from the software center .

If the shell is not installed the Gnome session will not work unless you install the fall-back session .```
sudo apt-get install gnome-session-fallback
```

Done all that you have suggest. and much more. The above gnome-session-fallback, gnome-shell, KDE and others by synaptic None will show up in the list of available managers. Why I am trying to find out as well as give us that want choices what we need.

---

### Post by RhubarbnCustard on 2011-11-01
> **wstreet said:**
> Imagine my surprise after 11.10 install and no way to get to 'Classic' desktop.  As a developer, Unity just doesn't work for me - it's just in the way.  I've loved Ubuntu in the past because I can install and go to work and still have the option to configure as I please.

Unity may be fine for the average user but at least give us developers the option of easily selecting the environment that we prefer.

Reminds me too much of Windows 7.  I guess I'll be looking to a different distribution soon.

I felt the same way initially - but once I started using Unity I started to see the point.

I also have to say that just 4 years ago Ubuntu was a pain to install and configure - for me at least. Ironically, most of these problems were ironed-out by 10.04. The installation for 11.10 actually worked 100% 'out-of-the-box' as they say.

I'm not a developer, but I do use my system semi-professionally and for study. I'd be interested to know what the problems are for developers, and maybe collectively solutions can be found?

---

### Post by TBABill on 2011-11-01
> **shanta said:**
> Done all that you have suggest. and much more. The above gnome-session-fallback, gnome-shell, KDE and others by synaptic None will show up in the list of available managers. Why I am trying to find out as well as give us that want choices what we need.I really don't think it's the OS blocking you from having choices. If anything, it's a bug, not an intentional design. I have installed KDE, LXDE and XFCE on mine and they all show up and work fine. Have you tried installing 11.10 from a fresh and clean download again, then adding each DE one at a time? It could be that something glitched during an update or during install that prevents it from working as designed.

---

### Post by Codflinger on 2011-11-01
> **TBABill said:**
> Assuming you are using 11.10, simple. Click logout. At the login prompt, enter your password but don't hit enter. Click the little icon in the upper right where you enter your password. Select the DE you want, then click enter. That should take you to whatever you have chosen.
Thanks Mate!
Life is good again.

---

### Post by Frogs Hair on 2011-11-01
> **shanta said:**
> Done all that you have suggest. and much more. The above gnome-session-fallback, gnome-shell, KDE and others by synaptic None will show up in the list of available managers. Why I am trying to find out as well as give us that want choices what we need.

I was wondering if you had installed Gnome fallback that is why I wrote that . Something is very wrong with your installation if your installed options are not appearing . If It were me I would have reinstalled by now , but though that is a possible option me , not everyone can or wants to do that.

Gnome no longer supports Gnome 2 it has reached end of life (Classic Ubuntu) and now is only developing Gnome 3 . Canonical / Ubuntu has decided to use the Gnome 3 platform for Ubuntu leaving Unity as default. Other desktop environments are optional for installation .  

As I wrote in my first post Gnome 2 is gone and not coming back unless you go back an earlier release or another Linux distribution that uses it. The only release that had two desktop environments installed was 11.04 . Now only the default environment is offered as in releases prior to 11.04 .

---

### Post by shanta on 2011-11-04
It seem that now that the Linux media has taken up the issue that there is now official word that power users are really not forgotten. This is good because we were under the impression that we were by the lack of clear discussion from them on the topic.

It should be noted that only Unit was under discussion or improvement not our desire for choices. 

On my quest to get my laptop back I have found the fallowing pints of interest,

Only gnome based desktop seem to show up and only when installed with the default  installer.They come up with the gnome-panel that takes over the desk top and hides all running application. Hiding the fact that your programs are running you just can see them. 

first reaction is the desktop dose not work. When in fact it is the panel that is blocking your view use always on top and it works for the one you wish to use.

I have gotten gnome classic with no extras (gnome-panel not included). It work fast and allows me to install new os in Virtual box and have power left to use a program or two in the host system. Not able to have this option since Unity was introduced as the desktop. I in the past blamed it on the laptop self but now I see that it us unity based.


Another thing that seems apparent that any non gnome based desktop KDE fxlm etc don't show up in the choices of desktops.

---

### Post by cybergalvez on 2011-11-04
> **shanta said:**
> Done all that you have suggest. and much more. The above gnome-session-fallback, gnome-shell, KDE and others by synaptic None will show up in the list of available managers. Why I am trying to find out as well as give us that want choices what we need.

There is something seriously wrong with your setup because all I did was install gnome-shell and it shows up on the list and install xubuntu-desktop and it shows up as well no issues. 

At this point I would back up your home folders and do a clean install.If you don;'t like Unity then pick something else you have all kinds of choices, I personally like Unity, and currently using Gnome-shell and have used xubuntu when I want that classic feel

---

### Post by oldrocker99 on 2011-11-05
My personal recent experience with 11.10 in an Xubuntu installation had showed no top or bottom panels, only the right-click menus available, and NO System menus!:mad:

I started Synaptic (from the shell...) and installed Unity, GNOME 3, gnome-fallback, Cairo Dock, and kde-full. KDE still makes me grit my teeth somewhat, but at least it is a usable desktop, with a System menu, which none of the others, including the otherwise swell GNOME with Cairo allow menu access to system programs. This is simply inexcusable. GNOME 2.x wasn't very broken. Neither was KDE 3.x. Both times, developers took what basically wasn't broken and "improved" it.](*,)

I have just installed LXDE, and when I log out, I'll try it. I understand that Linus himself was quoted as saying he's going to XCFE (as I recall, it might have been LXDE) rather than the much-disliked GNOME 3. He said somethign to the effect that, "***E is a downgrade from GNOME 2, but it's an upgrade from GNOME 3.":cool: He had earlier abandoned KDE for GNOME 2.x when KDE v4 came out.

gnome-fallback just isn't as useful to a power user as myself as GNOME 2x. Unity would be a great interface for a tablet or snartphone, but it is unsuited for useful work on a desktop. Why have developers decided to abandon the cascading menus that have been in GUIs for nearly 30 years? A new Ubuntu user isn't going to know all the names of all the programs, and rolling through dozens of huge icons is (to say the least) counterPRODUCTIVE.:confused:

Just my $0.02 worth.

---

### Post by oldrocker99 on 2011-11-05
Well, I'm using LXDE now, and it has a Preferences menu with all the old System items back in the day. Looks nice and runs snappy too. For now, I'm happy. I'm just glad I can run Nautilus...

---

### Post by shanta on 2011-11-06
Did a complete re install of anything unity or kde related. Before I had a chance to test. There was a bunch of updates to unity done by which got things working again I don't know. desktop choices are now beginning to appear in the start up lit as they should. Kde hows but uses a lot of resources bit better than unity and more con fig options seem to be able to be found.

xfce is what I am now writing this in has all of the old menus and works fast to ether of the unity or gonome options.

may be be able to get more than 3 windows maximized before thing go white. a problem I have been having since the introduction of Unity.

Right now I can get into on both the laptop monitor and the external display with unity and unity-2d both cannot run much as the demand on the system is too high. 

All most working again.

---

