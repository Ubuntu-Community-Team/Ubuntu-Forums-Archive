---
title: "Cairo dock missing icons in opengl mode"
date: 2009-11-07
forum: Desktop Environments
---

### Post by fhmanas on 2009-11-07
I just installed Karmic and Cairo-dock from repos.  The standard Cairo (w/o Opengl) works ok.  The Opengl Cairo works and all but it is missing some icons, like my switcher, trash, show desktop, the clock face, etc.  Anything, I can do about this, I am new with Cairo.  I know this is not OpenGL related, bec other icons appear and work.

Please help, OpenGL looks better than standard Cairo.

Thanks.

Francis

---

### Post by fhmanas on 2009-11-07
I just discovered that the missing icons come from the Desktop section of the configuration.  Anything I activate there does not appear to have an icon.  I can't find an icon for it.  Where can I locate the icons for dustbin, switcher, etc.  Does not matter what theme i use, it just doesn't show.

Attach screenshot to show what I mean.

Thanks

---

### Post by fabounet on 2009-11-07
try with indirect rendering, it works for most of Intel cards at the moment.
```
cairo-dock -o -i
```

---

### Post by fhmanas on 2009-11-08
Thanks for trying to help but it did not work, I still don't have icons for Desktop utilities

---

### Post by fabounet on 2009-11-09
what if you detach them as desklets ?
anyway this seems a driver issue, you may want install the latest one, and if the problem persists, to report it to the devs of your drivers to help improve them.

---

### Post by BurgerKing on 2010-01-23
I'm sorry for bringing this old thread up again, but I've got the same problem and found this thread while searching for an answer.
Exactly the same here, if I launch cairo-dock in OpenGL-Mode, the icons for applets like the recycle-bin and else are missing, the non-Open-GL-mode works perfectly. May also interesting, if I change an applet's icon it's showed like it should.
Anyone knows how to solve this issue?
Currently using Ubuntu 9.10 on an Thinkpad R51 2888 with an Intel-82852/855 graphics-chip (like sysinfo said) with the latest driver from [x-swat-ppa]("https://launchpad.net/~ubuntu-x-swat").

---

### Post by fabounet on 2010-01-24
start the dock with 
```
cairo-dock -oi
``` 
the reason is that your graphic card drivers don't support OpenGL completely

---

### Post by allcolor-g on 2010-04-02
Well, I have the same problem as described here... after upgrading to Lucid, it works fine in non opengl mode, missing dust bin, show desktop icon, ... in opengl mode.

The -oi (or -o -i) doesn't change anything. And if it was a driver issue... what is special about these icons... the others are showing, don't tell me cairo dock use another code path to show these icons, as the effects and looks are just the same as the others that show up.

I have an ati card and i use the free driver radeon (not fglrx). Compiz works with it (did not before lucid)

---

### Post by eddyojb on 2010-05-12
BUMP!

This is also happening to me, running cairo-dock in 'no opengl' works fine but 'with opengl' it doesn't displayu the 'show desktop', 'recycle bin' and weather applet icons!

Its very irritating so if anyone could provide some help that would be great!

---

### Post by fabounet on 2010-05-14
that's a driver problem, you can't do much about it;
I guess you have an ATI card with free drivers ? in this case you can report the problem to the devs, it may help them improving their soft.

---

### Post by bdery on 2010-06-28
It's not always a driver issue, I'm using Ubuntu 10.04 Lucid Lynx, with Cairo-Dock v2.1.3-10, I've been running in Opengl mode for few weeks now, and today it started to make some of my icons disappear.  Same driver, same cairo-dock, no update done, the only thing I've did is add few icons, like netspeed, and wifi.  Well after few tests, I saw a relation between the number of icons in my dock, and the number of icon missing, the more I add icons, the more disappear into thin air, leaving only their name.

My solution, create another dock, beside the main dock, split my icons between those two docks, and voilà!, I now have all my icons visible.  On my computer, I can say that I can't have more than 22 icons per dock, at 23, 1 of my icons disappear, 24, 2, and so on...

Hope this help.

bdery

):P

Oh, by the way, I'm using a HP DV9347ca, with a NVIDIA geforce 8400M with 1gb memory, using nvidia proprietary driver 195.36.24

---

### Post by fabounet on 2010-06-29
strange, I've never had such a problem.
what if the icons inside the dock are only launchers ?
and what if you launch it with "cairo-dock -o -f" ?

---

### Post by Saraiva on 2010-07-29
Hi, 

I think you dont want it anymore but I had the same problem and solved it:

