---
title: "Using nautilus for desktop managment"
date: 2011-10-03
forum: Desktop Environments
---

### Post by m2xtreme on 2011-10-03
Hi all,

I finally found a work around for using nautilus for managing the desktop instead of xfdesktop!

Why?  I think nautilus is the **the best** file manager for Linux (until Marlin is released that is ;) ) despite it's gnome dependencies.   I wanted to find a way to use nautilus with xfce without install all the unnecessary dependencies and this is my not-so-elegant solution.

Before I continue, this tutorial assumes:

[LIST=1]
[*]You are using an xfce based distribution without gnome installed (if you have gnome installed you probably don't care about dependencies or resource usage)
[*]You can fill in the gaps of what I may have left out (this was written after I set things up so there are probably some steps missing)
[/LIST]
Okay, the first thing you're going to do is disable xfdesktop from showing a desktop image or desktop icons since we're going to make nautilus do all that.  So open up:

Xfce Settings > Desktop

In the Background Tab set the background Image to "none" and Colors as solid black.
In the Menus tab, disable all options under Desktop Menu and Window List Menu.
In the Icons tab, set Icon type to None.

You should now have a blank desktop.  If not, try again until there is nothing showing on your xfdesktop.  You want to do this to be sure that you aren't wasting resources on something you won't see (since it will be covered by the nautilus desktop).

Next, install nautilus.  To make sure you don't pull in all the unnecessary gnome dependencies you should run this command in terminal:

```
sudo apt-get install --no-install-recommends nautilus
```Now, launch nautilus (Alt+F2, "nautilus").  Open the Xfce Settings > Session and Startup.  Go to the Sessions tab.  At a bare minimum you should see xfwm4, xfce4-panel, xfce4-settings-helper, and nautilus.  Close any other applications you don't want running each time you log in and then click the "Save Session" button.

Now log out and log back in.  Congratulations, you should now have nautilus managing your desktop!

But you're not done yet.  If you notice, right clicking the desktop and choosing "Change Desktop Background" doesn't do anything.  This is because it relies on a command called gnome-appearance-properties, which itself is part of gnome-control-center.  But you don't want install this!  It will require an extra 40MB of disk usage for one command for which I have found a simple work around ;)

Instead you should install a simple program for managing gnome/nautilus desktop background, such as nitrogen.  There are other options out there but I will be using nitrogen for this example, feel free to look for an alternative (there are some cool apps that will change your background based on set time intervals for instance).

Anyways, run:

```
sudo apt-get install nitrogen && nitrogen
```You should now have nitrogen installed and running.  Test it out and make sure everything is working.  Typical wallpaper folders are...

> /usr/share/xfce4/backdrops
and
/usr/share/backgroundsOnce you know Nitrogen is working, you need to make a script which will pretend to be gnome-appearance-properties and will launch nitrogen instead.  Open a terminal and enter to following command (substituting "geany" with your text editor of choice).

```
sudo geany /usr/bin/gnome-appearance-properties
```enter the following text into your newly created file:

```
function --show-page=background
{
    nitrogen # background configuration
}

"$1"

exit 0
``` Save the file and close the text editor.  Now every time the command "gnome-appearance-properties --show-page=background" is run it will automatically launch nitrogen.  Try right clicking the desktop and choosing "Change Desktop Background" to confirm nitrogen is launched.  If it does, you're done!  Enjoy the benefits of nautilus combined with the light weight xfce desktop environment :)

Additionally, you should NOT remove xfdesktop.  It is used by xfce for things such as keybinds among other things.  You have been warned.

Lastly, if there is anything I forgot please let me know so I can update the original post.

Thanks!

---

### Post by Sonador on 2011-10-18
Hi Im fan of the xfce+nautilus mix too, unfortunately the guide doesnt work for me (nitrogen doesnt set wallpaper), probably because of the xubuntu and gnome version, which one do you use?

I use xubuntu 11.10 and this solution works for me: 
install *dconf-tools*, then run *dconf-editor *and set a background in org>gnome>desktop>background

---

### Post by m2xtreme on 2011-10-18
Sonador,

I am running Debian.  I started from a minimum install and installed xfce without all the dependencies and only installed what I wanted.  As far as I know it's the same process for installing this sort of setup in Debian or Ubuntu though.

Do you have gnome installed as well?  If that's the case, you do not need to follow this procedure since you will already have the gnome dependencies for the gnome desktop selector.

Also, I'm assuming you mean "gconf-editor".  It sounds like you have nautilus controlling the desktop all right.  Does launching nitrogen manually and changing the wallpaper that way work?

---

### Post by Sonador on 2011-10-19
Thanks for reply.

So it is really gnome2 vs. gnome3 reason. Debian (except unstable sid) use gnome2 (gtk2) + gconf-editor and nitrogen works for it. But Xubuntu 11.10 repositories use gnome3 (gtk3) with new configuration system and the nitrogen was not made to edit configuration file in ~/.config/dconf/user so i edit it with dconf-editor.

And no, I dont have gnome installed, cause I dont like either gnome-shell or unity. Therefore I dont use ubuntu anymore, god bless xfce+nautilus ;-), it is like old good gnome2 and it is somehow easier to customize...

---

### Post by m2xtreme on 2011-10-19
> **Sonador said:**
> Thanks for reply.

So it is really gnome2 vs. gnome3 reason. Debian (except unstable sid) use gnome2 (gtk2) + gconf-editor and nitrogen works for it. But Xubuntu 11.10 repositories use gnome3 (gtk3) with new configuration system and the nitrogen was not made to edit configuration file in ~/.config/dconf/user so i edit it with dconf-editor.

