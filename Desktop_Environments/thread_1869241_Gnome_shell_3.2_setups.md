---
title: "Gnome shell 3.2 setups"
date: 2011-10-25
forum: Desktop Environments
---

### Post by cbowman57 on 2011-10-25
Thought it would be helpful to have a thread showing some ways gnome shell can be configured, as well as a place to share any tips & tricks you've discovered.

[ATTACH]205462[/ATTACH]  [ATTACH]205463[/ATTACH]  [ATTACH]205464[/ATTACH]

*These images contain screenshots that show theme, fonts & extensions, information that should be helpful in setting up any gnome shell system. 

Let's create a gallery showing the diversity & potential of Gnome shell.

---

### Post by sidewalkcynic on 2011-10-25
I am somewhat confused with the way the Ubuntu desktop has evolved. I understand that it is designed for touchscreen and traditional peripheral inputs, but with the quantity of applications that I work with the touch screen menu tends to be confining. Basically, I would prefer the old fallback classic Ubuntu menu.

The touchscreen menu might work well as a mouse menu if the icons were smaller. And definitely, I need the ability to reorganize the menu categories. Because it seems that I have to use the application search tool - maybe that's what they are trying to do, anyway.

When I tried the 'fallback' on my initial install of 11.10, it did not seem that I could have both at the same time - it was one desktop, or the other.

So, if there is a way to meet those demands, I'll be happy

---

### Post by BazookaAce on 2011-10-25
@Sidewalkcynic: You can make the menu icons smaller if you want to, and you can get a menu a la "gnome desktop" like this: 

[IMG]http://img225.imageshack.us/img225/1908/screenshotat20111025184.png[/IMG]

[IMG]http://img838.imageshack.us/img838/1908/screenshotat20111025184.png[/IMG]

---

### Post by cbowman57 on 2011-10-25
A lot can be done through the use of extensions, a good place to start is [Webupd8]("http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html")

---

### Post by sidewalkcynic on 2011-10-25
> **BazookaAce said:**
> @Sidewalkcynic: You can make the menu icons smaller if you want to, and you can get a menu a la "gnome desktop" like this
That looks pretty good. I like the use of transparent background for app menus. I am going to want to put the app menu on the right side of the top panel - how do I do all that? I'll see what is at Webupd8

---

### Post by sidewalkcynic on 2011-10-25
thanks,

I installed the tweaks and themes, and something else, from WebUpD8.

I noticed that it installed the fallback package, and noticed that it reoccurred the login page that I experienced before, and so I was better prepared for what was coming - I can deal with it.

I'll check the WebUpD8 a bit more.

I installed Jupiter - I think I have noticed that had a lower battery life. If it had to do with the kernal update then I would have been oblivious to it somewhat, because I got the Aspire One at about the time of the update.

---

### Post by sanderd17 on 2011-10-25
> **sidewalkcynic said:**
> That looks pretty good. I like the use of transparent background for app menus. I am going to want to put the app menu on the right side of the top panel - how do I do all that? I'll see what is at Webupd8

The extension developer decides where everything gets placed, luckily, extensions are made with quite readable JavaScript, so you can edit it yourself if you want. Editing an icon or a color of a theme is normally pretty easy, but editing placement can be difficult I think. I never tried that.

---

### Post by sidewalkcynic on 2011-10-25
> **sanderd17 said:**
> The extension developer decides where everything gets placed, luckily, extensions are made with quite readable JavaScript, so you can edit it yourself if you want. Editing an icon or a color of a theme is normally pretty easy, but editing placement can be difficult I think. I never tried that.

Well,I have the menu like the screen shot, Bazooka gave; and I forget that it is there, and I wind up clicking on Activities which leads to the desktop-like menu with the large icons. The drop-down menu is pretty, and I think the scroll bar feature is interestingly different. I have to kind of re-think my organization. But definitely, I would prefer that drop down menu on the right side and put the message/log-out menu on the left.

---

### Post by sidewalkcynic on 2011-10-25
I added TuxCards to my StartUp list, and the desktop that I got from WebUpD8 could not handle it - froze. had to Ctrl+Alt+Del to log out.

I logged back in to Gnome classic (no effects), to get to the StartUp menu and I removed TuxCards, but when I log into Gnome to get the fancy new desktop, it gives me an openbox interface.

---

### Post by BigCityCat on 2011-10-25
You can edit the settings of some extensions with dconf-editor. 

sudo apt-get install dconf-editor

Then navigate to ORG/GNOME/SHELL/EXTENSIONS.

---

### Post by BigCityCat on 2011-10-25
Here is mine. :D

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshotat2011-10-21180749.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshotat2011-10-21180749.png)

---

### Post by Copper Bezel on 2011-10-25
I'll bite: does anyone know if, and if so, how, GTK3 and Clutter can handle rgba or other transparency in menus? I've been playing with a LiveCD, and usability-wise, it's a step up from what I'm using now, but I really, really like transparent menus.

I don't mean the Shell menus, by the way, which are rgba-toting CSS objects - I mean specifically the application menus from right-click or the menu bar.

---

### Post by 23dornot23d on 2011-10-26
This one is with Clarity icons - I still seem to need need a few more ....... 

[IMG]http://img265.imageshack.us/img265/8487/snapshot1hy.jpg[/IMG]

---

### Post by cbowman57 on 2011-10-26
> **Copper Bezel said:**
> I'll bite: does anyone know if, and if so, how, GTK3 and Clutter can handle rgba or other transparency in menus? I've been playing with a LiveCD, and usability-wise, it's a step up from what I'm using now, but I really, really like transparent menus.

I don't mean the Shell menus, by the way, which are rgba-toting CSS objects - I mean specifically the application menus from right-click or the menu bar.

Can't say it with certainty but the gtk3 themes are nothing but .css files & widgets so if the shell can use transparency I think it would be possible to make the rest of the theme do it too.

This isn't a definitive answer, hopefully somebody that knows will chime in.

---

### Post by cbowman57 on 2011-10-26
> **23dornot23d said:**
> This one is with Clarity icons - I still seem to need need a few more ....... 

Looks good but I was hoping to show screenshots that actually provided the information people would find useful to emulate the look or discover an extension they were unaware of. :)

---

### Post by 23dornot23d on 2011-10-26
A ha ...... ok with you now ..... will go in search of new things .... :D


[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

Fedora ...

[http://www.dnmouse.org/autoten/gnome-3-extra-tips/192-gnome-shell-weather-extension.html](http://www.dnmouse.org/autoten/gnome-3-extra-tips/192-gnome-shell-weather-extension.html)

---

### Post by cbowman57 on 2011-10-26
> **23dornot23d said:**
> A ha ...... ok with you now ..... will go in search of new things .... :D

Cool! :)

I don't think a lot of people know what the shell can do, wanted to show them some possibilities & how to set it up with gnome-tweak-tool (Advanced Settings).  There are other desktop threads but they are more like  beauty pageants & by the time you ask somebody how they achieved a particular look or function the screenshot is 5 pages back.

---

### Post by Frogs Hair on 2011-10-26
Cheat Sheet: [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by Copper Bezel on 2011-10-27
[QUOTE=cbowman57]Can't say it with certainty but the gtk3 themes are nothing but .css files & widgets so if the shell can use transparency I think it would be possible to make the rest of the theme do it too.[/QUOTE]
I think you're right about this. Specifically, menu objects seem to be the same stretched .png as ever, but with rgba support built in.

Too much fun stuff to play with. = )

Edit: Does anyone know why there's an "open" animation but not a "close" animation for windows? = /

---

### Post by cbowman57 on 2011-10-27
> **Copper Bezel said:**
> I think you're right about this. Specifically, menu objects seem to be the same stretched .png as ever, but with rgba support built in.

Too much fun stuff to play with. = )

Edit: Does anyone know why there's an "open" animation but not a "close" animation for windows? = /

Most of this goes right over my head but you might be able to make sense of Finn Murphy's blog [http://blog.fpmurphy.com/page/3](http://blog.fpmurphy.com/page/3) .He might cover that in some of his earlier entries.

---

### Post by cbowman57 on 2011-10-27
Gnome shell theme [Pantheon]("http://gnome-look.org/content/show.php/Gnome-Shell+Pantheon?content=146291") . Removed Elementary branding by replacing logo.png, logo.svg & overview.jpg

Very well done G-S theme, I particularly like the way the author tightened up the icon spacing on the panel.

[ATTACH]205593[/ATTACH]  [ATTACH]205594[/ATTACH]  [ATTACH]205595[/ATTACH]

---

### Post by cbowman57 on 2011-10-28
How to move the applications menu from the Frippery collection from left side of panel to the right side.    The screenshot contains the metadata.json so you can verify you are using the same extension.

In the extension.js (located either in the /usr/share/gnome-shell/extensions/apps-menu@gnome-shell-extensions.gnome.org or ~/.local/share/gnome-shell/extensions/apps-menu@gnome-shell-extensions.gnome.org folder depending on whether you installed it globally or per user) change ```
let appsMenuButton;

function enable() {
    appsMenuButton = new ApplicationsButton();
    Main.panel._leftBox.insert_actor(appsMenuButton.actor, 1);
    Main.panel._leftBox.child_set(appsMenuButton.actor, { y_fill : true } );
```to this: ```
let appsMenuButton;

function enable() {
    appsMenuButton = new ApplicationsButton();
    Main.panel._rightBox.insert_actor(appsMenuButton.actor, 1);
    Main.panel._rightBox.child_set(appsMenuButton.actor, { y_fill : true } );
```Look in the vicinity of line 100-102, the key is to change leftBox to rightBox in just those 2 places.

The result looks like this & compliments the places or extended-places extension.

[ATTACH]205685[/ATTACH]

---

### Post by cbowman57 on 2011-10-28
Changing icon size of the Frippery Panel Favorites extension.

[ATTACH]205691[/ATTACH]


Still trying to figure out how to size icons displayed with icontopbar extension.

---

### Post by cbowman57 on 2011-10-31
As promised, Mr. Murphy has started updating his extensions, so far only the noripple extension is on his website. [http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

---

### Post by cbowman57 on 2011-10-31
Not Gnome shell specific but these are some handy wallpapers if you are trying to get more familiar with using linux from the commandline.

[Link to wallpaper]("http://www.google.com/search?q=useful+wallpapers+debian&hl=en&safe=off&imgrefurl=http://www.gefoo.org/generalfoo/%3Fcat%3D8&imgurl=http://www.gefoo.org/generalfoo/uploads/2011/03/linux-wallpaper-for-beginners.jpg&w=1280&h=1024&tbm=isch&tbs=simg:CAQSEgl-monQJ6vUryEkxAuMn_1iXbw&sa=X&ei=D8SuTtylGYz4sQLMrt3lDg&ved=0CAUQrBE4GQ&biw=1173&bih=835")

---

### Post by cbowman57 on 2011-10-31
Ok, apparently I killed the thread, so in an attempt to revive it I revised the thread guidelines.  

Feel free to display your desktops. :)

---

### Post by sanderd17 on 2011-10-31
Just read on WebUpd8 that Pinguy is going to use a highly customised GS setup: [http://www.webupd8.org/2011/10/pinguy-os-1110-gnome-shell-edition.html](http://www.webupd8.org/2011/10/pinguy-os-1110-gnome-shell-edition.html)

Btw, good wall. Shared with some Linux friends on G+.

---

### Post by cbowman57 on 2011-10-31
> **sanderd17 said:**
> Just read on WebUpd8 that Pinguy is going to use a highly customised GS setup: [http://www.webupd8.org/2011/10/pinguy-os-1110-gnome-shell-edition.html](http://www.webupd8.org/2011/10/pinguy-os-1110-gnome-shell-edition.html)

Btw, good wall. Shared with some Linux friends on G+.

Thanks, hope it gets some use.  I need to check out G+ myself.

Yeah, looks like the direction Linux Mint is going in too.

---

### Post by Copper Bezel on 2011-11-01
[QUOTE=cbowman57]Feel free to display your desktops. :)[/QUOTE]

I've been playing with mine a bit, mostly just tweaking the GTK3 theme, and posted [in the screenshots thread](http://ubuntuforums.org/showthread.php?p=11414111#post11414111). I installed the global menu extension, but it's not very useful, since it's a lot of clicks to dig down to whatever you're looking for. I do like the dock extension, particularly in that it matches itself to the Shell theme.

I'm having ridiculous stability problems and finding all of my favorite Gnome features broken. I like Shell in concept, but some things are going to have to happen before I could consider using it for actual work.

---

### Post by cbowman57 on 2011-11-01
The shell has been real stable for me, I've been using it exclusively for almost 6 months.

---

### Post by Copper Bezel on 2011-11-01
Well, let me clarify. I've only had the *shell* it crash without any apparent reason once, coming back from suspend, and even then, only the top panel disappeared. Wild and wonky things have happened, but usually only if I change the theme or something without logging out and logging back in. Terribly discomfiting things, like windows being stacked in crazy ways in the overview, but only if I've changed settings.

I've also had my touchpad randomly deactivate itself and have to be toggled off and back on again from Pointing Devices to come back, inordinately long pauses in the Dash search where even the mouse freezes, and other random weirdness. That's on top of irritations like Nautilus' keyboard navigation being broken (typing a bit of a folder name no longer works in any predictable fashion) and the lack of any meaningful keyboard navigation in the shell, Gnome 3 oddities like my backlight staying shut off if I close the laptop lid (without suspending) and open it again after a minute or so, and troubles with my trackpad and the 3.0 kernel, which has jack all to do with Gnome 3 but certainly colored my experience.

And then there are dialogue sheets, which are just ugly as all get out.

I really wanted to like Shell. It's a great concept, and most of the workflow makes sense. I think I *do* like Shell. The workspace management, for instance, is the most sensible there is; the way that secondary displays are separate from workspaces is brilliant, for instance, and sorting windows between workspaces is incredibly clean and neat; Shell's method for combining the Exposé with the workspace switcher in the Overview is the best I've seen, making it easy to tab through everything and stay organized at the same time. Compiz doesn't come close.

Gnome 3, on the other hand, is not remotely close to where Gnome 2 was, and I'm running out of arguments for why Gnome is more a "real" or "full" DE than XFCE. I have to assume that these are growing pains and that Gnome will be back to the top spot in DEs in short order. But I'm not exaggerating to say that it's completely unusable for me in its present condition.

---

### Post by cbowman57 on 2011-11-01
Watching Finn's progress on the updated extensions.  The noally extension doesn't work if you applied the earlier hack to the frippery app menu extension that relocated the menu to the right side.

[ATTACH]206064[/ATTACH]

---

### Post by cbowman57 on 2011-11-01
@Copper Bezel, I understand your frustration.  I don't use a laptop myself but reading the forums it seems they have their own unique sets of problems with most flavors of Linux.

---

### Post by Copper Bezel on 2011-11-01
They do, but that's not strictly my point. Out of the problems I've had under Gnome 3, not all of them have anything to do with my hardware, and most of them didn't exist under Gnome 2. I'm finding that some of them are known bugs and some of them are easy fixes, but there's a lot of polishing to be done before Gnome 3 is the complete and usable system that Gnome 2 was. But that's natural, because 3 has had six months, and 2 had several years, to get to where they are now.

---

### Post by cbowman57 on 2011-11-01
> **Copper Bezel said:**
> [...]  But that's natural, because 3 has had six months, and 2 had several years, to get to where they are now.

Exactly, we're having some growing pains.

Gnome 3 is still evolving, I'm sure it will get where it should be given a little more time.

---

### Post by werewolves on 2011-11-01
Here is my contribution.  After a little resistance at first, I'm starting to love Gnome 3 :cool:

---

### Post by cbowman57 on 2011-11-04
Just thought I'd mention that the Linux Mint extensions are available, link is in this post [http://ubuntuforums.org/showpost.php?p=11425449&postcount=33](http://ubuntuforums.org/showpost.php?p=11425449&postcount=33)

---

### Post by cbowman57 on 2011-11-05
Mr. Murphy is slowly populating his website with extensions for 3.2

Here's a shot of his latest in action, the Great Menu.

[ATTACH]206447[/ATTACH]

[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

---

### Post by BazookaAce on 2011-11-05
[IMG]http://img528.imageshack.us/img528/8123/screenshotat20111106024.png[/IMG]

---

### Post by cbowman57 on 2011-11-05
Looks very clean & functional.

An Ikea designed desktop. :)

---

### Post by cbowman57 on 2011-11-05
Mr. Murphy has reworked the mint menu extensions, IMHO they feel a little smoother & lighter than the one from the git, though I'm sure they aren't quite done yet.

Here's a very short video of the rhsmenu & lhsmenu in action. With the panel favorites incorporated into the menus I was able to remove that  clutter from my panel.

>> : [URL="http://youtu.be/xO1-5AW2nX0?hd=1"]Link to youtube video Gnome 3.2 shell twin menus

[/URL]  [IMG]http://youtu.be/xO1-5AW2nX0[/IMG]

---

### Post by Copper Bezel on 2011-11-07
Unrelated, but I guess I'll update on what I've been using.

I'm liking the Journal and Jump List extensions you'd suggested earlier, as [_here_]("http://123linuxtutorials.com/ubuntu-tutorials/three-nifty-gnome-shell-extensions-that-use-zeitgeist/"). The search isn't quite as nice as Synapse and not remotely as quick, but it's nice to have it integrated into the shell. I had shied away from them a big because the Gimme and Advanced Search extensions both cause problems in using the keyboard - hitting Enter doesn't reliably launch the highlighted item anymore when either one is enabled. I do very much like the Journal integration, however - even just flicking through it with the mouse, I find it comforting to have a feature in the shell to thumb through my recent files, and that they're sorted as they are in the Activity Journal is all the better. 

I haven't installed the extended data sources, but one possible bug I noticed with the Journal is that it doesn't include Music items, even though the music search in Unity works. I don't use this feature, but I don't think it's working, either.

Really, despite the mousiness of everything, I'm really settling into the Shell workflow. I just wish the search wasn't so bloody incomprehensibly slow, particularly in contrast to Synapse.

The Jump Lists, on the other hand, offer the only thing I was really missing from DockBarX. It really does save a step to have recent documents available from the launcher instead of waiting for the app to load and launching them from there, and the fact that selecting the file doesn't exit the shell is icing. (I'll have to figure out how to modify the extension to include more than four recent items in place of the "favorite" files.)

