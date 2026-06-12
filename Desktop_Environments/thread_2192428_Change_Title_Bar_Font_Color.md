---
title: "Change Title Bar Font Color"
date: 2013-12-07
forum: Desktop Environments
---

### Post by Confused Computer User on 2013-12-07
Hi,

As the title indicates I am looking to change the color of the title bar font. More speciffically I want to have the inactive window title to have the same color as that of the active window since it's easier to read.

See the pic below.

[ATTACH=CONFIG]248422[/ATTACH]


I'm running Kubuntu 12.04 with KDE backports ppa activated

The Desktop theme in use is: Eleonora and the window decoration theme in use is: Seven.
The color scheme is: Windows 7 Colors.

I have tried several times to change the Title Bar color via the system settings but to no avail.

What am I missing?

---

### Post by Frogs Hair on 2013-12-08
The inactive color would be a feature of the theme and probably not influenced by any system settings. I know nothing of KDE theming, but there is information available. [http://techbase.kde.org/Development/Tutorials/Plasma/ThemeDetails#Colors](http://techbase.kde.org/Development/Tutorials/Plasma/ThemeDetails#Colors)

---

### Post by PaulW2U on 2013-12-08
> **Confused Computer User said:**
> I have tried several times to change the Title Bar color via the system settings but to no avail.

Where did you go?

System Settings | Application Appearance | Colours  - I think that's where your screen shot is taken from.

On the Colours tab, with Common Colours selected, scroll down to Inactive Titlebar and change the colour there.  The colours that I see there as being selected do reflect the colours in my theme, which is not the default.

I haven't tried changing anything myself as I don't want to experiment on my system which is set up exactly the way I want it. If that's what you've already tried then I'm out of ideas I'm afraid. :D

---

### Post by Confused Computer User on 2013-12-08
Hi all,

Thank you both for your prompt replies. So here we go with my answers.

> **PaulW2U said:**
> Where did you go?

System Settings | Application Appearance | Colours  - I think that's where your screen shot is taken from.

On the Colours tab, with Common Colours selected, scroll down to Inactive Titlebar and change the colour there.  The colours that I see there as being selected do reflect the colours in my theme, which is not the default.

Yes, indeed that is where I first went to change the color. The issue is that I've tried to do this with several other themes, including Oxygen which is part of the default theme package, and nothing happened. The colors I saw did not reflect the theme, at least in what Title Bars were concerned. Everything else seemed to work. So for instance I can change the Tool-tip Background and Text, and the effect takes place the moment I press Apply. I repeat the same procedure for Inactive Titlebar and nothing happens.

> **Frogs Hair said:**
> The inactive color would be a feature of the theme and probably not influenced by any system settings. I know nothing of KDE theming, but there is information available. [http://techbase.kde.org/Development/Tutorials/Plasma/ThemeDetails#Colors](http://techbase.kde.org/Development/Tutorials/Plasma/ThemeDetails#Colors)
The link seems to be refering to the Desktop Theme. My issue is with the Window Decoration. I can't find anything on it. I presume that there exists some folder containing the settings file for the Window Decorations but I have yet to find it.

Is there anyone with some experience in Theme or Window Decoration design?

Also, just a reminder, I am using the KDE backports ppa. Not sure if that makes that much of a difference.

---

### Post by mpmistr on 2013-12-10
The title bar text color is adjustable via System Settings > Application Appearance > Colors then select the Colors tab. While this does work, there is an exception.

If you happen to have the setting to "Follow Hint Style" selected under Window Decorations in System Settings, your color theme will NOT allow you to change the title bar font color. It will follow the option for Window Text instead.

I personally prefer "Follow Hint Style" being enabled, because it makes windows look much nicer, but you can disable this to gain access to the color options for title bars. You can also override this on a per application/window basis under Workspace Appearance > Window Decorations > Configure Decoration and select the Window-Specific Overrides tab. I do this in Chrome to make it look more native since it does not look quite right when using Follow Hint Style.

Hope this helps!

**Update #1, did a little more testing, it appears I was incorrect at least when using the Oxygen window theme. It would seem changing title bar color and text does not work in Oxygen. You can change title bar color via Window Text, but will change the fonts for a lot of other stuff too. Tried this with Use Solid Color/Radial Gradient.

**Update #2, I was able to change the title bar color independently of Window Text using the 'Plastik' window decoration, I believe the Oxygen window decoration simply does** not **recognize the title bar / inactive title bar color settings.

---

### Post by Confused Computer User on 2013-12-10
> **mpmistr said:**
> 
**Update #1, did a little more testing, it appears I was incorrect at least when using the Oxygen window theme. It would seem changing title bar color and text does not work in Oxygen. You can change title bar color via Window Text, but will change the fonts for a lot of other stuff too. Tried this with Use Solid Color/Radial Gradient.

**Update #2, I was able to change the title bar color independently of Window Text using the 'Plastik' window decoration, I believe the Oxygen window decoration simply does** not **recognize the title bar / inactive title bar color settings.

Wow...thank you for you dedication in trying this out on your own time. I greatly apreciate the feedback.
The issue gets a bit more complicated when looking at the non-default Window Decorations.
In the case of all the decorations I manualy added, if I click on Configure Decoration in System Settings > Workplace Appearance > Window Decorations I'm only given two options: Border and Button size.

I'm hoping someone has the magic solution because switching to Plastik is not an option for me.

Thank you again mpmistr for your dedicated reply.

---

### Post by Confused Computer User on 2014-01-25
Got it.... took a while but it's solved.

So, what I did was to navigate to: /.kde/share/apps/aurorae/themes/seven/

There I edited a file called: "sevenrc"

I changed:
> ActiveTextColor=0,0,0,255
InactiveTextColor=150,150,150,150
UseTextShadow=false             
ActiveTextShadowColor=255,255,255,255 
InactiveTextShadowColor=224,224,224,255

to
> ActiveTextColor=0,0,0,255
InactiveTextColor=0,0,0,255
UseTextShadow=false             
ActiveTextShadowColor=255,255,255,255 
InactiveTextShadowColor=255,255,255,255 

I saved the file, then went to system settings, changed the window theme, applied the theme, reselected the window theme I modified, clicked apply and now I have what I want.

[ATTACH=CONFIG]249739[/ATTACH]

Hope this helps others. I'm marking the thread as solved. Thank you again to those who contributed and tried to help.

---

