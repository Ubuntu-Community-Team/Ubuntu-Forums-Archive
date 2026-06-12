---
title: "Desktop Alternatives for Precise Pangolin 12.04"
date: 2013-03-12
forum: Desktop Environments
---

### Post by Kixtosh on 2013-03-12
**The issue:**

I started using Ubuntu in 2009 and have been using it ever since. What I like about it:


[LIST]
[*]Running on a laptop with a core 2 duo 1.2 GHz CPU and a maximum allowed 2GB of RAM, boot requires about 17 seconds from the GRuB menu. Halt takes 3 seconds flat.
[*]This laptop uses a 64GB Samsung SSD that looks like a mSATA, only bigger, and it's PATA. It has a funky proprietary connector, so I haven't found a way to upgrade it. Fortunately, dual booting with Windows, I only need to reserve 7GB for Ubuntu.
[*]On a second laptop with a Celeron 900 single core 2.2 GHz and 2GB of RAM, boot requires about 35 seconds and halt takes about 4 seconds. This laptop uses a regular 7200 rpm hard drive.
[*]Firefox opens from cold in 1-2 seconds on both laptops, or 1 second when "hot" (already booted previously during the same session).
[*]I use shortcuts I like for various tasks, such as Super+B for browser, CTRL+ALT to switch desktops, ALT+F1 to access the panel menus ...
[*]Using Lucid Lynx 10.04, I've had three years of trouble free usage without having to tweak things every six months.
[/LIST]

With long term support for Lucid Lynx coming to an end, I've finally taken time to try out Precise Pangolin 12.04. I know that Unity has not been liked by many, but I actually do like it. However, it slows everything down on my two laptops. They must just be too modest in capabilities for it to shine. Boot is still pretty fast, maybe just a few seconds slower, but halt now takes twenty seconds. This is actually slower to halt than either W7 or W8, which take about six to ten seconds. Firefox also seems to have more lag. I haven't played with Windows much, but I do need to dual boot for some infrequent stuff, so ...

I've tried switching around a few desktops, like LXDE and XFCE, and both give me back the exact same fast operation as before, but I don't really like either of these all that much. I'm now wondering what else might be out there that I should try. Here would be my preferences:


[LIST]
[*]Something a bit more "polished" in my view than Puppy, standard LXDE or XFCE.
[*]Something equally fast as Lucid Lynx 10.04, or Precise Pangolin 12.04 without Unity.
[*]Something where keyboard shortcuts are available, easy to customize, and the more of them the better!
[/LIST]

Any ideas?

---

### Post by ManamiVixen on 2013-03-12
gnome-session-fallback
mate
Cinnamon
Gnome-Shell

---

### Post by Kixtosh on 2013-03-13
A few questions, and observations:

[LIST]
[*]I was wondereing about MATE and Cinnamon, but then I wondered why I wouldn't just use Mint instead of Ubuntu in that case. Is there a reason to choose one instead of the other for either desktop? 
[*]Both seem very classic. Windows 8 is making a lot of classic stuff look a bit dated. I think I might be ready for something more adventurous. 
[*]Just tried Unity 2D, and it seems to have the same speed as before, or really close to it. I don't understand the difference with 3D though. 
[*]The shortcuts are also very different from Lucid Lynx, but I think I could get used to those. Maybe Unity 2D could be my solution. 
[/LIST]

---

### Post by quequotion on 2013-03-13
> **Kixtosh said:**
> A few questions, and observations:

[LIST]
[*]I was wondereing about MATE and Cinnamon, but then I wondered why I wouldn't just use Mint instead of Ubuntu in that case. Is there a reason to choose one instead of the other for either desktop? 
[*]Both seem very classic. Windows 8 is making a lot of classic stuff look a bit dated. I think I might be ready for something more adventurous. 
[*]Just tried Unity 2D, and it seems to have the same speed as before, or really close to it. I don't understand the difference with 3D though. 
[*]The shortcuts are also very different from Lucid Lynx, but I think I could get used to those. Maybe Unity 2D could be my solution. 
[/LIST]


Unity 2D will be deprecated. Future versions of Ubuntu will use llvmpipe to run Unity on systems without a dedicated GPU.
Pantheon, from the elementary project, looks very nice and works well--but the [keyboard shortcuts]("http://elementaryos.org/journal/keyboard-shortcuts-luna-beta-one") take some getting used to, and are still in development.

---

### Post by Kixtosh on 2013-03-13
> **quequotion said:**
> Unity 2D will be deprecated. ...Not before the end of Long Term Support for Precise Pangolin, in 2017, right ... or is that something completely different?

---

### Post by ibjsb4 on 2013-03-13
Yep, you will get support till 2017.  If you want the old desktop look (10.04) there's gnome-classic which can run with effects (compiz) or without (metacity).

