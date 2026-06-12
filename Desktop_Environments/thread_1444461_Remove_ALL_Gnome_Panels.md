---
title: "Remove ALL Gnome Panels"
date: 2010-04-01
forum: Desktop Environments
---

### Post by johnathanamber on 2010-04-01
Hey everyone!

I want to solely use AWN for my desktop.

I no longer need any panels.

I can not delete the last panel on my desktop, the 'Delete This Panel' is grayed out.

I've already searched the forums and found two commands that could work in previous versions of Ubuntu, but they do not work in Karmic.

Here is the output of my term with the results of each command:
> 
$ killall gnome-panel
$ gnome-session-remove gnome-panel
gnome-session-remove: command not found


The '$ killall gnome-panel' actually does kill the panel... however it comes back just as soon as it is removed.

Thank you very much and God bless,
Johnathan

---

### Post by nothingspecial on 2010-04-01
```
sudo mv /usr/bin/gnome-panel ~/.panel_backup
```

You might want to have a look at gnome-do before you do because you will loose Alt-F1 and Alt-F2

If you decide you don`t like it

```
sudo mv ~/.panel_backup /usr/bin/gnome-panel
```

---

### Post by johnathanamber on 2010-04-01
@nothingspecial,

Evidently you ARE special!

That worked flawlessly.... I had to log off and then back in for it to work out, but it did work out.

I made some bash scripts to bring those back if I had to.

Now I am using AWN for everything... looking GREAT.

I am real big on saving as much as possible in real estate on my desktop. Now all of my apps span the entire screen with nothing in the way... AWESOME!

Again thank you nothingspecial.

Thank you and God bless,
Johnathan

---

### Post by asmoore82 on 2010-04-01
Future updates will restore the gnome-panel binary and
you'll be back where you started.

I think you can accomplish this cleaner by going into `gconf-editor`
and changing "/desktop/gnome/session/required_components_list"

Or better yet you might be able to just change
"/desktop/gnome/session/required_components/panel" to "awn"

---

### Post by johnathanamber on 2010-04-01
@asmoore82,

Thank you for that.

Question... how would I do this in a script so I can easily back this out if I need to?

Thank you and God bless,
Johnathan

---

### Post by mcduck on 2010-04-01
> **johnathanamber said:**
> @asmoore82,

Thank you for that.

Question... how would I do this in a script so I can easily back this out if I need to?

Thank you and God bless,
Johnathan

You can use gconftool-2 to edit gconf keys from command line:

```
gconftool-2 --type string --set /desktop/gnome/session/required_components/panel "awn"
```

```
gconftool-2 --type string --set /desktop/gnome/session/required_components/panel "gnome-panel"
```

---

### Post by johnathanamber on 2010-04-05
@mcduck,

Thank you for that information. gconfigtool-2 is not available... I assume that I will have to install it from the repositories??!!?

Would this work instead:
```

gconf-editor --type string --set /desktop/gnome/session/required_components/panel "awn"

```

And:
```

gconf-editor --type string --set /desktop/gnome/session/required_components/panel "gnome-panel"

```

Thank you and God bless,
Johnathan

---

### Post by oldos2er on 2010-04-05
It's gconftool-2 (not gconfigtool-2). Copy and paste the commands mcduck gave you.

---

### Post by johnathanamber on 2010-04-05
@oldos2er,

Yeah sorry about that... mind tricks.

Thank you and God bless,
Johnathan

---

### Post by Mi11z on 2010-09-25
> **johnathanamber said:**
> @oldos2er,

Yeah sorry about that... mind tricks.

Thank you and God bless,
Johnathan

Yeah i used the gconf method, but i know that's cleaner but i swear theres a "smoother" way that doesn't sacrifice alt-f2 etc, anyway cheers.

---

### Post by electrofreak on 2010-11-17
Sorry, but I have to bring this apparently solved problem back up. 

I would rather not remove the gnome-panel binary... because that limits other users from using the panel.

And setting desktop/gnome/session/required_components --> panel evidently does NOTHING. Some sites said just clear it, some said right click and "unset key" (which apparently just sets it back to gnome-panel), and this thread suggested setting it to "awn". Doesn't matter what method I use... nothing works. Gnome-panel still comes back.

Please Help.

Edit: I suppose I should mention I'm on 10.10. Fairly fresh install.

---

### Post by mcduck on 2010-11-18
Actually changing the gconf key works perfectly, I just tried it. It's just that the current version of AWN is launched using the command "avant-window-navigator", not "awn", so you need to change that in the key.

edit: Also, if you want it to auotmatically launch AWN, you don't change the *desktop/gnome/session/required_components*-key but the *desktop/gnome/session/required_components/panel*-key instead. (The first one tells what type of components should be included in the session (panel, window manager, file manager), while the second one actually tells what program to use as that component)

---

### Post by electrofreak on 2010-11-18
> **mcduck said:**
> Actually changing the gconf key works perfectly

false.

```
todd@todd-ubuntu:~$ cat .gconf/desktop/gnome/session/required_components/%gconf.xml 
<?xml version="1.0"?>
<gconf>
	<entry name="panel" mtime="1290124654" type="string">
		<stringvalue>avant-window-navigator</stringvalue>
	</entry>
	<entry name="windowmanager" mtime="1290048047" type="string">
		<stringvalue>compiz</stringvalue>
	</entry>
