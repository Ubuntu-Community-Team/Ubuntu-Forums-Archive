---
title: "Left/Right buttons + mouse not rotating cube after update?"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by dustintinsley on 2007-09-04
After a recent update, my Beryl Fusion hasn't been working the same. I use to be able to hit the left mouse button + the right mouse button the initiate the cube rotation. When I did this, the cube would "zoom out" and I could rotate the cube with my mouse.  That no longer works.  Hitting the left/right mouse buttons together no longer initiate the cube rotation.  What can I do to get that function back?

---

### Post by dustintinsley on 2007-09-04
This is in Compiz Fusion, btw...

---

### Post by Inxsible on 2007-09-04
that functionality has been removed from Compiz Fusion for some reason.

It was sure nice to have tho :(

---

### Post by dustintinsley on 2007-09-04
Oh.. Wow, that makes no sense what so ever...

---

### Post by dchky on 2007-09-04
After an update thismorning I could no longer rotate the cube to the right - left works fine.

After opening up the rotate cube keybindings - completely missing from the list is the keyboard option to "rotate right"

Bit of a hassle, I touch type, so CTRL+ALT Left/Right is pretty important. Any idea where compiz stores these keybindings? I'd love to tweak the files by hand, only it's a bit of a convoluted mess to figure out where things are.

---

### Post by isaacj87 on 2007-09-04
It works for me now after today's update (Trevino's repo)

Unfortunately, the ctrl+alt right function is broken...somehow it doesn't have a binding to rotate right anymore?? only left.

Today's update was not a good one for me...actually the worse I've had in awhile. I'm confused as to why it's still 0.5.5 when bleeding edge is already 0.6.0. GIT

---

### Post by meermanr on 2007-09-04
I'm also getting this problem - I even tried hacking a new setting in gconf-editor at "/apps/compiz/plugins/rotate/allscreens/options called "rotate_right_key" but gconf-editor said that my new entry didn't have a schema. It didn't appear to work anyway, so I've removed it.

I'd really like to be able to go right as well as left when rotating... :(

---

### Post by isaacj87 on 2007-09-04
I wouldn't worry about it. I'm sure in the next few days it'll be fixed. I'm just glad that my mouse rotating function is back.

---

### Post by hyperair on 2007-09-04
I noticed that while the mouse rotating function is back, this time it won't let go unless you click the left button. Not that I'm complaining, it doesn't inconvenience me majorly or anything.

Also, the Rotate Left and Rotate Right mouse bindings are back in Rotate Cube =P I've always used that in the past.

Also Scale Addons refuses to load, because it can't find a Scale plugin with ABI 20070830 or something of that sort. Perhaps Trevino forgot to recompile the new one?

@meermanr: You could use the Expo to get to the right =P. Trigger the Expo and use the arrow keys.

---

### Post by isaacj87 on 2007-09-04
> **hyperair said:**
> I noticed that while the mouse rotating function is back, this time it won't let go unless you click the left button. Not that I'm complaining, it doesn't inconvenience me majorly or anything.

Also, the Rotate Left and Rotate Right mouse bindings are back in Rotate Cube =P I've always used that in the past.

Also Scale Addons refuses to load, because it can't find a Scale plugin with ABI 20070830 or something of that sort. Perhaps Trevino forgot to recompile the new one?

@meermanr: You could use the Expo to get to the right =P. Trigger the Expo and use the arrow keys.

Yeah, I'm thinking Trevino may have goofed up on something here. I checked the GIT status and everything is okay. What I'm not sure about is why we're still at 0.5.5. I saw a thread that said bleeding edge was 0.6.0, which is supposed to be the stable release?

---

### Post by hyperair on 2007-09-05
Perhaps 0.6.0 isn't stable enough for him to use in his repositories. Anyway it could be that he forgot to recompile the compiz-fusion-plugins-unsupported package. That'll be the reason Shift Switcher and Scale Addons refuse to work properly. As for the CCSM, it's probably a Compiz Fusion team problem.

---

