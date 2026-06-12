---
title: "windows come out of cube in beryl?"
date: 2007-11-16
forum: Desktop Effects &amp; Customization
---

### Post by Codix121 on 2007-11-16
Is it possible to make the windows hover away from the cube in Beryl?
I know compiz has it.

[http://goberylgo.blogspot.com/2006/12/segunda-imagen-en-el-blog-skydome.html](http://goberylgo.blogspot.com/2006/12/segunda-imagen-en-el-blog-skydome.html)

something like that one,
where the windows hover out.
Thanks guys.

---

### Post by PatrickFisher on 2007-11-16
Yes, it is definitely possible. When I had Feisty I ran Beryl with this effect. Unfortunately, I've moved to Gutsy and CF so can't give you the exact directions.

It should be under "Visual effects" or something to that effect, then "3D effects". Change "Window Spacing" or something of the like to a higher number, and you should get the desired effect.

If "3D effects"  is not available, perhaps you have to install the unsupported plugins.

---

### Post by applehead on 2007-11-16
I've got the same problem. as far as I know there's no way of doing it with gusty and CF

---

### Post by PatrickFisher on 2007-11-16
> **applehead said:**
> I've got the same problem. as far as I know there's no way of doing it with gusty and CF

No, he's talking about Beryl. It's very easy to do in CF.

System>Preferences>Advanced Desktop Effect Setting

Find 3D windows under "effects", change the setting to what you want, activate and go.

---

### Post by scorp123 on 2007-11-16
> **PatrickFisher said:**
>  System>Preferences>Advanced Desktop Effect Setting

Find 3D windows under "effects", change the setting to what you want, activate and go. I don't have that here (in "Gutsy"). Which packages did you download? Or did you use any third-party repos?

---

### Post by 469tc on 2007-11-16
> **PatrickFisher said:**
> No, he's talking about Beryl. It's very easy to do in CF.

System>Preferences>Advanced Desktop Effect Setting

Find 3D windows under "effects", change the setting to what you want, activate and go.

I am also having the opposite effect. had it working perfectly with 7.04 and Beryl but don't have the option for 3D windows with CF and 7.10. Am I missing something simple?:confused:

---

### Post by PatrickFisher on 2007-11-16
> **scorp123 said:**
> I don't have that here (in "Gutsy"). Which packages did you download? Or did you use any third-party repos?

You need to install compizconfig-settings-manager

While you're at it, Emerald and the extra plugins are nice to have

---

### Post by PatrickFisher on 2007-11-16
> **469tc said:**
> I am also having the opposite effect. had it working perfectly with 7.04 and Beryl but don't have the option for 3D windows with CF and 7.10. Am I missing something simple?:confused:

You probably have to install more plugins. I have compiz-fusion-plugins-unofficial compiz-fusion-plugins-extra and compiz-fusion-plugins-main installed.

One of those should include 3D windows. I'm sorry, I don't know which one.

---

### Post by 469tc on 2007-11-16
> **PatrickFisher said:**
> You probably have to install more plugins. I have compiz-fusion-plugins-unofficial compiz-fusion-plugins-extra and compiz-fusion-plugins-main installed.

One of those should include 3D windows. I'm sorry, I don't know which one.

All of the above mentioned  are already installed as well as the settings manager. I also have Emerald with plugins installed. I just don't understand??? If it means anything I also have another bootable iteration of 7.10 on a separate hard drive with the same issue... Maybe the video card? Wouldn't think so though 'cause it is a 7900GTX and it was working fine with 7.04...??

---

### Post by 469tc on 2007-11-16
> **PatrickFisher said:**
> You probably have to install more plugins. I have compiz-fusion-plugins-unofficial compiz-fusion-plugins-extra and compiz-fusion-plugins-main installed.

One of those should include 3D windows. I'm sorry, I don't know which one.

Come to think of it I also have some other rather strange problems. Water and rain effect don't work properly. Screen just dims when hitting shift+f9. Also in the right lower part of the desktop where the contents of the 4 cubes are displayed never change when changing desktops. If I click on one of the empty cubes the entire desktop aside from wallpaper just disappears. I have to use Control+Alt+Backspace to regain icons, taskbars, etc. I am getting just a bit frustrated with CF...Think it might have something to do with restricted graphics card drivers? I made a few changes to Screens and Graphics settings and had some strange issues. Finally able to resolve but don't remember exactly what I did. Don't know if this is pertinent or not. Anyway, thanks for all of your input! 'Tis greatly appreciated!:)

