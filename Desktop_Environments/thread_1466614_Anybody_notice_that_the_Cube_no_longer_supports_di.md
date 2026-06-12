---
title: "Anybody notice that the Cube no longer supports different wallpapers?"
date: 2010-04-30
forum: Desktop Environments
---

### Post by LongFist on 2010-04-30
Forgive me if this is posted elsewhere (if it is, the title text is severely lacking and is un-illuminating).

Did anybody (but me) notice that the Desktop Cube appears to have the *same wallpaper* on *each* desktop?  You'd think a change as radical as that would generate some sort of discussion, wouldn't you?

I just upgraded from Ubuntu 8.04 LTS to 10.04 LTS, and discovered that my Cube (multiple desktops) shows the same wallpaper for each desktop, regardless of how many wallpapers I add under **Preferences->CompizConfig Settings Manager->Desktop->Desktop Cube->Appearance**.  Can anybody explain that?  I sacrificed the normal display of the Desktop (with icons, etc) to have that capability, and now it appears to have been compromised.

What's going on?  Is there any way to get that (different wallpaper per desktop) functionality back?

---

### Post by Turwaithien on 2010-04-30
I have noticed that! In fact I was trying to fix it just now. But I don't know how. I also noticed that all of my customized shortcuts that involve the super/win/cmd key don't work anymore. It had made me realize how much I rely on my shortcuts. :P

---

### Post by Turwaithien on 2010-04-30
Okay. So I've fixed it! Yay. 

I went to synaptic package manager ('cause I'm still a bit old-school and don't understand how to use the new package manager well), searched compiz, and installed the package called plugin-extras (or something like that). All the options that went away with the upgrade to Lucid came back. 

It's a little different in that there's a plugin called Wallpapers under Utilities in the Compiz Settings Manager. But it does the same thing and works the same way, as far as I know. I got my wallpapers back anyway.

---

### Post by LongFist on 2010-04-30
So, reading that, I opened **System->Preferences->CompizConfig Settings Manager**, and scrolled down, past the **General**, **Accessibility**, and **Desktop** headers, down, down, down past **Effects**, **Extras**, and **Image Loading**, only to find "WallPaper" in the **Utility** section.

No module loading necessary.

On a lark, I loaded three wallpapers, clicked the "Enable Wallpaper" checkbox, and before I could close the configuration screen, my wallpapers were restored!

A thousand [COLOR="SeaGreen"]**t**hank[/COLOR]-[COLOR="SeaGreen"]**y**ou's[/COLOR]: I would never have though to look there.

:P  Eureka: My wallpapers have returned!  Yayyy!!! :P

---

### Post by Ayukawa on 2010-05-02
I followed the same instructions and set three wallpapers and checked the enable wallpapers box, and nothing happened - all my desktops still have the same wallpaper (the one set in System -> Preferences -> Appearance

---

### Post by LongFist on 2010-05-02
There is still one detail left: once you get your Cube enabled, and your Wellpapers enabled and set up: you have to tell Nautilus **not** to display the (original) desktop.

Open a terminal, and type "**[COLOR="Green"]sudo gconf-editor[/COLOR]**" (without the double quotes, of course) and hit enter.

The gconf editor will pop up - it's actually a graphical editor, like what you're used to working with.  (I just don't know another way to get it running with root access.  Sooo...)

Under **[COLOR="Teal"]Apps->Nautilus->Preferences[/COLOR]** you'll find a checkbox next to "Show Desktop".  Un-check this checkbox.  By the time you click on the OK and get out of the editor, you *should* be able to see the multiple wallpapers you have selected and set up.

I guess we should have mentioned that earlier, huh?  :(  Sorry about that.  Guess I just sort of took it for granted that everybody knew...

Well, let me know if this doesn't work, but it should get you all squared away.
[RIGHT]:guitar:[/RIGHT]

---

### Post by coffeecat on 2010-05-02
> **LongFist said:**
> No module loading necessary.

The package Turwaithien was referring to is compiz-fusion-plugins-extra. You must have had it installed already. It doesn't come with a default install, and it's not a dependency of compizconfig-settings-manager, so most people will have to install it.

> **LongFist said:**
> Open a terminal, and type "**[COLOR=Green]sudo gconf-editor[/COLOR]**" (without the double quotes, of course) and hit enter.

...

(I just don't know another way to get it running with root access.  Sooo...)

You should not run gconf-editor as root. Just run "gconf-editor" without the "sudo". If you can't run gconf-editor without sudo in your own account  then something is wrong with your system.

> **LongFist said:**
>  Under **[COLOR=Teal]Apps->Nautilus->Preferences[/COLOR]** you'll find a checkbox next to "Show Desktop".  Un-check this checkbox.  By the time you click on the OK and get out of the editor, you *should* be able to see the multiple wallpapers you have selected and set up.

You also have to restart the xserver by logging out and in again. But the problem with unchecking 'show desktop' is that all desktop icons disappear.

---

### Post by LongFist on 2010-05-02
True, you lose your desktop view entirely (links, shortcuts, etc.) but that's the price you pay to have the snazzy cube desktop manager, complete with a different wallpaper per desktop.

At least, back in the 8.04 LTS day, that was all there was.  I suspect that you can simply enable the "Wallpaper" module (under Utility) and have a different wallpaper per desktop, shortcuts and all -  but I haven't tried it (yet).

That would probably be the only item on my wish list - to combine the functionality of the Cube desktop manager with the Nautilus desktop - but I've only had this new version of Ubuntu for a few days, now, so I'm not at all sure *what* it can/can't do.

But I'm willing to experiment to find out...  :P

---

### Post by Ayukawa on 2010-05-02
There we go.  I saw a lot of forums saying to turn off the show_desktop entry, but it still didn't work.  Restarting the X Server fixed it for me, and now I have my desktops with different backgrounds (although it seems unable to display .png as backgrounds for some reason).

A litle disappointing that I lose my desktop icons, hopefully that'll be fixed at some point.

---

### Post by terranoid on 2010-05-29
Not running gconf-editor as root as coffeecat suggested was the only way i could get it to work.

I have to repeat that. Coffeecat's suggestion that it shouldn't be necessary to run gconf-editor as root is an understatement. In that particular case, running it as root simply doesn't work, so don't do that. I guess the reason for that is that it is *your* desktop, not root's that you want to change.

Other than that i tried to post that repeatedly, still was told that  my post was too short and i had to expand it to at least one character. Strange!

---

### Post by bernabap on 2010-06-15
Hey guys,

I found a way to  create different icons for each desktop.

Actually are not  icons but Screenlets, but in the end it has the same function of the  icons (shortcuts to programs).

I am posting a megaupload link with two  videos. The first video is a  demonstration and the second one is a how to add icons. If anyone has  any questions post here and I will try to help.

[http://www.megaupload.com/?d=25LUAF7N](http://www.megaupload.com/?d=25LUAF7N)


bernabap

---

### Post by tarahmarie on 2010-06-17
Anyone know how to make this work in KDE?

---

### Post by asif_1088119 on 2010-07-18
running as smooth as a silk...thanx mate

---

