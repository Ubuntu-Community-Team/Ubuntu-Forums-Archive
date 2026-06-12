---
title: "Trying to make the gnome desktop look nice(r)"
date: 2006-08-23
forum: Desktop Environments
---

### Post by mwob on 2006-08-23
Hi,

I've played around with some settings to get Gnome look nicer in ubuntu - it does look a lot nicer now its got to be said (I changed the DPI to 96 I think, and installed the tahoma font).

Anyway, I still can't get it properly sorted. Take a look at this screenshot:

[http://img129.imageshack.us/my.php?image=screenshotdn9.jpg]("http://img129.imageshack.us/my.php?image=screenshotdn9.jpg")

Firstly, the radio buttons in google and any other application look a bit rubbish! Secondly, some apps I launch look like that dark grey one you can see under firefox....why do those (older) apps look so bad?

Many thanks!

Matt

---

### Post by kerry_s on 2006-08-23
You should grab a theme for firefox from the firefox site. The colors can be changed in the theme section, there's 3 choices color,windows,icons. Themes are really easy to install in gnome you just drag and drop in the theme window. Visit gnomelook.org to grab some gnome eye candy. Also check out the how to section on getting eye candy in gnome.

---

### Post by mwob on 2006-08-25
Thanks for the reply, but they don't really help my specific issue.... Those radio buttons look naff in any applicaiton, not just firefox. Chaning the theme in ubuntu doesn't seem to make a difference either.

As for those weird dark-grey applications like the one in the screenshot, I still cant make them look any nicer....

---

### Post by Metacarpal on 2006-08-25
What resolution is your screen set to?

---

### Post by llamakc on 2006-08-25
You have two issues: first is with the widgets inside of Firefox. You could try different gtk-engines to get a different look. 

Give an example of something you do like and people may be able to help you easier.

Second: that 'dark-gray' window for pppconfig is probably using a different toolkit to draw the windows, something like tk or gtk1. Those programs are just ugly to look at it. Maybe somebody knows of a pppconfig program that uses gtk2?

---

### Post by mwob on 2006-08-26
> **llamakc said:**
> You have two issues: first is with the widgets inside of Firefox. You could try different gtk-engines to get a different look. 

Give an example of something you do like and people may be able to help you easier.

Second: that 'dark-gray' window for pppconfig is probably using a different toolkit to draw the windows, something like tk or gtk1. Those programs are just ugly to look at it. Maybe somebody knows of a pppconfig program that uses gtk2?

Thanks - I know little about linux at the momemnt, I didn't know about the different toolkits for UI rendering in gnome. The radio buttons and checkboxes in most (if not all) ubuntu apps are very nice and look fine. Its just when I load firefox and any websites that render radio buttons on the screen look pretty bad to me (just blocky and nafff) - I'm confused as to why they're not the same as all my non-firefox apps... In windows, if IU changed the windows theme then all radio buttons that are rendered anywhere are affected.

So... does firefox render UI elements from websites using different engines and/or toolkits? and if so how do I change them?

---

### Post by llamakc on 2006-08-26
No, Firefox widgets will be uniform according to the theme you're using. Try different themes for Firefox (TOOLS | THEMES) and give different gtk-engines (in System | Preferences | Themes) a try also.

---

### Post by mejy on 2006-08-26
> **mwob said:**
> Thanks - I know little about linux at the momemnt, I didn't know about the different toolkits for UI rendering in gnome. The radio buttons and checkboxes in most (if not all) ubuntu apps are very nice and look fine. Its just when I load firefox and any websites that render radio buttons on the screen look pretty bad to me (just blocky and nafff) - I'm confused as to why they're not the same as all my non-firefox apps... In windows, if IU changed the windows theme then all radio buttons that are rendered anywhere are affected.

So... does firefox render UI elements from websites using different engines and/or toolkits? and if so how do I change them?

Contrary to what has been said, although widgets in firefox itself will render like most Gnome Apps, buttons and radio buttons on web pages won't

The fact is, they look very ugly on Linux and OS X by default.  However, if you don't mind a small number of sites having a few issues (I'm never had a problem with it, but I'm told there are some such websites) then you can use a CSS to improve their appearance.

Hacked widgets won't look the same as the rest of your applications, but they won't look all that bad.  Too apply this hack, go to Applications -> Accessories -> Terminal, and enter the following commands:

```
wget http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz
tar -xvzf firefox-form-widgets-ots.tar.gz
sudo cp /usr/lib/firefox/res/forms.css /usr/lib/firefox/res/forms.css.bak
cat firefox-form-widgets-ots/res/forms-extra.css | sudo tee --append /usr/lib/firefox/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets-ots/res/form-widgets /usr/lib/firefox/res
rm -rf firefox-form-widgets-ots
```

Now, if you're looking to improve the appearance of your other applications, take the following steps:

Go to System->Preferences->Fonts.  Change Application Font to Size 9.  You might want to change the font, but if it's any bigger you may have icon issues.

If your looking to improve the appearance of Gnome, might I suggest the [Murraine Engine ]("http://www.gnome-look.org/content/download.php?content=42755&id=2"), [Metacity (Window Border)]("http://www.kernow-webhosting.com/~bvc/theme/mcity/Murrine.tar.gz") and[ Color Schemes]("http://www.kernow-webhosting.com/~bvc/theme/gtk/murrine/") (needed to use the engine).

Many more great themes and icons etc.  can be downloaded from [Gnome-Look]("http://www.gnome-look.org/index.php?xsortmode=new&page=0").

Note:

To install a metacity theme, download it and drag it into the theme manager (System->Preferences->Themes).  Do the same for a Color Scheme/GTK Theme or an Icon Set.

For a theme engine, download it and open it.

Hope this helps.

---

### Post by llamakc on 2006-08-26
Thanks for the howto mejy. I didn't realize this about the widgets.

---

### Post by llamakc on 2006-08-26
mwob, take mejy's advice: this made some of the widgets much better to look at.

---

### Post by mejy on 2006-08-26
There was an old how to about it for breezy or horay... i forget which.  All that needs to be changed for Dapper is some of the paths.  I might make a small zenity script and post a how to.

Oh ye - remember to do this each time you update firefox.

---

### Post by mwob on 2006-08-26
I'll give it a go and report back - thanks for the info guys!

---

### Post by mwob on 2006-08-28
mejy,

Thanks very much - forefox looks muxh nicer with those css hacks applied :)

---

### Post by Omnios on 2006-08-28
Im not shure if this will work but it takes the ugly Gtk 1 theme and spices it up a bit. 
[http://ubuntuforums.org/showthread.php?t=107135](http://ubuntuforums.org/showthread.php?t=107135)

 Also this rounded pannel makes things look a bit better.
[http://ubuntuforums.org/showthread.php?t=108446](http://ubuntuforums.org/showthread.php?t=108446)

 I also use the ish theme from gnome-look.org that has rounded upper and bottom window frames.
[http://www.gnome-look.org/content/show.php?content=30859](http://www.gnome-look.org/content/show.php?content=30859)

 Cheers and good luck

---