---

### Post by PatrickFisher on 2007-11-16
> **469tc said:**
> Come to think of it I also have some other rather strange problems. Water and rain effect don't work properly. Screen just dims when hitting shift+f9. Also in the right lower part of the desktop where the contents of the 4 cubes are displayed never change when changing desktops. If I click on one of the empty cubes the entire desktop aside from wallpaper just disappears. I have to use Control+Alt+Backspace to regain icons, taskbars, etc. I am getting just a bit frustrated with CF...Think it might have something to do with restricted graphics card drivers? I made a few changes to Screens and Graphics settings and had some strange issues. Finally able to resolve but don't remember exactly what I did. Don't know if this is pertinent or not. Anyway, thanks for all of your input! 'Tis greatly appreciated!:)

Ok, well, here we go:

1) Water effect

Your video card is likely not supported. Water Effect sucks up specs like nobody's business. Sorry, but it's not likely fixable

2) "Changing desktops"

This is easily fixed. Go to Preferences>Advanced Desktop Effects Settings

Go to "General Options, Desktop Size". Change "Number of Desktops" to "1" and adjust "Horizontal (or Vertical) Virtual Size" to the number of desktops you want.

That should cover it.

---

### Post by PatrickFisher on 2007-11-16
> **469tc said:**
> All of the above mentioned  are already installed as well as the settings manager. I also have Emerald with plugins installed. I just don't understand??? If it means anything I also have another bootable iteration of 7.10 on a separate hard drive with the same issue... Maybe the video card? Wouldn't think so though 'cause it is a 7900GTX and it was working fine with 7.04...??

Oops, my mistake.

This thread will help you out:

[http://ubuntuforums.org/showthread.php?t=585491](http://ubuntuforums.org/showthread.php?t=585491)

---

### Post by scorp123 on 2007-11-17
> **PatrickFisher said:**
> You need to install compizconfig-settings-manager. While you're at it, Emerald and the extra plugins are nice to have I have all those packages but none of that stuff provides e.g. the "3D windows" effect. I am going to checkout the link you posted in one of your postings above, maybe that will help.

---

### Post by quanumphaze on 2007-11-29
Sorry everyone but the 3D Windows plugin is not included in the Gutsy Compiz Fusion packages.
It is considered an experimental plugin from the Beryl-Fusion merger and had some bugs so they didn't include it yet.
Here's a link to the CF wiki:
[http://wiki.compiz-fusion.org/Plugins/Cube#3d]("http://wiki.compiz-fusion.org/Plugins/Cube#3d")
> The **3D Windows** plugin causes the windows on the cube to lift off the cube at different levels as the cube shrinks away from them to show the space between them and their stacking order. The shrinking cube is an updated effect to compensate for clipping of the windows with the **Cube Reflection** plugin when rotating off axis. As it is being re-written, it is currently part of the Compiz Fusion, but not yet in any plugin set.
Some instructions to install it [here.]("http://wiki.compiz-fusion.org/Install/PluginsFromGit") I haven't personally tried it so I can't tall you if it works. Oh and **USE AT YOUR OWN RISK.**

---

### Post by frank392 on 2007-11-30
Hi Scorp123,
Just wanted to say hi, glad to see you!
Take care and have a great Day :)

---