### Post by ayoli on 2007-09-05
I have also the broken CTRL+ALT+Right issue and a issue with firefox menus that now use the open animation effect even with plugin workaround/fix_for_firefox_menus enabled.
Hope it will be fixed in next update.
edit: it will since this binding has just been forget. It's fixed now just have to wait to Trevino's updates
[http://forum.compiz-fusion.org/showthread.php?t=3919](http://forum.compiz-fusion.org/showthread.php?t=3919)

---

### Post by swiftrahul on 2007-09-05
I am having the same problem as well.
The left rotation seems to be working fine, but I can't right rotate my cube using keys.
Also, there is no option in the "key bindings" for right rotating the cube using keyboard.

any fix to this problem ??

---

### Post by Inxsible on 2007-09-05
I updated today Sept 05. But I dont see that problem. I can still use the Ctrl + Alt + Right to move right.

---

### Post by isaacj87 on 2007-09-05
> **Inxsible said:**
> I updated today Sept 05. But I dont see that problem. I can still use the Ctrl + Alt + Right to move right.

Are you using Trevino's repo? Because the update was for yesterday. There isn't a new update yet.

---

### Post by isaacj87 on 2007-09-05
> **hyperair said:**
> Perhaps 0.6.0 isn't stable enough for him to use in his repositories. Anyway it could be that he forgot to recompile the compiz-fusion-plugins-unsupported package. That'll be the reason Shift Switcher and Scale Addons refuse to work properly. As for the CCSM, it's probably a Compiz Fusion team problem.

You're having problems with the shift switcher? I noticed it was acting funny too. It's just the key bindings got screwed up...they actually work except you have to check the key bindings to make sure they're not conflicting with other plugins.

---

### Post by hyperair on 2007-09-05
Shift switcher working for me. Ctrl+Alt+Right not. >< Feels a bit funny without. The CCSM entry is missing too.

---

### Post by isaacj87 on 2007-09-05
I've noticed that certain animations are different with Trevino's Repo. What gives? For example, the magic lamp animations is noticeably different than other repo/compiling from scratch. Plus, he doesn't provide a deb for the fusion-icon. Which I thought was strange as well.

---

### Post by Inxsible on 2007-09-05
> **isaacj87 said:**
> Are you using Trevino's repo? Because the update was for yesterday. There isn't a new update yet.
yeah i use Trevino's...but I didn't get an update yesterday...I got it in the morning today

---

### Post by ayoli on 2007-09-05
> **Inxsible said:**
> yeah i use Trevino's...but I didn't get an update yesterday...I got it in the morning today

so you must be lucky :)

---

### Post by mpospisil on 2007-09-05
I also just updated my Compiz Fusion using Trevino's Repo and my Ctrl + Alt + Right button no longer works and it is no where to be found in the CCSM.  I hope they fix this soon because this is annoying.  On another note, I also had a kernal update this morning that kind of screwed me a little bit.  After updating the kernal for a security update my sound card driver had to be recompiled and installed.  Thats the second time I've done that.

---

### Post by Inxsible on 2007-09-05
> **ayoli said:**
> so you must be lucky :)