</gconf>
```

It literally does nothing. gnome-panel still launches. and killall gnone-panel still doesn't work for more than a half second (because it gets relaunched).

for fun I set it to 'vlc'... and it does NOT launch when I login. This setting appears to be completely ignored. I will try removing "panel" from the required components list.

Edit: Ok, I removed "panel" as a required component... and again... it was completely ignored. Other than deleting the gnome-panel binary... I cannot get this stupid panel to go away.

---

### Post by mcduck on 2010-11-18
Like I said, I just did this, on a fresh new user account  on 10.10. And it works just fine, gnome-panel doesn't launch and AWN is launched instead.

```
metaduck@Hyperion:~$ cat .gconf/desktop/gnome/session/required_components/%gconf.xml 
<?xml version="1.0"?>
<gconf>
	<entry name="panel" mtime="1290071773" type="string">
		<stringvalue>avant-window-navigator</stringvalue>
	</entry>
</gconf>
metaduck@Hyperion:~$
```

---

### Post by TNT1 on 2010-11-18
> **mcduck said:**
> Actually changing the gconf key works perfectly, I just tried it. It's just that the current version of AWN is launched using the command "avant-window-navigator", not "awn", so you need to change that in the key.



I tried that, and the panel is still there, awn is still there, and my windows lost their borders. Help?

---

### Post by mcduck on 2010-11-19
> **TNT1 said:**
> I tried that, and the panel is still there, awn is still there, and my windows lost their borders. Help?

Whatever you do with that setting, it simply can't affect your window borders. You must have changed a wrong gconf key or something.

Just to be sure, could you run the following commands & post the output here:
```
gconftool -g /desktop/gnome/session/required_components_list
gconftool -g /desktop/gnome/session/required_components/panel
```

---

### Post by TNT1 on 2010-11-19
> **mcduck said:**
> 
```
gconftool -g /desktop/gnome/session/required_components_list
gconftool -g /desktop/gnome/session/required_components/panel
```

```
[windowmanager,panel,filemanager]
```

and 

```
avant-window-navigator
```

---

### Post by mcduck on 2010-11-19
> **TNT1 said:**
> ```
[windowmanager,panel,filemanager]
```

and 

```
avant-window-navigator
```

That seems to be correct. I really have no idea why this isn't working for you, it's the correct way based on both Gnome's and AWN's documentation, and works just fine for most of us. Also I'm not even able to replicate the problem you are having, not even if I specifically *try* to do so.

Sorry, but at least with the information I have now about how your desktop I can't help. I can only think that there must be some information missing about your setup, but truly don't know what might cause the gconf setting to not work like it should. Like I said, I can't replicate that behavior even if I try.

You could perhaps try if it works if you create a fresh new user account, just to check if some of your current user's settings is stopping this from working like it should.

---

### Post by TNT1 on 2010-11-19
Yeah, I'll try that. I am sure it's something I've tweaked in my settings that is preventing this from happening. At least getting the window borders back was easy enough, but I really want to remove the panel.

---

### Post by electrofreak on 2010-11-19
```

[windowmanager,filemanager]
avant-window-navigator

```

I also tried like TNT1 (and the default except for the change to the panel setting:

```

