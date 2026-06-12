---
title: "Wrong background color for google desktop tray icon"
date: 2010-04-30
forum: Desktop Environments
---

### Post by reablom on 2010-04-30
After installing Ubuntu 10.04 the background of the google desktop tray icon does not match the color of the upper panel. It seems not all themes have this problem. Ambiance, dust, radiance and New wave do, but the other standard themes don't.

I guess one picture says more than a thousand words so: 

[[IMG]http://img688.imageshack.us/img688/9872/googleicon.jpg[/IMG]]("http://img688.imageshack.us/i/googleicon.jpg/")

Any idea how to solve this?
[IMG]http://yfrog.com/j4googleiconj[/IMG][IMG]http://yfrog.com/j4googleiconj[/IMG]

---

### Post by tak1150 on 2010-04-30
Same problem here with OOo quicklauncher icon and Beagle icon as well.

---

### Post by miceagol on 2010-04-30
Ditto, but with the terminal and drapes icons. In addition there seems to be a ghost menu attached to my panel. Anyone know how to remove this? It was there also before I upgraded.

[IMG]http://folk.uio.no/michaeka/tilverden/ghost_panel.png[/IMG]

---

### Post by CalebWishart on 2010-05-01
> **miceagol said:**
> Ditto, but with the terminal and drapes icons. In addition there seems to be a ghost menu attached to my panel. Anyone know how to remove this? It was there also before I upgraded.

[IMG]http://folk.uio.no/michaeka/tilverden/ghost_panel.png[/IMG]
It looks like you are running global menu bar. That's the "ghost menu" (bookmarks, tools, help). You can move it over (right click, select move) to use it, or you can remove it (right click, select remove from panel).

As for the wrong color behind the icons, I have the same problem with the Google Desktop icon. I my guess is that the icon doesn't have a transparent background, but I can't find the right icon to change.
I tried changing both the [FONT="Courier New"]/opt/google/desktop/resources/gdl_small.png[/FONT] and the [FONT="Courier New"]/opt/google/desktop/resources/gdl_large.png[/FONT] both of which are Google Desktop icons, but that only changed the icons in the application menu.

If anyone knows where the Google Desktop icon that is displayed in the tray is stored, please let me know.

---

### Post by c-shadow on 2010-05-01
Same problem here with more applications and ambiance and radiance.
Clean install with /home partition from karmic. Tried removing ~/.gconf/apps/panel and restarting panel but it didn't help. New created users have the same problem. Both themes do not look good if size is changed above 24 pixels because of this color gradient.

---

### Post by reablom on 2010-05-01
> **CalebWishart said:**
> ...

As for the wrong color behind the icons, I have the same problem with the Google Desktop icon. I my guess is that the icon doesn't have a transparent background, but I can't find the right icon to change.
...

I don't think transparency is the problem as it works fine in some themes (e.g. "High Contrast Inverse"). It looks more like the wrong background color is chosen: the sand color of the letters and other icons instead of the greyish brown of the bar.

---

### Post by Tuchkata on 2010-05-04
I have the same problem with 10.04. My problem is with VLC and CheckGMail. Still no solution ? With Karmic everything was ok.

---

### Post by xDarkicex on 2010-05-04
I have this problem with a few of the themes off gnome-look

---

### Post by Tuchkata on 2010-05-04
Any solutions ? Is there a launchpad report about the problem ? Hope the fix is coming ...

---

### Post by mister_k81 on 2010-05-04
I'm having the same problems with aMSN and VLC in the systray using 10.04. I've never experienced this issue before 9.10, 9.04 or even 8.10. It looks like a bug in the latest version of Gnome.... 

I really hope someone fixes this in an update, because it's a real eyesore to look at.

---

### Post by Zaff on 2010-05-08
Same problem here with Amarok 1.4 (yes I'm going to change someday) and gmail-notify.

---

### Post by bornagainpenguin on 2010-05-11
Ohh!  I know, we could fix real bugs like this one or pull our roots while playing with windicators...

Guess which one the Canonical developers did?

--bornagainpenguin

---

### Post by apostate on 2010-05-11
> **bornagainpenguin said:**
> Ohh!  I know, we could fix real bugs like this one or pull our roots while playing with windicators...

Guess which one the Canonical developers did?

--bornagainpenguin



LOL.

Yeah, I can't help think that the interface for Lucid is something of a regression from Karmic. Lame. I wish they would stop "enhancing" GNOME by crippling it even further, and fix the stuff people have been bitching about for years.

---

### Post by reablom on 2010-05-13
> **bornagainpenguin said:**
> Ohh!  I know, we could fix real bugs like this one or pull our roots while playing with windicators...

Guess which one the Canonical developers did?

--bornagainpenguin

Are you being sarcastic? Anyway, I find this bug quite annoying.

---

### Post by TWilliam on 2010-05-16
No solution to offer, but I do have a bit of info that might be helpful.

It seems that the issue is not with icon transparency, but with the background color of the Notification Area Applet. It appears that the Notification Area Applet doesn't take its background setting from the Panel, but rather from the theme's Window Background color.

Go to System--->Preferences--->Appearance

Select the Theme tab. Whatever your current theme is should already be highlighted.

Click the Customize button (1, see attached image).

Select the Colors tab. The button indicated by 2 in the attached image will bring up a color selection dialog. If you change the color here, in addition to changing the color of your window backgrounds you will also see the unruly icons in your Notification Area change.

So I guess the question is, is there a way to either change the Notification Area Applet so that it sets its background from the same parameter that sets the Panel background, or to set the Notification Area Applet's background transparent so that the Panel shows through?

---

### Post by blendmaster1024 on 2010-05-17
i have part of a solution, at least an area to research (though i do not have this problem with dust-sand).

the theme is setting a different background for the notification area than the rest of the panel. this is going to require some theme knowledge to fix, and it's hard to be specific about how it's doing this and why it looks bad when i don't have the problem myself.

hopefully useful....

---

### Post by Knacker on 2010-05-17
same problem with google-desktop icon. finding a fix for the notification area color/transparency problem is the most important thing, but it would also be great if anyone knows where the google desktop icon is or how it can be changed (i.e. changed to fit with lucid's monochrome taskbar icons). 

anyway, +1 people who would be really grateful for a fix to this. 

Thanks!

---

### Post by bornagainpenguin on 2010-05-18
> **reablom said:**
> Are you being sarcastic?

I'm feeling stressed actually--that's the confused state caused when ones mind overrides the body’s natural desire to choke the living &*%$ out of some %$#* that desperately needs it.  And why wouldn't I feel that way?  This is yet another bug being ignored while the Canonical developers do anything and everything ***but*** fix the problem.  The past has shown it does no good to complain, make bug reports, threaten to leave, actually leave, etc etc...

Seeing as there was nothing constructive I could do, I simply aim to amuse myself as I save up my pennies for a MacBook.  Sorry if you feel caught in the crossfire.  Feel free to amuse yourself by flinging some poo right back at me.

> **reablom said:**
> Anyway, I find this bug quite annoying.

You and me both, friend!  But what can we do about it?  Canonical doesn't give a flying Shuttleworth what you or I like or consider to be a bug.

Not to worry though, if you think things are buggy now, wait for the Meerkat release!  :guitar:

--bornagainpenguin

---

### Post by Ascurion on 2010-06-10
I got the same bug running 10.04 but unfortunately no solution either. Since the last message is three weeks old I wanted to ask if there is some progress on this.
 Thanks!

---

### Post by desgua on 2010-06-13
None that I'm aware of.

---

### Post by JoeGoalie on 2010-06-13
Really?  None?  That really sucks.  I'm having the same issue with gmote.

---

### Post by t.rei on 2010-06-14
*sigh* and another one. Well at least this bug is getting some PR.

There are quite a lot of apps that show this behavior. Maybe it's time to play around a bit and get a works and works not list:

Works not: 

[LIST]
[*] Ambience theme (yey default not working!):
Murrine Engine?
Equinox Engine?
[*]Human theme
[*]Human Clearlooks theme
[*]Radiance theme
[*]WoW-* themes
[*]elementary theme
[*]Amaranth theme (pixmap?)
[*]Clearlooks classic
[*]Dust
[*]Dust Sand
[*]Glider
[*]Glossy
[*]Gorilla
[*]*Contrast*
[*]Inverted
[*]Lush
[*]New Wave
[*]Simple
[/LIST]
Sadly I don't seem to have anything installed.

To test this I did: Set panel BG to colored, semi-transparent. 
Compared the gajim (ppa version, supposed to be fixed) icon to the way the pidgin icon behaved.
To be fair: there are some themes that explicitly theme the panel and therefore are in the not-working-list.

[B] Can anyone report of any working theme / theme-engine ?

*edit* 
[/B]This bug is so widespread and so everpresent and such an obvious one... it SHOULD be locatable.
Step one: find engine that does it right,
Step two: if no engine does it right, compare code of working (pidgin) tray icon handling to not working ones (vlc, gajim, google, openoffice,...)Step three: find the fix and spam each and every one of the 'not working' users, be it theme or app with the solution:D

---

### Post by luceerose on 2010-06-18
I'm having this problem with the openoffice quickstarter icon.
Using a customized Ambience theme with Ubuntu-Mono-Light icons.

In the attached screenshot, you can see that I'm actually not having this trouble at all with Thunderbird's Firetray icon or the Screenlets Daemon icon.
The Amarok icon is in the Indicator Applet & not the Notification Area.

Maybe someone could find a hack to make the Notification Area get it's color from somewhere else ???
Or maybe there could be a way to make the offending icons show up in Indicator Applet rather than Notification Area ???

[ATTACH]160877[/ATTACH]

---

### Post by afrodeity on 2010-06-20
My google-desktop icons are in /opt/google/desktop/resource/gdl_large.png 

and /opt/google/desktop/resource/gdl_small.png

I've uploaded two versions of the above with white on transparent background. Please test them.

[http://www.mediafire.com/?sharekey=41d4076c3ada40351f8e0fff488e27e031a0b94cd9ffdb13515d15c8b368bfbe](http://www.mediafire.com/?sharekey=41d4076c3ada40351f8e0fff488e27e031a0b94cd9ffdb13515d15c8b368bfbe)

also

Check this thread [http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by afrodeity on 2010-06-20
The large icon will land up in your menu. I kept the default icon which is much better against a white background.

To refresh the icon:

pkill gnome-panel

However after doing this, my Google-Desktop is no longer showuing up in the panel. I can call it using my hotkey which happens to be Alt-G.

I suspect one has to update the icon cache somehow, or logout and back in.

```
cd ~/.icons
gtk-update-icon-cache ICONSETNAME

```

Thus haven't managed to sucessfully use the above icons, will test next boot.

---

### Post by Knacker on 2010-06-21
good idea. but changing icons in /opt/google/desktop/resource/ has no effect on the notification area icons for me. then again, i've not tried too much outside the obvious (which for me is not a lot...). 

anyone else have any luck? or any ideas?

---

### Post by neurosk8 on 2010-06-27
no soluttions? this problem is so annoiyng

---

### Post by justtrying on 2010-06-27
same problem here too. and in addition i can not make the top panel transparent like i used to do with all previous Ubuntu versions........Please we need a fix.
I used to be able to go to the panel properties and change its background color to solid then adjust the transparency to my liking.....not no more....if you try to do this you end up with a very ugly looking panel..it is like the middle part of the panel becomes transparent but the notification area as well as the places and system areas on the other end remain solid. 
Ubuntu used to be a lot more fun. 
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by t.rei on 2010-06-27
If the notification area, the clock and the menu items have backgrounds, this is caused by settings in the theme. 

pick your theme - and look for its gtkrc file either in:
/usr/share/themes/<yourthemename>/gtk-2.0/
or in:
~/.themes/<yourthemename>/gtk-2.0/

and look for what is done to the panel in there by searching for 'panel' i.e. and experimenting. ;) Sry, it's way too complex to write in a post but not too difficult to figure out.

Alternatively use a different theme. :/


As for the single items that have no transparent background... I am afraid theres nothing one can do, except wait for updates. Well you COULD ofcourse write the update and submit it to the maintainers... ;)

---

### Post by desgua on 2010-07-04
I could not figure out what to do because I don't find nothing specifically linked to Google Desktop. May be someone knows where the icons are located and we can change that.;)

---

### Post by scotty2718 on 2010-08-06
WORKAROUND FOR GMAIL-NOTIFY 1.6.1 TRAY ICON BACKGROUND COLOR NOT MATCHING GNOME PANEL IN UBUNTU 10.04

The problem can be fixed by changing the icons to match the new system theme.

The icons can be found in /usr/share/apps/gmail-notify.  The icons that set the tray icon are icon.png (red) and icon2.png (blue).  Both have transparent backgrounds, but that doesn't appear to be working with the notification applet.  You can either manually change the icons with the ones included in the "new-icons.tar.gz" file or follow the terminal instructions below.

I've included instructions below:

Download the attached new-icons.tar.gz file and extract the contents to the desktop.  To extract the contents, first move "new-icons.tar.gz" to your desktop, right click the icon, and then choose "extract here."  A new folder called "new-icons" should now be visible on your desktop.    

Before continuing, make sure the desktop has a new directory named "new-icons" with two pictures inside (icon.png and icon2.png).

Now run the following commands one at a time in the terminal:

mkdir ~/Desktop/original-icons
cd /usr/share/apps/gmail-notify
cp icon.png icon2.png ~/Desktop/original-icons
cd ~/Desktop/new-icons
sudo cp icon.png icon2.png /usr/share/apps/gmail-notify
cd ~/Desktop/new-icons
rm icon.png icon2.png
rmdir ~/Desktop/new-icons

Alternatively, you could run the bash script I attached.  Note, the script has to be run after the "new-icons" directory exists. 

How to run the script:
0) Make sure the "new-icons" folder is on your desktop
1) Download the "icon-change.sh" file and put it on the desktop.
2) Right click the file and choose properties.
3) Click on the "permissions" tab and check "allow executing file as program".
4) Double click the file.
5) When the dialog box pops up, choose "run in terminal"

