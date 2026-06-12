---
title: "Fluxbox Install"
date: 2008-03-02
forum: Desktop Environments
---

### Post by Belak on 2008-03-02
Ok, what is the recommended way for installing fluxbox? I have a laptop and want to install fluxbox because I want to use a lightweight window manager... I guess idk if this belongs in the Desktop Environments then....

Anyway, after I install Fluxbox, how would I go about enabling the nvidia-glx-new drivers. I tried previously but noticed no improvement in the gradients in the themes... some were still a little grainy.

I don't want to use Fluxbuntu either. I can do an install of a command line system and get it to work, but I have to type my username and password into a command line login. It's especially annoying because idk when my computer is ready for me to login because some of the code executes and it runs over and past the login prompt... any idea why this is happening?

Ok, I guess, Here's my list of stuff I want to know how to do...

[LIST]
[*]Install Fluxbox from a command line system
[*]Enable nvidia-glx-new package and get it to work
[*]Graphical login
[*]Overflow problem in command line login
[/LIST]


Thanks,
Belak

---

### Post by mbsullivan on 2008-03-02
Hi Belak,

Fluxbox is great, and very easy to install from an Ubuntu server install. You don't need Fluxbuntu or anything, and your installation will be very slimmed down. You can install fluxbox with the following command:

```
sudo aptitude install fluxbox
```

After installing Fluxbox, you can use any graphical login you'd care for, including gdm, etc. If you don't need an ultra lightweight system, I'd probably use gdm (but this is just personal preference):

```
sudo aptitude install gdm
```

As for the nvidia OpenGL drivers, I'm not sure (I have an Intel integrated GPU). However, there is a "nvidia-glx-new" package in Ubuntu, so it seems sensible to start with:

```
sudo aptitude install nvidia-glx-new
```

Does this give you an error when trying to remove nvidia-glx? If not, my guess is you should be all set up. Now customize your Fluxbox install!

Nothing earth-shattering, here. Let me know if I didn't answer your question completely.
Mike

---

### Post by Belak on 2008-03-02
Well, there's just this then:
Overflow problem in command line login

I haven't tried the nvidia one yet, but the rest appear to work... thanks.

Oh, how do you evit the menu? Fluxbox is so different than gnome or KDE or XFCE. I've tried all the major ones, so I decided to try this and I wanted to edit the menu...

Also, the menu doesn't update when I install stuff... is there a way around this?
Maybe a shortcut to the sudo update-menus command? I just though of that... anyway, thanks for all your help...

Also, what is the point of the fluxconf package?

---

### Post by yabbadabbadont on 2008-03-02
> **Belak said:**
> Well, there's just this then:
Overflow problem in command line login

I haven't tried the nvidia one yet, but the rest appear to work... thanks.

Oh, how do you evit the menu? Fluxbox is so different than gnome or KDE or XFCE. I've tried all the major ones, so I decided to try this and I wanted to edit the menu...

Also, the menu doesn't update when I install stuff... is there a way around this?
Maybe a shortcut to the sudo update-menus command? I just though of that... anyway, thanks for all your help...

Also, what is the point of the fluxconf package?

RedSquirrel has an excellent tutorial on the fluxbox menu here: [http://www.ubuntuforums.org/showthread.php?t=371144](http://www.ubuntuforums.org/showthread.php?t=371144)

---

### Post by eriqjaffe on 2008-03-03
> **Belak said:**
> Oh, how do you evit the menu? Fluxbox is so different than gnome or KDE or XFCE. I've tried all the major ones, so I decided to try this and I wanted to edit the menu...

Also, the menu doesn't update when I install stuff... is there a way around this?
Maybe a shortcut to the sudo update-menus command? I just though of that... anyway, thanks for all your help...

Also, what is the point of the fluxconf package?
RedSquirrel's thread is really the best place to get answers, but here are some quick ones.

1) The menu is just a flat text file, ~/.fluxbox/menu.  IIRC, it will call another file with the actual guts of the menu, but I prefer to just re-create that in the file I mentioned since you don't have to use sudo to edit it.

