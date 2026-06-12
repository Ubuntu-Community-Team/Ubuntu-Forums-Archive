---
title: "One step away from beryl... looks like a syntax error somewhere, or maybe otherwise"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by djrobthaman on 2007-04-26
Okay, so I know this is my 3rd post about how I can't get beryl to work but... I think I'm almost there and I actuall have something a bit more concrete than "a white window shows up".

The window no longer shows up because I started from scratch and used [this howto]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29") to install beryl.  I went all the way through and even downloaded the .deb file (the 64 bit version cuz I'm using the 64 bit version) and  completed the command.  

So now, when I log in to the xgl session the wobbly windows work and such, but it's obvious that metacity is the windows decorator.  Once I run beryl-manager though, the windows go stiff, and all beautiful desktop enhancements go away.  I figured I'd run this through the terminal and see what output I'd get and here it is:

```

douglas@douglas-desktop:~$ beryl-manager
douglas@douglas-desktop:~$ Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/usr/bin/beryl-xgl: 1: Syntax error: "(" unexpected
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

The second line ("Window manager... toggle shaded") comes immediately.  The rest of it comes when I click on the beryl icon in the menu bar and try and switch the windows manager to beryl (when I look in the drop down menu it's set to metacity).

Does anyone know what i can do to fix this?

Thanks

---

### Post by waveslider on 2007-06-19
I encountered this exact same problem after running Beryl successfully for several weeks since I upgraded to Feisty.

After lots of trial & error (and pulling out most of my hair), I discovered that the error only occurs when I apply a skydome image in Beryl Settings Manager under Desktop -> Desktop Cube -> Skydome (tab). 

I noticed that the tooltip for that option says the "dimensions for the image must be a power of 2 (i.e. 1024, 2048, 4096), so I tried selecting a different image that met that criteria, but Beryl still crashed after applying the setting.

Once I remove the skydome image from that option, Beryl runs just fine.

[COLOR="DarkRed"]Update: [/COLOR] After further experimentation, it seems that I can get the skydome image to work using an image with the dimentions 4096x1024. I have dual monitors with the resolution on both set to 1280x1024, and I have an Nvidia card.

---