So, what just happened? Well, three things.

1) The icons in the gmail-notify have been replaced with the ones in the "new-icons" folder.

2) The old icons have been backup up in the folder "original-icons" that is now on your desktop.

3) The "new-icons" folder you extracted earlier has been deleted.

It may take some time for the notifier icon to change (you have to wait until it checks for mail again).  You could always restart the application or click the "Check now" button if you want it to change immediately.

---

### Post by Knacker on 2010-08-13
Just so that the above post doesn't cause anyone any confusion: please note that this is not a work around for the problem discussed in this thread. This is a fix for Gmail-Notify and has nothing to do (as far as I can tell) with google-desktop icon problem...which is still very much broken. 

> **scotty2718 said:**
> WORKAROUND FOR GMAIL-NOTIFY 1.6.1 TRAY ICON BACKGROUND COLOR NOT MATCHING GNOME PANEL IN UBUNTU 10.04

The problem can be fixed by changing the icons to match the new system theme.

The icons can be found in /usr/share/apps/gmail-notify.  The icons that set the tray icon are icon.png (red) and icon2.png (blue).  Both have transparent backgrounds, but that doesn't appear to be working with the notification applet.  You can either manually change the icons with the ones included in the "new-icons.tar.gz" file or follow the terminal instructions below.

I've included instructions below:

