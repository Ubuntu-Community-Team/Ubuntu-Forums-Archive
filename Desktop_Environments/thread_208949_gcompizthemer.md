---
title: "gcompizthemer"
date: 2006-07-04
forum: Desktop Environments
---

### Post by encho on 2006-07-04
Just discovered this package in stormquinn's repo. Finaly we can change the borders and customize the XGL look \\:D/

---

### Post by Tagmaster on 2006-07-04
Really nice :D , the basic-glass theme is awsome, thxn!

---

### Post by Ubuntuud on 2006-07-05
It made my quinn irrepearable slow. So I needed to switch to Vanilla... I miss quinn.

---

### Post by encho on 2006-07-05
I've noticed that it has become a bit slower, maybe it is some plugin issue.

---

### Post by panurge77 on 2006-07-05
New themes are submitted here:
[http://www.compiz.net/viewtopic.php?id=1271&p=11](http://www.compiz.net/viewtopic.php?id=1271&p=11)

---

### Post by desperado666 on 2006-07-05
How to install new themes manually ???

---

### Post by Ubuntuud on 2006-07-05
[QUOTE=encho]I've noticed that it has become a bit slower, maybe it is some plugin issue.[/QUOTE]

What card have you got? I have a i915 with aiglx, I assume it can't cope with it. Even if I dissable a lot of the plugins. But wobbly etc. work flawlessly, so maybe it's the cube plugin. But that's what I liked most :(

---

### Post by viraptor on 2006-07-05
Quite contrary in my box... with the last 3, or 4 updates of compiz (quinn packages) I've had a great speed boost with aixgl and i855gm card. Works great now. Also less frames are dropped so fading and 'flying in' effects are really smooth.

---

### Post by zerwas on 2006-07-08
Since the newest Update i don't have themes to select anymore :(.
Somebody knows where the themes are saved? or somebody there with the same issue?

Greetings,
zerwas

EDIT: ok, the themes come with
```

sudo apt-get install gcompizthemer-themes
```
sorry for the post

---

### Post by lazyd2 on 2006-07-08
> **zerwas said:**
> Since the newest Update i don't have themes to select anymore :(.
Somebody knows where the themes are saved? or somebody there with the same issue?

Greetings,
zerwas
```
sudo apt-get install gcompizthemer-themes
```;)

---

### Post by reacocard on 2006-07-08
just tried this. works perfectly on my i915 graphics using compiz-vanilla and aiglx.

---

### Post by llamakc on 2006-07-08
After installing did you restart compiz, X, reboot? What? I installed the gcompizthemer package and ran it from the CLI and selecting themes does nothing for me.

---

### Post by reacocard on 2006-07-08
none of them. just check both the check boxes, then it works.

---

### Post by llamakc on 2006-07-08
I'm using the vanilla compiz packages and checking both boxes doesn't switch themes when I press apply. Thanks for the reply though.

---

### Post by jimmygoon on 2006-07-08
Its quite buggy. If you select a theme even if you have "enable themes" turned off, certain things like drop shadows will still be applied. there's also no really easy way to edit the themes on the fly which stinks. Gnome/Metacity has needed that for a VERY long time.

---

### Post by RawMustard on 2006-07-09
> **desperado666 said:**
> How to install new themes manually ???

Put themes in ~/.compiz/themes

---

### Post by RAOF on 2006-07-09
> **jimmygoon said:**
> ...
there's also no really easy way to edit the themes on the fly which stinks. 
...
All theme settings that compiz-quinn can use are **easily** set on the fly - gcompizthemer includes an editor, the settings of which can get applied on the fly.

Additionally, gcompizthemer **only** works for the quinn compiz - the themeable gnome-window-decorator is built by her, and isn't in compiz-vanilla.

---

### Post by llamakc on 2006-07-09
Thank you, RAOF.

--llamakc

---

### Post by KFASheldon on 2006-07-17
Hi

Now you can select the window widgets theme too , role on a large collection of cool widgets

---

### Post by jimmygoon on 2006-07-17
> **RAOF said:**
> All theme settings that compiz-quinn can use are **easily** set on the fly - gcompizthemer includes an editor, the settings of which can get applied on the fly.

Additionally, gcompizthemer **only** works for the quinn compiz - the themeable gnome-window-decorator is built by her, and isn't in compiz-vanilla.

yep. not sure what I was thinking when I wrote that part... Oh well! I'm using quinn's repo's and package so thats not to worry :) I LOVE COMPIZ!

---

### Post by gamma on 2006-07-17
Just found out about this today. Glad to see compiz is finally themeable. I want to see the ability to use metacity themes though..

---

