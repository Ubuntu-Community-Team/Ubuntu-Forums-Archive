---
title: "Installing this Dock"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by Matuku on 2007-08-31
The original thread I got this from ([http://ubuntuforums.org/showthread.php?t=537815&highlight=AWN](http://ubuntuforums.org/showthread.php?t=537815&highlight=AWN)) said that the dock in this picture (see below) was AWN; but I've got AWN and it doesn't look like this for me. Were they incorrect in what dock it was or has it been modified (I looked through the options but couldn't find anything about making a reflection, etc).

PS On another not how to I embed the image like has been done in that other thread? Is it simply HTML?

---

### Post by FuturePilot on 2007-08-31
Open the AWN settings manager and go to Bar Appearance and make sure it's set to 3D look.
The Bar Angle should be 45
Bar Height 45
Icon Offset 15

---

### Post by Matuku on 2007-08-31
My Bar Appearance Tab doesn't have that option (see image); also for me it wasn't AWN Settings Manager it was System>Preferences>Avant Preferences; is the Settings Manager somewhere else? Also how do I embed the images?

---

### Post by FuturePilot on 2007-08-31
Only the latest version can do the 3D dock thing. Try this
```
sudo apt-get remove --purge avant-window-navigator
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```
System>Preferences>AWN Preferences is the same thing.

To embed an image you have to use [IMG] tags like 
[.IMG]http://www.imagehost.com/picture.png[/IMG]
without the . in it though

---

### Post by Ascension on 2007-08-31
Where can I get a dock?

---

### Post by Matuku on 2007-08-31
> **FuturePilot said:**
> Only the latest version can do the 3D dock thing. Try this
```
sudo apt-get remove --purge avant-window-navigator
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```
System>Preferences>AWN Preferences is the same thing.

To embed an image you have to use [IMG] tags like 
[.IMG]http://www.imagehost.com/picture.png[/IMG]
without the . in it though

I thought it may be a version problem. I did the code that you said but the menu button generated doesn't do anything and when I try to use the terminal to access it I get:

```
matuku@matuku-desktop:~$ awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 100, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 149, in __init__
    self.setup_font(TITLE_FONT_FACE, self.wTree.get_widget("selectfontface"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 267, in setup_font
    font_btn.set_font_name(self.client.get_string(key))
TypeError: GtkFontButton.set_font_name() argument 1 must be string, not None
```

Any ideas?

---

### Post by Matuku on 2007-08-31
> **Ascension said:**
> Where can I get a dock?
You could try the second line of the code I was given:
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```
This should install the Avant Window Navigator (AWN) Dock; but I can't remember if you need to add any additional repositories anymore...
If it comes up with an error or can't do it then you probably need to add extra repositories but I can't remember which ones.

---

### Post by FuturePilot on 2007-08-31
Oops forgot something. Try
```
sudo apt-get remove --purge avant-window-navigator-svn libawn-svn
```

---

### Post by Matuku on 2007-08-31
> **FuturePilot said:**
> Oops forgot something. Try
```
sudo apt-get remove --purge avant-window-navigator-svn libawn-svn
```
It's odd, I can access the properties by starting AWN then right-clicking on it but not from System>Preferences>etc; that just doesn't do anything.

EDIT: Oops, now it works. Thanks!

---

### Post by Matuku on 2007-08-31
How do I change the icon that the Trashcan uses?

---

### Post by FuturePilot on 2007-08-31
That should be dependent on the system icon theme you are using.

---

### Post by uglykigjoe on 2007-08-31
Guys,
Can i know which repositoties that you`ve added?
Please..


:)

---

### Post by Matuku on 2007-09-01
> **FuturePilot said:**
> That should be dependent on the system icon theme you are using.
I would have thought so too but I'm using glass icons but the trashcan on AWN still looks like the normal theme.

---

### Post by Matuku on 2007-09-01
> **uglykigjoe said:**
> Guys,
Can i know which repositoties that you`ve added?
Please..


:)

Sorry about that, thought I had edited my previous post with the Repo info (obviously didn't work).

The repos you need to add are:
```
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```

I'm assuming you're on Feisty?

Then you need to do this:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg 
sudo apt-key add 8434D43A.gpg
rm 8434D43A.gpg
sudo apt-get update
```

Then you should be able to use the code from my previous post (the code I was told to use).

That should do it,
Matuku

**PS:** I found the thread where I got my instructions again: [http://ubuntuforums.org/showthread.php?t=385981&](http://ubuntuforums.org/showthread.php?t=385981&)
**PSS:** Just re-read that thread and it points out that you need a compositor (Compiz, Compiz Fusion or Beryl) for AWN to work properly.

EDIT: Sorry for the slowness of my reply; I know whats its like to be new and to have to wait for a reply, you normally get replies within 30min so sorry about the delay.

---

### Post by Inxsible on 2007-09-01
I cant get the AWN Manager to come up at all. Neither from the System-->Preferences --> Awn Manager nor from the AWN Dock itself :(

I also tried removing it and installing it again. 

Oh and I do have CF running.

---

### Post by FuturePilot on 2007-09-01
Hmm. What do you get with```
awn-manager
```

---

### Post by jrharvey on 2007-09-01
I have AWN dock but for some reason I can't get the stupid black box to come out from behind it. What is wrong and how do i fix it?

---

### Post by rogun on 2007-09-02
> **jrharvey said:**
> I have AWN dock but for some reason I can't get the stupid black box to come out from behind it. What is wrong and how do i fix it?

It sounds like you're not using Compiz-Fusion, which is a requirement for AWN.

---

### Post by [Alsharifi] on 2007-09-02
Yea u have to be running compiz or beryl.

its a great dock. 

AWn > kiba

---

### Post by Inxsible on 2007-09-02
> **FuturePilot said:**
> Hmm. What do you get with```
awn-manager
```

```
inxsible@HPdv9000t:~$ awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 199, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 97, in __init__
    self.launchManager = awnLauncher(self.wTree, self.AWN_CONFIG_DIR)
  File "/usr/share/avant-window-navigator/awn-manager/awnLauncher.py", line 66, in __init__
    self.make_model()
  File "/usr/share/avant-window-navigator/awn-manager/awnLauncher.py", line 124, in make_model
    self.refresh_tree(uris)
  File "/usr/share/avant-window-navigator/awn-manager/awnLauncher.py", line 134, in refresh_tree
    self.model.set_value (row, 0, self.make_icon (i))
  File "/usr/share/avant-window-navigator/awn-manager/awnLauncher.py", line 168, in make_icon
    if "/" in name:
TypeError: argument of type 'NoneType' is not iterable
inxsible@HPdv9000t:~$ 

```

---

### Post by FuturePilot on 2007-09-02
There seems to be something with one of the launchers causing this. There's a bug report here.
[https://bugs.launchpad.net/awn/+bug/133901]("https://bugs.launchpad.net/awn/+bug/133901")

You might also want to check this thread as it's the official AWN thread
[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")
I'm kind of at a loose on this one. Sorry:(

---

### Post by Inxsible on 2007-09-02
> **FuturePilot said:**
> There seems to be something with one of the launchers causing this. There's a bug report here.
[https://bugs.launchpad.net/awn/+bug/133901](https://bugs.launchpad.net/awn/+bug/133901)

You might also want to check this thread as it's the official AWN thread
[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
I'm kind of at a loose on this one. Sorry:(Thanks man.
That helped. Funny it should be a launcher that I didnt give an icon too. And to think, I removed and installed AWN twice to see if the problem would go away.

---

### Post by FuturePilot on 2007-09-02
> **Inxsible said:**
> Thanks man.
That helped. Funny it should be a launcher that I didnt give an icon too. And to think, I removed and installed AWN twice to see if the problem would go away.

Whoa! So that was the issue.:lol:
Glad you got it working:)

---

### Post by Inxsible on 2007-09-02
I am trying to add some launchers to AWN, but when I try to select an icon for it, it takes me to /usr/share/pixmaps, however i want it to use the icons from the current theme that i use.

how do i do this ?

---

### Post by FuturePilot on 2007-09-02
> **Inxsible said:**
> I am trying to add some launchers to AWN, but when I try to select an icon for it, it takes me to /usr/share/pixmaps, however i want it to use the icons from the current theme that i use.

how do i do this ?

It should use the icons from you current theme if that theme has an icon for that program. For example certain themes don't have an icon for Firefox so it uses the default one. But you could still browse around in your current icon theme for something that might look good. Just navigate to either /usr/share/icons/ or /home/USER/.icons/

---

### Post by Inxsible on 2007-09-03
> **FuturePilot said:**
> It should use the icons from you current theme if that theme has an icon for that program. For example certain themes don't have an icon for Firefox so it uses the default one. But you could still browse around in your current icon theme for something that might look good. Just navigate to either /usr/share/icons/ or /home/USER/.icons/

I did that...but maybe I wasn't clear enough.

What I meant was will the icons change if I change the theme that I use ?Doesn't seem to do that for me :(

---

### Post by FuturePilot on 2007-09-03
It should. Hmmm.:confused:

---

### Post by Inxsible on 2007-09-03
When I create a launcher, I click on the No Icon button and then go to /home/USER/.icons and select the appropriate icon for that launcher. 

Then I change my theme...and the icons do not change :(

Is there something I am missing? Is there a different way to select icons?

What is the Themes in AWN Manager..is that for AWN Themes or for system themes that we change from System-->Preferences-->Themes ?


BTW, I really appreciate the help you give me so far FP :)

---

### Post by FuturePilot on 2007-09-03
Ah. That's because when you set a custom icon then it will only use that icon and ignore a total icon theme change.
Try just dragging the program out of the menu onto the dock instead. It's easier too.;)
Then it will use your icon theme.

No problem. That's why I'm here:)

---

### Post by Inxsible on 2007-09-03
> **FuturePilot said:**
> Ah. That's because when you set a custom icon then it will only use that icon and ignore a total icon theme change.
Try just dragging the program out of the menu onto the dock instead. It's easier too.;)
Then it will use your icon theme.

No problem. That's why I'm here:)
Aha !!

Will try dragging them now :)

---

### Post by Inxsible on 2007-09-03
Because I used specific icons earlier, even dragging the apps in the bar now uses the icons i used.

I guess I will have to remove the config files and then add the apps again. Now where do i find the config files?

/home/user/.awn is not there :(

---

### Post by FuturePilot on 2007-09-03
/home/USER/.config/awn
You might just be able to clear out the custom icons folder.
You might want to restart AWN afterwards too.

---

### Post by Inxsible on 2007-09-03
yeah..i found that..and now I get different icons for different themes :)

few more issues....(it never ends does it ? :) )

1 ) I have a launcher for terminal...but when I launch it, i do not get a separate window for it,

I mean, how do i open multiple instances of an app for which I have a launcher ?

When i click on the app again, it simply minimizes it.

2) How do I add a 'Show Desktop' launcher in AWN ? Do you know the command for it ?

3) What does the Themes tab in Awn Manager do ? support themes for awn ? or the system themes?

---

### Post by FuturePilot on 2007-09-03
Lol:lol:

1. I haven't figured that one out myself
2. I don't think that's possible yet. It would most likely have to be in the form of an applet but there doesn't seem to be one. Maybe one day there will be one though.:)
3. I haven't fooled around with that, but I'm thinking it's for different dock positions, colors, opacity etc. Like you could get a theme file and then load it instead of manually changing everything.

---

### Post by Inxsible on 2007-09-03
> **FuturePilot said:**
> Lol:lol:

1. I haven't figured that one out myself
2. I don't think that's possible yet. It would most likely have to be in the form of an applet but there doesn't seem to be one. Maybe one day there will be one though.:)
3. I haven't fooled around with that, but I'm thinking it's for different dock positions, colors, opacity etc. Like you could get a theme file and then load it instead of manually changing everything.
Thank you
Thank you &
Thank you :D

---

### Post by FuturePilot on 2007-09-03
You're welcome!:D

---

