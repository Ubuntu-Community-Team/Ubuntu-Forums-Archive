---
title: "gtk 1.x ugly fonts"
date: 2005-04-12
forum: Desktop Environments
---

### Post by James Brown on 2005-04-12
Hi

Apps that use gtk1.x, like Amule, Xmms (options) looks very bad in my machine, with huge fonts. I've tried gtk-theme-switch and didn't worked. Tried to edit .gtkrc and nothing. What can I do?

Thanks

---

### Post by mathjazz on 2005-04-12
Do you have a screenshot?

You should know that fonts in gtk1 are not antialiase, however they sould not be bigger than the ones of gtk2.

---

### Post by James Brown on 2005-04-12
[QUOTE=mathjazz]Do you have a screenshot?

[/QUOTE]

Here it goes...

---

### Post by Spudgun on 2005-04-12
I have the same problem in apps like 'nmap Frontend', looks really ugly :/

---

### Post by mathjazz on 2005-04-12
[QUOTE=James Brown]Here it goes...[/QUOTE]

You don't have antialiased fonts at all!

But I'm not sure what did you do wrong. Have you installed 'msttcorefonts' package? Do you have antialiased fonts enabled (Sys -> Pref -> Fonts)?

---

### Post by James Brown on 2005-04-12
[QUOTE=mathjazz]You don't have antialiased fonts at all!

But I'm not sure what did you do wrong. Have you installed 'msttcorefonts' package? [/QUOTE]Yes. Something is wrong with that?

[QUOTE=mathjazz] 
Do you have antialiased fonts enabled (Sys -> Pref -> Fonts)?[/QUOTE]No

---

### Post by Spudgun on 2005-04-12
Here's a screen shot of mine...

---

### Post by Spark* on 2005-04-12
Yep, at some point during Hoary they broke. Before they were clean and small (not anti-aliased, but okay looking), now they are large and jagged.

---

### Post by sethmahoney on 2005-04-12
[QUOTE=mathjazz]You don't have antialiased fonts at all!

But I'm not sure what did you do wrong. Have you installed 'msttcorefonts' package? Do you have antialiased fonts enabled (Sys -> Pref -> Fonts)?[/QUOTE]

I do have fonts antialiased, and I have installed the msttcorefonts package, but I have the same issue with aMule.

(Mine also happened after a Hoary update - I think it was an aMule update, but I'm not entirely sure.)

---

### Post by gunnyman on 2005-04-12
I have same issues with Mplayer.

---

### Post by Spudgun on 2005-04-13
Any ideas how we can fix this?

---

### Post by mathjazz on 2005-04-13
You cannot fix this for gtk1 apps (mplayer, xmms, amule ...), because gtk1 does not support antialiasing. However for gtk2 you must enable font antialiasing (sys - pref - fonts).

---

### Post by felix.rommel on 2005-04-13
Hi,

1.) open your text editor and write the following line:

[B][FONT=Courier New]
include "/home/YOUR_USER_NAME/.gtkrc.mine"[/FONT][/B]

replace YOUR_USER_NAME with your login name and save the file with the following name in your home directory:

**[FONT=Courier New].gtkrc-1.2-gnome[/FONT]**

2.) Create a new text file in your editor and write the following lines:

[B][FONT=Courier New]
style "default-text" {
      fontset = "-adobe-helvetica-medium-o-normal--10-100-75-75-p-57-iso10646-1,\
                                          -*-r-*-iso10646-1,*"
}
class "GtkWidget" style "default-text"[/FONT]
[/B]

save the file with the following name in your home directory:

**[FONT=Courier New].gtkrc.mine[/FONT]**

This uses Helvetica 10 Points as font. Have a look in the file

/usr/X11R6/lib/X11/fonts/75dpi/fonts.dir

For more bitmap fonts to choose for your Gtk1 app. You can also use TTF fonts for your Gtk1 app but I first have to look where I get the information for old X font style definition.

Greetings

---

### Post by Spudgun on 2005-04-13
Great, things are starting to look better now :)

Another question though, how does Fedora Core 3 get gtk apps to looks so nice?

Thanks in advance,
Spudgun

---

### Post by felix.rommel on 2005-04-13
[QUOTE=Spudgun]Great, things are starting to look better now :)

Another question though, how does Fedora Core 3 get gtk apps to looks so nice?

Thanks in advance,
Spudgun[/QUOTE]

I think they use TTF fonts in their GTK apps. With the upper instruction you can use also TTF fonts. I found the definition under SUSE 9.2 it should be fine with .gtkrc.mine:

[B]
[FONT=Courier New]style "default-text" {
      fontset = "-bitstream-bitstream vera sans-medium-o-normal--10-0-0-0-p-0-iso10646-1,\
			-adobe-helvetica-medium-o-normal--10-100-75-75-p-57-iso10646-1,\
                                          -*-r-*-iso10646-1,*"
}
class "GtkWidget" style "default-text"
[/FONT][/B]

this uses Bitstream Vera TTF font which should also be better than helvetica. Ubuntu seems not to create old fonts.dir files for truetype fonts that's why it's a little bit difficult to get the truetype font information in old X syntax.

---

### Post by gunnyman on 2005-04-13
yet another reason I LOVE this distro.
Excellent community with GREAT help!  The tip above fixed me right up!

---

### Post by James Brown on 2005-04-13
Thanks for the help! :grin: 

Now that I've learned how to do, let me contribute...

Try for .gtkrc-1.2-gnome2:

[B]include "/usr/share/themes/Industrial/gtk/gtkrc"

include "/home/"your_login_here"/.gtkrc.mine"[/B] 

and for .gtkrc.mine:

[B]style "default-text" {
 fontset = "-adobe-helvetica-medium-r-normal-*-*-80-*-*-p-*-iso10646-1"
 }
 class "GtkWidget" style "default-text"[/B] 

This gives me a nice looking "Industrial" theme with very small fonts. Maybe you'll need to install the theme and/or the font from the repositories.

---

### Post by burlap on 2005-04-14
For me changing default locale from UTF to iso did the trick... (As I was missing also some characters in mc, I'll just stick to iso and wait until everything is UTF compatible...).

---

### Post by Teren on 2005-04-14
[QUOTE=burlap]For me changing default locale from UTF to iso did the trick... (As I was missing also some characters in mc, I'll just stick to iso and wait until everything is UTF compatible...).[/QUOTE]
 I know this might be a stupid question: I know how to change the locale in a terminal, but it only works for apps ran from the same terminal, how do you make it work in X?

---

### Post by burlap on 2005-04-14
I think that you should:
```
sudo dpkg-reconfigure locales
```
There you may choose locales with different encoding. When they're reconfigured, you probable need to reboot (or at least restart X, but I think in Warty a complete reboot was necessary). In gdm you'll get extra languages in the language menu.

---

### Post by sethmahoney on 2005-04-27
[QUOTE=burlap]I think that you should:
```
sudo dpkg-reconfigure locales
```
There you may choose locales with different encoding. When they're reconfigured, you probable need to reboot (or at least restart X, but I think in Warty a complete reboot was necessary). In gdm you'll get extra languages in the language menu.[/QUOTE]
 Another solution is to install the new aMule.  Instructions here: [http://ubuntuforums.org/showthread.php?t=30074](http://ubuntuforums.org/showthread.php?t=30074)

---

