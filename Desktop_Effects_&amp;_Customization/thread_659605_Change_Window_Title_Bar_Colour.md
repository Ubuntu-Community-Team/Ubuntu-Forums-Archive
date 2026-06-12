---
title: "Change Window Title Bar Colour"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by Tech_Power888 on 2008-01-05
Hi there,

Just wanting to know how i can go about changing the colour on the title bar of active windows. I have looked around in System -> Preferences -> Appearance and I can't seem to find how to go about it. Obviously I can't change my theme settings or I lose my current theme. I have also looked in System -> Preferences -> Windows without any luck. Any help would be greatly appreciated! Thanks!

Ryan.

---

### Post by Tech_Power888 on 2008-01-06
i'll give it a friendly bump :)

---

### Post by Casual Fan on 2008-01-06
Right click on the desktop...click on "change desktop background"...select the tab for themes, and you can modify your theme there...click on "customize" i think.

---

### Post by gupta_sumesh63 on 2008-01-06
Right click on the menu bar, choose properties, backgrounds and then you can choose whatever you want.
Cheers

---

### Post by Casual Fan on 2008-01-07
> **gupta_sumesh63 said:**
> Right click on the menu bar, choose properties, backgrounds and then you can choose whatever you want.
Cheers

I think he wants application windows, not panels.

---

### Post by Tech_Power888 on 2008-01-07
Thanks for you interest and help guys,

what i'm actually referring to is the title bar at the very top of an active window - for example, the bar that contains "minimize" "maximise" and "close" buttons. mine has changed from the default colour to maroon. i can change the LOOK of it (eg glass, misty, classic, human etc) under the themes tab and then hitting customise, however there doesn't seem to be an option for changing the actualy colour of this bar. I am only bringing this up because for some reason (and we were very drunk that night, toying with my new installation) it changed from the regular colour to maroon. this isn't a bad  thing, i'm taking a liking to it...would just like to know how to change it, thats all :)

thanks in advance!

Ryan

---

### Post by Arcnsparc on 2008-01-07
try using emerald & compiz, they allow you to do pretty much anything to that bar.

---

### Post by Forlong on 2008-01-08
In Appearance Preferences click on **Customize** and go to the **Color** tab - is that what you are looking for?

---

### Post by Tech_Power888 on 2008-01-10
Unfortunately this is not what I am looking for, as it only seems to change the colour of the actual inner window, and the font...I could have an orange window with green text, but the title bar on the window is still maroon! Sorry to be a pain, your suggestions are very helpful but they still don't answer my question..keep trying! I appreciate it!

Ryan.

---

### Post by Tenken on 2008-01-10
Are you using Compiz or Metacity as your window manager? Because I don't think you can adjust the color on Compiz themes

---

### Post by Forlong on 2008-01-10
> **Tech_Power888 said:**
> Unfortunately this is not what I am looking for, as it only seems to change the colour of the actual inner window, and the font...I could have an orange window with green text, but the title bar on the window is still maroon!
I guess you are using Emerald then.

Go to *System &#8594; Preferences &#8594; Emerald Theme Manager* to pick another theme or edit the one you are currently using.

---

### Post by Tech_Power888 on 2008-01-10
I am sure that I am using Compiz Fusion...I normally go to System - Preferences - Appearance to change my themes. But in System - Preferences there is also an Emerald theme manager...but it is empty. I have never really used emerald theme manager before.

---

### Post by Forlong on 2008-01-10
Well, what's the output of
```
ps -e | grep emerald
```

---

### Post by Tech_Power888 on 2008-01-10
Sorry, i'm not too sure what that output means...do i need to type it into terminal? i'm still noob...sorry...

---

### Post by Forlong on 2008-01-10
No need to be sorry.
When someone posts a command in CODE tags, it means thats something you can type (or c&p) in the terminal.

Just open a terminal, mark the command with your mouse and paste it by middle clicking into the terminal. Then hit enter and post the output here.

---

### Post by Tenken on 2008-01-10
If you are using Emerald (compiz) and don't see any themes in the theme manager it is going to it's default theme which is red. Try downloading some emerald themes (they have a .emerald extension) from [gnome-look]("http://gnome-look.org/index.php?xcontentmode=103") or [compiz-themes]("http://www.compiz-themes.org/") and install the file with the emerald theme manager.