[windowmanager,panel,filemanager]
avant-window-navigator

```

I wonder if there is a version problem??

```
$ gnome-session --version
gnome-session 2.32.0
```

I think that's just the latest on 10.10.

---

### Post by TNT1 on 2010-11-19
> **electrofreak said:**
> ```

[windowmanager,filemanager]
avant-window-navigator

```I also tried like TNT1 (and the default except for the change to the panel setting:

```

[windowmanager,panel,filemanager]
avant-window-navigator

```I wonder if there is a version problem??

```
$ gnome-session --version
gnome-session 2.32.0
```I think that's just the latest on 10.10.

Dunno, I'm ```
$ gnome-session --version
gnome-session 2.30.0
```

So?

---

### Post by electrofreak on 2010-11-23
So.... I dunno.

I'd still really like to get this resolved. I really don't like having a blank panel at the top of my left monitor. It's wasting so many pixels!

---

### Post by lanetherif on 2010-11-27
> **electrofreak said:**
> So.... I dunno.

I'd still really like to get this resolved. I really don't like having a blank panel at the top of my left monitor. It's wasting so many pixels!

I've got the same problem here. The solutions offered don't work.
By the way, do you have a notification in Key Documentation that tells "This key is not writable"  ? Although I don't have any basis, I am thinking that it might be about it.

---

### Post by Michalxo on 2010-12-12
Hello!

 Has anyone found out yet how to remove them all?
I am stuck with last undeletable and unkillable gnome-panel. Trying to substitute it with AWN, with no positive result. 
I hide last gnome-panel using hide buttons on sides of panel, but I'd like to completely remove it. 
Would be fine if someone could finally solve this issue.
Cheers Mich

---

### Post by pedi0022003 on 2010-12-23
why this thread is marked as solved?!

---

### Post by Version Dependency on 2010-12-23
There are several ways to prevent gnome-panel from loading.  The most common way is to use gconftool2 to replace gnome-panel on startup with AWN or some other dock/panel that you wish to use:
```
gconftool-2 --type=string --set /desktop/gnome/session/required_components/panel 'avant-window-navigator'
```The above code has AWN startup instead of gnome-panel.

Another simple way is to make gnome-panel unexecutable...but make sure you have another panel/dock ready to load in your startup applications when you reboot:

```
 sudo chmod -x /usr/bin/gnome-panel
```Then reboot.  To make gnome panel executable again simply run:

```
 sudo chmod +x /usr/bin/gnome-panel
```And, if you use Ubuntu Tweak, under Session Control you can change your default panel, window manager, and file manager.  Useful program if you don't already have it.

Best of luck!  :D

---

### Post by erusnex on 2011-01-11
For me when using gconfeditor
It displays
"This key is not writable."
-only for the panel option.
The others seem 'normal'

What have I done?

Thx

---

### Post by GoGoGulliver on 2011-02-17
I've been having the same problem (I think). No matter what I do to change gnome-panel to avant-window-navigator, it keeps coming back. I've tried Ubunte Tweak, changing the thing in Configuration Editor, doing the same thing in Terminal, making it un-executable, with and without sudo... no luck.

This is odd, as it worked on a previous install. (I did a reinstall because I severely borked something, now it's working better than before with this one exception).

Has anyone got any ideas? The session manager seems to be holding on to gnome-panel, even though I told it not to. Or something.

Any bright ideas?

---

### Post by Krytarik on 2011-02-17
I suppose you already checked the above mentioned setting in
"/desktop/gnome/session/required_components/panel",
also "/desktop/gnome/session/required_components_list"?

Did you also check if gnome-panel is instead listed in "Startup Applications"?
That was the case when I tried AWN.

---

### Post by GoGoGulliver on 2011-02-17
Yeah, done all that, sadly. At the moment, I'm setting for autohiding the gnome-panel at the top of the screen  and pretending it's not there. Still, it's annoying as it worked before, but now it doesn't.

---

### Post by Copper Bezel on 2011-02-17
How is it possible that it could run without being executable? There's something fairly weird going on there.

---

### Post by GoGoGulliver on 2011-02-17
I sudo nautilus'ed that mofo and unclicked the executable box. Something must have gone awry when I did it through Terminal. Hopefully it won't "correct" itself in an update.

Fanks!

---

### Post by Krytarik on 2011-02-17
> **GoGoGulliver said:**
> I sudo nautilus'ed that mofo and unclicked the executable box. Something must have gone awry when I did it through Terminal. Hopefully it won't "correct" itself in an update.

Could you please post the output of:
```
ls -al /usr/bin/gnome-panel
```
Mine is:
```
-rwxr-xr-x 1 root root 544196 2010-07-07 16:49 gnome-panel
```

---

### Post by bprins on 2011-02-21
I had the exact same problem and just found a way to get past it. The problem was in my profile, somewhere, dunno exactly where.

After tons of threads and the knowledge that I removed all gnome-panels in the past, I started to move profile folders. 

```