### Post by Lunar_Lamp on 2006-07-21
I have compiz-themer installed, but when I select a theme and click apply (or leave auto-apply ticked) nothing happens.  If I go down to the edit box, I can see it's having an effect down there, but no change happens.  What am I doing wrong?
Edit: just upgraded to 0.14, and now there isn't even any option to apply the changes!

---

### Post by lazyd2 on 2006-07-21
> **Lunar_Lamp said:**
> I have compiz-themer installed, but when I select a theme and click apply (or leave auto-apply ticked) nothing happens.  If I go down to the edit box, I can see it's having an effect down there, but no change happens.  What am I doing wrong?
Edit: just upgraded to 0.14, and now there isn't even any option to apply the changes!Install all the latest compiz debs(quinn21) and **cgwd**.You will have to edit your startup compiz script.
Change "gnome-window-decorator" with "cgwd"

I use startcompiz (/usr/bin/startcompiz) which was
```
#!/bin/sh 
killall **gnome-window-decorator** 
wait

** gnome-window-decorator** & 
compiz --replace gconf &
``` 
With cgwd (custom-generic-window-decorator) now it should be like this:
```
#!/bin/sh 
killall **cgwd** 
wait

** cgwd** & 
compiz --replace gconf &
```

---

### Post by Lunar_Lamp on 2006-07-21
I'd forgotten to start cgwd *sheepish look*.

---

### Post by Tagmaster on 2006-07-21
i noticed that the new update is based on the cgwd decorator, why they changed to this decorator?

---

### Post by lazyd2 on 2006-07-21
> **Tagmaster said:**
> i noticed that the new update is based on the cgwd decorator, why they changed to this decorator?
Read all about it [here]("http://www.compiz.net/viewtopic.php?id=1895")

---

### Post by fusiontu on 2006-07-21
guys, I have Compiz-Vanilla installed...

I installed compiz-themer but the look'n'feel and the borders are not changing! when I change a skin I notice the Shadow of the window only changing...

any idea??

---

### Post by RAOF on 2006-07-22
The vanilla compiz **doesn't support theming**.  If you want themeable compiz stuff, you need Quinn's compiz packages (they're just called "compiz" rather than "compiz-vanilla").

---

### Post by fusiontu on 2006-07-22
Thanks RAOF!

I installed Quinn's compiz packages and the themer worked fine! but I had to run "cgwd --replace" on startup...

---

### Post by utnubu001 on 2006-07-22
btw wats da difference btween compiz-vannila and compiz

---

### Post by mscman on 2006-07-22
> **utnubu001 said:**
> btw wats da difference btween compiz-vannila and compiz

As far as I know, the difference is the fact that vanilla is pure compiz - i.e. none of the patches and theming capabilities found in the quinnstorm version. I'm not quite sure why someone would choose to use vanilla instead of quinnstorm unless they were trying to do development.

---

### Post by duncanmhor on 2006-07-22
Hi there. I've installed gcompizthemer, updated my startup script,restarted my session and still cannot apply themes using compiz themer. I get the feeling that I'm missing something blindingly obvious, but I'm still missing it. Any suggestions would be appreciated.

---

### Post by binarymelon on 2006-07-24
I replaced cgwd and now I can't launch gcompizthemer.  Which sucks because I'm stuck on some nasty Vista theme.

I get the following error:

```
7442: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4628.
This is normally a bug in some application using the D-BUS library.
7442: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4592.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
Aborted

```

---

### Post by n00bWillingToLearn on 2006-07-25
> **mscman said:**
> As far as I know, the difference is the fact that vanilla is pure compiz - i.e. none of the patches and theming capabilities found in the quinnstorm version. I'm not quite sure why someone would choose to use vanilla instead of quinnstorm unless they were trying to do development. I may be misunderstanding you but I have compiz-vanilla installed ( no real reason, just decided vanilla sounded better than quin :) ) and I have installed compiz themer and theming works fine ( after running cgwd ).:-k

---

### Post by RAOF on 2006-07-25
> **n00bWillingToLearn said:**
> I may be misunderstanding you but I have compiz-vanilla installed ( no real reason, just decided vanilla sounded better than quin :) ) and I have installed compiz themer and theming works fine ( after running cgwd ).:-k

As far as I'm aware, cgwd is **not** in vanilla compiz!  It is (as far as I'm aware) pretty much a fork of gnome-window-decorator from vanilla that's being worked on by QuinnStorm (et al).  It would surprise me if that had made it upstream yet ;)

---