Download the attached new-icons.tar.gz file and extract the contents to the desktop.  To extract the contents, first move "new-icons.tar.gz" to your desktop, right click the icon, and then choose "extract here."  A new folder called "new-icons" should now be visible on your desktop.    

Before continuing, make sure the desktop has a new directory named "new-icons" with two pictures inside (icon.png and icon2.png).

Now run the following commands one at a time in the terminal:

mkdir ~/Desktop/original-icons
cd /usr/share/apps/gmail-notify
cp icon.png icon2.png ~/Desktop/original-icons
cd ~/Desktop/new-icons
sudo cp icon.png icon2.png /usr/share/apps/gmail-notify
cd ~/Desktop/new-icons
rm icon.png icon2.png
rmdir ~/Desktop/new-icons

Alternatively, you could run the bash script I attached.  Note, the script has to be run after the "new-icons" directory exists. 

How to run the script:
0) Make sure the "new-icons" folder is on your desktop
1) Download the "icon-change.sh" file and put it on the desktop.
2) Right click the file and choose properties.
3) Click on the "permissions" tab and check "allow executing file as program".
4) Double click the file.
5) When the dialog box pops up, choose "run in terminal"

So, what just happened? Well, three things.

1) The icons in the gmail-notify have been replaced with the ones in the "new-icons" folder.