mkdir ~/profile.backup
mv ~/.* ~/profile.backup

```

Then I logged out, and back in in order to create fresh defaults for gnome. 

```

gconftool-2 -s /desktop/gnome/session/required_components/panel -t string "avant-window-navigator"

```
			
Again, logout and log back in and my annoying gnome-panels were gone.

Just so that you don't run into the same wall, I started out with just moving the gnome related folders into a profile.backup, but that didn't resolve the problem. So I am not sure which folder is ruining the gconftool-2 command. 

I only know that after moving all profile folders and restoring new defaults the gconf tool gave me what I wanted => No more gnome-panel.

Hope this helps any of you.

Regards.

Bas

---

### Post by Krytarik on 2011-02-21
If you want to try this, I would, this command would reset all settings of "session" to their defaults, and leave all the rest untouched:
```
gconftool --recursive-unset /desktop/gnome/session
```

---

### Post by Todd_1215 on 2011-02-25
I have ubuntu 10.10 and using the gconf-editor nor the ubuntu-tweak meathod worked. Both just change the same registry entry I believe.

How I got mine to away was to set the gnome-panel execute bit off by doing the following:

sudo chmod 644 /usr/bin/gnome-panel
sudo killall gnome-panel

I was logged out by the desktop and when I logged back in gnome-panel was gone.

The results are the same but getting there was very different.

---

### Post by false truths on 2011-02-25
I'm surprised at how complex of methods for removing the GNOME panel people are using. When I want my panels gone, I do the following:

```
gksudo nautilus /usr/bin
```

Find the gnome panel application, cut it, and paste it in your home folder for later use. Log out and back in, and all GNOME panels are gone. If you need to re-enable them temporarily, use

```
~/gnome-panel
```

and your panels will reappear until you log out again.


I've never had any trouble from GNOME from being unable to find its own panel application, and it was significantly easier to do then modifying things in gconf or ubuntu tweak.

---

### Post by Copper Bezel on 2011-02-25
I know it doesn't seem to work for everyone, but the gconf method is also the only one actually *designed to do this*, so I'd think of it as the preferred one in that sense as the first thing to try. Changing the gconf key or the app's permission to run is a smaller change than moving the whole binary, and gconf doesn't require root privileges or affect other user accounts. 

Still, it's just a matter of what's intuitive, isn't it? Between the three, no one is more involved than any other - they all involve opening a utility program (elevated Nautilus or gconf-editor) and clicking down a couple of layers of folders, then changing one item. *Shrug*

---

### Post by jonbwilson on 2011-03-08
I was able to remove all gnome panels from gconf-editor just fine.  I wonder, is there a way to restore the alt+F2 functionality without bringing the gnome panel back?  I much prefer it to gnome-do.

Any suggestions, or is that impossible?

---

### Post by Krytarik on 2011-03-08
Since the usual "Alt+F2" dialog is a feature of gnome-panel, you cannot run it without running gnome-panel.

But you can try "grun", it's in the official repos.

---

### Post by jonbwilson on 2011-03-08
> **Krytarik said:**
> Since the usual "Alt+F2" dialog is a feature of gnome-panel, you cannot run it without running gnome-panel.

But you can try "grun", it's in the official repos.

I'll give it a whirl when I get home from work. Thanks for the suggestion.

---

### Post by bprins on 2011-03-09
Map alt f2 as key binding for gnome-do :P

---

### Post by jonbwilson on 2011-03-09
> **Krytarik said:**
> Since the usual "Alt+F2" dialog is a feature of gnome-panel, you cannot run it without running gnome-panel.

But you can try "grun", it's in the official repos.

I like this much better than gnome-do. Thank you!

---

### Post by rykel on 2011-03-13
I just found out to my horror that neither gconf-editor nor Ubuntu Tweak could remove the top Gnome panel. Why is it so HARD to simply remove a panel??

---

### Post by Krytarik on 2011-03-13
> **rykel said:**
> I just found out to my horror that neither gconf-editor nor Ubuntu Tweak could remove the top Gnome panel. Why is it so HARD to simply remove a panel??
Although you most likely may have checked that already, did you check if it is enabled in "Startup Applications"? (Just to be sure.)

---

### Post by Breambutt on 2011-03-13
Here's a little out of the box thinking: you could just hide the panel in some cases.

I have it on the widget layer through a Compiz plugin, everything from Alt+F1 to Alt+F2 works as if it was still there. Because it is still there. And everything meaning at least two F-keys.

---

### Post by lanetherif on 2011-03-13
Sometimes, it is as if working on arbitrary basis. Months ago it was not possible to change it through gconf-editor, yesterday it has just worked...

---

### Post by Frogs Hair on 2011-03-13
Why not just delete them instead of removing them completely ? At least you would have the option to easily use them. Whoops Solved

---

### Post by Krytarik on 2011-03-26
Does anybody in here still have an issue with recurring gnome-panel?

If not already tried, delete the content of "~/.config/gnome-session/saved-session", there seem to be some inconsistencies regarding that feature.

Greetings.

---

### Post by ubuntu_cork on 2011-03-31
I solved this on Lucid (10.04) using most of the tips as suggested but here is the full recipe I used to replicate this on another user account to confirm it.

[LIST=1]
[*]Launch gconf-editor from a terminal.
[*]Goto Gnome -> session -> required_components
[*]Change gnome-panel to avant-window-navigator
[*]Now go to Gnome -> session
[*]Change the value of required_components_list to [windowmanager, filemanager] by removing the panel option in the list.
[*]Set AWN to start on login by right clicking on the AWN panel and going to Dock Preferences and selecting the box at the bottom that says "Start AWN Automatically".
[*]remove everything in the directory ~/.config/gnome-session/saved-session/
[*]Log out and then log back in and there should be no more gnome-panel, albeit only confirmed on Ubuntu 10.04(Lucid Lynx).
[/LIST]
I hope this helps people :popcorn:

---

### Post by Krytarik on 2011-03-31
> **ubuntu_cork said:**
> 

[LIST=1]
[*]Launch gconf-editor from a terminal.
[*]Goto Gnome -> session -> required_components
[*]**[COLOR=Blue]Change gnome-panel to avant-window-navigator[/COLOR]**
[*]Now go to Gnome -> session
[*]**[COLOR=Blue]Change the value of required_components_list to [windowmanager, filemanager] by removing the panel option in the list.[/COLOR]**
[*]**[COLOR=Green]Set AWN to start on login by right clicking on the AWN panel and going to Dock Preferences and selecting the box at the bottom that says "Start AWN Automatically".[/COLOR]**
[*]remove everything in the directory ~/.config/gnome-session/saved-session/
[*]Log out and then log back in and there should be no more gnome-panel, albeit only confirmed on Ubuntu 10.04(Lucid Lynx).
[/LIST]

Thanks for sharing! However, if you do step (3), you wouldn't need to do step (5), this way you could also spare step (6). At least if those options have their intended effect. Didn't they? It's a while ago that I tried AWN, and I don't exactly remember if I needed to place it into "Startup Applications", it may well be. But I do remember, that after I did step (3), gnome-panel appeared all of a sudden in "Startup Applications" intead, which is kinda weird. I had to disable it there.

---

### Post by Copper Bezel on 2011-03-31
Yes, replacing Gnome Panel with Avant Window Navigator as the required Panel works without the other steps. It launches in place of Gnome Panel (although it doesn't inherit its unkillability.)

---

### Post by Krytarik on 2011-03-31
> **Copper Bezel said:**
> (although it doesn't inherit its unkillability.)
Maybe it will do so, if you modify "/usr/share/applications/avant-window-navigator.desktop" this way:```