Well I should say I was....Now I too have the Ctrl + Alt + Right problem as in i dont move to my desktop on the right :(

---

### Post by 3ark on 2007-09-05
I also have this problem, no way to go rotate right from the keyboard. On the plus side, my AWN is running soooo smooth now. In fact everything appears to be much smoother (particularly noticeable on my lower-end lappy). So, should we all report this to anyone or should this thread suffice?

---

### Post by tak1150 on 2007-09-05
> **3ark said:**
> I also have this problem, no way to go rotate right from the keyboard. On the plus side, my AWN is running soooo smooth now. In fact everything appears to be much smoother (particularly noticeable on my lower-end lappy). So, should we all report this to anyone or should this thread suffice?

Yeah, I'd like to know how to report these things (I too have the Ctrl+Alt+**Right** problem) so that I'll know how in the future even if somebody already has reported it.

I think this problem is some extreme **left** winger's conspiracy :)

---

### Post by ayoli on 2007-09-05
> **3ark said:**
> I also have this problem, no way to go rotate right from the keyboard. On the plus side, my AWN is running soooo smooth now. In fact everything appears to be much smoother (particularly noticeable on my lower-end lappy). So, should we all report this to anyone or should this thread suffice?

There is already a thread for the rotate right key binding problem on [compiz forums]("http://forum.compiz-fusion.org/showthread.php?t=3919").
For the plus side feel free to report it on their forum

---

### Post by Inxsible on 2007-09-05
> **tak1150 said:**
> I think this problem is some extreme **left** winger's conspiracy :)
LOL:lolflag:

---

### Post by smithman89 on 2007-09-05
I fixed the rotate right function on my computer after having the same problem all you guys had.  It was a fault in the file '/usr/share/compiz/rotate.xml'  The devs forgot to add a section of code for the rotate_right_key (they only had one for the button which doesnt work).  So i copy and pasted the rotate_right_button code, and changed the 2 instances of the word button to key.  Restarted compiz and tada!  It worked :D

A little howto:
```
gksu gedit
```
Open up /usr/share/compiz/rotate.xml
```
<option type="key" name="rotate_right_key">
		<short>Rotate Right</short>
		<short xml:lang="ca">Gira cap a la dreta</short>
		<short xml:lang="cs">Oto&#269;it vpravo</short>
		<short xml:lang="da">Roter højre</short>
		<short xml:lang="de">Rechts drehen</short>
		<short xml:lang="es">Girar a la derecha</short>
		<short xml:lang="fi">Käännä oikealle</short>
		<short xml:lang="fr">Rotation à droite</short>
		<short xml:lang="hu">Forgatás jobbra</short>
		<short xml:lang="it">Ruota a Destra</short>
		<short xml:lang="ja">&#21491;&#12395;&#22238;&#36578;</short>
		<short xml:lang="pl">Obró&#263; w prawo</short>
		<short xml:lang="pt">Girar para a Direita</short>
		<short xml:lang="pt_BR">Girar para a Direita</short>
		<short xml:lang="ru">&#1042;&#1088;&#1072;&#1097;&#1072;&#1090;&#1100; &#1074;&#1087;&#1088;&#1072;&#1074;&#1086;</short>
		<short xml:lang="sv">Rotera åt höger</short>
		<short xml:lang="zh_CN">&#39034;&#26102;&#38024;&#26059;&#36716;</short>
		<short xml:lang="zh_TW">&#24448;&#21491;&#26059;&#36681;</short>
		<long>Rotate right</long>
		<long xml:lang="ca">Gira cap a la dreta</long>
		<long xml:lang="cs">Oto&#269;it vpravo</long>
		<long xml:lang="da">Roter til højre</long>
		<long xml:lang="de">Rechts drehen</long>
		<long xml:lang="es">Girar a la derecha</long>
		<long xml:lang="fi">Käännä oikealle</long>
		<long xml:lang="fr">Rotation à droite</long>
		<long xml:lang="hu">Jobbra forgatás</long>
		<long xml:lang="it">Ruota a destra</long>
		<long xml:lang="ja">&#21491;&#12395;&#22238;&#36578;</long>
		<long xml:lang="pl">Obró&#263; w prawo</long>
		<long xml:lang="pt">Girar para a direita</long>
		<long xml:lang="pt_BR">Girar para a direita</long>
		<long xml:lang="ru">&#1042;&#1088;&#1072;&#1097;&#1077;&#1085;&#1080;&#1077; &#1074;&#1087;&#1088;&#1072;&#1074;&#1086;</long>
		<long xml:lang="sv">Rotera åt höger</long>
		<long xml:lang="zh_CN">&#39034;&#26102;&#38024;&#26059;&#36716;</long>
		<long xml:lang="zh_TW">&#24448;&#21491;&#26059;&#36681;</long>
	    </option>
```
Copy and paste this large chunk of code above this line of code in the file:
```
<option type="button" name="rotate_right_button">
```
Save, restart compiz, and enjoy!

---

### Post by ayoli on 2007-09-05
Here is a fix from doppler from compiz forums:

```
gksudo gedit /usr/share/compiz/rotate.xml
```
Insert this right after the closing tag of "rotate_left_button" and right before the opening tag of "rotate_right_button":

```
 <option name="rotate_right_key" type="key">
    <short>Rotate Right</short>
    <long>Rotate Right</long>
    <default>&lt;Control&gt;&lt;Alt&gt;Right</default>
</option>
```
Restart compiz, that fix the problem for me :)

EDIT : Lol, a bit too late :D

---

### Post by smithman89 on 2007-09-05
> **ayoli said:**
> EDIT : Lol, a bit too late :D
Just by a hair :D

---

### Post by Inxsible on 2007-09-05
Sweet !!

Can't wait to get home and try it :D

---

### Post by ayoli on 2007-09-05
> **Inxsible said:**
> Sweet !!

Can't wait to get home and try it :D
Keep in mind that it is only a fix, next update should correct this.

---

### Post by Inxsible on 2007-09-05
> **ayoli said:**
> Keep in mind that it is only a fix, next update should correct this.
Yeah....but who's gonna wait until the next update !!

In anycase now that I know which file controls that plugin...I might just go exploring the XML code there...to see how they implemented the nifty things 

:)

---

### Post by ayoli on 2007-09-05
> **Inxsible said:**
> Yeah....but who's gonna wait until the next update !!

:)
Just in case update comes before you get back home :)
> **Inxsible said:**
> 
In anycase now that I know which file controls that plugin...I might just go exploring the XML code there...to see how they implemented the nifty things 