[https://www.google.com/search?hl=en&client=ubuntu&hs=vDx&channel=fs&tbm=isch&source=univ&sa=X&ei=ihZBUcG-LsmkqgGBhICwCg&ved=0CDAQsAQ&biw=1024&bih=604&q=12.04%20gnome%20classic%20desktop%20pics](https://www.google.com/search?hl=en&client=ubuntu&hs=vDx&channel=fs&tbm=isch&source=univ&sa=X&ei=ihZBUcG-LsmkqgGBhICwCg&ved=0CDAQsAQ&biw=1024&bih=604&q=12.04%20gnome%20classic%20desktop%20pics)

---

### Post by Kixtosh on 2013-03-13
That's great news ... I think I'll try Unity 2D to see if I can get used to it. I like the novelty and some of the shortcut options are actually better for me than before, so I like that too (the Super+X digit to call up items in the dock launcher, for example). Others don't seem to be there at all (and I don't seem to be able to add them either, at least, not yet).

By the time 2017 comes around, I'll be ready for new laptops anyway. They're two or three years old already.

---

### Post by drfox on 2013-03-13
What's unpolished about XFCE/Xubuntu? What do you need that XFCE doesn't offer?
I've been using it for 2+ years and love it.

---

### Post by Cheesemill on 2013-03-14
Have you seen the wiki page describing how to make 12.04 fallback look like Gnome 2?
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Kixtosh on 2013-03-15
> **drfox said:**
> What's unpolished about XFCE/Xubuntu? What do you need that XFCE doesn't offer?
I've been using it for 2+ years and love it.
Thanks for commenting, drfox. Part of this may be personal perceptions, or just not knowing how to do certain things, but this is what I remember about my trials with XFCE:

