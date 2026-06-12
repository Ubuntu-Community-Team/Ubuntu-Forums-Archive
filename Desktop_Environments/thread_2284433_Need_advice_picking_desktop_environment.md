---
title: "Need advice picking desktop environment"
date: 2015-06-29
forum: Desktop Environments
---

### Post by gentimjs2 on 2015-06-29
I've been away from Ubuntu for a while (My primary desktop has been solaris10/sparc running an older KDE for quite some time at home, along with windows7 at work)

I've run into an unending laundry list of minor annoyances that are "deal breakers" with every desktop environment I've tried currently on ubuntu 15.04. 

What I'm looking for, and was able to setup as recently as 2 years ago very easily in KDE/Kubuntu but am now unable to replicate: 

[LIST]
[*]A left-side-of-screen "panel", that I can add icons/launchers too. 
[*]A desktop-switcher on the panel that allows me to mouse-over the switcher, and use the mouse wheel to switch desktops OR allows me to use the mouse wheel to switch desktops while hovering/focused out on desktop blankspace. 
[*]The volume/mute keys on my Sun Type7 USB keyboard to work 
[*]Min/Max/Close buttons on the right hand side of the window bar. 
[*]A traditional style "main menu" rather than a unity/windows8/android type menu. 
[/LIST]

I don't think this should be an especially demanding thing to want out of my desktop environment, however thus far I've tried all the ones I could find a way to download and none of them provide it. 
[LIST]
[*]Unity lacks right-side min/max/close buttons, no way I can find to get the mousewheel to switch desktops, and the main menu is horrible. just really, really, bad. (Yes, I've tried ClassicMenu Indicator but having it stuck up in the top bar is highly annoying) Also the maximized windows joining the top-mac-style bar is highly annoying. 
[*]Plasma/LatestKDE doesn't seem to have a desktop-switcher widget for the panel anymore, nevermind mousewheel switching. I wish I knew why such a basic feature has been removed. The volume keys on my KB are also non functional. 
[*]LXDE has many problems (cant relocate panel, add launchers, etc), the "logout" button does nothing, and the volume keys dont function. 
[*]generic "Gnome" lacks most customization options I like (position of panel, ability to add stuff to it, etc) 
[*]gnome metacity and gnome compiz similarly lack customization of the panel location and contents 
[*]openbox lacks panels entirely 
[/LIST]

I haven't found a way to install XFCE (would strongly prefer not having to re-install off a xubunutu cd) so I haven't been able to test drive it.

Anyone have any suggestions of a desktop environment I might try that's installable on ubuntu 15.04(64bit) without much hassle?

---

### Post by yetimon_64 on 2015-06-29
> I haven't found a way to install XFCE 
The next code, entered in a terminal, will install an xfce DE on a standard ubuntu install. You can the switch unity/xfce sessions and log into the xfce desktop from the lightdm login screen by clicking the power cog icon beside where you enter your password normally.

```
sudo apt-get install xubuntu-desktop
```

Seems from your list that xfce should be an alright choice. Cheers, yeti.

---

### Post by gentimjs2 on 2015-06-29
Will using the XXXbuntu-desktop meta packages replace the login/session manager and mess with my app repositories?
(Might be an ignorant question - again, I've been out of the ubuntu loop for a while)

---

### Post by yetimon_64 on 2015-06-29
No the xubuntu-desktop package integrates into the lightdm login screen/sessions well. It may change the splash screen, if so about 2 or 3 terminal commands can revert the splash screen back to the stock ubuntu splash screen if it does.

I have installed other DEs with unity in the past with the only real change being in the splash screen changing (but only if supplied from the Ubuntu repos, don't try with DEs that supply their own repos ... they can do as you note above ... and have done so to me recently)

 It will download quite a few alternative programs that may duplicate some of unitys functionality  but the desktop config files can be adjusted if necessary to keep the 2 systems to themselves applications wise.

---

### Post by gentimjs2 on 2015-06-29
Installed the xubuntu-desktop meta package, and sure enough - the generic XFCE desktop has everything I wanted. 

Thanks Yeti, good advice. :p

Now if I can get unity's session manager's background to be blue instead of purple, all will be right with the world - but I can research that elsewhere. 
Thanks again.

---

### Post by buzzingrobot on 2015-06-29
> 

[LIST]
[*]A left-side-of-screen "panel", that I can add icons/launchers too. 
[/LIST]

Unity's Launcher is located on the left side. Icons and launchers can be added . Unlike a traditional Windows-esque panel, no little boxes appear when a window is minimized. Minimized windows are accessible via a right-click on the appopriate icon.

KDE and XFCE, used in Kubunt and Xubuntu respectively, and installable on Ubuntu, have traditional panels that can be relocated to any of the 4 sides of a display.

> 


[LIST]
[*]A desktop-switcher on the panel that allows me to mouse-over the switcher, and use the mouse wheel to switch desktops OR allows me to use the mouse wheel to switch desktops while hovering/focused out on desktop blankspace. 
[/LIST]

KDE and XFCE and LXDE both allow scrolling between workspaces with the mouse wheel. Typically enabled by default in KDE and LXDE, and not enabled in XFCE. 

A windows list indicator may be available for Unity; you'd need to look around.  However, Unity is a Compiz plugin and Compiz allows workspace changing with the mouse wheel.  You need to add the 'compizconfig-settings-manager' package and launch it to configure and enable the appropriate settings. (Don't mess with the 'Unity Plugin' section, though.)

> 


[LIST]
[*]The volume/mute keys on my Sun Type7 USB keyboard to work 
[/LIST]

Obscure hardware will likely require third-party driver support. If that functionality is enabled in the kernel, it should work out-of-the-box.

> 


[LIST]
[*]Min/Max/Close buttons on the right hand side of the window bar. 
[/LIST]

Buttons default to the right in KDE, XFCE, LXDE. They are fixed to the left in Unity.

> 


[LIST]
[*]A traditional style "main menu" rather than a unity/windows8/android type menu. 
[/LIST]

A selection of traditional menu styles is available in KDE, XFCE, LXDE.


KDE, XFCE and LXDE are all available in the standard Ubuntu repositories. They have been packaged in various ways, some that include the Kubuntu/Xubuntu/Lubuntu desktops and some that do not. You can search all of the repos here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

You may also wish to consider the Ubuntu MATE distribution. MATE is a mild fork of the defunct Gnome 2 project.  It will meet all your requirements.

---

### Post by ajgreeny on 2015-06-29
To avoid adding all the default packages of Xubuntu, except the file-manager,  with your new desktop you could have installed **xfce4** instead of **xubuntu-desktop**

Having more than one full DE can make for confusing menus if you are not careful, but as long as you're happy, all is well.

I use Xubuntu 14.04 and have an auto-hiding left side panel stuffed full of launchers; it works brilliantly for my way of working, and sounds just like the way you want your desktop.

---

### Post by gentimjs2 on 2015-06-29
I snagged the xubuntu-desktop meta package as Yeti suggested, and am using the xfce (as opposed to xubuntu) desktop from the session manager list - so far, it's giving me 99% of what I want.
The volume/logout buttons on my sun KB "just worked", the panel is configurable like I want, and the desktop-switcher mousewheel functionality is adequate. It'll probably take me a little while to settle on a window manager theme, but with so many to choose from it shouldn't be hard to find one. 

Of course, as a few mentioned, with so many desktop environments installed my "settings" menu is .. cluttered .. but that isn't really a big deal since 99% of the time I'll only be using 8 or 9 apps, launched from the panel. 

Thanks again folks, great tips.

---

### Post by v3.xx on 2015-06-29
Heres a comparison

[http://packages.ubuntu.com/vivid/xubuntu-desktop](http://packages.ubuntu.com/vivid/xubuntu-desktop)

[http://packages.ubuntu.com/vivid/xfce4](http://packages.ubuntu.com/vivid/xfce4)

---