I'm also finding small bits of the Frippery Collection very useful. All of them together make for a slow and clunky Gnome-2-like experience, but I very much like the Shut Down menu, if for no other reason than that it makes suspending the computer as simple as hitting the power button and clicking the Suspend option, instead of having to select it from the session menu.

---

### Post by cbowman57 on 2011-11-07
I'm glad you're finding some of them useful.

I just checked something, I'm not in Ubuntu right now and music doesn't show up either, wasn't aware of it until you mentioned it.

I haven't gotten the hang of using the jump list yet, might take some practice on my part.

The frippery pack is really a good one, and fpmurphy's collection is too, well it will be when he gets it updated.

---

### Post by Copper Bezel on 2011-11-07
Yeah, I guess I'd been sort of trained to the jump list after using them in DockBarX for so long. It's not a common mode of interaction, but I've found it a useful one, at the very least for pulling up documents I close by accident or just didn't realize I'd need again. It's one of those features that lets your system be the organized one that keeps track of things so you don't have to. = )

And yeah, the Frippery pack is extremely well thought-out and written. I don't necessarily see the need to recreate a Gnome 2 workflow under Shell, but they're very well done. And after all, since the extensions I'm using just replicate my Synapse / DockBarX workflow fairly closely instead, I can't well judge. = )

---

### Post by sanderd17 on 2011-11-07
> **Copper Bezel said:**
> 

Really, despite the mousiness of everything, I'm really settling into the Shell workflow. I just wish the search wasn't so bloody incomprehensibly slow, particularly in contrast to Synapse.


I don't think search algo is very slow, but they do have a problem with rendering. I don't know what takes so much time (is it interpreting the CSS, or fetching the icon files), but the rendering should happen faster. You also get the same effect when you hit the "applications" button (again, they need to fetch a bunch of icons here).

When you just search and hit enter (so you skip the rendering), it's quite fast after all. 

Btw, thanks for mentioning the zeitgeist extensions again. The last time I tried them, they were all bundled into one extension. And since the search is still not very good, I disabled the whole extension with jump lists and journal.

---

### Post by Copper Bezel on 2011-11-07
Yeah, I had one of those bundled ones at some point, too. I think it was the Gimme extension I mentioned earlier, which looks a lot like the Journal extension but breaks the application search.

I've noticed that the rendering problem is worse on the first run after a log in or after a certain period of time, too - or maybe it's after resuming from suspend? I can't really tell. In any case, the search calms down a bit after the first couple of uses, but that first run is bloody unbearable, five seconds or so of a completely nonresponsive interface. I guess you're right that it probably has to do with fetching the icons or something of that sort; I notice that when I tab through the Journal, its icons are loaded on-demand, so they slowly appear as the screen renders (which is naturally still preferable to waiting for all of them to be fetched at once.) And I've done the same thing with smacking Enter before the application search screen can render, so I see what you mean about it being independent of the search algorithm.

---

### Post by cbowman57 on 2011-11-07
One of the members of this forum (werewolves) managed to nicely repackage Carlo Marchiori's hack to the old autohide top panel extension to work with 3.2, the link to the post is [http://ubuntuforums.org/showpost.php?p=11431904&postcount=7](http://ubuntuforums.org/showpost.php?p=11431904&postcount=7)

---

### Post by cbowman57 on 2011-11-07
Speaking of icons, in one of my searches some time back a speed tip was to use an icon theme made up of **.png**, not .svg files.  So if things feel a little sluggish you might want to try other icon themes, apparently some perform better than others.

---

### Post by sanderd17 on 2011-11-07
> **cbowman57 said:**
> Speaking of icons, in one of my searches some time back a speed tip was to use an icon theme made up of **.png**, not .svg files.  So if things feel a little sluggish you might want to try other icon themes, apparently some perform better than others.

The problem is that most png themes look pixelised with Gnome Shell (certainly because every theme uses a different size for the icons).

I know Faenza has all icons in svg, and most of them also in png with sizes of 48x48, 32x32, 24x24, 22x22 and 16x16. But the 48x48 size is still too small for most GS themes. It should be easy to convert the svg files to a custom png size, but only to one size.

Do you have an example of a png theme that looks good with GS. I might be able to find out how it works.

---

### Post by 23dornot23d on 2011-11-07
Just found out the cardapio extension used on Unity also works in the shell .....

just saw it in the Tweak Tool Extensions as I added it to try out ..... but I also remove
applications menu as they seemed to occupy the same space on the top bar.

[IMG]http://img836.imageshack.us/img836/1916/cardapio.jpg[/IMG]

[[COLOR=Blue]_**a familiar menu for those that want it**_[/COLOR]]("http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html") ........ Updated .. as a link was given by Beew

---

### Post by cbowman57 on 2011-11-07
> **sanderd17 said:**
> The problem is that most png themes look pixelised with Gnome Shell (certainly because every theme uses a different size for the icons).

I know Faenza has all icons in svg, and most of them also in png with sizes of 48x48, 32x32, 24x24, 22x22 and 16x16. But the 48x48 size is still too small for most GS themes. It should be easy to convert the svg files to a custom png size, but only to one size.

Do you have an example of a png theme that looks good with GS. I might be able to find out how it works.

I like AwOken, it appears to be all .png.

---

### Post by cbowman57 on 2011-11-07
> **23dornot23d said:**
> Just found out the cardapio extension used on Unity also works in the shell .....

just saw it in the Tweak Tool Extensions as I added it to try out ..... but I also remove
applications menu as they seemed to occupy the same space on the top bar.

[[COLOR=Blue]_**a familiar menu for those that want it**_[/COLOR]]("http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html") ........ Updated .. as a link was given by Beew

I've run into a collision of extensions on at least one occasion also.

I used to really like using cardapio, especially before I discovered synapse.

Did you have to do anything special to install it in the shell?

---

### Post by 23dornot23d on 2011-11-07
> 
Did you have to do anything special to install it in the shell?


Nope nothing other than follow the instructions on webupd8 .....

I had gone to the extensions to set something else when I noticed it there .....

but on switching it on ..... noticed its position on the top bar ..... so I automatically
disabled the other menu .... as it appeared it would conflict.

I never tried it with both on though ..... 

Quite like this myself ...... was not keen on the other one so much ....

But the layout of this one is very familiar and works well ........ :D

---

### Post by sanderd17 on 2011-11-07
> **cbowman57 said:**
> I like AwOken, it appears to be all .png.

I changed to AwOken, and the shell worked faster. I also tried hicolor. That theme has larger resolution png files available. And I noticed that those files got preferred over the svg files. But the 48x48 files were also preferred (if that was the biggest resolution). And even worse, when I returned to Faenza, the 48x48 icons were also used (and looked quite good). The shell now works a bit faster, but I don't know how I did it.

I've been busy with some icons lately, and I always thought that the svg files were used, and now after some switching, the png files got used.

Was I wrong about the first thought? Or have I just seen some magic?

---

### Post by cbowman57 on 2011-11-07
I experienced a similar anomaly the other day after toggling some accessibility bits on & off.

Makes me think that there are some default settings that aren't optimized on installation & somehow get "fixed" after being manually set.

---

### Post by Frogs Hair on 2011-11-07
I have the Web Upd8 extensions PPA installed and applications menu extension is included . I have tested it , but don't keep it activated because I want get used to using the shell without it . I have activated the places status indicator though. :D

I know there are extensions outside of the PPA I am using , but I fear conflicts . I think some extensions were developed for Fedora so I am more than little cautious about installing and using them .  Any thoughts on this ?

---

### Post by sanderd17 on 2011-11-07
> **Frogs Hair said:**
> I have the Web Upd8 extensions PPA installed and applications menu extension is included . I have tested it , but don't keep it activated because I want get used to using the shell without it . I have activated the places status indicator though. :D

I know there are extensions outside of the PPA I am using , but I fear conflicts . I think some extensions were developed for Fedora so I am more than little cautious about installing and using them .  Any thoughts on this ?

There is no problem with using extensions that were developed for another OS. If and only if they are compatible with gnome shell 3.2. Most extensions for Fedora are only compatible with GS 3.0, since that's the version used by the latest stable Fedora.

---

### Post by cbowman57 on 2011-11-07
I haven't run into any distro specific extensions yet.

I freely copy my extensions between Arch & Ubuntu to keep them in sync and haven't encountered a problem yet.

I have to confess, I'm no purist, I'll add whatever extension or app I think will make using my desktop easier.  It's funny, in one thread somebody was lambasting Gnome shell's poor "out of the box" functionality and basically called me a heretic because I use synapse. :)

I can't think of a single OS, distro or DE that I was ever satsified with the default.

---

### Post by sanderd17 on 2011-11-07
> **cbowman57 said:**
> 

I can't think of a single OS, distro or DE that I was ever satsified with the default.

This, and it's not Gnome's task to set the default. OS makers (like mint and Pinguy) set the default for their users.

I'm trying to make some icons for Faenza (this is my first one: [http://sanderd17.deviantart.com/art/LaTeX-editor-icon-faenza-style-267544086](http://sanderd17.deviantart.com/art/LaTeX-editor-icon-faenza-style-267544086) ), but I'm running into problems with Java apps. When I use another icon for Geogebra, or JOSM (both Java apps with a loading screen), the icon is used in the activities view etc, but once launched, the icon is still the default one.

Would there be any way to change that? I don't like low-res icons in my alt-tab switcher.

---

### Post by cbowman57 on 2011-11-07
That looks good, I'm sure there is a way to fix that problem but I don't have a clue how to do it.

---

### Post by 23dornot23d on 2011-11-07
> **Frogs Hair said:**
> I have the Web Upd8 extensions PPA installed and applications menu extension is included . I have tested it , but don't keep it activated because I want get used to using the shell without it . I have activated the places status indicator though. :D

I know there are extensions outside of the PPA I am using , but I fear conflicts . I think some extensions were developed for Fedora so I am more than little cautious about installing and using them .  Any thoughts on this ?


The system the last time I had a problem with extensions ...... comes up with the tweak toggle on/off list
straight away (rather than error stop dead) so you can switch off the offending ones ......

and then it restarts straight away

Much better than before ..... ;)

---

### Post by Copper Bezel on 2011-11-07
[QUOTE=cbowman57]I have to confess, I'm no purist, I'll add whatever extension or app I think will make using my desktop easier. It's funny, in one thread somebody was lambasting Gnome shell's poor "out of the box" functionality and basically called me a heretic because I use synapse. :)[/QUOTE]
Yeah, I'm probably on the other side of that, but only because I'm trying to give the Shell a fair go as it is, and also because everything is so neatly integrated that it seems to defeat the purpose a bit to try to work around the Shell instead of with it. Otherwise, I'd rather just use Synapse and DockBarX and Compiz and put up with the fact that they don't talk to one another very well, since each one by itself has advantages over what Shell offers. But I'm definitely making use of extensions.

I'll have to try removing the Scalable icons from Faenza and seeing if that fixes the rendering problem.

Yuck - I've discovered a new problem with LibreOffice and Gnome 3's interaction on Suspend. It looks like I either remember to save and close my gradebook between classes, or jack things up. = P

Edit: Actually the last bit seems to be a Frippery bug. I've been using the Shut Down menu extension because it adds "Suspend" to the list in the pop-up when I press the power button. What I really need to do is figure out the Javascript to make the power button just suspend the machine like I'm used to.

---

### Post by 23dornot23d on 2011-11-07
Just put 2 launchers on the desktop ......

one with 

gnome-shell --replace 

one with

compiz --replace


if you have UNITY set to run in compiz - it will pop up and work ..... as normal ......

you can have the best of both worlds - as I do ........

______________________________________________________________

If suspend works better from UNITY ...... switch to it using the launcher and implement it from there ..... see if you get the same results ... ( test it )

---