2) The old icons have been backup up in the folder "original-icons" that is now on your desktop.

3) The "new-icons" folder you extracted earlier has been deleted.

It may take some time for the notifier icon to change (you have to wait until it checks for mail again).  You could always restart the application or click the "Check now" button if you want it to change immediately.

---

### Post by Knacker on 2010-08-20
though it seems like google is paying, and intends to pay zero attention to google-desktop on linux, i've posted questions/requests on the google group for google-desktop on linux...

i hope i described the problem correctly:

[http://groups.google.com/group/google-desktop-linux-something-broken/browse_thread/thread/c9bcc6bdb62d7583](http://groups.google.com/group/google-desktop-linux-something-broken/browse_thread/thread/c9bcc6bdb62d7583)

---

### Post by florin-ganea on 2010-09-01
Well... it's within Google application; no workaround spotted.

I did the following:
- thunderbird (3.1.2) with firetray (0.2.8) add-on
- I changed in firetray configuration the icon both to:
---- /opt/google/desktop/resource/gdl_large.png
and 
---- /opt/google/desktop/resource/gdl_small.png
In both cases the icon was shown perfectly. Therefore the problem is not in icons, nor in notification area, nor in gnome, nor in gtk.

So, unless Google fixes it or someone likes to decompile GDS... we need to live with it.

All the best,
Florin

---

### Post by florin-ganea on 2010-09-02
I have performed further testing... and it might be the case that also the theme (controls part) has something wrong.

I noticed that the GDS icon is displayed perfectly in the following themes (controls):
- clearlooks
- clearlooks classic
- crux
- dust sand
- high contrast - all
- industrial
- inverted
- mist
- qtcurve
- raleigh
- redmond
- simple
- thin ice

Other themes display the GDS icon wrong:
- ambiance
- dust
- new wave - all
- radiance

All the best,
Florin

---

### Post by fpoehler on 2010-10-25
The themes that work should be the ones which have the same panel background as normal application windows. That's why the problem is not apparent there. However, newer themes often use a different color or a background image for the panel.

The fix is to apply the panel's properties (background color or background image) to GtkPlug widget class, which is not considered in most stock themes.

Steps:

[LIST=1]
[*]Find out your panel's background color or the path to its background image (in case it has one).
For the color the hexadecimal value is needed (e.g. "#A1B2C3).
The image in most cases resides in /usr/share/themes/<Your_Theme's_Name>/gtk-2.0/ or a subfolder of that.

For Radiance theme it is
```
/usr/share/themes/Radiance/gtk-2.0/apps/img/panel.png
```
[*](In case there is a background image) copy the background image to your home folder (or a subfolder of your home folder).
[*]Open (or create) the file named ".gtkrc-2.0" in your home folder.
[*]Copy the following into the file:
```
style "GoogleDesktopIconFix" {
    # In case your panel has a background image, add this line
    bg_pixmap[NORMAL] = "subfolder/panel.png"     # replace "panel.png" with the actual file name or (relative) path

    #In case your panel has no background image, add this line
    bg[NORMAL] = "#000000"              # replace "#000000" with your color value
}
class "*oPlug"    style "GoogleDesktopIconFix"
```
[*]Open a terminal and type ```
pkill gnome-panel
```
[*]enjoy :-)
[/LIST]

---

### Post by Zaff on 2010-10-25
> **fpoehler said:**
> The themes that work should be the ones which have the same panel background as normal application windows. That's why the problem is not apparent there. However, newer themes often use a different color or a background image for the panel.

The fix is to apply the panel's properties (background color or background image) to GtkPlug widget class, which is not considered in most stock themes.

Steps:

[LIST=1]
[*]Find out your panel's background color or the path to its background image (in case it has one).
For the color the hexadecimal value is needed (e.g. "#A1B2C3).
The image in most cases resides in /usr/share/themes/<Your_Theme's_Name>/gtk-2.0/ or a subfolder of that.

For Radiance theme it is
```
/usr/share/themes/Radiance/gtk-2.0/apps/img/panel.png
```
[*](In case there is a background image) copy the background image to your home folder (or a subfolder of your home folder).
[*]Open (or create) the file named ".gtkrc-2.0" in your home folder.
[*]Copy the following into the file:
```
style "GoogleDesktopIconFix" {
    # In case your panel has a background image, add this line
    bg_pixmap[NORMAL] = "subfolder/panel.png"     # replace "panel.png" with the actual file name or (relative) path

    #In case your panel has no background image, add this line
    bg[NORMAL] = "#000000"              # replace "#000000" with your color value
}
widget "GtkPlug"    style "GoogleDesktopIconFix"
```
[*]Open a terminal and type ```
pkill gnome-panel
```
[*]enjoy :-)
[/LIST]
Would this work for wine applications ? I'm running spotify and it's the only icon still having this problem (banshee used to do the same in 10.04 but it's not anymore).
I'll look into it but if anyone knows how to fix spotify's icon in the tray that'd be great.

---

### Post by fpoehler on 2010-10-25
Unfortunately I can't answer your question since I don't have Wine applications in use.
I suggest you simply try it out. It does not take you longer than 2 minutes and if it does not work for you, just delete the image and the .gtkrc-2.0 file (or undo the changes if the file was already there), restart the gnome panel and you're done.

---

### Post by Zaff on 2010-10-25
> **fpoehler said:**
> Unfortunately I can't answer your question since I don't have Wine applications in use.
I suggest you simply try it out. It does not take you longer than 2 minutes and if it does not work for you, just delete the image and the .gtkrc-2.0 file (or undo the changes if the file was already there), restart the gnome panel and you're done.

Just tried it, doesn't look like it's working though, could be a wine problem. Not too concerned about it, just thought I'd give it a shot.
Thanks.

---

### Post by fpoehler on 2010-10-25
Maybe the icon itself has no transparent background. In that case, the only way is to replace it with another icon that does have a transparent background.

---

### Post by florin-ganea on 2010-11-01
It works for me; thanks.

---

### Post by florin-ganea on 2010-11-01
I use radiance; and the fix has an interesting effect on the "lock" screen :-)
I have reverted the changes.

---

### Post by fpoehler on 2010-11-01
Ooops... Looks nice :) . Didn't notice that since I never lock my screen.

