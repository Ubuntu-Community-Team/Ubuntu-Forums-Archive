---
title: "Can't change keyboard language on xfce/"
date: 2011-06-06
forum: Desktop Environments
---

### Post by ph03nix on 2011-06-06
I installed xfce today(i don't like unity and want to try xfce) and i can't find how to change keyboard language.I want to switch from english to greek with alt+shift and visa versa.Also searching on the greek forum  i tried this:

1.    cat /etc/X11/xorg.conf 

2.    setxkbmap -option grp:switch,grp:alt_shift_toggle us,gr

3.    sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

4.    sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

and on the window that opened i added this:

5.Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us,gr"
    Option         "XkbVariant" ",extended"
    Option         "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection

But after i logged out/in mozilla won't maximize.If i try to maximize i get an error.Also i cannot run commands on terminal.Terminal opens but when i hit enter the command is not taken!(it's like i didn't hit enter)

---

### Post by d0.higgs on 2011-08-15
I did not like unity, too and I am having the same problem.
Could you solve your problem? How?

I want to use both English and Arabic. I am used to use the left window button to switch between the two layouts. Any hint?

thanks

---

### Post by ph03nix on 2011-08-15
> **d0.higgs said:**
> I did not like unity, too and I am having the same problem.
Could you solve your problem? How?

I want to use both English and Arabic. I am used to use the left window button to switch between the two layouts. Any hint?

thanks


I did not manage to solve it,and abandoned xfce cause that really annoyed me.Also,if you just want to get rid of unity when ubuntu starts,to the prompt where you are asked to enter your password to login,down and a bit right change the value to "Ubuntu Classic" or something like that. I think that this way you can at least get rid of Unity.(do not login; firstly make the change then login.)

---

### Post by jastonas on 2011-10-18
I too changed to xfce because of unity!

Still can't find a way to change layouts. Is it that hard??

---

### Post by jastonas on 2011-10-18
I am going to double post.

**SOLVED**

I don't know how because I don't know at which point it worked but I'll give you all the steps I did.

Instructions (for greek):

a) sudo apt-get install language-selector
b) Open Language Selector and install Greek
c) settings > input method switcher > use ibus
d) settings > keyboard input methods > Tick all 3 just to help you have the icon.
e) System > Run ibus
e) setxkbmap -option grp:switch,grp:alt_shift_toggle us,gr

And now, for some reason, I can write Greek. &#932;&#949;&#963;&#964;... &#947;&#961;&#940;&#966;&#949;&#953; &#956;&#953;&#945; &#967;&#945;&#961;&#940; :)

---

### Post by ankspo71 on 2011-10-18
Hi,
We can also install the 'xfce4-xkb-plugin' keyboard switcher applet for XFCE, which is also a part of the 'xfce4-goodies' package that gives us more panel plugins/applets. 

Here is the homepage [http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-xkb-plugin)

---

### Post by TBeholder on 2011-10-23
Another scarred-for-life-by-Unity happy Xubuntu user here. :P
> **jastonas said:**
> **SOLVED** [...]
a) sudo apt-get install language-selector
b) Open Language Selector and install Greek
c) settings > input method switcher > use ibus
> **ankspo71 said:**
> Hi,
We can also install the 'xfce4-xkb-plugin' keyboard switcher applet for XFCE, which is also a part of the 'xfce4-goodies' package 
To choose the set of supported languages, there's "Language Support" in category "Setup" (gnome-language-selector). It also allows to select input methods (iBus, etc), but that's all.
To set up layout and keys switching between them, add "Keyboard Layout plugin" on a panel and set up preferences in it. There's a choice *which* of layouts for that language to use, too.
So actually both are needed, though normally the first one is already used on installation stage.

---