2) As far as auto-updating menus, take a look at [marchfluxmenu](http://code.google.com/p/marchfluxmenu/), which has a daemon mode to modify the menu when packages get installed (assuming they create a .desktop file).  One small thing with marchfluxmenu is that the version of Fluxbox in the repos isn't configured with imlib support, so a number of the menu entries won't have icons attached to them unless you re-compile Fluxbox (although that's pretty easy).

3) The fluxconf package is just a handful of GUI tools for modifying the menu, hotkeys, etc.  I personally find it quicker to just edit the text files in a text editor.

---

### Post by Adnarim on 2008-03-03
I wouldn't recommend to use gui's to edit the fluxbox files and especially not fluxconf! Some of them are known to have problems with newer fluxbox-files and are messing them up! Just use vim and a fluxbox-style file and everything is well :)

And one of the best places for fluxbox-help is [http://fluxbox.org/docbook/en/html/](http://fluxbox.org/docbook/en/html/)

greets

PS: If you are totally new to fluxbox don't forgett to check out tabbing and auto-grouping. After you did this you will never ever change to a different windowmanager.

---

### Post by RedSquirrel on 2008-03-03
> **Belak said:**
>  ... I can do an install of a command line system and get it to work, but I have to type my username and password into a command line login. It's especially annoying because idk when my computer is ready for me to login because some of the code executes and it runs over and past the login prompt... any idea why this is happening?

It has to do with the order of things being loaded. You just have to make the login prompt appear after everything else is done. Have a look at the following link:

[https://answers.launchpad.net/upstart/+question/9887](https://answers.launchpad.net/upstart/+question/9887)

If you don't want to bother with that, your computer should be ready for you to login once you see something about "rc.local". It looks like the computer is stuck, but it's not. Just press ENTER and the login prompt will appear.

You could also install gdm as mentioned above and you'll have a nice graphical login presented to you. ;)

---

### Post by Belak on 2008-03-05
Just a few more things... I hope

I got all of the above working... I'm using a custom menu file
And I want to know how to get a working "Run" command in my menu. The sudo command doesn't work in there for whatever reason... 
EDIT: I got it working with gksu instead of sudo

What's a good network manager for Fluxbox? I guess I could use the Gnome one, but I've read of people having problems with that.

Where would you reccomend me getting styles from?
Is there any way to add a menu to the Toolbar? I hate having to minimize everything just to open a new program.

Now, hopefully the last thing:
I had multimedia keys working in Gnome, but not in Fluxbox. Any idea why?

Thanks.

I hate to sound like a n00b with all these questions... I'm just new to fluxbox

---

### Post by eriqjaffe on 2008-03-05
To add a Run command to the menu...

```
[exec] (Run...) {fbrun} <your/icon/here/if/you/want/one>
```

---

### Post by markjensen on 2008-03-05
> **Belak said:**
> ...
Where would you reccomend me getting styles from?

Is there any way to add a menu to the Toolbar? I hate having to minimize everything just to open a new program.
...
I got my preferred fluxbox style/theme from googling, and found it on freshmeat.net, here: [http://freshmeat.net/projects/fluxaqua/](http://freshmeat.net/projects/fluxaqua/)
I did some small modifications to set it up the way I like.   You can also make your own, if you like pixmaps in there, you can gimp up your own.  Or just use the built-in gradient options.

Instead of adding a menu to the taskbar, I added an option to my keys file like this:
Mod4 m :RootMenu
And that calls up the menu without needing background "desktop" access by using Windows+M
I also set up a few keyboard shortcuts to match the Windows systems at work, so Win+L locks the screen, and ALT+F4 closes the current window.

If you want help in making your own theme, there are guides online, or I could answer a few questions.


EDIT:  Forgot to answer your question regarding multimedia keys.   Since fluxbox is a simpler Window Manager (and not a full Desktop Environment), you will have to set your multimedia keys up yourself, binding them in your keys file.  For example, I have a line for
None 174 :Exec amixer set PCM 5%-
which bumps down the main PCM channel of my sound when I press my volume down button.

Find your specific keycodes using the **xev** app.

---

### Post by eriqjaffe on 2008-03-05
> **Belak said:**
> Is there any way to add a menu to the Toolbar?I didn't notice this question before...

Yes, it can be done, but it requires compiling fluxbox from source.  It's pretty painless, really (I did it myself, in fact).  I don't know why it's not just part of the normal source code, but it's not.

[http://ubuntuforums.org/showthread.php?p=3130878&highlight=rootmenu#post3130878](http://ubuntuforums.org/showthread.php?p=3130878&highlight=rootmenu#post3130878)

---

### Post by jviscosi on 2008-03-06
> **Belak said:**
> 
Where would you reccomend me getting styles from?


You can get a bajillion styles [here]("http://tenr.de/").

---

### Post by RedSquirrel on 2008-03-06
More styles:

[http://box-look.org](http://box-look.org)
[http://customize.org](http://customize.org)

---

### Post by RedSquirrel on 2008-03-06
If you want a panel with a menu, you could also look at **fbpanel**.

---

### Post by eriqjaffe on 2008-03-06
I seem to remember that fbpanel is a bit flaky in terms of restoring minimized windows...at least, it was when I tried it out.  YMMV.

---

### Post by RedSquirrel on 2008-03-06
> **eriqjaffe said:**
> I seem to remember that fbpanel is a bit flaky in terms of restoring minimized windows...at least, it was when I tried it out.  YMMV.
I haven't seen that, but then I use it with Openbox. That might make a difference.

---

### Post by Belak on 2008-03-06
Wow. All really helpful. Now just for a Wireless Manager (I'm on a laptop and switch between 2 networks quite frequently)

Thanks so much.

---

### Post by eriqjaffe on 2008-03-06
> **Belak said:**
> Wow. All really helpful. Now just for a Wireless Manager (I'm on a laptop and switch between 2 networks quite frequently)

Thanks so much.I use [wicd]("http://wicd.sourceforge.net/"), which is in the gutsy repos.  Works pretty much flawlessly with both my office and home networks.  A lot of people swear by WiFi Radar, but I couldn't get it to work - wicd will scan for available networks, even though WiFi Radar said it wasn't possible for my card.  Go figure.

---

### Post by jviscosi on 2008-03-06
> **eriqjaffe said:**
> I seem to remember that fbpanel is a bit flaky in terms of restoring minimized windows...at least, it was when I tried it out.  YMMV.

I saw this with older versions of fbpanel, but newer versions work correctly.  There was also a stretch where Fluxbox SVN was pretty badly borked in terms of properly representing its windows to external taskbars, but that's fixed too.

---

### Post by Belak on 2008-03-08
Ok, I got the network manager applet working but I don't know how to get the stupid thing to remember the network key. I'm getting sick of typing it in.

Thanks.

And, no, I couldn't get wicd working. At all. I mean it was working, but the wep didn't work.

Thanks

---

### Post by Adnarim on 2008-03-23
Well nm is using the gnome-keyring to save the networkkey so you have to activate this. But I would really recommend using wicd and trying to solve your problem you have with it. The Networkmanager is overloaded...

---

### Post by Belak on 2008-03-23
> **Adnarim said:**
> Well nm is using the gnome-keyring to save the networkkey so you have to activate this. But I would really recommend using wicd and trying to solve your problem you have with it. The Networkmanager is overloaded...

Yeah, I don't use Fluxbox any more... gnome is just easier... I would use fluxbox, but I don't have the time.

Thanks for all the replies, though!

-Belak

---

