---
title: "Enabling Bitmap Fonts - Copy"
date: 2005-10-13
forum: Desktop Environments
---

### Post by a monkey on 2005-10-13
I am re-posting this, because I had posted it in a forum that is now closed.

I recently installed the package "xfonts-artwiz" and noticed that the fonts in the package did not show up under System > Preferences > Font. I was told to enable bitmap fonts by either editing /etc/fonts/local.conf or running the command "dpkg-reconfigure fontconfig". My system appeared to be lacking the file "/etc/fonts/local.conf", so I was forced to do the latter. I ran "sudo dpkg-reconfigure fontconfig", chose to enable bitmap fonts, and restarted X. To my dismay, the artwiz fonts still didn't show up under System > Preferences > Font. Did anyone ever have a similar problem? Can anybody help? Any help appreciated. Thanks.

---

### Post by johannes on 2005-10-13
I haven't gotten the "xfonts-artwiz" package to work in Gnome in niether Hoary or Breezy. As I didn't find any info on how to do it I installed them from source. That was really simple and it worked great.

1. Get the source package at [http://artwizaleczapka.sourceforge.net/](http://artwizaleczapka.sourceforge.net/). Note that there are currently three character sets avalible, English, German and Swedish.

2. Extract it in your home folder.

3. In terminal, make a new folder in /usr/share/fonts/type1/gsfonts/ called artwiz. I guess you could put them somewhere else in the /usr/share/fonts folder, but this works for me.
```
sudo mkdir /usr/share/fonts/type1/gsfonts/artwiz
```
4. Move the artwiz fonts there:
```
sudo mv ~/artwiz-aleczapka-en-1.3/*.* /usr/share/fonts/type1/gsfonts/artwiz
```
(It seems you have already done the next steps, but I'll include it here anyway.)

5. Run "sudo dpkg-reconfigure fontconfig" in terminal and choose to enable bitmap fonts.

6. Restart X (Ctrl+Alt+Backspace)

Now you should be able to choose them in System > Preferences > Font.

:)

---

### Post by a212359 on 2005-12-02
I just wanted to mention (since I just wasted a lot of time trying to figure this out) that the above method will get the fonts to show up in System-Preferences-Font, however if you try to use the fonts for a terminal (e.g. in  .Xdefaults, or as in "$xterm -fn snap" or whatever) X won't be able to find the fonts. What worked for me was:

$xset fp+ /usr/share/fonts/type1/gsfonts/artwiz-aleczapka-en-1.3/

---

### Post by docomo on 2005-12-03
[FONT=monospace]I installed the xfonts-artwiz package, then I made a link like this:

[/FONT][FONT=monospace]sudo ln -s /usr/X11R6/lib/X11/fonts/misc [/FONT]/usr/share/fonts/type1/gsfonts/artwiz

...and it works.

Bitmap fonts have to be enabled, see the posts above.

---

### Post by Strider420 on 2005-12-19
Has anyone been able to fix the fact that this causes firefox to look crappy?

---

### Post by funkyade on 2006-06-10
Have had bitmap fonts enabled for a while and running without probs, although I haven't been using any for my terminal font (except Terminus).

When I try to enable a bitmap font, i.e. an artwiz one like lime or gelly, by selecting it using the font selector for whatever thing i'm using the application crashes completely.

I've been able to use them in stuff like GIMP fine but when I try to use them for apps they force the app to crash...

Anyone got any ideas on this one... and yes I have reconfigured fontconfig etc...!

:-(

---