---

### Post by Tech_Power888 on 2008-01-10
Thanks Forlong, the output is:

 5941 ?        00:00:00 emerald

Tenken, I will have a go at downloading some emerald themes tonight. I use gnome-look.org for all my current themes, so would I be able to download the same themes for emerald? I happen to like my current appearance, except for that darn title bar...

Ryan.

---

### Post by Forlong on 2008-01-10
Alright that means you are in fact running Emerald.

If you don't want to use it, you can either remove it:
```
sudo apt-get remove emerald && sudo apt-get autoremove
```
Or you can use this command to skip Emerald:
```
mkdir -p $HOME/.config/compiz && echo 'USE_EMERALD="no"' >> $HOME/.config/compiz/compiz-manager
```

Then you will use the matching titlebar to your theme (you like so well).

---

### Post by Tenken on 2008-01-10
[quote=Tech_Power888]Tenken, I will have a go at downloading some emerald themes tonight. I use gnome-look.org for all my current themes, so would I be able to download the same themes for emerald? I happen to like my current appearance, except for that darn title bar...[/quote]

The emerald themes on gnome-look are under both the Beryl and Compiz sections, and the only thing they affect appearance wise is the title bar. The panels/scroll bars/menus are controlled by your GTK theme, which is under Appearance->Customize->Controls.

---

### Post by Tech_Power888 on 2008-01-10
Ok great thanks guys! That explains a lot. I am currently at work but I will go home tonight and have a look into this. Is it recommended that I use emerald or skip it? If it is pretty much the same as compiz, but allows me to change my title bar then I will switch to emerald instead.

Thanks again. If there's anything else I will let you know. Will report back and let you know how I went.

---

### Post by lolzlolz on 2008-01-10
emerald doesnt do any desktop effects
see compiz is the desktop effect manager
while emerald manages window colors etc although to make a "theme" u usually need both an emerald and gnome theme (gnome theme as in system preference appearance)
so you would want to use both compiz and emerald if you want desktop effects and customized windows :)

---

### Post by Tech_Power888 on 2008-01-10
Ahh right, now I understand.

So Compiz is the "desktop effect manager" whereas emerald is the "theme manager" as such, is that correct? And having both means that I can customize basically everything?

---

### Post by Tech_Power888 on 2008-01-11
Thanks guys, I figured it all out!

I went into emerald theme manager -> edit themes. There, you are able to select the Frame Engine, which instantly allows me to adjust the window frame colours, all individually. Thanks for bringing everything to my attention guys! God bless ubuntu forums!

Ryan.

---

### Post by gdrumm on 2008-05-15
I'm kind of getting used to this myself.  One thing I've found is that you typically cannot change the "Human" theme.  Change it to one of the other window themes (like Human Clearlooks), under Controls,  and then make the changes to the Selected Items under colors.

---

### Post by muadnu on 2008-06-28
I don't know if anyone's still interested in this, but there is a way to change the window title color without emerald. Install gnome-color-chooser via synaptic, then open it with System->Preferences->Gnome Color Chooser, go to the Specific tab, and change the colors next to compiz. It doesn't work for me right away when I click apply (unlike the rest of the other options), but it does work after logging out.

---

### Post by S1ght on 2008-07-23
To change the title bar colour, right click desktop change background, themes, customize,colors and the selected items background color is the title bar color

---

### Post by esha123 on 2008-07-24
It is simple, first of all you go to control panel and moved to display menu chose the color what you want.........
--------------------------------------------------
Suzie
[Guaranteed ROI](http://www.inspire-itsolutions.com)
[Viral Marketing](http://www.inspire-itsolutions.com)
[Social Media Marketing](http://www.inspire-itsolutions.com)
[Search Engine Submissions](http://www.inspire-itsolutions.com)
[Email Marketing](http://www.inspire-itsolutions.com)
[Search Engine Marketing](http://www.inspire-itsolutions.com)
[Search Engine Optimization](http://www.inspire-itsolutions.com)

[Inspire Internet Marketing](http://www.inspire-itsolutions.com)

---