[Desktop Entry]
Type=Application
Name=Avant Window Navigator
Name[af]=Avant Verster Navigator
Name[ar]=&#1605;&#1604;&#1575;&#1581; &#1575;&#1604;&#1606;&#1608;&#1601;&#1584;&#1577; &#1571;&#1601;&#1575;&#1606;&#1578;
Name[ast]=Avant Window Navigator
Name[bg]=Avant Window Navigator
Name[ca]=Navegador de finestres Avant
Name[cs]=Avant Window Navigator
Name[csb]=Nawigatora Òknów Avant
Name[da]=Avant Window Navigator
Name[de]=Avant Window Navigator
Name[el]=&#928;&#955;&#959;&#951;&#947;&#972;&#962; &#928;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957; Avant
Name[en_AU]=Avant Window Navigator
Name[en_CA]=Avant Window Navigator
Name[en_GB]=Avant Window Navigator
Name[eo]=Avant fenestro-eksplorilo
Name[es]=Navegador de ventanas Avant
Name[et]=Avant Window Navigator
Name[eu]=Avant Window Navigator
Name[fi]=Avant Window Navigator
Name[fr]=Avant Window Navigator
Name[gl]=Avant Window Navigator
Name[he]=Avant Window Navigator
Name[hi]=&#2309;&#2357;&#2306;&#2340; &#2357;&#2367;&#2306;&#2337;&#2379; &#2344;&#2366;&#2357;&#2367;&#2327;&#2366;&#2335;&#2352;
Name[hr]=Avant Window Navigator
Name[hu]=Avant ablaknavigátor
Name[id]=Avant Window Navigator
Name[is]=Avant Window Navigator
Name[it]=Avant Window Navigator
Name[ja]=Avant Window Navigator
Name[jv]=Avant Window Navigator
Name[kab]=Avant Window Navigator
Name[ko]=&#50500;&#48152;&#53944; &#50952;&#46020;&#50864; &#45236;&#48708;&#44172;&#51060;&#53552;
Name[ku]=Avant Window Navigator
Name[lt]=Avant lang&#371; tvarkytuvas
Name[ms]=Pengemudi Tetingkap Avant
Name[nds]=Avant Window Navigator
Name[nl]=Avant Window Navigator
Name[oc]=Abans Window Navigator
Name[pl]=Nawigator Okien Avant
Name[pt]=Avant Window Navigator
Name[pt_BR]=Avant Window Navigator
Name[ro]=Navigatorul de ferestre Avant
Name[ru]=Avant Window Navigator
Name[sk]=Avant Window Navigátor
Name[sq]=Avant Window Navigator
Name[sr]=&#1040;&#1074;&#1072;&#1085;&#1075;&#1072;&#1088;&#1076;&#1085;&#1080; &#1085;&#1072;&#1074;&#1080;&#1075;&#1072;&#1090;&#1086;&#1088; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088;&#1072;
Name[sv]=Avant Window Navigator
Name[tr]=Avant Pencere Gezgini
Name[uk]=Avant Window Navigator
Name[zh_CN]=Avant &#31383;&#21475;&#23548;&#33322;&#22120;
Name[zh_TW]=Avant Window Navigator
Comment=A dock-like window navigator.
Comment[af]='n Dokagtige venster navigator.
Comment[ar]=&#1605;&#1604;&#1575;&#1581; &#1606;&#1608;&#1601;&#1584;&#1577; &#1603;&#1575;&#1604;&#1605;&#1585;&#1587;&#1575;&#1577;.
Comment[ast]=Un restolador de ventanes tipu panel.
Comment[bg]=&#1044;&#1086;&#1082;-&#1087;&#1086;&#1076;&#1086;&#1073;&#1077;&#1085; &#1085;&#1072;&#1074;&#1080;&#1075;&#1072;&#1090;&#1086;&#1088; &#1085;&#1072; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088;&#1094;&#1080;
Comment[ca]=Un navegador de finestres de tipus acoblador.
Comment[cs]=Dokovací p&#345;epína&#269; oken
Comment[da]=En docklignende vinduesnavigator.
Comment[de]=Ein Dock-ähnlicher Fensternavigator.
Comment[el]=&#917;&#957;&#945;&#962; &#960;&#955;&#959;&#951;&#947;&#972;&#962; &#960;&#945;&#961;&#945;&#952;&#973;&#961;&#969;&#957; &#964;&#973;&#960;&#959;&#965;-dock
Comment[en_AU]=A dock-like window navigator.
Comment[en_CA]=A dock-like window navigator.
Comment[en_GB]=A dock-like window navigator.
Comment[eo]=Doka fenestro navigilo.
Comment[es]=Un navegador de ventanas tipo empotrado.
Comment[et]=Dokk-stiilis aknanavigaator.
Comment[eu]=Atrake (dock) moduko leiho-nabigatzailea.
Comment[fi]=Telakkamainen ikkunanavigaattori.
Comment[fr]=Une barre des tâches de type « dock »
Comment[gl]=AWN fornece unha barra de aplicativos entallable no escritorio
Comment[he]=&#1504;&#1493;&#1493;&#1496; &#1495;&#1500;&#1493;&#1504;&#1493;&#1514; &#1491;&#1502;&#1493;&#1497; &#1502;&#1506;&#1490;&#1503;.
Comment[hu]=Dokkszer&#369; ablaknavigátor
Comment[id]=Navigator jendela berjangkar.
Comment[is]=Stika sem hægt er að stilla.
Comment[ja]=&#12489;&#12483;&#12463;&#12521;&#12452;&#12463;&#12394;&#12454;&#12451;&#12531;&#12489;&#12454;&#12490;&#12499;&#12466;&#12540;&#12479;&#12540;
Comment[ko]=&#46021; &#48169;&#49885;&#51032; &#50952;&#46020;&#50864; &#45236;&#48708;&#44172;&#51060;&#53552;
Comment[lt]=Juostos tipo lang&#371; tvarkytuvas
Comment[ms]=Pengemudi tetingkap macam dock.
Comment[nl]=Dock-achtige vensternavigatie
Comment[oc]=Una barra dels prètzfaches de tipe « Dock »
Comment[pl]=Dokopodobny nawigator okien.
Comment[pt_BR]=Um navegador de janelas estilo doca.
Comment[ro]=Un navigator de ferestre asem&#259;n&#259;tor barei de docare.
Comment[ru]=&#1055;&#1072;&#1085;&#1077;&#1083;&#1077;&#1087;&#1086;&#1076;&#1086;&#1073;&#1085;&#1099;&#1081; &#1085;&#1072;&#1074;&#1080;&#1075;&#1072;&#1090;&#1086;&#1088;
Comment[sk]=Dokovací prepína&#269; okien
Comment[sq]=Nje panel navigues dritaresh.
Comment[sv]=En dock-liknande fönsternavigator.
Comment[tr]=Yuva benzeri pencere gezgini
Comment[uk]=&#1055;&#1072;&#1085;&#1077;&#1083;&#1100;&#1110;&#1082;&#1086;&#1085;&#1085;&#1080;&#1081; &#1085;&#1072;&#1074;&#1110;&#1075;&#1072;&#1090;&#1086;&#1088; &#1085;&#1072; &#1086;&#1089;&#1085;&#1086;&#1074;&#1110; &#1087;&#1072;&#1085;&#1077;&#1083;&#1077;&#1081;.
Comment[zh_CN]=Dock&#26679;&#24335;&#30340;&#31383;&#21475;&#23548;&#33322;
Comment[zh_TW]=&#19968;&#20491; dock &#39006;&#22411;&#30340;&#35222;&#31383;&#23566;&#35261;&#24037;&#20855;
Exec=avant-window-navigator
Icon=avant-window-navigator
Categories=GNOME;Utility;
StartupNotify=true
Terminal=false
X-GNOME-AutoRestart=true
X-GNOME-Autostart-Notify=true
```
Maybe placing it into "~/.local/share/applications" will also work.

Hope it works!

---

### Post by Copper Bezel on 2011-03-31
No effect, but there's no practical necessity. With *just* Gnome Panel, there's no Run Dialog to bring it back if it crashes, but you could always use a terminal and setsid, and most folks have Synapse or Do running anyway. Since AWN doesn't even have a Run Dialog, I'm already using XFRun4 (run on Alt+F2 by Compiz) and Synapse (which is my system's default Run Dialog but could be run even if not only AWN but the window manager crashed as well.) All a bit hypothetical, since I've never actually crashed any of these applications save Compiz.

---

