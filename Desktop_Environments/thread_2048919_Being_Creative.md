---
title: "Being Creative"
date: 2012-08-27
forum: Desktop Environments
---

### Post by DJNightchild on 2012-08-27
Hi guys,

I was thinking how to install a beautiful but lightweight Ubuntu Gui.
I was thinking what to install, as I browsed through different options like:

[LIST]
[*]gnome2
[*]gnome3
[*]kde
[*]unity
[*]xfce
[*]lxde
[*]mate
[*]fluxbox
[*]cinnamon
[/LIST]
And then i thought, maybe you guys would like to help me and being creative together,
So my question is, how would you compile your own ubuntu gui.

There are a few thing I want you to keep in mind:


[LIST]
[*]I use the Ubuntu Server OS (yes I know there is an alternative iso, but i find the server iso more stable).
[*]no use of sudo apt-get install ubuntu-desktop xubuntu-dekstop lubuntu-desktop etc. Start from scratch.
[*]It can be a Ubuntu Server or Desktop, what ever you like.
[*]tell us (as in every reader) what you did to create your ubuntu.
[*]have fun. That whats really important.
[*]It doesn't matter what you use; a virtual machine or a physical computer.
[*]OPTIONAL: A screenshot of what you did.
[/LIST]
Well since I started this post, this is what i did:

I use a x64 Machine

I installed fluxbox with xdm as display manager, and i used xorg.
```
sudo apt-get install fluxbox xdm xorg
```Then I installed thunar firefox xtrlock and file-roller to manage my files (and internet).
```
sudo apt-get install thunar tango-icon-theme lxappearance firefox file-roller
```Then I used lxappearance to set the icon theme for thunar.

after that i installed wine and configured it to install Microsoft Office 2007:

```
sudo apt-get install wine wine1.4 winetricks winbind wine-gecko1.4
rm -rf ~/.wine
export WINEARCH=win32
wineboot --update
```download msxml3 from [http://www.download.com]("http://download.cnet.com") and place it in ~/.cache/wine/winetricks/msxml3
```
winetricks dotnet20 msxml3 gdiplus riched20 riched30 vcrun2005
```Install Office 2007 using Wine Program Loader.

i configured xtrlock by editing the keys file in fluxbox
```
nano ~/.fluxbox/keys

[CENTER]------NANO------ 
Mod1 F12 :ExecCommand sleep 1 ; xtrlock
------NANO------
[LEFT]
Because of this, I can use alt f12 to lock my screen.[/LEFT]
[/CENTER]

```[CENTER][LEFT]

I downloaded the theme addr-pyramid form [URL="http://www.customize.org"]http://www.customize.org
[/URL] 
I found this picture somewhere on the interwebz:
[ATTACH]223253[/ATTACH]
and use this as wallpaper.

And that's it. I also downloaded virtualbox and this machine is now used for virtualization. 

(screenshot will follow).
[/LEFT]
[/CENTER]

---