Try replacing *class "GtkPlug"* by *class "*oPlug"* to fix the issue.

---

### Post by florin-ganea on 2010-11-03
Now it's better; thank you.

---

### Post by vanbosco on 2010-11-21
It works also for me, thanks a lot.  :D

---

### Post by daucourt on 2010-11-22
Works for me on lucid LTS. Now beagle search icon has correct background.
During the step by step fix, I had to close gnome session ("pkill gnome-panel" what not enough)
Thanks a lot
Thierry

---

### Post by reablom on 2010-11-22
Ok. Works fine for me.
Thanks!

---

### Post by Redlichd on 2010-12-24
Ok guys so im new to this but bear with me i think i have it fixed
the problem seems to be with the theme itself, more specifically ambiance which is the default theme for 10.10 im not sure about 10.04
you can solve this by copying this into your terminal 
sudo gedit '/usr/share/themes/Ambiance/gtk-2.0/apps/gnome-panel.rc'
then you will see the file then put a # in front of line 10 where it says "bg_pixmap[NORMAL] = "img/panel.png"
log out then log back in and all should be well  :p

---

### Post by gamhead on 2011-02-20
Good work !

fpoehler is the  man!

Now my utorrent and google desktop integrate perfectly - thanks! I went through so many rubbish forums before I found this.. :KS

