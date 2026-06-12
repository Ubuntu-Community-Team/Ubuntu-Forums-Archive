---
title: "Help: Multiple (Non Programming) Languages &amp; Keyboard Layouts"
date: 2006-08-08
forum: Desktop Environments
---

### Post by cheuschober on 2006-08-08
First off I am very sorry if anyone has posted on this before a search on 'multiple language keyboard' yields hundreds of results on python, C(X), php, and the occasional 'change your locale' thread but it's nigh unto impossible to disambiguate.

So what I need is a little direction. I do business in two major languages: english and brazilian portugues (which is a latin font). At work on my windows machine I have the option of using the 'regional and language settings' to change the language I'm writing in via a hotkey. My US standard keyboard then becomes 'intelligent' and listens for proper key combinations (' + a = accented a) to display portugues specific characters.

Does such a tool exist for linux? Where should I look?

If it doesn't do I have alternatives? Is there a program that I can use to set up hotkeys of sorts to print the proper characters in whatever window is currently active?

I'm not looking to change my keyboard layout as I'm not actually changing keyboards, just the key combinations. Any and all help is, as always, appreciated.

~Chad

---

### Post by hopstah on 2006-08-08
under System > Preferences > Keyboard, you can change the entire layout of the keyboard, so that you can do alternate characters.  for example, i type a lot in german, and am equally familiar with the german layout as with english, so i set my keyboard up to switch between the layouts with Alt + Shift.  this turns my ; into an ä, for example.  but i don't know how to get combinations like that.

---

### Post by tsphan on 2007-02-22
i think you're trying to get an international keyboard setting. If you're using GNOME, this should be capable, like hopstah says, in one of the GUI system configuration settings.

If you're using XFCE or another window manager like I am, you can configure your xorg.conf settings to look somewhat like this:

Just edit your keyboard settings.

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,us"
        Option          "XkbVariant"    "basic,intl"
        Option          "XkbOptions"    "lv3:ralt_switch,grp:alts_toggle,grp_led:scroll"
EndSection

With these settings, when I press both ALTs, the shift lock light will turn out and I can then type in accented with the deadkeys that Windows uses.
' + e = é
" + o = ö
^ + i = î
Alt + , = ç (Helpful for me since I type in French a lot)



They can also be set with the terminal command:
setxkbmap -option lv3:ralt_switch,grp:alts_toggle,grp_led:scroll us,us basic,intl
Which is basically the same thing, except doing it in real time.

Read the file /usr/lib/X11/xkb/rules/base.lst for settings and options for your xorg and setxkbmap command.

---