### Post by volkerbradley on 2011-11-07
> **cbowman57 said:**
> One of the members of this forum (werewolves) managed to hack the autohide top panel extension to work with 3.2, the link to the post is [http://ubuntuforums.org/showpost.php?p=11431904&postcount=7](http://ubuntuforums.org/showpost.php?p=11431904&postcount=7)

In all fairness, it appears that werewolves just nicely repackaged Carlo Marchiori work. See [http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html#comment-356318148](http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html#comment-356318148)

---

### Post by cbowman57 on 2011-11-07
> **volkerbradley said:**
> In all fairness, it appears that werewolves just nicely repackaged Carlo Marchiori work. See [http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html#comment-356318148](http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html#comment-356318148)

Yeah, that was the original source but it was unusable the way it was.

I however should have phrased that a bit better. :)

---

### Post by Copper Bezel on 2011-11-07
It seemed to work. I duped the 48 folders into the scalable folders, adjusted the theme index accordingly, and altered the shell theme to use 48px icons in place of 96px, although they're still stretched to 96 in the Journal tab. Anyway, the search rendering seems much faster.

---

### Post by werewolves on 2011-11-07
> **volkerbradley said:**
> In all fairness, it appears that werewolves just nicely repackaged Carlo Marchiori work. See [http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html#comment-356318148](http://www.webupd8.org/2011/06/autohide-top-bar-gnome-shell-extension.html#comment-356318148)

Absolutely true.

So here is my properly converted 3.2 version, meaning it will enable and disable as expected. Also, instead of just statically setting the panel height to 25 pixels, this version reads the current panel height when it initializes (allows for different shell themes).

---

### Post by cbowman57 on 2011-11-08
If any of you are playing with the MGSE extensions today's tarball had an improved windowlist extension, it works in the top panel if the bottom panel isn't used.

Anyway, I was looking at the code for the window list extension and discovered a way to make the icon size change for the active window, it's a subtle effect but it's a neat visual.

```
        let icon = this.app.get_faded_icon(1.55 * PANEL_ICON_SIZE);
        this._iconBox.set_child(icon);
        }
        else {
            this.actor.remove_style_pseudo_class('focus');
        let icon = this.app.get_faded_icon(1.15 * PANEL_ICON_SIZE);
        this._iconBox.set_child(icon);
        }
```In the file I looked at today this started near line 206.  The default is 1.15, I increased the value to 1.55 in this example.

Hope I made some sense out of trying to explain it.

Here's a very small thumbnail showing what it does.    [ATTACH]206703[/ATTACH]

---

### Post by Copper Bezel on 2011-11-08
Ooh, very cool. = D Much improved.

Is anyone having trouble with the Global Menu extension? It stopped working for me and disappeared from Gnome Tweak Tool, but its settings are still stored in dconf (where it's still listed as active.) I tried reinstalling it from git, but it didn't help. I can still switch the hack that removes the menu bars from the applications on and off, but the menu doesn't appear in the Appmenu button.

---

### Post by cbowman57 on 2011-11-08
Today's desktop, with a touch of Mint.

[ATTACH]206721[/ATTACH]

---

### Post by sanderd17 on 2011-11-09
> **cbowman57 said:**
> Today's desktop, with a touch of Mint.

[ATTACH]206721[/ATTACH]

tastes good ;)

---

### Post by cbowman57 on 2011-11-09
> **sanderd17 said:**
> tastes good ;)

:lol: Tried to do a little video of it in action [http://youtu.be/_6Z9eWwabWo?hd=1](http://youtu.be/_6Z9eWwabWo?hd=1)

* The video is on my Arch setup but the extensions perform the same on Ubuntu.

If you watch the window list carefully you can see the resizing of the active icon that was accomplished by editing the window list extension I explained yesterday.

---

### Post by cbowman57 on 2011-11-09
fpmurphy just put an updated movehotcorner extension on his site for 3.2.

For those that may not have seen it, this one adds a hot corner to the upper right.

---

### Post by Copper Bezel on 2011-11-10
Yeah, I might have to check that out. I'm still catching myself trying to hit the upper-right corner once in a while, since that used to be my Expo edge. I *did* have to remove the puddle effect for the normal hot corner, but although there's an extension for that, all you really have to do is modify the shell theme not to use it.

I'll probably play more with these extensions once the newness of the Shell wears off. Right now, I'm actually just using Noa11y and Journal, the latter of which I'm finding to by Synapsey enough for my needs. I am also using Alternate Tab, but it seems broken - the previews mode doesn't work at all and jacks up my input in general once it's invoked, and the icons mode only rarely shows a popup at all and only switches between the two most recent windows. I still find that slightly more useful than the app-based switcher, though.

---

### Post by sebinbenjamin on 2011-11-10
Hi,

My gnome shell seems to be having a problem with the panels. i am using ubuntu 11.10. i also remember disabling global menu, but re-enabling it hasn't solved the problem. Any help would be appreciated.   

[IMG]http://i43.tinypic.com/10yp72t.png[/IMG]

---

### Post by BillyBoa on 2011-11-10
> **sebinbenjamin said:**
> Hi,

My gnome shell seems to be having a problem with the panels. 

[IMG]http://i43.tinypic.com/10yp72t.png[/IMG]

I think you have the same problem like me with the ATI drivers. We have to wait for a solution....

---

### Post by sebinbenjamin on 2011-11-10
oh, i thought it had something to do with the 'global menu'. So i guess i will have to stick with unity .:(

[IMG]http://i41.tinypic.com/308xixi.png[/IMG][IMG]http://tinypic.com/?t=postupload[/IMG]

---

### Post by cbowman57 on 2011-11-10
> **Copper Bezel said:**
> Yeah, I might have to check that out. I'm still catching myself trying to hit the upper-right corner once in a while, since that used to be my Expo edge. I *did* have to remove the puddle effect for the normal hot corner, but although there's an extension for that, all you really have to do is modify the shell theme not to use it.

I'll probably play more with these extensions once the newness of the Shell wears off. Right now, I'm actually just using Noa11y and Journal, the latter of which I'm finding to by Synapsey enough for my needs. I am also using Alternate Tab, but it seems broken - the previews mode doesn't work at all and jacks up my input in general once it's invoked, and the icons mode only rarely shows a popup at all and only switches between the two most recent windows. I still find that slightly more useful than the app-based switcher, though.

If you were using the upper right for the expo edge it would probably suit you, I feel lost without it.  I went with a  minimalist approach when there was little choice, but now I'm just going for as comfortable & convenient as I can make it.

@sebinbenjamin, better to use the open source drvers if you have  an ATI card, at least for the present.

---

### Post by Dragonbite on 2011-11-10
I had something kinda like that but I think my desktop has an nvidia card (and older one), not ATI.

---

### Post by don_quixote on 2011-11-10
Bit the bullet and switched from Unity to the Shell.  Thought I'll try and give it a second chance.  With extensions, it's starting to feel productive, though some keyboard shortcuts are still missing (snap to left half or right half of screen, anyone???).  It does look very nice with a slightly modified Zukitwo theme -- just a touch more polished all around than Unity.

Also, when I bring the activities overview, it bothers me to no end that there isn't a CTRL+# or ALT+# to bring up the numbered applications on the left 'dock' as in Unity.  It would also be nice if I could switch to a workspace with a key combination (I know there is an extension for this, but it's far from perfect).

My present setup includes these extensions:

User Themes 
Arrow Key Window Selector  
Shut Down
Move Clock
noa11y
Static Workspaces
Auto Move Windows

------

As far as I am concerned, these should be optional GNOME 3 settings that can be toggled, as they are really basic options that a lot of users might like.  I remembered when I first realized I could not switch between applications with arrow keys in the activities overview, I though the whole thing is pretty much broken.  Why NOT have that???

---

### Post by Copper Bezel on 2011-11-10
That's just not how Gnome's doing things now. They have an open framework, and all customization options are left to third parties. Through the magic of open source, though, we're getting exactly the sorts of things we'd want. The arrow key selector you mentioned is something I'd hoped someone would write; thanks for bringing it up! It does seem like a fairly obvious feature, although I have to admit after trying it that the mouse selection is still probably faster.

---

### Post by werewolves on 2011-11-10
> It would also be nice if I could switch to a workspace with a key combination

I have mine set up for Mod4+F1 through F4.  I didn't need an extension, I just used the keyboard shortcuts >> navigation setting.

---

### Post by don_quixote on 2011-11-10
> **Copper Bezel said:**
> That's just not how Gnome's doing things now. They have an open framework, and all customization options are left to third parties. Through the magic of open source, though, we're getting exactly the sorts of things we'd want. The arrow key selector you mentioned is something I'd hoped someone would write; thanks for bringing it up! It does seem like a fairly obvious feature, although I have to admit after trying it that the mouse selection is still probably faster.

Yeah I suppose...  as long as there is some sort of customization, I don't much mind.  

As for the arrow keys, mouse may be faster on a desktop.  On the laptop with a crappy trackpad, keyboard is definitely a way to go.

> **werewolves said:**
> I have mine set up for Mod4+F1 through F4.  I  didn't need an extension, I just used the keyboard shortcuts >>  navigation setting.

Yeah, I have a similar setup as well.  It doesn't work when in the activities overview though :(

---

### Post by cbowman57 on 2011-11-13
This is more mint than Mint, but with the release of the LM Lisa RC release this deserved some recognition.

The theme is not default Linux Mint.

[ATTACH]207102[/ATTACH]       [ATTACH]207103[/ATTACH]

---

### Post by Hells_Dark on 2011-11-16
Hi, I have a request :]

I find the gnome-shell animation quite good.
Except when I quit the Activity view.
I find it weird because when I open the activity view, it's fast !
But when I close it to go back to the desktop, the animation is weird, like if it was in 2 times.

Am I the only one to think this way ?
I'm not sure I'm making myself understood ^^
But I'm sure it can be resolved :]

---

### Post by cbowman57 on 2011-11-16
Did you already try shortening the length of the animation on line 30 of the overview.js?

---

### Post by cbowman57 on 2011-11-17
Something useful if you'd like the older mount behavior for partitions in Nautilus.

Create this file
```
gksu gedit [FONT=monospace]/etc/polkit-1/localauthority/50-local.d/50-filesystem-mount-system-internal.pkla[/FONT]
```Put this inside the file you just created
```

Mount a system-internal device] 
Identity=* 
Action=org.freedesktop.udisks.filesystem-mount-system-internal 
ResultActive=yes
```Save & exit

Now you won't be prompted every time you want to mount a partition from within Nautilus.

(Borrowed from the [Archwiki Gnome Tips]("https://wiki.archlinux.org/index.php/GNOME_Tips#Turn_off_Authentication_needed_to_mount_internal_drive_in_Nautilus"))

---

### Post by Sonybuntu on 2011-11-17
Arch (old shot) : [http://71kr117.deviantart.com/gallery/31323371#/d48yhql](http://71kr117.deviantart.com/gallery/31323371#/d48yhql)

I'm in the process of installing 11.10.

---

### Post by Hells_Dark on 2011-11-18
> **cbowman57 said:**
> Did you already try shortening the length of the animation on line 30 of the overview.js?

Well, It's faster but not smoother. Nevermind.

I have another issue : I can't hide the gnome-terminal menu..
It's like.. forced :???:

---

### Post by Psyael on 2011-11-19
There seems to be some very smart GNOME users in this thread, so I thought I'd ask a question: is there any way to get rid of that bar that hides at the bottom of the screen? 3.2 was an improvement on 3.0 in that it only pops up in the very bottom right corner, but that can still be a nuisance in applications like 3D games, especially if even when hidden it still leaves a 'line' across the bottom row of pixels, which the setup I'm using currently does.

I need to figure out how to remove that 'line' at least, probably a theme setting, though I wish there was some way to get rid of that hidden bottom taskbar altogether.

---

### Post by cbowman57 on 2011-11-19
Well moving or renaming messageTray.js doesn't work so don't try that. :)

I took a quick look at the .js file, I'm sure there is a way to disable it, but the solution didn't jump out at me.  Hopefully someone more familiar with java script can come up with a solution for you.

---

### Post by Frogs Hair on 2011-11-19
Hello Shell Users ,

I tried the instruction at the link to reduce icon size and it works until restart . It seems the saved changes to css revert after restart . I was wondering if the instruction is incomplete in some way ?

[http://abhizweblog.blogspot.com/2011/06/gnome3-change-icon-size.html](http://abhizweblog.blogspot.com/2011/06/gnome3-change-icon-size.html)

---

### Post by cbowman57 on 2011-11-19
Yeah, it doesn't take into account user themes from what I can see.

Did you already try editing the corresponding entries in your shell theme?

---

### Post by Frogs Hair on 2011-11-19
No , I didn't , but that's probably the missing link . Thanks !

---

### Post by cbowman57 on 2011-11-19
I'm still trying to learn how everything interacts. ;)

---

### Post by sanderd17 on 2011-11-19
Isn't there an extension to move the notifications to the top bar (I think it's used in Mint).

That would remove the bottom bar.

---

### Post by Copper Bezel on 2011-11-19
You can hide the message tray by setting its size to 0 in gnome-shell.css. Search for "tray."

I haven't tried editing the icon grid spacing (although I will now,) but changing the icon size in the same file changed the size permanently for me. I had to, actually, to use Faenza, which uses massive scalable icons for anything bigger than 48 px and caused the search screen to take forever to fetch them and render.

Edit: No problems scaling the icon grid, either. Lots of little buttons on my tiny netbook screen.

---

### Post by Bobhuber on 2011-11-19
Here are some pics of a custom Tron-Legacy with cairo-dock and screenlets. I made all of the icons in inkscape and gimp along with modifying the basic theme for different colored menu backgrounds etc.

---

### Post by cbowman57 on 2011-11-19
> **Bobhuber said:**
> Here are some pics of a custom Tron-Legacy with cairo-dock and screenlets. I made all of the icons in inkscape and gimp along with modifying the basic theme for different colored menu backgrounds etc.

I rather like that but I noticed there were none with an open window.  What gtk &/or metacity theme do you use to tie it all in?

---

### Post by Bobhuber on 2011-11-19
> **cbowman57 said:**
> I rather like that but I noticed there were none with an open window.  What gtk &/or metacity theme do you use to tie it all in?
It started out with Adwaita - Then modified with pieces of the default gnome-shell - Sammy 0.7.4 from gnome looks.org and the original Tron-legacy.

---

### Post by cbowman57 on 2011-11-19
I'm trying to figure out a way to keep my username from being displayed in the status menu.  I used to have a way to do it with the old version but they've made some significant changes since then.

If anyone comes across a way to do it I'd appreciate knowing about it.

I don't want to get rid of the im status, just my name, but if you run across a noim extension that works with 3.2 maybe I could take a look & see if anything inside gives me a clue.

---

### Post by actprime on 2011-11-21
The modifications to ubuntu 11.10 to get back to a useful desktop are getting far too much.
1.First I have to get the menu based Classic layout ( now requires installing software) , 
2. The I have to switch window buttons to the right ( I can do that)
3. I have to get windows with a theme I can see & not these black shadows.   I cannot find that at present because the preferences menu has disappeared along with lots of other items. text editor , terminal .   I cannot remember all these shortcuts mentioned in most posts .

Solution - revert back to 11.04 .
I guess I will be back on XP after that & after that

---

### Post by cbowman57 on 2011-11-21
Remove username from top panel:

Open up userMenu.js & locate this line: ```
_updateUserName: function() {
```

Then comment out the next 4 lines:    ```
 _updateUserName: function() {
       // if (this._user.is_loaded)
       //     this._name.set_text(this._user.get_real_name());
      //  else
       //     this._name.set_text("");
```

The result is a user menu that doesn't display your name.
[ATTACH]207733[/ATTACH]

---

### Post by cbowman57 on 2011-11-21
> **actprime said:**
> The modifications to ubuntu 11.10 to get back to a useful desktop are getting far too much.
1.First I have to get the menu based Classic layout ( now requires installing software) , 
2. The I have to switch window buttons to the right ( I can do that)
3. I have to get windows with a theme I can see & not these black shadows.   I cannot find that at present because the preferences menu has disappeared along with lots of other items. text editor , terminal .   I cannot remember all these shortcuts mentioned in most posts .

Solution - revert back to 11.04 .
I guess I will be back on XP after that & after that

This isn't a "I'm gonna kill myself if Ubuntu doesn't revive Gnome 2" thread.  Plenty of those available, I have no idea why you thought this comment belongs here.

---

### Post by Copper Bezel on 2011-11-21
Indeed, given he's talking about Unity, anyway. Neat trick re: the username!

Argh, the Shell search is irritating the hell out of me. It uses ~/.local/share/recently-used.xbel rather than Zeitgeist, which is fine, except that it never clears old paths from moved or deleted items and doesn't indicate that they're deleted. I started _[a bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/892997")_ on this. The alternative, using one of the Zeitgeist-based search extensions, would be equally fine if not for the fact that they're all actually the same extension and break the use of the Enter key in the search. I really don't know which is worse.

---

### Post by cbowman57 on 2011-11-21
> **Copper Bezel said:**
> Indeed, given he's talking about Unity, anyway. Neat trick re: the username!

I do get tired of the noise, but yeah, I like the clean look up in the panel, plus I have a tendency to orient everything to upper right & I like it compact.
> 
Argh, the Shell search is irritating the hell out of me. It uses ~/.local/share/recently-used.xbel rather than Zeitgeist, which is fine, except that it never clears old paths from moved or deleted items and doesn't indicate that they're deleted. I started _[a bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/892997")_ on this. The alternative, using one of the Zeitgeist-based search extensions, would be equally fine if not for the fact that they're all actually the same extension and break the use of the Enter key in the search. I really don't know which is worse.

Haven't run into that myself but it's almost like the zeitgeist search brings up too much info, not sure that I actually like it, jury is still out. Seems it tries to default to contacts if it can't locate anything else.  I think we need more tools like activity log manager to "tune" what it finds.

Do you have a link to that search extension you're using?  I might try it out & see if i suits me.

btw, I started a thread this evening for extensions, new, different, modified, etc.  So if you run across anything interesting.  [http://ubuntuforums.org/showthread.php?t=1884693](http://ubuntuforums.org/showthread.php?t=1884693)

---

### Post by Copper Bezel on 2011-11-21
Yeah, I saw your other thread - very cool. = )

On the searching - really, all of the Zeitgeist search extensions have this problem. An example is [_this one_]("http://www.omgubuntu.co.uk/2011/10/nifty-gnome-shell-extensions-zeitgeist/"), "Zeitgeist Search," but there's one called "Gimme" and one called "Advanced Search" that all behave the same way. Anyway, they're unusable as far as I'm concerned, because they break the basic type-and-hit-Enter launching that Shell wants to use as the basic way to launch non-Favorite apps. That boils down to "the Enter key doesn't work," and that's really my only complaint with them, but it's a big one.

My hangup is that the basic search, without any extensions, doesn't use Zeitgest at *all*. It doesn't respond to the Activity Log Manager (so "private" files display in the search) and it doesn't remove deleted items. I don't mind the "noise" of extra items returned by indexed content, etc. from Zeitgeist, but it's absurd to me that the search includes items that no longer exist, or have been moved, or I've specifically excluded from indexing.

I get the contacts items, too, and they're fairly useless, of course. They're usually off the bottom of the screen and I just tend to ignore them.

---

### Post by cbowman57 on 2011-11-21
Ah, ok, it will locate them but then you have to mouse-click to launch?

Yeah, just looked, I was using the "Advanced Search", I disabled that and like the way it searches better. One less extension to load I guess. :)

I'm still feeling my way along, I know that in time there will be a specific set of extensions that I'll want to install but I haven't arrived at that yet.

---

### Post by actprime on 2011-11-24
> **cbowman57 said:**
> This isn't a "I'm gonna kill myself if Ubuntu doesn't revive Gnome 2" thread.  Plenty of those available, I have no idea why you thought this comment belongs here.
When you have taken about 5 hrs to do an "upgrade" and a few more hours to try & make sense of it . Then you decide someone should be told, you don't expect abuse.
Its true I am not a habitual of such forums - but in 2009 ubuntu was pretty useful , maybe I should change to  LTS so I don't hit incompatibility problems so often.

---

### Post by BlinkinCat on 2011-11-25
I have what is probably a really simple question but I don't know the answer.

I am using gnome shell but don't know how to use the tweak tool to activate the User-Theme extension which I downloaded from Web Upd8 GNOMES PPA?

Could you help me out? I have posted a question on the forum with no result.

I hope you can help me,

Edit - I solved problem with the help of this thread but not sure what I actually did.

[http://ubuntuforums.org/showthread.php?t=1746110](http://ubuntuforums.org/showthread.php?t=1746110)

I would very much appreciate it cbowman57 if you could spell out the actual procedure in activating the Theme via the tweak tool - I'm not real bright.  

Regards - :)

---

### Post by cbowman57 on 2011-11-25
Not sure I am either. :)

I think that old thread was in regards to mis-matched user theme extensions.

If you have gnome-tweak-tool (Advanced Settings..) installed it's just a matter of selecting the theme.

I ran into this same problem the other day with a fresh Precise installation, I think rebooting might have been what fixed it after installing the theme extension.  

Is it still giving you problems?

---

### Post by Perfect Storm on 2011-11-26
Is it possible to set a sub-category like 'games' or 'internet' in application overview to a different icon size than the rest?

From the .css;

```

/* Apps */

.icon-grid {
    spacing: 50px;
    -shell-grid-item-size: 210px;
}

.contact-grid {
    spacing: 36px;
    -shell-grid-item-size: 272px; /* 2 * -shell-grid-item-size + spacing */
}

.icon-grid .overview-icon {
    icon-size: 192px;
}

.all-app {
    padding: 2px 0 5px 10px;
    spacing: 60px;
    font-size: 8pt;
```

I can tweak all the icon size, space between etc. 
My question; is it possible?

---

### Post by Frogs Hair on 2011-11-26
> **Artificial Intelligence said:**
> Is it possible to set a sub-category like 'games' or 'internet' in application overview to a different icon size than the rest?

From the .css;

```

/* Apps */

.icon-grid {
    spacing: 50px;
    -shell-grid-item-size: 210px;
}

.contact-grid {
    spacing: 36px;
    -shell-grid-item-size: 272px; /* 2 * -shell-grid-item-size + spacing */
}

.icon-grid .overview-icon {
    icon-size: 192px;
}

.all-app {
    padding: 2px 0 5px 10px;
    spacing: 60px;
    font-size: 8pt;
```

I can tweak all the icon size, space between etc. 
My question; is it possible?

I don't know if this helps , but I tried the method at the link for changing all icons and the changes would not remain after reboot . It was suggested on this thread that the GTK theme CSS may require changes also.

 [http://abhizweblog.blogspot.com/2011/06/gnome3-change-icon-size.html](http://abhizweblog.blogspot.com/2011/06/gnome3-change-icon-size.html)

---

### Post by cbowman57 on 2011-11-26
The shell theme affects the changes to overview.js so you also need to look at that to see what portions of the default it changes.

---

### Post by Tomween1 on 2011-11-26
sorry man, gotta say it's all real confusing to me. I have read almost EVERY post here and I'm still a lost cause. I tried using this thread [GTK3 Mac OS X Lion]("http://www.upubuntu.com/2011/11/how-to-install-gtk3-mac-os-x-lion-theme.html") to install the theme. Not so good :(

---

### Post by cbowman57 on 2011-11-26
> **Tomween1 said:**
> sorry man, gotta say it's all real confusing to me. I have read almost EVERY post here and I'm still a lost cause. I tried using this thread [GTK3 Mac OS X Lion]("http://www.upubuntu.com/2011/11/how-to-install-gtk3-mac-os-x-lion-theme.html") to install the theme. Not so good :(

A what point did it go bad?

I'm assuming gnome-tweak-tool is installed, are you being given the option of switching themes?  If not than you are probably lacking the exension for user-themes.

That link is straightforward but it assumes that you already have extension & theme support installed.

---

### Post by cbowman57 on 2011-11-26
Ok, for the shell you need to install a couple things to enable extension & theme support.  To get started you are going to want to install :

[https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-common_3.2.0-2%7Ewebupd8%7Eoneiric_all.deb](https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-common_3.2.0-2%7Ewebupd8%7Eoneiric_all.deb) & [https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-user-theme_3.2.0-2%7Ewebupd8%7Eoneiric_all.deb](https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-user-theme_3.2.0-2%7Ewebupd8%7Eoneiric_all.deb) at a minimum.  If it gives you extensions that you don't want you can leave them disabled or delete them.

& gnome-tweak-tool, it's in the repository.

---

### Post by Tomween1 on 2011-11-26
> **cbowman57 said:**
> Ok, for the shell you need to install a couple things to enable extension & theme support.  To get started you are going to want to install :

[https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-common_3.2.0-2%7Ewebupd8%7Eoneiric_all.deb](https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-common_3.2.0-2%7Ewebupd8%7Eoneiric_all.deb) & [https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-user-theme_3.2.0-2%7Ewebupd8%7Eoneiric_all.deb](https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-user-theme_3.2.0-2%7Ewebupd8%7Eoneiric_all.deb) at a minimum.  If it gives you extensions that you don't want you can leave them disabled or delete them.

& gnome-tweak-tool, it's in the repository.First off... Thank you for this post and your help

Yup, installed the Gnome tt. Shortly after installation of 11.10. That is the only way I've been able to do any customization. 

Regarding where did it go wrong... When cut and paste (or even type out) the commands from the link I get errors. When I retry, it works. Or so it seems, the commands never show in advanced settings (Gtt)

All of this aside, If I end up getting it to work, will I lose it all when I upgrade to 12.10?

---

### Post by aeronutt on 2011-11-26
FYI Mint 12 final iso is released, and I'm liking it. (Comes with gnome-shell installed and as default, with about 10 or so extensions; many of which I've turned off. :))

---

### Post by cbowman57 on 2011-11-26
> **Tomween1 said:**
> First off... Thank you for this post and your help

Yup, installed the Gnome tt. Shortly after installation of 11.10. That is the only way I've been able to do any customization. 

Regarding where did it go wrong... When cut and paste (or even type out) the commands from the link I get errors. When I retry, it works. Or so it seems, the commands never show in advanced settings (Gtt)

All of this aside, If I end up getting it to work, will I lose it all when I upgrade to 12.10?

Make sure you restart the shell (alt+f2 r enter) & close & reopen gnome-tweak-tool so it reads in the extensions (if necessary).

No, updating to 12.10 shouldn't break any extensions, unless of course they go with GS 3.4 by then, in which case it's hard telling if the current extensions will keep up.

---

### Post by sanderd17 on 2011-11-26
One would think I have enough experience to solve this, nevertheless, I have a pretty silly problem.

I had some problems with Gnome breaking (it just stopped working, and I could't even get into the tty to check the problem). Now, I have removed and reinstalled gnome, and the crashing is over. Hurray for that. But now I have a problem with themes.

As you see on the screenshot, I have the user-themes extension enabled, but I'm still unable to select a theme (with the text that I need to install the user themes extension). And all this while other extensions work (you can see the weather extension on the screenshot).

Does anyone has an idea?

---

### Post by cbowman57 on 2011-11-26
Double check looking glass & see if there are any clues.

Also, reboot if you haven't already tried that.

---

### Post by Perfect Storm on 2011-11-26
> **Frogs Hair said:**
> I don't know if this helps , but I tried the method at the link for changing all icons and the changes would not remain after reboot . It was suggested on this thread that the GTK theme CSS may require changes also.

 [http://abhizweblog.blogspot.com/2011/06/gnome3-change-icon-size.html](http://abhizweblog.blogspot.com/2011/06/gnome3-change-icon-size.html)

I'm aware on how to change the icon size in application overview. The thing I'm looking for is if it's possible to have two different size icons in the applications overview.
The reason is I'm setting up some ubuntu gaming desktop, where the icons in the 'Games' category needs to be bigger than the rest.

See: [http://ubuntuforums.org/showpost.php?p=11490060&postcount=491](http://ubuntuforums.org/showpost.php?p=11490060&postcount=491)

---

### Post by cbowman57 on 2011-11-26
I don't know how that would be done but it seems possible the more I think about it.  An overview or theme extension **might** be able to adjust the display size for certain categories but that's hypothetical & I wouldn't have any idea where to start.

appDisplay.js maybe?

Here's a thought, but I don't know how exactly to make it work.  Copy appDisplay.js to something extension.js & build it into an extension so that you'd have Windows, Applications, Games when you activate overview, it's own little menu that you could modify your icons & spacing to suit.  That may actually be a lot easier than having the overview.js or appDisplay.js parse out the Games category.

I started a thread specifically for custom extension contributions, maybe we should widen the scope for brainstorming extensions?

---

### Post by BlinkinCat on 2011-11-26
> **cbowman57 said:**
> Not sure I am either. :)

I think that old thread was in regards to mis-matched user theme extensions.

If you have gnome-tweak-tool (Advanced Settings..) installed it's just a matter of selecting the theme.

I ran into this same problem the other day with a fresh Precise installation, I think rebooting might have been what fixed it after installing the theme extension.  

Is it still giving you problems?

I changed theme and that seemed to do the trick - I have now installed all published extensions without a hitch. Thanks for a great thread Chuck.

Keep up the good work - :)

---

### Post by cbowman57 on 2011-11-26
@BlinkinCat, glad you got it working. :)

---

### Post by sanderd17 on 2011-11-27
The looking glass shows that the user themes extension is loaded without problems, and is now active. I don't see any problems.

---

### Post by cbowman57 on 2011-11-27
> **sanderd17 said:**
> The looking glass shows that the user themes extension is loaded without problems, and is now active. I don't see any problems.

Did you get it working?
I had a theme, or the theme extension, do something strange the other day.  Anyhow, I was in the process of trying some things & ran into what appeared to be this same problem.  What happened to me is that something renamed /usr/share/gnome-shell/themes to themes.original and created a link called themes that connected to the actual theme directory.  I don't remember the name of the theme that it occurred with.

You might also try a different user themes extension from a different source.  

Let me know how it goes, and what you discover.

---

### Post by Tomween1 on 2011-11-27
Hey Chuck, what do I use for a screen shooting tool? I have screens to share that I just don't understand.

It took me a day to figure out how to "shut down" when running Gnome, but how do I add it as one of the options in the top right (My Name) area? It's in the list when running Unity...

---

### Post by cbowman57 on 2011-11-27
> **Tomween1 said:**
> Hey Chuck, what do I use for a screen shooting tool? I have screens to share that I just don't understand.

It took me a day to figure out how to "shut down" when running Gnome, but how do I add it as one of the options in the top right (My Name) area? It's in the list when running Unity...

PrtScr will still do a screenshot or you can use the gnome-screenshot app if you want to select windows, or have a delay.

For the power off you need the  alternate-status or shutdown extension.

---

### Post by cbowman57 on 2011-11-27
Been tinkering with subtle things, like icon spacing in the panel.

Here's the setup for today.

[ATTACH]208103[/ATTACH]  [ATTACH]208104[/ATTACH]  [ATTACH]208105[/ATTACH]

---

### Post by sanderd17 on 2011-11-28
> **cbowman57 said:**
> Did you get it working?
I had a theme, or the theme extension, do something strange the other day.  Anyhow, I was in the process of trying some things & ran into what appeared to be this same problem.  What happened to me is that something renamed /usr/share/gnome-shell/themes to themes.original and created a link called themes that connected to the actual theme directory.  I don't remember the name of the theme that it occurred with.

You might also try a different user themes extension from a different source.  

Let me know how it goes, and what you discover.

/usr/share/themes is still a directory. I didn't solve the problem this far.

---

### Post by cbowman57 on 2011-11-28
@sanderd17, Other than trying a different user-themes-extension I'm running out of ideas.

---

### Post by maxkaspar on 2011-11-30
> **cbowman57 said:**
> Remove username from top panel:

Open up userMenu.js & locate this line: ```
_updateUserName: function() {
```

Then comment out the next 4 lines:    ```
 _updateUserName: function() {
       // if (this._user.is_loaded)
       //     this._name.set_text(this._user.get_real_name());
      //  else
       //     this._name.set_text("");
```

The result is a user menu that doesn't display your name.
[ATTACH]207733[/ATTACH]

Thank you very much :P

---

### Post by cbowman57 on 2011-11-30
> **maxkaspar said:**
> Thank you very much :P

Glad it worked for you.

Not sure if I've put this one up before or not.

Never fails, you find that great shell theme & the status icons are strung too far apart, this is where to look in the theme's gnome-shell.css to adjust that. ```
.panel-button {
    -natural-hpadding: 3px;
    -minimum-hpadding: 3px;
```Typically you find numbers between 4-12, but this i pretty close to my spacing for the way I have the panel favorites extension set up.

I'm not sure what the difference is between natural & minimum but I haven't run into a problem with the same value for both.

---

### Post by malspa on 2011-12-01
> **cbowman57 said:**
> Remove username from top panel:

Open up userMenu.js & locate this line: ```
_updateUserName: function() {
```

Then comment out the next 4 lines:    ```
 _updateUserName: function() {
       // if (this._user.is_loaded)
       //     this._name.set_text(this._user.get_real_name());
      //  else
       //     this._name.set_text("");
```

The result is a user menu that doesn't display your name.
[ATTACH]207733[/ATTACH]

Is it possible to replace the username with another word?

---

### Post by satanselbow on 2011-12-01
> **malspa said:**
> Is it possible to replace the username with another word?

Uncomment the 1st and 4th lines only of your quote above and type what you like ;)

```

 this._name.set_text("Custard Cream Biscuits");

```

At a guess the max length would be the same as the max allowable username - 255 characters?

---

### Post by malspa on 2011-12-01
> **satanselbow said:**
> Uncomment the 1st and 4th lines only of your quote above and type what you like ;)

```

 this._name.set_text("Custard Cream Biscuits");

```

At a guess the max length would be the same as the max allowable username - 255 characters?

Ah, yes. Thanks! I like the word "User" there.

---

### Post by malspa on 2011-12-01
This is a good thread. I'm not even using GNOME Shell in Ubuntu yet, only in Fedora 16; but things I've found here have been very helpful.

---

### Post by xircon on 2011-12-01
I started a similar thread on the LMDE forum and have just pinched some stuff from here!  Thanks guys.

I also have some stuff you do not seem to have covered, such as manually changing mouse pointer theme:

[http://forums.linuxmint.com/viewtopic.php?f=201&t=85102&p=504674#p504674](http://forums.linuxmint.com/viewtopic.php?f=201&t=85102&p=504674#p504674)

I am actually on 3.2 now, not 3.0.2

Cheers

Steve

---

### Post by cecilpierce on 2011-12-01
I'm lost or CRS  :confused:

Where is "userMenu.js" located ?

Thanks Chuck for the thread, 
Cec

---

### Post by xircon on 2011-12-01
```
sudo gedit /usr/share/gnome-shell/js/ui/userMenu.js
```

This is my current setup on LMDE:
[[IMG]http://thumbnails64.imagebam.com/16221/309cdb162203483.jpg[/IMG]](http://www.imagebam.com/image/309cdb162203483)

---

### Post by cecilpierce on 2011-12-01
> **xircon said:**
> ```
sudo gedit /usr/share/gnome-shell/js/ui/userMenu.js
```

This is my current setup on LMDE:

Gee Whiz ! Thanks, I cant remember all this stuff and I keep a note book but trying to find things is something else, thanks :)

---

### Post by xircon on 2011-12-01
I use Tomboy, my mind is like a sieve :D

---

### Post by cecilpierce on 2011-12-01
I like your setup, I wish some one would write a book on all these neat setups, I wouldnt have to keep notes that I cant read half the time  :lolflag:

---

### Post by xircon on 2011-12-01
I have been tracking stuff on the Linux Mint Debian Edition forum, when I find good stuff I post it there:

[http://forums.linuxmint.com/viewtopic.php?f=201&t=85102&p=492375#p492375](http://forums.linuxmint.com/viewtopic.php?f=201&t=85102&p=492375#p492375)

Then I found this thread (haven't used Ubuntu since 10.04) full of good stuff, which I will "borrow" :)

But feel free to ask how I have done stuff, I can remember most of it (honest!).  

Gnome 3 is all javascript so everything will work in any distro, so Arch/Fedora forums are also really useful sources of info, along with Finbar's (Murphy) blog, OMGUbuntu and WebUpd8

---

### Post by iamnotthemessiah on 2011-12-01
anyone know how to remove the application title/icon from the top bar? 

[http://i.imgur.com/mPeau.png](http://i.imgur.com/mPeau.png)

---

### Post by xircon on 2011-12-01
The Window list extension changes it in to something more useful (more like the old behaviour on the gnome 2 panel), but I haven't tried to remove it.

---

### Post by Dragonbite on 2011-12-01
> **cecilpierce said:**
> I like your setup, I wish some one would write a book on all these neat setups, I wouldnt have to keep notes that I cant read half the time  :lolflag:

A book or Wiki-page would be great!

Actually Ubuntu's Wiki is pretty open and may be a good place to start tossing these thoughts & ideas!

---

### Post by cbowman57 on 2011-12-01
> **malspa said:**
> Is it possible to replace the username with another word?

If you uncomment the first & fourth line & insert the word you want between the "" I think that will do it but I haven't tried it.

If you do and it works I'd appreciate it if you would put it in a code box and annotate your tweak. :)

* Went back to fix an error & then noticed Satanselbow had already given you a working answer.

---

### Post by cbowman57 on 2011-12-01
> **malspa said:**
> This is a good thread. I'm not even using GNOME Shell in Ubuntu yet, only in Fedora 16; but things I've found here have been very helpful.

I've tried to focus on the shell, not the distro, it all works the same. :)

---

### Post by cbowman57 on 2011-12-01
> **xircon said:**
> I started a similar thread on the LMDE forum and have just pinched some stuff from here!  Thanks guys.

I also have some stuff you do not seem to have covered, such as manually changing mouse pointer theme:

[http://forums.linuxmint.com/viewtopic.php?f=201&t=85102&p=504674#p504674](http://forums.linuxmint.com/viewtopic.php?f=201&t=85102&p=504674#p504674)

I am actually on 3.2 now, not 3.0.2

Cheers

Steve

Good deal, I frequent the Mint forum too.  I used to run the shell on LMDE but gravitated away from it.  Still really like Ubuntu but I spend most of my time with Arch these days.

---

### Post by cbowman57 on 2011-12-01
> **cecilpierce said:**
> Gee Whiz ! Thanks, I cant remember all this stuff and I keep a note book but trying to find things is something else, thanks :)

It is a challenge for us old timers. :)

---

### Post by Copper Bezel on 2011-12-01
[QUOTE=cbowman57]I've tried to focus on the shell, not the distro, it all works the same. :)[/QUOTE]
In the main, yes, although I think there are small differences. The Alternate Tab extension seems universally broken in Ubuntu, for instance.

---

### Post by cbowman57 on 2011-12-01
> **Copper Bezel said:**
> In the main, yes, although I think there are small differences. The Alternate Tab extension seems universally broken in Ubuntu, for instance.

True, Ubuntu has their own way of doing things.

---

### Post by Dragonbite on 2011-12-01
> **cbowman57 said:**
> I've tried to focus on the shell, not the distro, it all works the same. :)

That's good to know.  One of the things I am hesitant with Unity is that it is so Ubuntu-centric and the other distros haven't picked it up yet.  I don't want to get too familiar to something that will "lock-me-in" to one distro or another.

Kinda like Ubuntu One isntead of Dropbox or some other cloud drive.

Just a disclaimer, it doesn't mean I don't like Unity.  Actually Unity has some really good parts, and so does Gnome shell.  Until I get a system that can run the Gnome shell, Unity wins on usability and pleasurable interface.

---

### Post by BigSilly on 2011-12-01
I dunno if this is the right place to get a little help with Gnome shell, but I'll give it a go. I'm currently using Gnome 3.2 on openSUSE 64 bit, and it's mostly stunning and excellent, but I've recently found a couple of the shell's application icons have reverted to the Gnome default "execute" icon. I don't know why this should be, they were there one minute then the next they'd changed. I installed a new theme in the hope this would improve things, but of course it hasn't. Any ideas? Thanks.

---

### Post by cbowman57 on 2011-12-01
> **BigSilly said:**
> I dunno if this is the right place to get a little help with Gnome shell, but I'll give it a go. I'm currently using Gnome 3.2 on openSUSE 64 bit, and it's mostly stunning and excellent, but I've recently found a couple of the shell's application icons have reverted to the Gnome default "execute" icon. I don't know why this should be, they were there one minute then the next they'd changed. I installed a new theme in the hope this would improve things, but of course it hasn't. Any ideas? Thanks.

If the icons changed universally I'd suspect a bug in the shell or a theme, if it's just in the panel or menu I'd suspect an extension.

---

### Post by BigSilly on 2011-12-01
> **cbowman57 said:**
> If the icons changed universally I'd suspect a bug in the shell or a theme, if it's just in the panel or menu I'd suspect an extension.

No it's literally just around five of the icons or so. I try to change them manually with Alacarte, but that doesn't work. :confused:

---

### Post by cbowman57 on 2011-12-01
> **BigSilly said:**
> No it's literally just around five of the icons or so. I try to change them manually with Alacarte, but that doesn't work. :confused:

Ok, I think that might be a question for the folks running Suse.

You changed the icons individually with alacarte to start with then they changed, or they changed from the installed icon theme on their own?

---

### Post by BigSilly on 2011-12-01
> **cbowman57 said:**
> Ok, I think that might be a question for the folks running Suse.

You changed the icons individually with alacarte to start with then they changed, or they changed from the installed icon theme on their own?

When I installed the apps, the icons showed up fine as they should, but then after a reboot they just changed. One of the applications is a game I won (here, as it happens!), that I have as both a .deb and a .rpm; And Yet It Moves. When I installed it, the dark cave icon showed as it should and does in other distros, but then a reboot later - gone. Other applications missing icons are ones from the repository - such as ScummVM, ScummVM Tools, SuSe Studio Imagewriter, etc. I'm very confused!

I posted up on the Suse forums, but I can't seem to get on the site at the moment...

---

### Post by cbowman57 on 2011-12-01
> **BigSilly said:**
> When I installed the apps, the icons showed up fine as they should, but then after a reboot they just changed. One of the applications is a game I won (here, as it happens!), that I have as both a .deb and a .rpm; And Yet It Moves. When I installed it, the dark cave icon showed as it should and does in other distros, but then a reboot later - gone. Other applications missing icons are ones from the repository - such as ScummVM, ScummVM Tools, SuSe Studio Imagewriter, etc. I'm very confused!

I posted up on the Suse forums, but I can't seem to get on the site at the moment...

I wonder if it's the too fast gnome-settings-daemon problem.

Try the info I found [here.]("http://ubuntuforums.org/archive/index.php/t-1704984.html")

Open a terminal & do this ```
killall gnome-settings-daemon
gnome-settings-daemon &
```If that clears it up then apply this workaround.

> Do you happen to have a link to the launchpad bug report?

This is the bug, still in progress:
Bug #649809
It is an upstream bug in gdm, caused by a race situation.

This is the workaround:
Add a delay (here 1 sec) before gnome-settings-daemon starts.
Change the line of the file /etc/xdg/autostart/gnome-settings-daemon.desktop:
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
to
Exec=bash -c "sleep 1; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

---

### Post by Copper Bezel on 2011-12-01
The race situation doesn't exist in Ubuntu, because Ubuntu doesn't use GDM. It uses LDM instead, which doesn't use Gnome Settings Daemon.

I have had Gnome Settings Daemon crash randomly, though (often soon after resume from suspend.) The result is that all GTK skinning is immediately lost and all icons revert to default, which is different from what BigSilly is describing.

---

### Post by BigSilly on 2011-12-01
Fixed thanks to [this reply on the openSUSE forums]("http://forums.opensuse.org/english/get-technical-help-here/applications/469032-gnome-3-shell-icons-changed-help.html#post2413235"). Hope this proves useful to others, so posting it up here too. Thanks all. :)

---

### Post by cbowman57 on 2011-12-01
> **Copper Bezel said:**
> The race situation doesn't exist in Ubuntu, because Ubuntu doesn't use GDM. It uses LDM instead, which doesn't use Gnome Settings Daemon.

I have had Gnome Settings Daemon crash randomly, though (often soon after resume from suspend.) The result is that all GTK skinning is immediately lost and all icons revert to default, which is different from what BigSilly is describing.

Ok, I had to re-read this, at first glance I thought it said Ubuntu doesn't use gnome-settings-daemon. :)    

Then I realized what you really wrote.

@BigSilly, glad you found the cure.  Been a lot of years since I had to apply that on linux, but I do vaguely remember doing that once or twice.

---

### Post by cecilpierce on 2011-12-02
Just wondering, after I changed user name in top bar I still get it when I click on it, besides a few blank screens while editing the file and I didnt have any "//" marks in there to remove but putting them in lines two and three it booted OK,
Im not to hip on this stuff but its fun watching you guys do all this niffty stuff  :P

---

### Post by cecilpierce on 2011-12-02
forgot the pic ! dah :confused:

cant hardly see the new name for the X, its Me

---

### Post by iamnotthemessiah on 2011-12-02
to answer my own questions [https://extensions.gnome.org/](https://extensions.gnome.org/) is up and running and theres an extension there that removes the app icon and name from the top panel :D

some other nice extensions there too

---

### Post by xircon on 2011-12-02
> **cecilpierce said:**
> forgot the pic ! dah :confused:

cant hardly see the new name for the X, its Me

Nice!  Like the wallpaper, where did you get it?

---

### Post by cbowman57 on 2011-12-02
> **iamnotthemessiah said:**
> to answer my own questions [https://extensions.gnome.org/](https://extensions.gnome.org/) is up and running and theres an extension there that removes the app icon and name from the top panel :D

some other nice extensions there too

Hey, that's right, it was coming on line, almost forgot about that.

---

### Post by cbowman57 on 2011-12-02
> **cecilpierce said:**
> forgot the pic ! dah :confused:

cant hardly see the new name for the X, its Me

Looks like you got it. :)

---

### Post by cecilpierce on 2011-12-02
> **xircon said:**
> Nice!  Like the wallpaper, where did you get it?

art.gnome.org/backgrounds

Category>gnome> page 5

lot of nice ones there

---

### Post by cecilpierce on 2011-12-02
> **iamnotthemessiah said:**
> to answer my own questions [https://extensions.gnome.org/](https://extensions.gnome.org/) is up and running and theres an extension there that removes the app icon and name from the top panel :D

some other nice extensions there too

I tried the site and I got this: 
"You do not appear to have an up to date version of GNOME3. You won't be able to install extensions from here. See the about page for more information"
Version here is 3.2.1
:confused:

---

### Post by xircon on 2011-12-02
You have to use only firefox for the time being, but I can't get anything to install:confused:

I turn the extension on and nothing happens.

---

### Post by cecilpierce on 2011-12-02
> **xircon said:**
> You have to use only firefox for the time being, but I can't get anything to install:confused:

I turn the extension on and nothing happens.

Fir some weird reason I cant get firefox to install  :confused:
I'll try another ubuntu install that has firefox working, thanks

---

### Post by iamnotthemessiah on 2011-12-02
> **xircon said:**
> You have to use only firefox for the time being, but I can't get anything to install:confused:

I turn the extension on and nothing happens.


works fine here but im on lm12 with firefox8

---

### Post by cecilpierce on 2011-12-02
got it going with GS v3.2.1 in ubuntu 11.10 with Firefox  :P

---

### Post by cecilpierce on 2011-12-02
> **xircon said:**
> You have to use only firefox for the time being, but I can't get anything to install:confused:

I turn the extension on and nothing happens.

Did you click on the off and on button in the upper left ? it brought up a install when I clicked 'ON' and it installed and worked without rebooting

---

### Post by xircon on 2011-12-02
Nope, will investigate tomorrow.

---

### Post by cecilpierce on 2011-12-02
Maybe Chuck can help you figure it out, Im not to hip on this stuff, I finally got Firefox working, had to copy the .mozilla directory over here from one that worked and its up and running now  :confused:

Going to try to install some now.

---

### Post by cbowman57 on 2011-12-02
Found a nice theme today called GnomishDark.  Thought I'd mess around with the MGSE bottom panel & see how hard it is to theme, seems to be pretty simple.

[ATTACH]208414[/ATTACH]

To have your bottom panel look like your top panel (should work with any theme), copy the **#panel** entry and name it **#bottomPanel**.  Should look something like this:

```

**#panel** {
    background-gradient-direction: vertical;
    background-gradient-start: rgba(88,88,88,0.7);
    background-gradient-end: rgba(0,0,0,0.6);
    color: rgba(255,255,255,0.98);
    border-top: 0px;
    border-left: 0px;
    border-right: 0px;
    height: 24px;
    box-shadow: 0px 3px 12px rgba(0,0,0,0.9);
    font-family: MintSpirit, cantarell, ubuntu, serif;
    font-size: 10pt;
}

**#bottomPanel** {
    background-gradient-direction: vertical;
    background-gradient-start: rgba(88,88,88,0.7);
    background-gradient-end: rgba(0,0,0,0.6);
    color: rgba(255,255,255,0.98);
    border-top: 0px;
    border-left: 0px;
    border-right: 0px;
    height: 24px;
    box-shadow: 0px 3px 12px rgba(0,0,0,0.9);
    font-family: MintSpirit, cantarell, ubuntu, serif;
    font-size: 10pt;
}
```*Modified GnomishDark theme attached.

[Link to original extension.]("http://gnome-look.org/content/show.php/GnomishDark?content=147290")

---

### Post by sanderd17 on 2011-12-03
Most extensions from the site show OK, and they install well. But I still have problems with one extension (still the user-theme).

Any ideas?

```
[sander@arch ~]$ pacman -Q gnome-desktop
gnome-desktop 3.2.1-1
```

---

### Post by cbowman57 on 2011-12-03
sanderd17, this is the user-theme-extension I'm using on my Arch setup.

Not certain but I might have just snagged this from git a day or so ago.

---

### Post by sanderd17 on 2011-12-03
> **cbowman57 said:**
> sanderd17, this is the user-theme-extension I'm using on my Arch setup.

Not certain but I might have just snagged this from git a day or so ago.

Bloody hell, now I get a segmentation fault when I try to open gnome tweak tool. And before that, it complains that the user theme extension is not installed. The looking glass shows that the extension is enabled though.

I'm gonna try to remove all relevant settings directories.

EDIT: Ok, now I can open my gnome-tweak-tool again, but I still can't use the user theme extension.

---

### Post by cbowman57 on 2011-12-03
> **sanderd17 said:**
> Bloody hell, now I get a segmentation fault when I try to open gnome tweak tool. And before that, it complains that the user theme extension is not installed. The looking glass shows that the extension is enabled though.

I'm gonna try to remove all relevant settings directories.

EDIT: Ok, now I can open my gnome-tweak-tool again, but I still can't use the user theme extension.

I'm guessing that you tried it in both /usr/share/gnome-shell/extensions & ~/.local/share/gnome-shell/extension?  Shouldn't make a difference but it might.

---

### Post by cbowman57 on 2011-12-06
Ok, today's Ubuntu setup highlighting the [Quick Launch]("https://extensions.gnome.org/extension/37/quicklaunch/") extension.

[ATTACH]208633[/ATTACH]   [ATTACH]208634[/ATTACH]

---

### Post by BigSilly on 2011-12-06
I love trying out the new Gtk3 and Shell themes, but if I'm completely honest I haven't found anything that's made me want to switch away from the default Adwaita theme. I always come back to it, because I find something that I don't like in the newer themes, such as tool boxes that are a bit clunky and old looking, or greyed out icons that just don't look very nice. Adwaita seems to me to be the most complete and polished theme, but it's early days I suppose and I'll keep an eye on this thread for upcoming fresh new themes. :)

---

### Post by cbowman57 on 2011-12-06
Adwaita is just too shiny for my taste but it's fast & works well, and from what I remember never caused a crash.

I'm just trying to give the thread some color, it's not really about the themes, it was intended to try & share what we're learning about different tweaks, settings, extensions, etc.. though there is also a separate thread to focus more on extensions.

---

### Post by BigSilly on 2011-12-06
> **cbowman57 said:**
> Adwaita is just too shiny for my taste but it's fast & works well, and from what I remember never caused a crash.

I'm just trying to give the thread some color, it's not really about the themes, it was intended to try & share what we're learning about different tweaks, settings, extensions, etc.. though there is also a separate thread to focus more on extensions.

No, no, I'm not criticising! I love the theme discussions and screenshots, be they Gtk3 or Shell themes. It's massively cool to see how it's all progressing. I just haven't found any themes I like more than the default yet. ;)

---

### Post by xircon on 2011-12-06
I like the Nord theme, the rest are a bit black, prefer a transparent bar.  Where abouts in Sheffield are you?  I am in Hillsborough :)

---

### Post by BigSilly on 2011-12-06
> **xircon said:**
> I like the Nord theme, the rest are a bit black, prefer a transparent bar.  Where abouts in Sheffield are you?  I am in Hillsborough :)

Not far from you really. I'm at Sheffield Lane Top. :)

---

### Post by cortman on 2011-12-06
> **BigSilly said:**
> I love trying out the new Gtk3 and Shell themes, but if I'm completely honest I haven't found anything that's made me want to switch away from the default Adwaita theme. I always come back to it, because I find something that I don't like in the newer themes, such as tool boxes that are a bit clunky and old looking, or greyed out icons that just don't look very nice. Adwaita seems to me to be the most complete and polished theme, but it's early days I suppose and I'll keep an eye on this thread for upcoming fresh new themes. :)

Have you tried MetalX and Aqua? Aqua was a bit transparent for my tastes, and I tweaked a few colors on MetalX to where it's just about perfect for me.

---

### Post by BigSilly on 2011-12-06
> **cortman said:**
> Have you tried MetalX and Aqua? Aqua was a bit transparent for my tastes, and I tweaked a few colors on MetalX to where it's just about perfect for me.

I've tried the Aqua shell theme and quite liked it, but not enough to switch. I'm now trying out Dark Shine, and the Evolve window bar. I tried the Evolve Gtk3 theme but didn't like what it did to the bookmark toolbar buttons on Firefox, so I'm using the above with Adwaita and I like it so far. :)  Dark shine is a nice shell theme, and I like how it doesn't make a fuss of the transparent bar at the bottom in the shell overview. You can hardly see it unless there's something like Banshee on it. It's the one thing Gnome Shell can do without imho - having a whole bar at the bottom. Only the right hand side ever gets used!

---

### Post by cortman on 2011-12-06
> **BigSilly said:**
> It's the one thing Gnome Shell can do without imho - having a whole bar at the bottom. Only the right hand side ever gets used!

AMEN to that one! I tried for a long time to locate an extension to remove the message tray, even contacting the legendary FP Murphy himself, but to no avail. So I'm trying my hand at Javascript here, to see if I can do it myself.

---

### Post by BigSilly on 2011-12-06
> **cortman said:**
> AMEN to that one! I tried for a long time to locate an extension to remove the message tray, even contacting the legendary FP Murphy himself, but to no avail. So I'm trying my hand at Javascript here, to see if I can do it myself.

I like having a notification on the bottom right for Banshee, Thunderbird, whatever, but I just don't see the point of the whole bar. It does nothing.

---

### Post by cortman on 2011-12-06
> **BigSilly said:**
> I like having a notification on the bottom right for Banshee, Thunderbird, whatever, but I just don't see the point of the whole bar. It does nothing.

Sure, part of my strategy is to somehow incorporate those notifications into the top bar.

---

### Post by cbowman57 on 2011-12-06
> **cortman said:**
> Sure, part of my strategy is to somehow incorporate those notifications into the top bar.

Use Finn's gnote extension, once you look in it you'll see how easy it is to add additional programs.

Real life has Finn busy right now so it might be a while before he gets a chance to create any new extensions.

---

### Post by BigCityCat on 2011-12-06
I put this stuff together. There is a bunch of things in there.

[http://sishnizzle.deviantart.com/#/d4e4qnh](http://sishnizzle.deviantart.com/#/d4e4qnh)

---

### Post by cbowman57 on 2011-12-07
If anyone is interested in collaborating on a theme I've started a thread [here]("http://ubuntuforums.org/showthread.php?p=11521177#post11521177") & would seriously be interested in some assistance.

Here's the link again ["**Help me name this Gnome shell theme"**]("http://ubuntuforums.org/showthread.php?p=11521177#post11521177")

---

### Post by Frogs Hair on 2011-12-13
_Login Sound Fix-Gnome Shell on Ubuntu_

Install the following. 

sudo apt-get install dconf-tools 

Open from dash by typing dcon .

Proceed to org > gnome > desktop > sound and make sure event sounds box is checked . 

Next to "theme name" replace the words "free desktop" with ubuntu in lower case .

---

### Post by cbowman57 on 2011-12-13
> **Frogs Hair said:**
> _Login Sound Fix-Gnome Shell on Ubuntu_

Install the following. 

sudo apt-get install dconf-tools 

Open from dash by typing dcon .

Proceed to org > gnome > desktop > sound and make sure event sounds box is checked . 

Next to "theme name" replace the words "free desktop" with ubuntu in lower case .

For some reason that doesn't like to stick sometimes.  The freedesktop sound theme are oga files, what I've found works best is just to copy the contents of the ubuntu sound theme into the freedesktop folder.

YMMV, the preferred method is to use dconf-editor, but if that doesn't work try my workaround.

---

### Post by cbowman57 on 2011-12-15
This is what's been occupying my time lately.

[ATTACH]209148[/ATTACH]   [ATTACH]209149[/ATTACH]

---

### Post by cbowman57 on 2011-12-22
@Cecil

You might like this one [RatRod]("http://cbowman57.deviantart.com/#/d4jpn4z")

---

### Post by Frogs Hair on 2011-12-22
Hi Chuck ,

I like the changes to shell theme . I think the gold highlights look nice when I center this wallpaper . RatRod is not working for me , the color is right but the theme looks like a dark version of  the root administrative theme . I will reinstall and get back to you .

---

### Post by cbowman57 on 2011-12-22
> **Frogs Hair said:**
> Hi Chuck ,

I like the changes to shell theme . I think the gold highlights look nice when I center this wallpaper . RatRod is not working for me , the color is right but the theme looks like a dark version of  the root administrative theme . I will reinstall and get back to you .

I am really pleased with ChocoLatte, it's a beautiful theme.  A gal over on deviantART applied what she could of it to Gnome 2.32 & it's amazing.

Yeah, RatRod requires the gtk3-engine unico & murrine.  I think I updated that info on Gnome-look, I better check deviantART & make sure I mentioned that somewhere too.

Even if you don't like it I'd at least like you to get a proper look at it. ;)

---

### Post by Frogs Hair on 2011-12-23
Hi , Chuck

Here is my freshly downloaded / installed RatRod theme with the GTK engines installed and restarted . This used to happen with the Atolm theme before updated . :confused:

---

### Post by cbowman57 on 2011-12-23
> **Frogs Hair said:**
> Hi , Chuck

Here is my freshly downloaded / installed RatRod theme with the GTK engines installed and restarted . This used to happen with the Atolm theme before updated . :confused:

It's a puzzle to me, I've had dark themes that did the same on my system, I never was able to solve it.

---

### Post by Frogs Hair on 2011-12-23
A new start blood doesn't work at all , so I wonder if it is related . I don't know how much of that theme was integrated in to your theme .

---

### Post by cbowman57 on 2011-12-23
> **Frogs Hair said:**
> A new start blood doesn't work at all , so I wonder if it is related . I don't know how much of that theme was integrated in to your theme .

Mostly A New Start Blood, only some color changes for the most part.

Are there any other Unico dependent themes that have worked for you?  I think Zukiwito is unico, I never could get a dark theme with it.

Atolm-gtk is built around Adwaita engine, I started modifying that one and located the one I'm using when my frustration level was peaking. :)

---

### Post by Frogs Hair on 2011-12-23
> **cbowman57 said:**
> Mostly A New Start Blood, only some color changes for the most part.

Are there any other Unico dependent themes that have worked for you?  I think Zukiwito is unico, I never could get a dark theme with it.

Atolm-gtk is built around Adwaita engine, I started modifying that one and located the one I'm using when my frustration level was peaking. :)

I have Zukitwo , Zukitwo Colors ,and Zukini all working fine .

---

### Post by cbowman57 on 2011-12-24
> **Frogs Hair said:**
> I have Zukitwo , Zukitwo Colors ,and Zukini all working fine .

Pretty sure I've done some of the development on an Ubuntu install, but maybe I overlooked that.

I did find an error, missing** ;** on a color code on line 65 of the gtk.css.  Shot in the dark but close that & see if it works.

---

### Post by cecilpierce on 2011-12-24
> **cbowman57 said:**
> @Cecil

You might like this one [RatRod]("http://cbowman57.deviantart.com/#/d4jpn4z")

Pretty cool Chuck, brings back the good ole daz  :P

---

### Post by cbowman57 on 2011-12-24
> **cecilpierce said:**
> Pretty cool Chuck, brings back the good ole daz  :P

Yeah, very simple, but I like the color combination.

Did you give it a try?

@Frogs Hair, tried it in Ubuntu & it worked.  Have no idea what the problem is.

I know I had to reinstall unico on one of my installations the other day, it's almost like an update threw it out of whack or something.

---

### Post by Frogs Hair on 2011-12-24
> @Frogs Hair, tried it in Ubuntu & it worked. Have no idea what the problem is.

I will try again another time , it's not like I have a lack of working themes . :o

---

### Post by Bobhuber on 2011-12-24
Has anyone gotten the shell extensions site to work (extensions.gnome.org) with the newer versions of Firefox (9.0b6) 
Works in 8.0b6 just fine.

Never Mind - Now it started working - Have no clue.

---

### Post by cbowman57 on 2011-12-24
> **Frogs Hair said:**
> I will try again another time , it's not like I have a lack of working themes . :o

Yeah, I don't stress myself about it  either. :)

---

### Post by cbowman57 on 2011-12-26
Current version of RatRod, image [here.]("http://fc04.deviantart.net/fs70/i/2011/360/4/d/gnome_shell_suite_ratrod_by_cbowman57-d4jpn4z.png")

---

### Post by cbowman57 on 2011-12-28
Ok, as I'm slowly trying to wean myself off of menu extensions & synapse I mapped my old synapse key <menu>, to Activities Overview. (put synapse on ctrl+menu as a security blanket).

Quickly discovered that in comparison to synapse it's a little slow.

Let's speed it up.  Open /usr/share/gnome-shell/js/ui/overview.js line 30 ```
// Time for initial animation going into Overview mode
const ANIMATION_TIME = 0.01;
``` default is 0.25, I cut it drastically as you can see here.

Now locate easeOutQuad, use search & replace to replace 'easeOutQuad with 'default'

In the tweener.js don't forget to change the refresh rate to that of your display (currently line 210) ```
    FRAME_RATE : 170,
```, or you can do what I do, a habit I picked up from using compiz, put in a value of twice your refresh rate, not positive the difference is noticeable but it doesn't break anything.

Let me know what you discover.  For me the Activities Overview now pops into action almost immediately.

Alternatively 'easeNone' can be used in place of 'default' but I can't determine if there is any noticeable difference.

---

### Post by Perfect Storm on 2011-12-28
Anyone know an extension/a hack/an option to disable/remove "all" from the overview?

When you have a lot of stuff, "all" slow down the performance.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209817&stc=1&d=1325079141[/IMG]

---

### Post by Frogs Hair on 2011-12-28
> **cbowman57 said:**
> Ok, as I'm slowly trying to wean myself off of menu extensions & synapse I mapped my old synapse key <menu>, to Activities Overview. (put synapse on ctrl+menu as a security blanket).

Quickly discovered that in comparison to synapse it's a little slow.

Let's speed it up.  Open /usr/share/gnome-shell/js/ui/overview.js line 30 ```
// Time for initial animation going into Overview mode
const ANIMATION_TIME = 0.01;
``` default is 0.25, I cut it drastically as you can see here.

Now locate easeOutQuad, use search & replace to replace 'easeOutQuad with 'default'

In the tweener.js don't forget to change the refresh rate to that of your display (currently line 210) ```
    FRAME_RATE : 170,
```, or you can do what I do, a habit I picked up from using compiz, put in a value of twice your refresh rate, not positive the difference is noticeable but it doesn't break anything.

Let me know what you discover.  For me the Activities Overview now pops into action almost immediately.

Alternatively 'easeNone' can be used in place of 'default' but I can't determine if there is any noticeable difference.

I decided not to use the menu extension because there  didn't seem to be much point in using the shell with it installed .  I am sure it must be faster to access applications with it and maybe I try the above and see if it is faster . I do use the places extension on a regular basis though .

---

### Post by cbowman57 on 2011-12-28
> **Frogs Hair said:**
> I decided not to use the menu extension because there  didn't seem to be much point in using the shell with it installed .  I am sure it must be faster to access applications with it and maybe I try the above and see if it is faster . I do use the places extension on a regular basis though .

Very true, early on though it was my goal to ease the transition so I was trying & using a lot of extensions that emulated the old behavior.  With time though I've come to the conclusion that it just adds an unneeded layer of redundancy that I can do without.

---

### Post by malspa on 2011-12-28
> **Frogs Hair said:**
> I decided not to use the menu extension because there  didn't seem to be much point in using the shell with it installed .  I am sure it must be faster to access applications with it and maybe I try the above and see if it is faster . I do use the places extension on a regular basis though .

> **cbowman57 said:**
> Very true, early on though it was my goal to ease the transition so I was trying & using a lot of extensions that emulated the old behavior.  With time though I've come to the conclusion that it just adds an unneeded layer of redundancy that I can do without.

This is pretty much how it went for me, too. I have the applications menu installed and I never use it.

---

### Post by aeronutt on 2011-12-28
> **cbowman57 said:**
> Ok, as I'm slowly trying to wean myself off of menu extensions & synapse I mapped my old synapse key <menu>, to Activities Overview. (put synapse on ctrl+menu as a security blanket).

Quickly discovered that in comparison to synapse it's a little slow.

Let's speed it up.  Open /usr/share/gnome-shell/js/ui/overview.js line 30 ```
// Time for initial animation going into Overview mode
const ANIMATION_TIME = 0.01;
``` default is 0.25, I cut it drastically as you can see here.

Now locate easeOutQuad, use search & replace to replace 'easeOutQuad with 'default'

In the tweener.js don't forget to change the refresh rate to that of your display (currently line 210) ```
    FRAME_RATE : 170,
```, or you can do what I do, a habit I picked up from using compiz, put in a value of twice your refresh rate, not positive the difference is noticeable but it doesn't break anything.

Let me know what you discover.  For me the Activities Overview now pops into action almost immediately.

Alternatively 'easeNone' can be used in place of 'default' but I can't determine if there is any noticeable difference.

Oh this sounds like a great tweek. I'll try this when I get home today!

---

### Post by cbowman57 on 2011-12-28
> **Artificial Intelligence said:**
> Anyone know an extension/a hack/an option to disable/remove "all" from the overview?



Line 274 appDisplay.js ```
        this._selectCategory(-1);
```On my system changing that -1 to 0 defaults to accessories, 1 to graphics, etc..  You could set it to default to your least populated or most used category.

Can also use the 'easeNone' tweak to perk it up.

---

### Post by Perfect Storm on 2011-12-28
> **cbowman57 said:**
> Line 274 appDisplay.js ```
        this._selectCategory(-1);
```On my system changing that -1 to 0 defaults to accessories, 1 to graphics, etc..  You could set it to default to your least populated or most used category.

Can also use the 'easeNone' tweak to perk it up.

Thank you very much.

---

### Post by cbowman57 on 2011-12-28
> **malspa said:**
> This is pretty much how it went for me, too. I have the applications menu installed and I never use it.

Yeah, I've been slowly whittling my way down to the essentials as I realize that  lot of things I'd grown to rely on are no longer necessary.

---

### Post by cbowman57 on 2011-12-28
> **Artificial Intelligence said:**
> Thank you very much.

Not done yet, it seems to work once then goes back to all.  There must be another location that needs to be changed.

Let me know if you find it before I do.

Found it, line 167 ```
                    this._selectCategory(0);
```

Should match what you have on line 254.

---

### Post by Perfect Storm on 2011-12-28
> **cbowman57 said:**
> Not done yet, it seems to work once then goes back to all.  There must be another location that needs to be changed.

Let me know if you find it before I do.

Aye, just discovered that too.

I'm looking in:
[i]/* This class represents a display containing a collection of application items.
 * The applications are sorted based on their name.
 */[/i]

There must be something to turn it off completely.

---

### Post by cbowman57 on 2011-12-28
> **Artificial Intelligence said:**
> Aye, just discovered that too.

I'm looking in:
[I]/* This class represents a display containing a collection of application items.
 * The applications are sorted based on their name.
 */[/I]

There must be something to turn it off completely.

I'm sure there is but disabling it might bring down the whole shell.

I updated my last reply with a solution that makes it consistent.

---

### Post by Perfect Storm on 2011-12-28
> **cbowman57 said:**
> I'm sure there is but disabling it might bring down the whole shell.

I updated my last reply with a solution that makes it consistent.

That solve it not to start at 'All'. I have reposted the question on Gnome forum and see what answer I'll get there.

---

### Post by cbowman57 on 2011-12-28
> **Artificial Intelligence said:**
> That solve it not to start at 'All'. I have reposted the question on Gnome forum and see what answer I'll get there.

I'll be curious to see what you find out, there may be alternatives that haven't even been considered yet. :)

You know what would be cool, at least for me, a Recent apps default, that would be super.  A recent top 10 maybe, but even better if the limit was configurable.

That would make a GREAT extension. ;)

---

### Post by xircon on 2011-12-28
This worked for me (slow searching for apps):
[https://bbs.archlinux.org/viewtopic.php?id=119689](https://bbs.archlinux.org/viewtopic.php?id=119689)

Basically:
```
rm ./.local/share/recently-used.xbel
mkdir ./.local/share/recently-used.xbel
```

Just create a directory so the file cannot auto create.

---

### Post by Perfect Storm on 2011-12-28
The question is here: [http://gnomesupport.org/forums/viewtopic.php?p=59660#59660](http://gnomesupport.org/forums/viewtopic.php?p=59660#59660)

---

### Post by cbowman57 on 2011-12-28
It looks like that forum is where Gnome questions go to die. :)

No response yet.

---

### Post by Perfect Storm on 2011-12-28
> **cbowman57 said:**
> It looks like that forum is where Gnome questions go to die. :)

No response yet.

Aye, activity there is equal 0.

---

### Post by cbowman57 on 2011-12-28
Just a note to let you all know that Finn has been working on some extensions, which I don't think are on extensions.gnome.org.

[http://www.fpmurphy.com/gnome-shell-extensions/](http://www.fpmurphy.com/gnome-shell-extensions/)

---

### Post by Frogs Hair on 2011-12-28
Where is the configuration file that remembers what extensions you have enabled and also the favorite applications on the left panel . Please and Thank You  !  :)

---

### Post by sanderd17 on 2011-12-29
> **Frogs Hair said:**
> Where is the configuration file that remembers what extensions you have enabled and also the favorite applications on the left panel . Please and Thank You  !  :)

It's in the dconf-editor, under org.gnome.shell, the key "enabled-extensions".

You can access dconf via the gui, or via the CLI like

```

dconf read /org/gnome/shell/enabled-extensions
...

```

---

### Post by Frogs Hair on 2011-12-29
Thank You  sanderd17 ! The command displays a list of active extensions , but I would like to find  the file . I have found and replaced  desktop and shell settings by deleting the configuration and restarting. 

An extension  that is giving an error and I want to delete the configuration because I don't think it is the extension that is causing it . I know where the extensions are installed and reinstalling does no good if the configuration is not removed . The extension will revert to its former behavior  . 

There must be a configuration / profile for extensions as with the other items in advanced settings .

---

### Post by cbowman57 on 2011-12-29
> **Frogs Hair said:**
> Thank You  sanderd17 ! The command displays a list of active extensions , but I would like to find  the file . I have found and replaced  desktop and shell settings by deleting the configuration and restarting. 

An extension  that is giving an error and I want to delete the configuration because I don't think it is the extension that is causing it . I know where the extensions are installed and reinstalling does no good if the configuration is not removed . The extension will revert to its former behavior  . 

There must be a configuration / profile for extensions as with the other items in advanced settings .

If it installed a schema you may have to remove that also.

Is there a particular extension that's giving problems?

---

### Post by Frogs Hair on 2011-12-29
After checking in looking glass again I found the source of the error and I am going to remove it and see what  happens . This extension is not enabled , but still generating an error .```
"uuid": "xrandr-indicator@gnome-shell-extensions.gnome.org",
"name": "Monitor Status Indicator",
"description": "Add a systems status menu for rotating monitors (overrides what is currently provided by gnome-settings-daemon)",
"shell-version": [ "3.2.0", "3.2" ],
"localedir": "/usr/share/locale",
"url": "http://git.gnome.org/gnome-shell-extensions"
}
```

---

### Post by Frogs Hair on 2011-12-29
The errors are gone .

---

### Post by cbowman57 on 2011-12-29
An interesting thing that I've noticed too, even disabled every extension gets loaded & some do still affect the shell.

To help avoid problems like that I try to keep the extensions I don't use or need archived so they don't get loaded at all, though I've slacked off some as of late.

---

### Post by Frogs Hair on 2011-12-31
I have created a Nautilus Root shortcut from the main menu with an icon that opens the password prompt when selected  before opening the root file system .

I was able to add this shortcut to the Unity panel , but when I try to add it to favorites in Gnome the icon reverts to a normal file browser icon after the password has been entered . When trying to use the icon again it  only opens the file browser as normal and not as root .

The shortcut works great from the applications list in the dashboard  but I am unable to move it to favorites .  I am wondering why , but this is more of a curiosity question than a problem .

---

### Post by sanderd17 on 2011-12-31
Great, the user-themes extension works again.

I can now finally test some themes again.

Cbowman, for your theme, it looks good, but now that I'm using it, I have some remarks:

[LIST]
[*]I would try to use a font where the bold signs are as wide as the non-bold ones. Now, if you hover certain UI elements, they become bold, and you get a jump in your theme (like when hovering the date on the top bar). That might be something you wanted that way, but I don't like such a jump
[*]The brown borders around the icons in application mode look good when used with simple icon themes (like token themes), but when used with more complex ones (like faenza), it all gets a bit too busy
[*]And a general thing with dark themes, some applications can't handle it well. E.g. in LaTeXila (which is advertised as a GTK app), with the default coloring schema and Chocolatte GTK, the highlighted current line isn't readable as it's black-on-dark-brown text. Weird enough, the default coloring schema is different between Gedit and LaTeXila. On non-gtk apps (like Libreoffice), it's even worse.
[/LIST]

What do you think about these issues?

Apart from those issues, it's a set of great themes.

---

### Post by cbowman57 on 2011-12-31
> **sanderd17 said:**
> Great, the user-themes extension works again.

I can now finally test some themes again.

Cbowman, for your theme, it looks good, but now that I'm using it, I have some remarks:

[LIST]
[*]I would try to use a font where the bold signs are as wide as the non-bold ones. Now, if you hover certain UI elements, they become bold, and you get a jump in your theme (like when hovering the date on the top bar). That might be something you wanted that way, but I don't like such a jump
[*]The brown borders around the icons in application mode look good when used with simple icon themes (like token themes), but when used with more complex ones (like faenza), it all gets a bit too busy
[*]And a general thing with dark themes, some applications can't handle it well. E.g. in LaTeXila (which is advertised as a GTK app), with the default coloring schema and Chocolatte GTK, the highlighted current line isn't readable as it's black-on-dark-brown text. Weird enough, the default coloring schema is different between Gedit and LaTeXila. On non-gtk apps (like Libreoffice), it's even worse.
[/LIST]

What do you think about these issues?

Apart from those issues, it's a set of great themes.

Yes, dark themes do present problems & I constantly tweak the theme for personal use. I don't use LibreOffice but do know that it rarely themes well, I haven't bothered to try & work around that though I think a few others have, though I don't know how successful they have been.

The shift to bold which causes a little animation is intentional, if it's annoying you can easily locate it in the gnome-shell.css & remove it.  

The beauty of the themes (actually gnome-shell in general) & open source is that it is so easy to change & really just takes some patience & exploration.

Overall though I'm pretty much just modifying it as I go & encounter something that bothers me.  It's no longer in a rapid development cycle. :)

I'm glad you like it despite it's shortfalls.

---

### Post by cbowman57 on 2011-12-31
> **Frogs Hair said:**
> I have created a Nautilus Root shortcut from the main menu with an icon that opens the password prompt when selected  before opening the root file system .

I was able to add this shortcut to the Unity panel , but when I try to add it to favorites in Gnome the icon reverts to a normal file browser icon after the password has been entered . When trying to use the icon again it  only opens the file browser as normal and not as root .

The shortcut works great from the applications list in the dashboard  but I am unable to move it to favorites .  I am wondering why , but this is more of a curiosity question than a problem .

That is odd.  How did you create the launcher?  Copy the desktop file & add gksu or create it with alacarte?

---

### Post by sanderd17 on 2011-12-31
> **cbowman57 said:**
> Yes, dark themes do present problems & I constantly tweak the theme for personal use. I don't use LibreOffice but do know that it rarely themes well, I haven't bothered to try & work around that though I think a few others have, though I don't know how successful they have been.

The shift to bold which causes a little animation is intentional, if it's annoying you can easily locate it in the gnome-shell.css & remove it.

The beauty of the themes (actually gnome-shell in general) & open source is that it is so easy to change & really just takes some patience & exploration.


Oh, yes I love that. I just removed the brown borders around the icons.

>   

Overall though I'm pretty much just modifying it as I go & encounter something that bothers me.  It's no longer in a rapid development cycle. :)

I'm glad you like it despite it's shortfalls.

Yep, it's a really smooth theme.

---

### Post by cbowman57 on 2011-12-31
> **sanderd17 said:**
> Oh, yes I love that. I just removed the brown borders around the icons.



Yep, it's a really smooth theme.

Great, if you find some fixes & workarounds I'll be happy to incorporate them.

---

### Post by Frogs Hair on 2011-12-31
> **cbowman57 said:**
> That is odd.  How did you create the launcher?  Copy the desktop file & add gksu or create it with alacarte?

I just selected the category on the main menu  where I wanted the item  to appear and added a launcher . I then copied an Icon from my current set , renamed it , and placed it in an icons folder .

---

### Post by cbowman57 on 2012-01-14
> **Artificial Intelligence said:**
> The question is here: [http://gnomesupport.org/forums/viewtopic.php?p=59660#59660](http://gnomesupport.org/forums/viewtopic.php?p=59660#59660)

Just revisited your question on the Gnome forum, that forum is quieter than a tomb.

Did you ever find a satisfactory solution?

---

### Post by Perfect Storm on 2012-01-15
Not yet. But I can live with it.

---

### Post by cbowman57 on 2012-01-15
> **Artificial Intelligence said:**
> Not yet. But I can live with it.

That's good, I was just curious.  Thanks.

---

### Post by cbowman57 on 2012-01-18
To totally change every instance of easeOutQuad with easeNone using sed in your gnome-shell/js/ui folder from the **command line**.

Open a terminal in the ui folder, then execute this: ```
sudo sed -i 's/easeOutQuad/easeNone/g' *.js
```**Be careful, using sed is not something to be taken lightly.**

Do a backup before you try it if you aren't certain what it does because used this way it does **exactly** what you tell it to, no prompting, no "are you sure?", nothing. :)

---

### Post by sanderd17 on 2012-01-19
> **cbowman57 said:**
> To totally change every instance of easeOutQuad with easeNone using sed in your gnome-shell/js/ui folder from the **command line**.

Open a terminal in the ui folder, then execute this: ```
sudo sed -i 's/easeOutQuad/easeNone/' *.js
```**Be careful, using sed is not something to be taken lightly.**

Do a backup before you try it if you aren't certain what it does because used this way it does **exactly** what you tell it to, no prompting, no "are you sure?", nothing. :)

Don't you need the 'g' flag at the end to do a global substitution? [http://www.grymoire.com/Unix/Sed.html#uh-6](http://www.grymoire.com/Unix/Sed.html#uh-6)

so ```
sudo sed -i 's/easeOutQuad/easeNone/**g**' *.js
```

---

### Post by cbowman57 on 2012-01-19
@Sander, doesn't appear to be needed, I didn't test it on Ubuntu though, figured sed was so basic it was the same across the board.  Having the /g added might be the absolute correct way, can't remember if I tried that or not.  Could have kicked myself yesterday for having my chat log turned off. Soon as I said thanks & clicked the message tray the line you gave me was gone. :)

Just double checked, example I used above is exactly what's still showing in my .bash_history.  Do you think I should change it?  All entries were changed.

*edit: As luck would have it the shell just got an update so I tried it both ways, & they both worked.  To try and avoid confusion though I added the /g to the original post to adhere with the tutorial you referenced.

---

### Post by sanderd17 on 2012-01-19
strange, with files, it seems to always work globally. But when you use pipes, it doesn't work globally.

```

echo "day 1, day 2" | sed 's/day/night/'

```
gives an other output then
```

echo "day 1, day 2" | sed 's/day/night/g'

```

But if you work with files instead, this doesn't matter.

Btw, a lot of people use pipes with sed. They type 
```

cat source.txt | sed 's/day/night/g' > result.txt

```
This also works, the advantage is that there is a more logical order (source -> command -> result), the disadvantage is that a pipe (|) needs an extra thread (so a lot of pipes would cause some overhead).

---

### Post by cbowman57 on 2012-01-19
Yeah, I find it confusing to tell the truth & just wanted to simplify it as much as possible.  I did add the /g since it does no harm & it seems to be correct according to the tutorial.

This will also come in handy to update all the metadata.json files of installed extensions with the correct version when 3.3 & possibly even 3.4 is released.

FWIW, I've been using 3.3.3 on Precise until it broke yesterday.  The majority of extension worked fine after matching the version.

sed is awesome, but as they say, with great power comes great responsibility. :)

---

### Post by markbl on 2012-01-19
> **sanderd17 said:**
> 
But if you work with files instead, this doesn't matter.

What do you mean here? It is simple. With the 'g' then all occurrences of the pattern are changed, without the 'g' then only the first is changed.

---

### Post by sanderd17 on 2012-01-20
> **markbl said:**
> What do you mean here? It is simple. With the 'g' then all occurrences of the pattern are changed, without the 'g' then only the first is changed.

Do this:

```

echo "day 1, day 2" > test.txt
echo "day 3" >> test.txt
sed -i 's/day/night/' test.txt
cat test.txt

```

and you'll see something

---

### Post by cbowman57 on 2012-01-20
That is interesting, obviously it worked for me because there are no instances of easeOutQuad twice on the same line that I know of.

For what I *thought* I was trying to accomplish using the /g is proper syntax.

Thanks guys, this helps me better understand how to use it.

> **sanderd17 said:**
> Do this

```

echo "day 1, day 2" > test.txt
echo "day 3" >> test.txt
sed -i 's/day/night/' test.txt
cat test.txt

```and you'll see something

---

### Post by markbl on 2012-01-20
> **sanderd17 said:**
> 
and you'll see something

I'll see exactly what I would expect. The substitutions are applied per input line. Adding the 'g' changes all occurrences of the pattern PER LINE rather than just the first occurrence.

---

### Post by sanderd17 on 2012-01-21
> **markbl said:**
> I'll see exactly what I would expect. The substitutions are applied per input line. Adding the 'g' changes all occurrences of the pattern PER LINE rather than just the first occurrence.

I interpreted "only the first" as "only the first of the file", but it means "only the first of each line". 

So I didn't know why the original way worked.

---

### Post by cortman on 2012-02-29
Just finished my first Gnome Shell theme, Earth Tones. Just a shell theme for now, not ready to do GTK quite yet...
Download from Gnome-look [here]("http://gnome-look.org/content/show.php/Earth+Tones?content=149258"). I'd be interested in any feedback or comments anyone might have on it. Thanks!

---

### Post by t.rei on 2012-03-04
There is this one thing I really really wish for: an extension (or hack) to disable the hiding of the notification panel. 

I have plenty of screen realestate (2x 1920x1200) - so the problem of "wasting space" becomes the totally different one: "move a hell of a lot of way with the mose to check for missed notifications". 

I did manage to get this via editing the messageTray.js on the 3.2 shell. But I upgraded and now the previous solution does not work anymore. And this time I seem to fail finding a new one. 

To me, that little change - just not hiding the notifications - made the whole usage of the shell A LOT more pleasant.

---

### Post by cbowman57 on 2012-03-04
Not sure I fully understand what you want but have you looked at this?

[https://extensions.gnome.org/extension/41/permanent-notifications/](https://extensions.gnome.org/extension/41/permanent-notifications/)

---

### Post by sjmp on 2012-03-04
hey guys Im totally new to linux and just installed ubuntu 11.04 on my dell laptop with nvidia graphics. 
the problem is when i install the graphics driver both lower and upper panels of gnome disappear. i need the driver so the Compiz (which i like it) works fine. but without driver Compiz doesnt do anything. any clues?
i couldnt re install gnome after installing driver cuz without the panels i couldnt connect to the net.
and a seccond question, where is the left sidebar/toolbar? should i do anything for it to appear?
sorry if its a wrong place for my question.
thanx 4 ur help

---

### Post by t.rei on 2012-03-05
> **cbowman57 said:**
> Not sure I fully understand what you want but have you looked at this?

[https://extensions.gnome.org/extension/41/permanent-notifications/](https://extensions.gnome.org/extension/41/permanent-notifications/)

Yes, I have - it's not what I'm looking for. This extensions keeps the notification popups open until clicked, thus making them really anoying. 

I want the "bottom panel" to always show. Make the little notification-indicators that show up in the bottom right corner never hide and remain visible at all times, not just on mouseover or when the overview is open.

---

### Post by t.rei on 2012-03-05
> **sjmp said:**
> hey guys Im totally new to linux.


welcome.

No, this was not the right place. Gnome-Shell is the next generation of gnome-desktop totally different from the 11.04 one. This thread is about how to configure, or tweak or set up the gnome-shell desktop environment.

Gnome-shell does not 'use' compiz. It uses it's own window manager (mutter).

Unity (the default ubuntu desktop) as well as the old one (11.04 was classic gnome 2) can use compiz for desktop effects.

The sidebar is only there in the unity interface. 11.10 and up.

I can't help you with your problem about the panels, though I vaguely remember some troubles back then. But may I suggest getting either 11.10 (recommended):
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
or if you feel more adventurous the beta of 12.04 (wich is pretty stable for me):
[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1)

---

### Post by cbowman57 on 2012-03-05
t.trei,it sounds like you might be happier using Cinnamon or the MGSE bottom panel extension.

---

### Post by t.rei on 2012-03-06
To be honest: I love the way so many things get done in gnome-shell, I doubt I'd be happier with cinnamon.

The MGSE bottom panel made things worse: an Icon in the bottom panel to show the notifications *sigh*.

All that I'd like to see is: **no autohide of the messageTray**.

And I'm slowly digging through the js source. But so far only breakage has been achieved.


*edit* I found it - seems to work nicely - at least optically. Lets see if I can change the panel itself to be clickthrough (or be just behind the messages)

This is what I got so far (I think thats all thats needed):

It basically makes the message tray behave just as if the overview was active.

messageTray.js
```
 
1432:        this._overviewVisible = [COLOR=Red]true[/COLOR];

``````
1465:                 this._overviewVisible = [COLOR=Red]true[/COLOR];

```Anyone got a hint on how to do this in an extension?

---

### Post by cromat on 2012-03-06
Been reading through this thread as I am currently using Linux Mint 12 with almost all the extensions turned off to make a more gnome-shell like experience. I want to move back to a pure ubuntu install and it looks like the tweaks in this thread make it very usable, is that correct?  Is everyone here running Ubuntu 11.10 or Arch as I saw in a couple posts. Is gnome shell on ubuntu generally a good experience or am I better going straight debian, arch, or other ubuntu flavor that embraces gnome-shell?

Thanks,

---

### Post by cbowman57 on 2012-03-06
> **cromat said:**
> Been reading through this thread as I am currently using Linux Mint 12 with almost all the extensions turned off to make a more gnome-shell like experience. I want to move back to a pure ubuntu install and it looks like the tweaks in this thread make it very usable, is that correct?  Is everyone here running Ubuntu 11.10 or Arch as I saw in a couple posts. Is gnome shell on ubuntu generally a good experience or am I better going straight debian, arch, or other ubuntu flavor that embraces gnome-shell?

Thanks,

Ubuntu is fine, personally I've grown to favor Arch but gnome shell doesn't really care & you won't notice any difference.

---

### Post by squilookle on 2012-03-06
> **cromat said:**
> Been reading through this thread as I am currently using Linux Mint 12 with almost all the extensions turned off to make a more gnome-shell like experience. I want to move back to a pure ubuntu install and it looks like the tweaks in this thread make it very usable, is that correct?  Is everyone here running Ubuntu 11.10 or Arch as I saw in a couple posts. Is gnome shell on ubuntu generally a good experience or am I better going straight debian, arch, or other ubuntu flavor that embraces gnome-shell?

Thanks,

I'm using Gnome Shell on Ubuntu 11.10 and I'm finding it a good experience. The install was easy, I'm not using any extensions as I'm happy with the default behaviour, and it runs pretty smoothly (incidentally, I had had to use Unity 2d because, even though my computer would run Unity, it was extremely laggy).

The only other distro I have tried Gnome Shell on was Suse 12.1 (I also tried Fedora but I could only get fallback mode on that) and there is very little difference in the experience between the two.

---

### Post by cromat on 2012-03-06
> **cbowman57 said:**
> Ubuntu is fine, personally I've grown to favor Arch but gnome shell doesn't really care & you won't notice any difference.

Cool thank, is arch pretty easy to use or it is a challenge compared to ubuntu. Hoping there is a GUbuntu spin soon, otherwise I might have to start one. I have been using Mint 12, with all the extensions removed.

---

### Post by squilookle on 2012-03-06
When I last used Arch (2 years ago) I found it wasn't difficult, you just had to follow the instructions carefully and take the time to get the system set up. 

In return though, I got a lightweight system and had a much better understanding of how it worked and what was in it. 

I assume things haven't changed much in that sense. 

On the other hand, I have always found Ubuntu easy in the sense that things tend to work out of the box, but if you run into a problem installing either system, the process you follow for solving the issue is pretty much the same.

---

### Post by cbowman57 on 2012-03-09
> **cromat said:**
> Cool thank, is arch pretty easy to use or it is a challenge compared to ubuntu. Hoping there is a GUbuntu spin soon, otherwise I might have to start one. I have been using Mint 12, with all the extensions removed.

I found it a little more difficult to get setup initially but I was comfortable with it pretty quick.  Both Ubuntu & Arch have their pros & cons, but Arch suits me better.  I never would have arrived at my choice though had  not started with Ubuntu & Linux Mint years ago. :)

---

### Post by polyrhythmic on 2012-03-20
Gnome-shell + gnome-do + docky with intelligent hide is amazing.  I started with a 12.04 beta1 mini.iso and added a few ppas*... the workflow is incredible.  Just make sure to install gnome-shell at the same time as gdm, installing gdm by itself will trigger a Unity install.

Can't wait for Do to be integrated back into Docky, it's on the roadmap for Docky 3.  Do + Docky together are like a faster and more immediate/intuitive version of the gnome-shell Activities view.  Really couldn't stand the Activities layout without them.

I held out with 10.04 LTS + compiz + cairo-dock for a long time, but gnome-shell has the features (like Expose and multiple desktops with multiple monitors) that I loved, but much easier and simpler to config.  Font rendering is very nice.  All very low on CPU.

I like that the UI is there when I need it and gets out of the way when I don't.

Arch Linux I love and I use it on my NAS, but for bleeding-edge desktop environments Ubuntu makes it much simpler to install thanks to the PPAs.



[*] I'm using the xorg-edgers, gnome3-team, ricotz-testing (gnome-shell), do-core, and docky-core-stable ppa's to achieve this.  I tried out tista-gdm-testing ppa but found it too unstable on my Radeon 4650.

---

### Post by cbowman57 on 2012-03-20
I really don't use docks, but I've been using synapse for years & it was a good fit with gnome shell too.

Personally I think that AUR gives me all the access I need to Ubuntu PPA's & riding the bleeding edge with Arch seems a lot more stable than it was with Ubuntu.

That said, everybody needs to use what works best for them. :)

---

### Post by mmesantos1 on 2012-06-02
Great thread Charles! :)

---

### Post by cbowman57 on 2012-06-02
> **mmesantos1 said:**
> Great thread Charles! :)

It was handy in it's time.  We've learned so much since.

---

### Post by scouser73 on 2012-06-03
I've just come across this thread, got me installing stuff I want.

---

### Post by cbowman57 on 2012-06-03
It started with the best of intentions.

Glad to help all I can.

---

