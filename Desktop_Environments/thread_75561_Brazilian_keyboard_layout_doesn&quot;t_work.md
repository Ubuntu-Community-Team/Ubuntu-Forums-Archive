---
title: "Brazilian keyboard layout doesn&quot;t work"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Marcos.Rufino on 2005-10-13
I"ve decided to try Ubuntu after I"d spent the last year with Fedora Core. I just downloaded Breezy Badger but I can"t make my keyboard works the way it should. 

In Fedora Core 4 this is as simple as choosing the Brazilian ABNT keyboard model and the Brazilian Portuguese layout. In Ubuntu I"m working on this 4 hours now!! 4 hours trying to accomplish a really simple thing! I can"t even find the "at" sign to write an e-mail. 
Man, is this a joke or what? 
I"ve also tried the "dpkg-reconfigure xserver-xorg" thing but with no success.

Does anyone have been successfull with this?

---

### Post by YourSurrogateGod on 2005-10-13
Do you have universe enabled?

If so, have you tried this?

System -> Administration -> Synaptic Package Manager

In Synaptic Package Manger...
Click on sections (bottom left group of buttons), then scroll down to the very bottom and select translations. From there install language-support-pt, language-pack-pt and language-pack-pt-base.

Then go to System -> Preferences -> Keyboard and select the language that you want.

Hope that helps...

---

### Post by ubuntumaneh on 2005-10-13
Try this in /etc/X11/xorg.conf

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkRules"       "xorg"
        Option          "XkbModel"      "abnt2"
        Option          "XkbLayout"     "br"
        Option          "XkbVariant"    "abnt2"
        Option          "XkbOptions"    "abnt2"
EndSection

Observe that its is XkRules and not Xkbrules. It will do.

---

### Post by YourSurrogateGod on 2005-10-13
You'll probably have to click on the Add button in Keyboard and select portugese from the list of keyboards... should work then...

---

### Post by neutro on 2005-10-13
Am I the only one with problems using the keyboard layout switch applet in Gnome? I can add layouts, but I cannot switch between them.

Also, if the brazilian keyboard is borked, it's not the only one: the ca_enhanced layout seems broken again (&#233;, &#231; don't work, and more importantly, nor does the alt key, preventing @, [, ], etc. and also preventing switching between virtual consoles). By chance, this layout is now correctly implemented using the ca layout, fr variant.

Also, to help the original poster, a workaround may involve using xmodmap. Does issuing "xmodmap /usr/share/xmodmap/xmodmap.pt" helps?

Edit: or xmodmap.br or any other layout available in /usr/share/xmodmap ...

---

### Post by Marcos.Rufino on 2005-10-14
Thank you guys!! I tried your suggestions and everything is working fine now.

---

### Post by Killer666 on 2005-10-14
[QUOTE=neutro]
Also, if the brazilian keyboard is borked, it's not the only one: the ca_enhanced layout seems broken again (é, ç don't work, and more importantly, nor does the alt key, preventing @, [, ], etc. and also preventing switching between virtual consoles). By chance, this layout is now correctly implemented using the ca layout, fr variant.
[/QUOTE]

I use xfce instead of kde, and the solution of System-->Preferences menu didn't work for me.
I experienced the same problem (no switch to virtual consoles, no @, etc...) and I solved it commenting out the alternative layout in /etc/X11/xorg.conf
I have a multimedia keyboard (btc9000) and italian layout.
This is the corrisponding section in my configuration file:

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option      "CoreKeyboard"
    Option      "XkbRules"  "xorg"
    Option      "XkbModel"  "btc9000"
    Option      "XkbLayout" "it"
#   Option      "XkbVariant"    "us"
EndSection

Hope this can be helpful to someone.

---

### Post by schlodowec on 2006-11-20
Brazilian keyboard is fine to me (abnt2), **except that** the keys "]" and "\" some other keys don't match.

As I change from brazilian, american and greek layouts too often, I made a simple script to correct the brazilian layout problem. Here it goes:

[FONT="Courier New"]setxkbmap -model abnt2 -layout br -variant abnt2 [/FONT]

Any other suggestions?

---

### Post by sesliu on 2006-11-20
well, I don´t have problems with brazilian keyboard, Only I choose type layout in system setup.

---

### Post by streeto on 2006-11-20
abnt2 layout has serious mood problems regarding locales. Here I was using iso-8859-1 (latin-1) on dapper, and some keys and accents stopped working when I upgraded to edgy. Setting my locale to pt_BR.UTF-8 solved most of my complains. It was discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=285259"). Currently, I only have problems in console, the (/?°) key is mute.

---