---

### Post by deezer on 2011-02-28
fpoehler you are the man!

Original poster, please mark as solved!

---

### Post by shahraeini on 2011-04-10
thanks fpoehler, It works great for me, but I have a question.
for other application what should we do?! I think this code works only for google desktop.
> **fpoehler said:**
> The themes that work should be the ones which have the same panel background as normal application windows. That's why the problem is not apparent there. However, newer themes often use a different color or a background image for the panel.

The fix is to apply the panel's properties (background color or background image) to GtkPlug widget class, which is not considered in most stock themes.

Steps:

[LIST=1]
[*]Find out your panel's background color or the path to its background image (in case it has one).
For the color the hexadecimal value is needed (e.g. "#A1B2C3).
The image in most cases resides in /usr/share/themes/<Your_Theme's_Name>/gtk-2.0/ or a subfolder of that.

For Radiance theme it is
```
/usr/share/themes/Radiance/gtk-2.0/apps/img/panel.png
```
[*](In case there is a background image) copy the background image to your home folder (or a subfolder of your home folder).
[*]Open (or create) the file named ".gtkrc-2.0" in your home folder.
[*]Copy the following into the file:
```
style "GoogleDesktopIconFix" {
    # In case your panel has a background image, add this line
    bg_pixmap[NORMAL] = "subfolder/panel.png"     # replace "panel.png" with the actual file name or (relative) path

    #In case your panel has no background image, add this line
    bg[NORMAL] = "#000000"              # replace "#000000" with your color value
}
class "*oPlug"    style "GoogleDesktopIconFix"
```
[*]Open a terminal and type ```
pkill gnome-panel
```
[*]enjoy :-)
[/LIST]


