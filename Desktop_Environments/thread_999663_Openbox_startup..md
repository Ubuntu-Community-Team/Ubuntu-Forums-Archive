---
title: "Openbox startup."
date: 2008-12-02
forum: Desktop Environments
---

### Post by Wise_Wolf on 2008-12-02
I've used Ubuntu for a while, but Gnome for me is too bulky so I decided to switch over to Openbox. I've user other distributions such as Arch, and with Arch all I'd have to do is edit .xinitrc and edit that a bit and all my programs would start once I log in. I'm just wondering since I've heard Gnome and GDM don't use .xinitrc, where do I edit my Openbox session to automatically start programs such as feh, pypanel and conky?

Thanks :D

---

### Post by Izek on 2008-12-02
I believe you'd use System > Preferences > Sessions and add it through there.

---

### Post by snowpine on 2008-12-02
Actually it is ~/.config/openbox/autostart.sh

Make sure to put a & symbol after each application.

---

### Post by malspa on 2008-12-11
I don't know why this works, but instead of ~/.config/openbox/autostart.sh, in Hardy I used /etc/xdg/openbox/autostart.sh and added **pypanel &**, seems to work fine.

---

### Post by urukrama on 2008-12-11
> **malspa said:**
> I don't know why this works, but instead of ~/.config/openbox/autostart.sh, in Hardy I used /etc/xdg/openbox/autostart.sh and added **pypanel &**, seems to work fine.

You add it to the default autostart file, which Openbox loads if it doesn't find a copy in ~/.config/openbox/

The advantage of editing the local ~/.config/openbox/autostart.sh is that you don't need to be logged in as root or use sudo and you can have different autostart files for different users.

The default autostart.sh file loads a lot of things I find unnecessary, such as gnome-settings-daemon.

To the OP, if you need more info on Openbox's autostart.sh, have a look at the [official documentation]("http://icculus.org/openbox/index.php/Help:Autostart") or the Openbox guide linked to in my signature.

---

### Post by malspa on 2008-12-11
> **urukrama said:**
> You add it to the default autostart file, which Openbox loads if it doesn't find a copy in ~/.config/openbox/

The advantage of editing the local ~/.config/openbox/autostart.sh is that you don't need to be logged in as root or use sudo and you can have different autostart files for different users.

The default autostart.sh file loads a lot of things I find unnecessary, such as gnome-settings-daemon.

To the OP, if you need more info on Openbox's autostart.sh, have a look at the [official documentation]("http://icculus.org/openbox/index.php/Help:Autostart") or the Openbox guide linked to in my signature.

Thanks for the explanation!  I'll make a note of it for future reference.

---

### Post by MedianMajik on 2008-12-12
Good choice on Openbox!  Once you have it configured you should be very happy!

---

### Post by malspa on 2008-12-12
I created **~/.config/openbox/autostart.sh**, and it works fine except for one thing.

I'm trying to use the script shown at this page for a random wallpaper -- [http://wiki.ubuntu.org.cn/UbuntuHelp:Openbox](http://wiki.ubuntu.org.cn/UbuntuHelp:Openbox).

Now, this script runs fine when I type **./wallpaper.sh** from a terminal.  I get random wallpapers each time I run **./wallpaper.sh** from the terminal.  But when I insert **./wallpaper.sh** into my autostart.sh script, nothing happens at all when I restart Openbox.

When I put **eval `cat $HOME/.fehbg` &** into the script and restart (as long as I've previously used feh to set a wallpaper), the previous wallpaper is set up like it should be.

But shouldn't **./wallpaper.sh** also work from **~/.config/openbox/autostart.sh**?  Not sure what's happening here.  Following is my **~/.config/openbox/autostart.sh**.


[I]# Run the system-wide support stuff
. $GLOBALAUTOSTART

# Programs to launch at startup

#numlock
numlockx &

# Programs that will run after Openbox has started
(sleep 2 && pypanel) &

#My wallpaper
eval `cat $HOME/.fehbg` &
./wallpaper.sh[/I]


In the "#My wallpaper" section, I've tried using either one line or the other, or both.  Whether I leave out the **eval `cat $HOME/.fehbg` &** line or leave it in, the wallpaper.sh script doesn't work.  If both lines are there, I just get the previous wallpaper that was set.  In any case, the wallpaper.sh script seems to be ignored.  Am I missing something?  Any help would be appreciated -- thanks!!!

---

### Post by urukrama on 2008-12-12
Does *./wallpaper.sh _**&**_*, instead of *./wallpaper.sh* make a difference?

Where did you save the script? You might have it in the wrong directory. Try using the following command: */path/to/script/wallpaper.sh &*

---

### Post by malspa on 2008-12-12
> **urukrama said:**
> Does *./wallpaper.sh _**&**_*, instead of *./wallpaper.sh* make a difference?

Where did you save the script? You might have it in the wrong directory. Try using the following command: */path/to/script/wallpaper.sh &*

OK, I've been trying different combinations in the script.

./wallpaper.sh &
~/wallpaper.sh &
/home/steve/wallpaper.sh &

Tried it those without the "&" and tried it with a sleep command.

No luck.

The autostart script is ~/.config/openbox/autostart.sh.

The wallpapers script is ~/wallpaper.sh.

---

### Post by malspa on 2008-12-12
Got it.

Of course it had to be a stupid, embarrassing mistake on my part.

In the wallpaper.sh script, I left out the "#!/bin/bash" at the beginning.  Everything is working fine now with ./wallpaper.sh in the autostart script.

And, by the way.  In the "My wallpaper" section of my autostart script, including both lines like this is unnecessary and doesn't work:

#My wallpaper
eval `cat $HOME/.fehbg` &
./wallpaper.sh

The new wallpaper comes in but then the eval line changes it back to the old wallpaper, of course.  So now I have this, which works:

#My wallpaper
./wallpaper.sh

Many thanks for your help looking at this!

---

### Post by urukrama on 2008-12-13
I'm glad you solved the problem. Have fun with Openbox.

---

### Post by malspa on 2008-12-15
> **urukrama said:**
> I'm glad you solved the problem. Have fun with Openbox.

Thanks -- it IS fun!  And thanks for the links to your blog and guide, very helpful.  This is my 2nd time around trying Openbox, but things have gone much more smoothly this time.  Still a big fan of Fluxbox -- I'm much more familiar with that one, and still use it quite often -- but Openbox is great, too!

(No opinion on which is better; as with KDE and GNOME, I'm quite happy using either one!)

---

