---
title: "flash help?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by higherness on 2005-10-17
hello everyone, 

ive had 5.04 since august, and ive had trouble with certain sites that use text on flash.

ie. [www.deathcabforcutie.com](www.deathcabforcutie.com)

i cant read any of the text.

any help?

thanks.

---

### Post by kayas80 on 2005-10-17
I use Firefox version 1.07 and can read the text on that website with no problems. I am using flashplayer-mozilla - available from Synaptic.

To see what Flash plugin you are using open Firefox and in the address bar type *about:Plugins*

You could try removing your current Flash player and installing flashplayer-mozilla.

---

### Post by racecat on 2005-10-17
[QUOTE=higherness]hello everyone, 

ive had 5.04 since august, and ive had trouble with certain sites that use text on flash.

ie. [www.deathcabforcutie.com](www.deathcabforcutie.com)

i cant read any of the text.

any help?

thanks.[/QUOTE]

I had a problem like this with flash when I installed from synaptic. The problem showed up with my roadrunner home page. The solution - load it from firefox. In case you're not familiar, Tools > Extensions > More Extensions. Select Plugins on the screen and follow the Flash directions. Also, you need msttcorefonts. Hope this helps.

Bill

---

### Post by higherness on 2005-10-19
thanks guys.

---

### Post by kayas80 on 2005-10-19
[quote=higherness]thanks guys.[/quote]

Did you get it working in the end, and if so how?

---

### Post by lespedeza on 2005-10-19
I, too, was having similar problems with text not displaying in flash apps.  I installed the msttcorefonts and that solved my problem.  Thanks for the advice.

lespedeza

---

### Post by racecat on 2005-10-19
[QUOTE=lespedeza]I, too, was having similar problems with text not displaying in flash apps.  I installed the msttcorefonts and that solved my problem.  Thanks for the advice.

lespedeza[/QUOTE]

Very happy to give a little back.

Bill

---

### Post by lik3n on 2005-11-09
Good band.

---

### Post by [HUN]Levente on 2005-11-15
I installed msttcorefonts and it solved nothing. I still don't have text in flash. What could be the problem?

in msttcorefonts.spec it says:

# mandrake 8.2 users should install the 'freetype-tools' package and change
# the define below to '/usr/sbin/ttmkfdir'

I don't have that file neither in bin nor in sbin, so?

---

### Post by racecat on 2005-11-15
[QUOTE='[HUN]Levente']I installed msttcorefonts and it solved nothing. I still don't have text in flash. What could be the problem?

in msttcorefonts.spec it says:

# mandrake 8.2 users should install the 'freetype-tools' package and change
# the define below to '/usr/sbin/ttmkfdir'

I don't have that file neither in bin nor in sbin, so?[/QUOTE]

That probably isn't an issue, unless, of course, you are using mandrake 8.2.  I'm really not an expert, but it does sound like a missing font problem. Do you have gsfonts installed? I've seen gsfonts-x11 mentioned, also.

Okay, I tried the deathcabforcutie site (good tunes BTW) and had no trouble. I perused my Synaptic list for installed packages after a search under font. Here is a list of what I have installed:

fontconfig
gsfonts
libfontconfig1
mplayer-fonts
msttcorefonts
ttf-freefont
ttf-indic-fonts
ttf-malayalam-fonts
xfonts-100dpi
xfonts-75dpi
xfonts-base
xfonts-scalable
x-ttcidfont-conf

Hope this helps. Good luck.

Bill

---

### Post by ragman on 2005-11-17
The one that did the trick for me was gsfonts-x11. I had this problem and originally thought it was Java related but it was the missing gsfonts-x11. I installed Flash from Macromedia and during the install it said Flash requires gsfonts and gsfonts-x11 which can both be installed with Synaptic Package Manager. 

Hope this helps! It took me 2 days of installing and re-installing Java. 

By the way this Java Install works properly.  To setup system and Firefox Plug-In. [http://www.ubuntuforums.org/showthread.php?t=76754&highlight=java+Sun]("http://www.ubuntuforums.org/showthread.php?t=76754&highlight=java+Sun")
You can test your java install here. [http://www.java.com/en/download/installed.jsp]("http://www.java.com/en/download/installed.jsp") 
Just click on verify install button.

---

### Post by [HUN]Levente on 2005-11-18
Sorry to say I have all of this packages installed, and I still can't see fonts in flashes... Any other idea?

---

### Post by CHUCKYCHUCK on 2005-11-19
that's weird i can read the text in the "deathcabforcutie" site, but i can't see a letter in the google analytics tool .... :s ( neither when i try to configure flashplayer by Rclicking=>parameters )

---

### Post by shadow07 on 2005-11-25
I cannot see any of the fonts within the Flash Config tool (right-click -> Preferences).  Nor, can I see text on certain web pages.

I have all of these font packages installed and more:

fontconfig
gsfonts
libfontconfig1
mplayer-fonts
msttcorefonts
ttf-freefont
ttf-indic-fonts
ttf-malayalam-fonts
xfonts-100dpi
xfonts-75dpi
xfonts-base
xfonts-scalable
x-ttcidfont-conf

I found a forum topic on Macromedias site:  [http://www.macromedia.com/cfusion/webforums/forum/messageview.cfm?catid=184&threadid=961824&highlight_key=y&keyword1=fonts]("http://www.macromedia.com/cfusion/webforums/forum/messageview.cfm?catid=184&threadid=961824&highlight_key=y&keyword1=fonts")
Which has a link to a Gentoo forum where someone was having similar problems.[http://forums.gentoo.org/viewtopic-t-196111-highlight-flash+fonts.html]("http://forums.gentoo.org/viewtopic-t-196111-highlight-flash+fonts.html")

Now, this is a completely brand new install of 5.10, and I have used Automatix to install packages.  

Has someone experienced the same problem as I am and can provide a fix?

---

### Post by [HUN]Levente on 2005-12-08
[QUOTE='[HUN]Levente']Sorry to say I have all of this packages installed, and I still can't see fonts in flashes... Any other idea?[/QUOTE]

I solved this problem. The ATI driver installer changes the xorg.conf, and does not write the Font paths in it. I just backed up my original xorg.conf, and after installing the ATI driver, I copied the Font paths back, and now I can see text in flash :)

---

### Post by shadow07 on 2005-12-10
[QUOTE='[HUN]Levente']I solved this problem. The ATI driver installer changes the xorg.conf, and does not write the Font paths in it. I just backed up my original xorg.conf, and after installing the ATI driver, I copied the Font paths back, and now I can see text in flash :)[/QUOTE]

Can you please provide more info on this, as I do have an ATI video card in my machine.

---