You can solve it using the ".conf" files of the Cairo's plugins. They are hidden/occult (just dont know what term is because I'm using a Portuguese/Brazilian version of Ubuntu Lucid) in your "home" path. For example, to show your Cairos dustbin plugin icon edit: [COLOR=Red]/home/your_chosen_name/.config/cairo-dock/current_theme/plug-ins/dustbin.conf
[/COLOR]
Open it with an editor and take a look at the item[COLOR=Red] "icon="[/COLOR]
Yours probably is empty. So, choose the image file you want to use as the dustbin icon and set it there (do a test with any image used by the others cairo's plugins in the same path). Ex:

[COLOR=Red]icon=/home/your_chosen_name/.config/cairo-dock/current_theme/audio-player.svg[/COLOR]

Now you just have to find a good image file to use. I just have installed Cairo today and had the problem, so I dont know where the right images is. They should be at "[COLOR=Red]/home/you_chosen_name/.config/cairo-dock/themes/your_downloaded_theme/icons[/COLOR]".
But in my case they're not there. A very strange issue.


Lucian

---

### Post by 50race on 2010-08-20
@Saraiva
thanks for the fix. I didnt believe it was a graphics driver problem. It is just unassigned in opengl mode. I found a lot of the icon here for anyone looking to fix their dock. 

/usr/share/cairo-dock

This fix doesnt directly work on animated icons like the weather or clock. I have found that by applying different themes different icons are fixed and other will disappear. So if you can find the right theme that changes all the icons the problem would be fixed...maybe

---

### Post by Cuco3 on 2010-08-24
I bought an Acer Aspire 5551-2036 with an ATI Radeon 4250 and here's what I'm experiencing:

OpenSource ATI Drivers: Works *GREAT* except it's missing some icons such as Compiz, Sound Control, Power Management, and others. Also, when you touch the screen border to raise the dock (or when the dock hides), the animation part is all white.

Proprietary ATI Drivers from Ubuntu Repositories: All icons appear, except now the dock flickers when you call it up (or hide it) and it also flickers when you hover the mouse over it. The dock no longer appears white when you hit the screen border to call it up or when it hides.

Anybody have any luck fixing this?

---

### Post by fabounet on 2010-08-25
no fix (except maybe try the latest version of the drivers), but a solution : report these problems to the drivers' devs, that could help them3

---

### Post by Cuco3 on 2010-08-25
> **fabounet said:**
> no fix (except maybe try the latest version of the drivers), but a solution : report these problems to the drivers' devs, that could help them3Thanks fabounet, but I don't know where to contact ATI. I checked their website, but I didn't see anything towards filing bugs for drivers. Do you know where to post bug reports?

I did sign a petition for AMD/ATI to improve their driver support for Linux.

---

### Post by fabounet on 2010-08-26
I don't know either, but it's maybe easier to contact the free drivers team.

---

### Post by daveerickson on 2010-08-26
WARNING: RANT STARTING ->

I have done my best to let off steam about cairo/glx-dock before posting, but this crap pisses me off!

I like using a dock. I started several years ago using AWN, then tried out cairo, and in the past year or so I have been using Gnome-do/Docky. The only one to handle exactly what I want has been Docky. Yes it is simple, but it always works!

I know many times drivers get in the way and cause graphical issues, but telling someone to go file bug reports when sometimes an icon shows up, and other times it does not....really???

If you REALLY think glx-dock is not to blame at least give them some ammo to go to the driver maintainers with! Tell them WHY that icon is different than the others, on how other icons being present is affecting that icon so it randomly disappears, otherwise it sounds like you are ignoring the problem and pushing off the blame.

I really like what glx-dock is trying to do. I think it has the potential to be a very customizable dock that could be setup for anyone, but as it stands now it is broke and will never be fixed without devs listening and helping out. Sorry, but if opengl is working with other apps that depend on it, such as compiz/games, the driver is probably not the problem. If it really is a driver problem then maybe glx should not make those opengl calls since other games/apps are also not using them. If glx really has to use those unique calls then work with a person who is stating a problem and help pin the problem on the driver so it can be fixed. I am an end user, not a dev, but I can still tell when things are not working. Unfortunately for glx, whether it is it's fault or not, it is what is broken, even if it is the drivers fault.

Again, really not trying to throw spears at the project. I want to see it succeed! However there are problems to be fixed that need the help of the devs. Please listen when a user takes enough time to start searching for a problem, finds this forum and posts their details. At a minimum, direct them to your bug tracker and ask specific questions there to resolve the issue.

Then again this is just my .02 and it isn't my project, so handle it how you wish...

---

### Post by MysticHLE on 2011-04-23
This is happening to me too, and I think I've somewhat isolated the bug - at least for me. I observed that if I set the icon sizes (in advanced options) to be different for the applets compared to the applications' and launchers', then this bug happens whenever I click on a few selected applet icons (show desktop, application launcher, etc.). The moment I resized the applet icons to match the application/launcher icon size and hit apply, this bug goes away.

Definitely a Cairo-dock bug.

P.S. Icons' size set at 80 pixels.

---

### Post by nmyrick on 2012-04-15
You can also easily manually add any image you want for the icon.  The easiest way is to right-click on the application in the dock, select 'configure this applet', go to the 'Icon' tab, and enter the file path for your icon.
 
If you are looking for the icons for your installed theme, in Ubuntu, you will find them in the filesystem under /usr/share/icons/[folder for your theme]/scalable/(apps, devices, filesystems, etc.).

It is best to use the scalable icon if there is one. Using the scalable icon allows you to adjust the size of your icons without loosing resolution. So open the scalable folder, then select the folder for the type of icon, then just enter that entire file path in the file path for your icon.

---

### Post by oldos2er on 2012-04-15
Closed, necromancy.

---