---

### Post by fpoehler on 2011-04-10
This code may or may not work with other applications. The name "GoogleDesktopIconFix" is only a kind of variable you assign key/value pairs to and then say elements of a certain class shall apply what's defined in that variable. It doesn't mean it works only for the Google Desktop icon.

So the key to the problem is not the [FONT=Courier New]style "GoogleDesktopIconFix"[/FONT] but the [FONT=Courier New]class [/FONT]name [FONT=Courier New]"*oPlug"[/FONT]: Every display element (e.g. a window, a button or a menu) has a GTK class and some parent classes (e.g. a toolbar is a special kind of a container. You can find a reference [here]("http://developer.gnome.org/gtk/2.24/gtkobjects.html")). Moreover, a developer can create subclasses with own names.

If you say [FONT=Courier New]class "*foo" style "bar"[/FONT], every element whose class name ends with "foo" will apply the style defined in "bar", e.g. a certain background color. (The "*" is a wildcard as known from file name searches).

So if you know the class name of the tray icon of your application, it's easy. Change [FONT=Fixedsys]"*oPlug"[/FONT] into that name and you shoud be done (provided the application does not use an icon with intransparent background). Unfortunately, there is no sure formula to find out that name (at least I don't know it). You'll find it somewhere in the source code, that's all I can say. 

If you don't want to dig into source code, you can solve the issue the trial-and-error way:

[LIST=1]
[*]Comment out the bg_pixmap line in the gtkrc and change the bg[NORMAL] color value to some "crazy" color (e.g. #F00, which is pure red).
[*]Change the class name in gtkrc to something else and save file.
[*]Open gnome-appearance-properties and choose any other theme.
[*]After the appearance has changed, change back to the theme of the gtkrc you are editing.
[*]See what has changed now (=what is now red in my example) and what has not.
[*]Repeat steps 2-5 until only the icon of your application has changed (it's recommended to have some more applications present in order to notice unwanted changes).
[*]Undo step 1, then type [FONT=Courier New]pkill gnome-panel[/FONT] in terminal. Everything should look good now.
[/LIST]
(For step 2 - do it methodically. First try excluding letters by changing the class name to "*x*" where x is a single letter (case matters!) and replace step 3-4 with typing [FONT=Courier New]pkill gnome-panel[/FONT] in a terminal. If your icon has not changed in step 5, you know that letter is not in the class name you want. After you are through, try combinations of 2 letters and so on).

But be warned: This is very annoying and may take a lot of time. Only do it if the ugly icon is even more annoying.

---

### Post by naczelny1 on 2011-11-29
Those are all crude workarounds. The only solution is to fix notification area so that it wouldn't take the bg colour from window bg, but instead from gnome-panel, or - better yet - to have this customisable, including opacity value. How about we spam  <ubuntu-desktop@lists.ubuntu.com> about this until someone reacts?

---