:)

yeah, this show us a bit how this app works, good side of the problem :)

---

### Post by mpospisil on 2007-09-05
> **ayoli said:**
> Here is a fix from doppler from compiz forums:

```
gksudo gedit /usr/share/compiz/rotate.xml
```
Insert this right after the closing tag of "rotate_left_button" and right before the opening tag of "rotate_right_button":

```
 <option name="rotate_right_key" type="key">
    <short>Rotate Right</short>
    <long>Rotate Right</long>
    <default>&lt;Control&gt;&lt;Alt&gt;Right</default>
</option>
```
Restart compiz, that fix the problem for me :)

EDIT : Lol, a bit too late :D

This worked like a charm.  Ctrl + Alt + Right now works again.  Thanks!

---

### Post by meermanr on 2007-09-06
I took an update this morning (so, er, about 2 hours before this post) and Ctrl+Alt+Right is working again. I'd not gotten around to hacking my rotate.xml, so this is just a plain old update!

And yes, I am using Tevino's repo:
```
# compiz-fusion by Tevino's Ubuntu feisty EyeCandy Repository
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

---

### Post by hyperair on 2007-09-06
Don't bother hacking.. the new update fixes it. I came home today and after the update it worked =P

---

### Post by Inxsible on 2007-09-06
> **hyperair said:**
> Don't bother hacking.. the new update fixes it. I came home today and after the update it worked =P

I am always late on the updates... I still haven't got one :(

By tonight, I shall I think.

---

### Post by hyperair on 2007-09-06
There's a way to speed up updates actually. First you update your APT repository:
```
sudo apt-get update
```

Then you run update-manager, or wait a few more minute for the icon to pop up:
```
update-manager
```

---

### Post by Inxsible on 2007-09-06
Thanks for the info. In any case, I am at work now :)

So I will have to wait until evening to do anything :)

But its good to know

---

### Post by ayoli on 2007-09-06
> **hyperair said:**
> Don't bother hacking.. the new update fixes it. I came home today and after the update it worked =P

I had the update, which has the fix, I did the hack before cause I couldn't wait :)
Now I have another problem (I think it's been since compiz 0.5.2) : 
Animation plugin causes screen to lock up. Mouse can still move but clics do not work and no keyboard. I must log in with ssh from another computer to reboot.
this thread in compiz forum looks like my problem.
Does anyone else experiment such a bug ?

---

### Post by Inxsible on 2007-09-06
I haven't seen it on my machine yet.

---

### Post by isaacj87 on 2007-09-06
I know it's weird...if I go to Trevino's page, I can see the update...but it won't show up in the update manager...

I've really disappointed lately as I've hit nothing but regressions for both Compiz Fusion and Avant-Window-Navigator :(...I guess that's what I get for using alpha/beta software.

---

### Post by Inxsible on 2007-09-06
> **isaacj87 said:**
> I know it's weird...if I go to Trevino's page, I can see the update...but it won't show up in the update manager...

I've really disappointed lately as I've hit nothing but regressions for both Compiz Fusion and Avant-Window-Navigator :(...I guess that's what I get for using alpha/beta software.

Do you really have so many problems ?

I am surprised because I don't. I had the Ctrl + Alt + Right thing...for a while and then I fixed it.

Have you seen additional problems ?

---

### Post by ayoli on 2007-09-06
> **Inxsible said:**
> Do you really have so many problems ?

I am surprised because I don't. I had the Ctrl + Alt + Right thing...for a while and then I fixed it.

Have you seen additional problems ?

I have, see my previous [post]("http://ubuntuforums.org/showthread.php?t=542990&page=4#40")

---

### Post by Inxsible on 2007-09-06
> **ayoli said:**
> I have, see my previous [post]("http://ubuntuforums.org/showthread.php?t=542990&page=4#40")

Now I am wondering if I should update !!!

Boy, Am I glad I get those updates late ;)

---

### Post by ayoli on 2007-09-06
> **Inxsible said:**
> Now I am wondering if I should update !!!

Boy, Am I glad I get those updates late ;)

I have this GUI freeze problem for two weeks, it seems to be related to animation plugin and comes most of the times after a couple of hours running the screensaver, or sometimes on window resizing.

---

### Post by Inxsible on 2007-09-06
I havent resized the windows much...but my screensaver runs thru the night ..but I haven't had the lock up that you talk about. What plugins are you using under Animations ?

---

### Post by ayoli on 2007-09-06
> **Inxsible said:**
> I havent resized the windows much...but my screensaver runs thru the night ..but I haven't had the lock up that you talk about. What plugins are you using under Animations ?

I used sidekick for open animations, but came back to defaults. defaults for all other. I just change a bit durations (to a bit longer time, ie + 50-100 ms)

---

### Post by isaacj87 on 2007-09-06
> **Inxsible said:**
> Do you really have so many problems ?

I am surprised because I don't. I had the Ctrl + Alt + Right thing...for a while and then I fixed it.

Have you seen additional problems ?

Yeah, it just doesn't seem to working the same. I dunno. For example, my menus are set to be transparent, so if I click"Applications" in my panel it'll be transparent. but if I move to games that sub-menu won't be transparent?!

I'm thinking of just compiling from source.

---

### Post by smithman89 on 2007-09-06
Ive been having a weird problem with xscreensaver while running compiz.  Certain screensavers will make my computer freeze (all but the mouse like other people were saying).  But ive had this happen before the latest update, like at least 2 weeks in advance.  I usually dont run any screensaver in compiz because of the transparency (it makes the screensaver transparent), so i usually run metacity --replace before locking the screen or whatever.

---

### Post by isaacj87 on 2007-09-06
> **isaacj87 said:**
> Yeah, it just doesn't seem to working the same. I dunno. For example, my menus are set to be transparent, so if I click"Applications" in my panel it'll be transparent. but if I move to games that sub-menu won't be transparent?!

I'm thinking of just compiling from source.

I may have spoke to soon...the only thing I can see broken is sometimes my panel doesn't come up on start up...and the firefox menu workaround is broken...everything else seems okay.

---

### Post by hyperair on 2007-09-06
Mine seems fine... I reckon there are some old settings which conflict from previous versions of Compiz Fusion. Try clearing all the settings:
```