And no, I dont have gnome installed, cause I dont like either gnome-shell or unity. Therefore I dont use ubuntu anymore, god bless xfce+nautilus ;-), it is like old good gnome2 and it is somehow easier to customize...

Oh, you're right!  Great catch, I didn't even think about it being a gnome2 vs gnome3 issue...

I agree, xfce is everything gnome2 was, but better since it doesn't tie together so many unnecessary dependencies.  My only complaints are that the xfce menu is boring and thunar isn't as good as nautilus.  I use a modified version of the mintmenu for problem 1 (but I wish I didn't have to use a gnome menu to enjoy xfce).  And problem 2 is nonexistant with this work around.

Somebody has to make a better menu for xfce, maybe it will be me when I get the time :)

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-23
Thanks for this post!!!  I had so much trouble figuring out how to change my background in Xubuntu while running nautilus.  maybe someone should also add something to edit the nautilus settings in the xfce settings manager, as it seems more than one person has this issue

---

### Post by gsmanners on 2011-10-23
> **TREESofRIGHTEOUSNESS said:**
> ...maybe someone should also add something to edit the nautilus settings in the xfce settings manager, as it seems more than one person has this issue

Nautilus is still a moving target and in the Gnome project, so asking the Xfce devs to support Nautilus would probably seem to them like us stepping on their toes. :(

---

### Post by m2xtreme on 2011-10-23
> **TREESofRIGHTEOUSNESS said:**
> Thanks for this post!!!  I had so much trouble figuring out how to change my background in Xubuntu while running nautilus.  maybe someone should also add something to edit the nautilus settings in the xfce settings manager, as it seems more than one person has this issue

If you found a command to launch nautilus preferences then you could do this, but you would have to uninstall thunar.  I don't think that as a feature is very useful though, I rarely change my nautilus preferences.

Regardless, I'm happy you found this useful.

---

### Post by gkimonas on 2011-10-24
Maybe thunar isn't so complete of functions as nautilus, but is really fast, do what is made to do.

Also, now with gigolo we can connect in samba shares, webdav etc easily from thunar.

After years of use nautilus, and now with thunar in xubuntu, I must say that thunar isn't what can expected someone compare to nautilus, konqueror but is very stable, comfort and really fast, much faster than nautilus.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-27
rox is pretty fast too.

@gsmanners  yeah... you are probably right on that.  I am not trying to step on toes... but the xfce team knows nautilus causes some issues, and they also should be aware that a lot of people use nautilus.  So, if it is a known bug, then they should at least find a way to edit the config, if they aren't going to "integrate" nautilus to the point that it doesn't cause the bug.

---

### Post by m2xtreme on 2011-10-30
Thunar is lacking one function that I need: tabbed browsing.  And unfortunately, it doesn't sound like the developers are willing to incorporate this feature :(  see here: [http://forum.xfce.org/viewtopic.php?id=5904](http://forum.xfce.org/viewtopic.php?id=5904)

Don't get me wrong, I still find thunar to be a handy file manager such as when changing a folder's permissions recursively, but overall I prefer nautilus.

I don't find rox filer to be an attractive solution at all, though I imagine it's really good for older systems with limited resources.

And as far as getting the xfce team to support bugs that occur when running gnome software, don't hold your breath.  You'd be better off fixing it yourself and perhaps even forking the project if you are so inclined.

---

### Post by Xanza on 2012-03-04
Sorry for necro-ing this but I'm stuck while following the steps. After launching nautilus from alt+f2. It's launched but When I go to Session Manager I don't see nautilus at all. Am I missing something?
Running Xubuntu 11.10

---

### Post by m2xtreme on 2012-03-04
> **Xanza said:**
> Sorry for necro-ing this but I'm stuck while following the steps. After launching nautilus from alt+f2. It's launched but When I go to Session Manager I don't see nautilus at all. Am I missing something?
Running Xubuntu 11.10

I don't think you're missing anything... Looks like things have changed?  I'm running Debian but I don't see nautilus in session manager either.  I don't see it in gconf-editor when I launch it either so that's strange... Maybe you can manually add it to your session?  There should be a file $HOME/.cache/sessions

I haven't used this method in a while so it may not work anymore, you'll have to play around and see what you can figure out.  Keep in mind that you will have to use *dconf-tools* and *dconf-editor *since you're using 11.10.

I may update this tutorial after precise launches, we'll see.  I still prefer xfwm over all others.

Best of luck to you.

---

### Post by tivatranquio on 2012-05-06
same problem

---

### Post by tivatranquio on 2012-05-30
ok, done stopping xfdesktop in the session manager, saving the session and adding "nautilus-n" to the "Application Autostart" list.

Now it works, but nitrogen doesn't.

I founded wallch that works by open it manually, but I can't set it on the "change desktop background" entry on the right click menu.

---

### Post by tivatranquio on 2012-05-30
solved: put a text file (check the permission) called gnome-control-center on /usr/bin , write in the file just the word *wallch*, that's it.

---

### Post by lildigiman on 2012-12-19
For anyone else who comes across this, let it be known that you can startup nautilus the *right* way by replacing xfdesktop in this file:

First
```
cp /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

```

Then edit this file with your favorite editor such that this part says nautilus instead of xfdesktop:

Before:
```

<property name="Client3_Command" type="array">
    <value type="string" value="xfdesktop"/>
</property>

```
After:
```

<property name="Client3_Command" type="array">
    <value type="string" value="nautilus"/>
</property>

```

Works better than the other method for me in Xubuntu 12.04.

---

### Post by Seb71 on 2012-12-22
If someone uses XFCE because is similar to Gnome 2 and if that someone also wants Nautilus, isn't a better idea to just switch to Mate?

---