[LIST]
[*]Didn't work well with older laptops. There was little to no performance gain compared to Ubuntu Lucid Lynx with Gnome. LXDE or Puppy Linux seemed much better choices for older or limited hardware. I don't use my older hardware much any more, however, so that's no longer really a concern.
[*]The default desktop backgrounds are somewhat "washed out", which is also true of LXDE frequently. I'm sure this is not that difficult to change, but by default, I find the desktop backgrounds offered to be bland and lacking in contrast.
[*]I love the XFCE default right click options on the desktop to access extended menus, including applications. Pupply Linux uses these too, but this is still much slower for me than Unity 2D where Super+X (digit) will open applications shown in the dock in the order 1 to 9 (or "t" for trash). You can open anything in one second, with just two keys pressed at the same time.
[*]I could not get shortcuts to change keyboard layouts to work (I type in French a lot, so I'm constantly switching from USA to FR).
[*]I could not get shortcuts for frequently used functions to work (such as ALT+F1 for Panel menus in Gnome, ALT+home, Super+B for Browser ...).
[*]I just find the Lucid Lynx flavor of Gnome more predictable and trustworthy when trying to set it up. With XFCE, I find myself embarking on constant internet searches for each and every tweak to see if I can get them to work.
[/LIST]
I also like certain aspects of Unity 2D in Precise Pangolin even when compared to Gnome in Lucid Lynx. Basically, I like that Unity 2D allows me to use the dock with fast shortcuts, and I like the the Dash search feature. I've set the dock to auto-hide so it doesn't use up my screen, and the Super key pulls it up, but thanks to those shortcuts, I don't even wait for it to appear before executing the command I want. The performance gains with XFCE on my newer hardware (which is still not very powerful) seem very minimal to imperceptible.

I'm happy to be proven wrong though, and I don't mind trying stuff out if there's a performance benefit in return.

---

### Post by Kixtosh on 2013-03-15
> **Cheesemill said:**
> Have you seen the wiki page describing how to make 12.04 fallback look like Gnome 2?
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

Thanks Cheesemill. I'll take a look at that, but I'm not certain I want a classic Gnome desktop with no enhancements. It's not that I don't like Unity 3D, it's that I find the delays on my hardware perceptible and annoying. I guess I must be impatient by nature. I find most classic desktops getting old and dated looking to me, and it's probably why I didn't just switch to Mint.

Unfortunately for me, perhaps, I even love the new W8 desktop, complete with Metro tiles and tons of new keyboard shortcuts (as well as speedy boot times). I find it dynamic and colorful, but I'm not sure I'm ready for that leap of faith yet though! I suffered too much pain with W2K and XP. The really painful experiences were rare occurrences, but even once every two years is too much to burden myself with after such a solid run with Lucid Lynx and it's stellar performance (in my view).

---

### Post by orhank on 2013-03-16
Real men use CDE :P

---

### Post by ibjsb4 on 2013-03-16
> **orhank said:**
> Real men use CDE :P

Thats really helpful.

And I guess everyone should know what CDE stands for.  Could you not of provided a link?

[http://sourceforge.net/projects/cdesktopenv/](http://sourceforge.net/projects/cdesktopenv/)

---

### Post by Kixtosh on 2013-03-17
Thanks ibjsb4! I may not be a "real man" apparently, and you just saved me the trouble of searching for myself! ... :KS

Edit: Just had a quick peek, and I'm not at all convinced that it's what I'm looking for, so I might be destined to remain forever a "girly-man" (thanks Arnold).

---

### Post by drfox on 2013-03-17
> **Kixtosh said:**
> Thanks for commenting, drfox. Part of this may be personal perceptions, or just not knowing how to do certain things, but this is what I remember about my trials with XFCE:

[LIST]
[*]Didn't work well with older laptops. There was little to no performance gain compared to Ubuntu Lucid Lynx with Gnome. LXDE or Puppy Linux seemed much better choices for older or limited hardware. I don't use my older hardware much any more, however, so that's no longer really a concern.
[*]The default desktop backgrounds are somewhat "washed out", which is also true of LXDE frequently. I'm sure this is not that difficult to change, but by default, I find the desktop backgrounds offered to be bland and lacking in contrast.
[*]I love the XFCE default right click options on the desktop to access extended menus, including applications. Pupply Linux uses these too, but this is still much slower for me than Unity 2D where Super+X (digit) will open applications shown in the dock in the order 1 to 9 (or "t" for trash). You can open anything in one second, with just two keys pressed at the same time.
[*]I could not get shortcuts to change keyboard layouts to work (I type in French a lot, so I'm constantly switching from USA to FR).
[*]I could not get shortcuts for frequently used functions to work (such as ALT+F1 for Panel menus in Gnome, ALT+home, Super+B for Browser ...).
[*]I just find the Lucid Lynx flavor of Gnome more predictable and trustworthy when trying to set it up. With XFCE, I find myself embarking on constant internet searches for each and every tweak to see if I can get them to work.
[/LIST]
I also like certain aspects of Unity 2D in Precise Pangolin even when compared to Gnome in Lucid Lynx. Basically, I like that Unity 2D allows me to use the dock with fast shortcuts, and I like the the Dash search feature. I've set the dock to auto-hide so it doesn't use up my screen, and the Super key pulls it up, but thanks to those shortcuts, I don't even wait for it to appear before executing the command I want. The performance gains with XFCE on my newer hardware (which is still not very powerful) seem very minimal to imperceptible.

I'm happy to be proven wrong though, and I don't mind trying stuff out if there's a performance benefit in return.

I'm using Xubuntu with xfce 4.10 on 4 different machines. One is a Atom-powered netbook, but I have installed it on friend's pentium-powered laptops. I switched from gnome to xfce when unity and shell came out and have occasionally used unity in a VM just to see if it made any sense, and imho, it still doesn't. I have played with lxde and found that unpolished. 
Kixtosh, je suis desolate, mais je suis americain. Donc, ce n'est pas necessaire pour mois a travailler en une lingue different que anglaise. (I hope I did that OK...it's been a long time since high school when I studied your language) Anyway, I can't speak to difficulty of changing the keyboard layout.
In answer to your other questions:
I find a great benefit to use xfce vs gnome on older machines and on my new machines, but I also found the feature of the r-mouse click to bring up menus to work slowly on old machines. 
I can't speak to the built-in desktop backgrounds...I use some of my own photos and some others and switch my wallpaper from time-to-time; it always looks ok to me.
I have customized keyboard shortcuts, and they always work fine (Ctrl-Shift-W for libreoffice-writer, Ctrl-Alt-Del for xfce4-taskmanager)
I use synapse for searches and also to type in applications for quick launch. Ctrl-spacebar brings up synapse.
I use cairo-dock as my bottom dock for eye-candy except for on my netbook where there's not much screen space. I use xfce-panel (as deskbar) on the left and drag frequently used apps to it.

Give it another try...you might like it.
Larry

---

### Post by Kixtosh on 2013-03-18
Larry, I probably will give it another try.

I've been experimenting more with Precise Pangolin, and although I have resolved all the speed issues with Unity 2D, there are other things that I don't think I'm going to get used to. It's going to be a toss-up between:

- Mint.
- Xubuntu (with XFCE).
- Mageia (this is just an experiment, since it's becoming very popular on distrowatch of late).

This will be mostly for the following types of machines:

- Toshiba Portégé with an integrated SSD an a modest Core 2 Duo 1.2 GHz.
- Arctic MC001 media center with an Atom D525 (I'll probably end up with OpenElec on this).
- Couple of other family laptops with fairly modest processors.

And thank you so much for the French, I understood every word of it! The usual key sequence for changing keyboard layouts is ALT+SHIFT (also in Windows). Works great with Ubuntu (unless it's XFCE), and Windows 8 (not so much in Vista or W7). I'll just have to figure out how to get it to work. It can't be rocket science.

---

### Post by LewisTM on 2013-03-20
Salut Kixtosh,

For changing the keyboard layout, you should have xfce4-xkb-plugin installed. The plugin can then be added to one of your panels (Keyboard Layouts). From there, you can configure it for multiple layouts and set the key sequence for switching. For maximum stability, you should go to Settings Manager -> Keyboard -> Layout and set it to use the system default, otherwise the plugin and your Xfce settings will try to override each other and cause trouble.

Also, drfox is right. Cairo-Dock and Synapse are the best things you can add to Xfce, to improve the interface and add features. They blend in perfectly.

Bonne chance!

---

### Post by Kixtosh on 2013-03-20
Thanks LewisTM! I will try that.

I also got a good laugh from your signature, so thanks for that as well!

---