rm -r ~/.gconf/apps/compiz
rm -r ~/.config/compiz

```

Then restart Compiz and use CompizConfig Settings Manager to start all over again. That usually fixed any error for me in the past.

---

### Post by Inxsible on 2007-09-07
just did a manual update. Everything seems to be working fine until now :)

---

### Post by ayoli on 2007-09-07
> **isaacj87 said:**
> I may have spoke to soon...the only thing I can see broken is sometimes my panel doesn't come up on start up...and the firefox menu workaround is broken...everything else seems okay.

Same here about firefox workaround

---

### Post by hyperair on 2007-09-07
Yeah same here too =\

---

### Post by ayoli on 2007-09-07
> **hyperair said:**
> Mine seems fine... I reckon there are some old settings which conflict from previous versions of Compiz Fusion. Try clearing all the settings:
```

rm -r ~/.gconf/apps/compiz
rm -r ~/.config/compiz

```

Then restart Compiz and use CompizConfig Settings Manager to start all over again. That usually fixed any error for me in the past.

I ve just done that (pretty anoying :-/ ), this didn't fix firefox workaround problem, I'll see if it fix the screen freeze later.
For those who have a scren+keyboard freeze:
hit:
**ALT+SysRq+R**
then hit:
**ALT+F1**
log into terminal and kill X:
```
sudo killall Xorg
```
this will restart X and GDM.

---

### Post by hyperair on 2007-09-07
What does Alt+SysRq+R do?

---

### Post by ayoli on 2007-09-07
> **hyperair said:**
> What does Alt+SysRq+R do?
We're going a bit offtopic but here is some usefull kernel key combos to know:
[LIST]
[*]**Alt+SysRq+r** : Turn off keyboard raw mode. This can be useful when your X session hangs.
[*]**Alt+SysRq+e** : Send a SIGTERM to all processes, except for init.
[*]**Alt+SysRq+B** : reboot (the fastest way to reboot)
[/LIST]

---

### Post by smithman89 on 2007-09-07
> **ayoli said:**
> I ve just done that (pretty anoying :-/ ), this didn't fix firefox workaround problem, I'll see if it fix the screen freeze later.
For those who have a scren+keyboard freeze:
hit:
**ALT+SysRq+R**
then hit:
**ALT+F1**
log into terminal and kill X:
```
sudo killall Xorg
```
this will restart X and GDM.

Thank god, it worked :D  There is one screensaver in xscreensaver that makes my computer freeze like that.  The alt+sysrq+r worked.  Its good to finally learn that command, restarting my comp takes too long for my patience.
EDIT:  Is there any way to get back to the desktop and out of terminal mode after pressing alt+F1?  Cause i killed the process that made the comp freeze, is there anyway to go back now?

---