### Post by n00bWillingToLearn on 2006-07-26
> **RAOF said:**
> As far as I'm aware, cgwd is **not** in vanilla compiz!  It is (as far as I'm aware) pretty much a fork of gnome-window-decorator from vanilla that's being worked on by QuinnStorm (et al).  It would surprise me if that had made it upstream yet ;) I forgot that I installed cgwd and compizthemer seperately, it did not come with compiz-vanilla. I would like to have all possible features, should I switch to quin or does vanilla + gcompizthemer + cgwd == quin?

---

### Post by RAOF on 2006-07-26
> **n00bWillingToLearn said:**
> I forgot that I installed cgwd and compizthemer seperately, it did not come with compiz-vanilla. I would like to have all possible features, should I switch to quin or does vanilla + gcompizthemer + cgwd == quin?

No.  Quinn compiz has a whole bunch of extra plugins, and patches and stuff.  More options, more plugins, more win!

---

### Post by nexxus on 2006-07-26
Hi,

My compiz was working fine before I did an update, but then the themes went completely wonky.

I found out it was because Gnome-Window-decorator was running, and I stopped this. Using cgwd I've got the themes back, but now I get a warning about it not being able to access the pixmaps.

The end result is a window, but with no minimise, maximise & close buttons.

Any ideas at all?

---

### Post by n00bWillingToLearn on 2006-07-26
> **RAOF said:**
> No.  Quinn compiz has a whole bunch of extra plugins, and patches and stuff.  More options, more plugins, more win!

How would I go about switching to quin from vanilla?

---

### Post by RAOF on 2006-07-26
> **n00bWillingToLearn said:**
> How would I go about switching to quin from vanilla?
```
sudo aptitude install compiz
```
should do it.

If it doesn't, then
```

sudo aptitude remove compiz-vanilla
sudo aptitude install compiz

```
will.

---

### Post by Hollowman on 2006-07-27
Ok, I finally got compiz up and running and I figured out how to change themes but how do I apply the change to the upper and lower panels, or is this possible?  Any ideas?

Hollowman

---

### Post by Nomis on 2006-07-27
> **nexxus said:**
> 
The end result is a window, but with no minimise, maximise & close buttons.


Same here. If I delete the ~/.compiz folder there are the buttons, but when I change the theme they are gone again. Anyone an idea?

Edit: Ok, I found the solution. In gcompizthemer under "General" there is "Title-bar Object Layout" There you have to choose one of the two layouts.

---

### Post by nexxus on 2006-07-28
Woohoo!

That sorted it. Thanks

---

### Post by javierfh on 2006-07-28
Hi,

im not sure if this is the right place, but anyway there it goes my question.
I installed and updated the Quinn repositories. So compiz works just fine and  in the icon that appears in the upper bar i can see theme selector.
There i can see lots of themes, i can select them and nothing happens, not either when i click refresh.
How are these applied?
I thought i had something wrong, and following the instructions here i went to /usr/bin and modify the file compiz-start.py. i add here the original file just in case someone sees something wrong there.
I really dont know what it is wrong, i changed the lines referring to gnome-window-decorator as someone suggested.

All the help would be more than welcome. I really cant apply these themes.

Thanks in advance,

Javi

---

### Post by bulldog on 2006-07-28
Change your compiz-start.py like the following and it should work:

def start_compiz():
	os.system("killall gnome-window-decorator")
	gobject.spawn_async(['cgwd'], \
			     flags=gobject.SPAWN_SEARCH_PATH)
	gobject.spawn_async(['compiz', '--replace', 'gconf'], \
			  flags=gobject.SPAWN_SEARCH_PATH)

It seams to be important that 'cgwd' must be there.
It works for me.

---

### Post by Furball666 on 2006-08-15
I cant seem to get Compiz installed on mine. I had it installed at one time but I tried to install the vanilla option and it uninstalled Compiz. Now I cant get it back. all I see is this when I try

> compiz:
  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed


---

### Post by undershepherd1 on 2006-08-15
I was having this same problem with libpango. Quinn advised me to check my repos in apt-get. Lo and behold, they were pointing to "breezy." So I replaced every instance in active repos from "breezy" to "dapper" and did a apt-get update and apt-get dist-upgrade and was able to install libpango and compiz updates.
Hope this helps.

---

### Post by Furball666 on 2006-08-15
well I ended up having to add a repo and then had to reinstall a load of lib files and whatnot over again. aAnd when I did that everything works fine but now I cant get the themes to change or anything. So on to the next problem. Thanks for you help though

---

### Post by jake3988 on 2007-02-16
where can I find this?

---

### Post by RAOF on 2007-02-17
You can't, and no longer want to.

This program no longer works - it was for configuring pre-beryl compiz-quinn.  Beryl has it's own configuration system, as does Compiz, and this won't work with either of them.

---

