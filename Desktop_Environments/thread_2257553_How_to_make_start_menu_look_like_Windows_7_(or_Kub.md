---
title: "How to make start menu look like Windows 7 (or Kubuntu)"
date: 2014-12-20
forum: Desktop Environments
---

### Post by fkervin on 2014-12-20
Hi all,

I've recently move from kubuntu to lubuntu and one of the things I would like to customize is que start menu.

I've install "alacarte" and with it I can add-remove elements, but the menu result tiny, and I would like to make font bigger, any idea?

I really would like to transform the menu to be as similar as possible to Windows 7 start menu, althought I also like a lot the menu of kubuntu. Is there any way to do this? It must not be impossible since [Zorin OS]("http://zorin-os.com/") (linux with LXDE) includes an start menu at the most Windows 7 style.

Many thanks in advance and regards

---

### Post by ajgreeny on 2014-12-20
I don't really know zorin, but it looks as if it is using the whisker menu that Xubuntu now uses as default.

This can be used in Lubuntu but it needs the xfce4-panel as well, and you would then have to either use both lx-panel and xfce4-panel or stop lx-panel from starting in the session and use xfce4-panel instead.  I am not sure how well that would work, ie stopping lx-panel from running, nor if there are other menu packages that look the same.

My whisker menu in Xubuntu 14.04 is shown in screenshot.

---

### Post by fkervin on 2014-12-20
Many thanks for the answer, ajgreeny

I have to say that I'm moving from kubuntu tu lubuntu becouse I had some problems in XBMC produced by KWIN, so I need an enviroment the lightest possible.

I'm not sure if I understand you, if having this menu means to the system having to manage in some way the lxfe and xfce4 at same time, it can be a bad idea, perhaps it's a best option using xubuntu directly.

If you tell me that it this way it's nor a problem, it could be good having lubuntu and this start menu, any link explaining a bit or a how-to?

Regards and thanks again

---

### Post by vasa1 on 2014-12-20
> **ajgreeny said:**
> ..
This can be used in Lubuntu but it needs the xfce4-panel as well, and you would then have to either use both lx-panel and xfce4-panel or stop lx-panel from starting in the session and use xfce4-panel instead.  ...
I tried the Whisker menu on Lubuntu by installing **xfce4-whiskermenu-plugin** (Alternate menu plugin for the Xfce desktop environment). As ajgreeny says, xfce4-panel is needed in the sense that it's one of some dependencies pulled in at the time of installing xfce4-whiskermenu-plugin.

You can run the whisker menu with lxpanel without running xfce4-panel.

In any case, the idea of making a Linux system look like a Windows system is not to my taste because the sooner one gets used to the difference, the easier it will be to settle in.

---

### Post by fkervin on 2014-12-21
Many thanks for your answer, vasa1,

I'm going to try it, my only "fear" it that it can cause some problem with XBMC, but I suppose that it does not have to be a problem for the system "stability and lightness" since it does not involve to install a windows composite or something similar, am I wrong?. If I install this whisker panel, am I installing some kind of compositing? I've read so, and it's just the reason to left kubuntu, problems in XBMC produced by window manager. I don't mind if system need some more RAM, but don't want add window management that can interfere with XBMC.

In the question of making Linux look like windows, I have to say that always when I ask questions related with it somebody says it, hehe :P. I simply want to make it be more attractive at first sight, make the user be able to get used to this system easily. Further this, in this case (start menu), in my opinion the default start menu of lubuntu is completely outdated, it is like the start menu of Windows 98. As I say in the tittle, the start menu of kubuntu is for me a great option, and would be as valid as the Windows' 7 one.

Just to try, I've just intall

```
sudo apt-get install xfce4-whiskermenu-plugin xfce4-panel
``` Regards

---

### Post by vasa1 on 2014-12-21
> **fkervin said:**
> Many thanks for your answer, vasa1,

I'm going to try it, my only "fear" it that it can cause some problem with XBMC, but I suppose that it does not have to be a problem for the system "stability and lightness" since it does not involve to install a windows composite or something similar, am I wrong?. If I install this whisker panel, am I installing some kind of compositing? ...
AFAIK, whisker doesn't need compositing at all.

---

### Post by fkervin on 2014-12-21
> **vasa1 said:**
> AFAIK, whisker doesn't need compositing at all.

Thanks A LOT,

I installed it as I told, but.... how can I activate it? I mean, I still have the lxde menu and after look at all the customization options I don't see how to make whisker replace the lxde menu.

I also wanted to tell I've found another menu that seems really beautiful, it is [GnoMenu]("http://linux.softpedia.com/get/Desktop-Environment/Tools/GnoMenu-42885.shtml"), could I install it on lxde? And if so... would it be a problem in terms of compositing and all this?

Other option apparently is Xfce4-appfinder, in[ this thread]("http://forum.lxde.org/viewtopic.php?f=3&t=36692") is menctioned as a good replacement for Gnomenu since Gnumenu is not updated sinde 2011. would it be best or lighter than whisker?, I've install it as reccomended in the link but don't know how to activate it (same problem that I've with wisker)

Many thanks again, and sorry for so many questions, it's I want to be sure that what I install is not goint to bring problems in XBMC.

Regards

---

### Post by fkervin on 2014-12-21
Hi guys,

I've spent a lot hours trying to do it but I'm unable to, I ask for some help, please, **really please.**

I told what I've done:

I've discard gnomenu since seems to be outdated and I've read that can have problems with it. So, I have 2 options of panels, on one one we have the **whisker menu**, and in the other hand there is the **xfce4-appfinder**.

_**Whisker menu:**_

I've install by:

```

sudo apt-get install xfce4-whiskermenu-plugin xfce4-panel
```

I have no find a way to add it to this panel, on Panel configuration, in the section I can add/remove elements it does not appear, even if i go to edit an application bar (I think it is not compatible with lxpanel)


If I run in terminal "xfce4-panel", this panel appears on top, and I can add whisker menu to it, but I think that this panel is not going to be ok for me since I can't add opacity to the panel without enabling compositing (and I don't want this), while lxpanel allows transparency without using compositing.

**_xfce4-appfinder_**

I've install by:

```
sudo apt-get install  --no-install-recommends xfce4-appfinder
```

I can launch it from terminal with "xfce4-appfinder":

[IMG]http://i60.tinypic.com/33audcn.jpg[/IMG]

Althought appears with the window bar, I suppose it will not appear if I can make it work via the start button.

The problem is that I'm completely unable to make "Menu" button launch this menu instead of lxpanelctl. I've try here:

[IMG]http://i58.tinypic.com/25pqn3k.jpg[/IMG]

In the place where says "Launcher manager" I've replace lxpanelctl with xfce4-appfinder with no result (I've restart and the menu is still the same"). I've also edit this file:

/etc/xdg/lxsession/Lubuntu/desktop.conf
[B]
And I've change this line:[/B]

launcher_manager/command=lxpanelctl

To this:

[B]launcher_manager/command=xfce4-appfinder

[/B]I have no result, I still have the lxpanelctl in the start menu.
Any idea?

Manu thanks in advance

---

### Post by ajgreeny on 2014-12-21
> **vasa1 said:**
> I tried the Whisker menu on Lubuntu by installing **xfce4-whiskermenu-plugin** (Alternate menu plugin for the Xfce desktop environment). As ajgreeny says, xfce4-panel is needed in the sense that it's one of some dependencies pulled in at the time of installing xfce4-whiskermenu-plugin.

**[COLOR=#000000]You can run the whisker menu with lxpanel without running xfce4-panel.[/COLOR]**[COLOR=#ff0000]
[/COLOR]
In any case, the idea of making a Linux system look like a Windows system is not to my taste because the sooner one gets used to the difference, the easier it will be to settle in.

How can you manage to do this;  all my attempts have resulted in the error saying that xfce4-panel is not running.

And just for your info, I don't want it because it looks like Windows; my last windows was XP which had nothing like this.  I want it because the whisker menu is so much faster to use than the old style menu.

---

### Post by fkervin on 2014-12-21
Hi Again,

ajgreeny, I've ask about it to the creator of whisker and he has told me that it's impossible to use in lxpanel, you need xfce4, you can see it [here]("https://gottcode.wordpress.com/2013/07/19/go-little-menu/#comment-780").

His answer:

> Well, Whisker Menu requires the Xfce panel, so you would have to swap  panels. I don&#8217;t use LXDE, so I&#8217;m sorry but I can&#8217;t help you. You should  ask on the Ubuntu forums and see if anybody else who is more familiar  with Lubuntu can help.

Meanwhile, I'm really desperate, please someone to help me, I want a better menu than default for Lubuntu, best if works with lxpanel, but I've spend a lot of time with **_xfce4-appfinder_** and can't make it work. I don't mind if it's this one or another similar, it's just that lxpanelctl seems to me completely outdated and simple. 

As I told in the title of the thread, a menu Windows 7 style would be great, but one kubuntu's style is the same great for me.

Many thanks to all in advance

---

### Post by Dennis N on 2014-12-22
Next time you choose your OS, give Xubuntu a try and you will have the excellent Whisker menu working as it should. Xubuntu is also relatively easy on system resources. Another option is Ubuntu Mate, which offers a  menu similar to the Mint Menu in Cinnamon. Ubuntu Mate is also relatively easy on system resources.

---

### Post by fkervin on 2014-12-22
Many thanks for your reply, Dennis N,

I chonen Lubuntu because it was the lighter destop and it seemt me the most appropiate given the fact I've had problems with kubuntu in XBMC for his compositing.

Said this, I don't want the most attrative start menu un Lubuntu, but I can't believe I can't use anyone that is more functional that the one that comes by default.

Anyone has any experience on this?

Regards and thanks

---

### Post by vasa1 on 2014-12-22
[s]I ran both xfce4-panel and lxpanel together. I configured the former to contain just the whisker menu and to take up minimum space at the top left corner of my screen. The rest of the horizontal space was assigned to lxpanel. For those keen on sticking with the "windows" look (IDK why), both panels could be placed at the bottom of the screen.[/s]

---

### Post by fkervin on 2014-12-22
Wow! it seems a perfect solution for doing what I want, hehe.

Could you help me to do this? At this moment i can launch xfce4-panel manually from the terminal and it's launched at the top of the screen, how could i configure it to start automatically and also be in the corner in the way you told??

Many thanks

---

### Post by vasa1 on 2014-12-22
> **fkervin said:**
> Wow! it seems a perfect solution for doing what I want, hehe.

Could you help me to do this? At this moment i can launch xfce4-panel manually from the terminal and it's launched at the top of the screen, how could i configure it to start automatically and also be in the corner in the way you told??

Many thanksHi, Sorry about the previous post. I'm having problems trying to do what I claimed I could do!

---

### Post by fkervin on 2014-12-22
Nothing to sorry, I only can thank you for your help.

If you're having problems with this I'm afraid that for me it's better not to even try :(.

I Really don't know what can be my solution, moving to Xubuntu could be, but its a pity since I've customize the whole LXDE and looks great (everything but the start menu). Perhaps if I use xfce4 panel instead of lxpanel, but I don't know how to, and also I don't want to lose the transparency effect of the lxpanel.

If you archieve to do this solution or another one that allow to change the default LXDE start menu please tell me, I've spent one whole day with this reading lots of links on google and I have nothing.

Regards and thanks again

---

### Post by Dennis N on 2014-12-22
> ...also I don't want to lose the transparency effect of the lxpanel.
Maybe you don't realize it, but the Xubuntu (xfce4) panel also has transparency. It is called 'alpha' in the Panel Preferences > Appearance.  alpha=0 is completely transparent, alpha=100 is no transparency.

---

### Post by ajgreeny on 2014-12-22
Following all these discussions, and just for my own amusement, I have now got both lxde and xfce4 panels running side by side on the same edge of the screen with lxpanel taking 95% on the right hand side and xfce4-panel using the remaining 5% on the left hand side so it looks like a single panel.  The xfce4-panel contains just the whisker menu, which works fine except for lacking the "Run" option of the lubuntu menu, and it also the action buttons for shutdown etc etc do not work from whisker menu.

Here's a screenshot of the left hand end of this "experimental" double panel with whisker menu open in my Lubuntu install, which I run only in VirtualBox, and have since 14.04 was in alpha release; Xubuntu is my main OS.  In the screenshot I temporarily made a gap between the two panels, just to show more easily how they fit together, by reducing the length of the lxpanel from 95 to 94.  No gap normally shows.

Worth trying, I think, if you really want whisker menu!

---

### Post by kerry_s on 2014-12-22
lol
you should grab a ubuntu mate to try live. its pretty much just as light, but with out all the hassles of being stripped down. it has several menu styles to choose from once you start messing around. its exactly like gnome was, just dead simple to use.
everything's already there you just move things around till you like it. lol

the thing about light weight systems is you really need some experience to get what you want out of it.

i'll throw some pics up. i'm just returning to linux & only got my setup up a couple of days ago. i had to butcher 5 broken systems to build 1 working system to install on, my specs suck.

atom 230 dual 1.6ghz 
2gb ram

there's more powerful netbooks now a days. lol

---

### Post by fkervin on 2014-12-22
> **Dennis N said:**
> Maybe you don't realize it, but the Xubuntu (xfce4) panel also has transparency. It is called 'alpha' in the Panel Preferences > Appearance.  alpha=0 is completely transparent, alpha=100 is no transparency.

You're right, but for doing this compositing is required and I can't use it this since I'm moving from Kubuntu to "other"buntu just for this, hehe. I had problems with XBMC and I need a light desktop, some that uses not composite.

> **ajgreeny said:**
> Following all these discussions, and just for my own amusement, I have now got both lxde and xfce4 panels running side by side on the same edge of the screen with lxpanel taking 95% on the right hand side and xfce4-panel using the remaining 5% on the left hand side so it looks like a single panel.  The xfce4-panel contains just the whisker menu, which works fine except for lacking the "Run" option of the lubuntu menu, and it also the action buttons for shutdown etc etc do not work from whisker menu.

Here's a screenshot of the left hand end of this "experimental" double panel with whisker menu open in my Lubuntu install, which I run only in VirtualBox, and have since 14.04 was in alpha release; Xubuntu is my main OS.  In the screenshot I temporarily made a gap between the two panels, just to show more easily how they fit together, by reducing the length of the lxpanel from 95 to 94.  No gap normally shows.

Worth trying, I think, if you really want whisker menu!

You are in the way of becoming my hero, you know? xD

Since I had no way to do what I wanted with Lubuntu today I've install Xubuntu (I'm getting out of -buntus :P). Those are my first impressions:

[I]**As positive:**

-Whisker menu by default.
-This distro is very light and works ok with XBMC if I disable compositing (apparently as good as Lubuntu)
-It allows changing wallpaper every x time (Lubuntu requires an external application, "Variety", and I don't like it at all)
-For what I see it seems more complete in terms of options and pre-installed software, what could save me time.

**Negative:**

-Does't allow transparency on panel (requires activating compositing)
-I'm unable to mod it to have the appearance of Windows 7 or similar* (the tools I have found does not work in xfce4).[/I]

In this point I'm completely lost, Xubuntu has surprise me for good, and If it were for me, I'd stay with it, you can be sure, but the negative thigs are important, mainly the second one, anyone know how to modify effectively to look like win7/8? (everything I've test is not compatible).

In the other hand I've a Lubuntu customized according to my needs, but still the problem of start menu, so if you help me to get xfce4-panel together with lxpanel in the way to tell, I could stay on Lubuntu (can you help me pleaseeeeeeee :) ).

Regards and many thanks to all.

*Please don't judge me by wanting to modify Linux to look like Windows, I have my reasons: this installation will be used by people I want to introduce in "linux world" and it's much easier if the "feel" of the system is the one they're used to. They pefectly knows it's Linux not Windows by they get used easier in this way.

---

### Post by Dennis N on 2014-12-22
> You're right, but for doing this [transparent panel] compositing is required 

Yes, you are right about Xubuntu. But, to throw another stick on the fire, in Ubuntu Mate, the panel has a transparency setting that works without the Window compositor activated. Just looked at this to be sure. Something you may want to look at for your next OS.

Enjoy your Xubuntu experience. I use it most of the time myself. If you are curious, attached is a shot of the Mate Menu in Ubuntu Mate in its default state. Some configuring is possible.

---

### Post by kerry_s on 2014-12-22
> **Dennis N said:**
> Yes, you are right about Xubuntu. But, to throw another stick on the fire, in Ubuntu Mate, the panel has a transparency setting that works without the Window compositor activated. Just looked at this to be sure. Something you may want to look at for your next OS.

Enjoy your Xubuntu experience. I use it most of the time myself. If you are curious, attached is a shot of the Mate Menu in Ubuntu Mate in its default state. Some configuring is possible.


i'll add to that. it can all be tweaked. here's a quick windows like setup, just quick, i don't want to get to far from my set up.
you can run ubuntu mate live & see if it will do what you want most of the settings are stock.

---

### Post by fkervin on 2014-12-22
Many thanks Dennis N,

What is the window manager of Mate? I choosen lubuntu for beign the lightest buntu, and now Xubunbu since it's supposed (if I'm not wrong) to be the secong lightest one. I'll give a try to this distro if i can get some time, hehe, but I hope be able to (at last) have in xubutu what I need.

I would like to ask you something, I'd really thank you if help: I've get the icons and some aspect of Windows, but the menus of the windows are still not, I've download this: [Seven Basic Theme]("http://xfce-look.org/content/show.php/Seven+Basic?content=120130"), but I don't know how to install, any help?

I don't discard completely the option of using lubuntu if ajgreeny helps me with the panels ;)

Regards

---

### Post by Dennis N on 2014-12-22
> I've download this: Seven Basic Theme, but I don't know how to install, any help?

Here's how:

Open the archive 120130-Seven-Basic-2.0.3.tar.gz with Archive Manager. Extract folder to: **~/.themes** (If you don't have this directory, create it). If you create it, be sure to include the period before "themes" in the name. That makes it a hidden folder.

Go to **Settings > Window Manager > Style Tab** and select "Seven Basic". It changes immediately.

---

### Post by Dennis N on 2014-12-22
Just in case you don't know how to unhide hidden folders in the file manager, use Ctrl+H as a toggle to hide and unhide them.

---

### Post by fkervin on 2014-12-22
Thanks a lot, Dennis N :)

It works not, it was a dumb thing, but i did't find an explanation like yours when researched.

Now I'm trying to make work cairo dock on Xubuntu but if I disable compositing fails, hehe.

I still have the faith in ajgreeny, It I can make work Whisker menu on Lubuntu with his method very probably will use it

Thanks

---

### Post by ajgreeny on 2014-12-22
Here you go then.

[LIST=1]
[*]Install **whiskermenu **and** xfce4-panel** (plus the dependencies).
[*]Start **xfce4-panel** with command in the "Run" dialogue box, then right click on it and go to Panel ->Panel preferences.
[*]Move it to where you want, temporarily it's easiest to put it on the same edge but just above your lxpanel, and resize the length; in my screenshot it is bottom and left and 5% of screen width. Once in place lock it (lock box is on the Display tab)
[*]Right click on the lxpanel and configure that to the same edge but to the right, and with a length of 95%, which should leave a space the same size as your xfce4-panel.
[*]Right click the xfce4-panel and unlock it to move it into the space (it will be slightly too big when unlocked, but will shrink again once relocked into the correct position, and if you have the panel size the same in both (mine were 24pixels) it should look like a continuous single panel, though you will perhaps need to experiment with colours and themes.
[*]Once you are happy add xfce4-panel to the Startup Applications tab in default applications for session from the Lubuntu preferences menu.  Both panels should now run at session start.
[/LIST]

I hope that helps and that I've not missed any parts of the procedure, but I think that should be enough to let you get a similar arrangement to mine.
Good luck!

---

### Post by fkervin on 2014-12-22
Hi ajgreeny,

I've this working now and its very good, the only problem is the one you had, buttons for shutdown, configuration, etc appears and even shows tooptip but doesn't work.... I'm going to ask to the creator of Whisper.

Manu thanks for your help :)

---

### Post by Fernando_Vilas_Paz on 2015-01-31
...

---

### Post by Fernando_Vilas_Paz on 2015-01-31
> **fkervin said:**
> Hi ajgreeny,

I've this working now and its very good, the only problem is the one you had, buttons for shutdown, configuration, etc appears and even shows tooptip but doesn't work.... I'm going to ask to the creator of Whisper.

Manu thanks for your help :) 

  I might have a fix for this.U can use both panels. 1 with a short xfce panel with whisker and 2 lxpanel with the exit option in the end, so u dont need to log out from whisker just use it  to find apps or whatever.So.. steps i made:


1 sudo apt-get install xfce4-whiskermenu-plugin xfce4-panel  or u can do it from synaptic
2 went to lxsession appside.xfce in the left 
3 in the launcher manager blanquet i set xfce4-panel (doing this, when u log in, bith panels will be launched)
4 then i configured both panels side by side.xfce in the left 24 size with whisker,showdesktop and pcmanfm.On the right with a 91 size the complete lxde panel with time, conexion,etc. 
5 to finish  i added right in the middle of the lxde panel  one last element...menu. with this u can log out and also will have the classic menu.
even if u dont want to add the panel u can log out usin the coman ctrl+ alt+ del

i dont now much about linux but i think this could fit 4 u, at least fit for me :)

---

### Post by Fernando_Vilas_Paz on 2015-02-01
just in case someone are still interested i just found out how to make buttons logout and change user works.Just going to whisker menu edit and change the behavior where appears log out i set this /usr/bin/lubuntu-logout. And it works perfectly

---

