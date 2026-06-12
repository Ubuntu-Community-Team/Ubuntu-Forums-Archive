---
title: "Guide to using Openbox session in Lubuntu"
date: 2013-09-08
forum: Desktop Environments
---

### Post by vasa1 on 2013-09-08
One of the sessions available with Lubuntu 13.04 is "Openbox". Anyone know of a current guide/faq/tutorial for the one in bold?

```
Openbox is minimalistic, highly configurable,  next  generation  window
       manager with extensive standards support.

       You can start Openbox in three ways:

       If  you  run  a display manager such as GDM, you will find 3 entries in
       the login session type menu  for  Openbox:  GNOME/Openbox,  KDE/Openbox
       and  Openbox.  If  you want to use Openbox within GNOME or KDE, you can
       choose the appropriate entry, and it will  launch  GNOME  or  KDE  with
       Openbox as the window manager.

      [B] The  third  option  at log in, which is Openbox       without a session
       manager, uses the openbox-session       command to  start  Openbox[/B].  On
       log  in,  openbox will run the ~/.config/openbox/autostart.sh script if
       it    exists,    and    will     run     the     system-wide     script
       /etc/xdg/openbox/autostart.sh  otherwise.  You  may  place anything you
       want to run automatically in those files, for example:

              xsetroot -solid grey &
              gnome-settings-daemon &

       Make sure that each line is followed by a "&" or else the  script  will
       stop  there  and further commands will not be executed. You can use the
       /etc/xdg/openbox/autostart.sh file as an example for creating your own.

       The  default /etc/xdg/openbox/autostart.sh runs a number of things with
       Openbox.
...
```From [http://manpages.ubuntu.com/manpages/hardy/man1/openbox.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/openbox.1.html)

---

### Post by CaptainMark on 2013-09-09
I'm not quite sure what you're asking here but Arch Linux has detailed wikis for everything you could ever need to know [https://wiki.archlinux.org/index.php/Openbox](https://wiki.archlinux.org/index.php/Openbox)

---

### Post by sudodus on 2013-09-09
Did you see this wiki page?

[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

Otherwise, to use it (without tweaking) is easy.

1. When you select Openbox at the log in screen of for example Lubuntu, you arrive at a grey screen in almost no time.

2. Right-click and you will get a small menu. Select ***terminal emulator***, and from that you can start any other program.

3. Right-click on the grey background again and select ***exit*** to return to the log in screen (or **[FONT=courier new]poweroff[/FONT]** from the terminal window).

---

### Post by vasa1 on 2013-09-09
Thank you for responding, CaptainMark and Sudodus. Yes, I have looked at the links you mentioned but what I'd really like is a how-to for users of vanilla Lubuntu who wish to try out the Openbox session. The Lubuntu wiki pages don't seem to have anything on the subject. I've managed to make a small start and hope to work out any wrinkles with a little help from the community :)

My first challenge is to get my icon theme (in ~/.icons) to be used. Right now, some other icon theme is being used.

---

### Post by CaptainMark on 2013-09-09
You don't have to find a Lubuntu specific guide, when using pure Openbox then everything else becomes irrelevant because your only running Openbox with bash as a shell. That's probably why there is no specific Lubuntu guide to Openbox

---

### Post by vasa1 on 2013-09-13
@Sudodus, I'm making some progress and will update this thread a little later.

---

### Post by sudodus on 2013-09-13
Sharing results is valuable for the community :-)

---

### Post by malspa on 2013-09-13
> **vasa1 said:**
> @Sudodus, I'm making some progress and will update this thread a little later.
Hm. I'm looking forward to seeing what you've put together.

I haven't used Lubuntu (yet), but I do use Openbox (not in Ubuntu right now, but in a few other distros), and on a few occasions (some time ago) I've installed LXDE in Ubuntu only to find myself using Openbox more than LXDE. 

I've made use of Openbox info at the Arch Wiki (excellent!) and other places. I may have seen the guide that sudodus mentioned above, but I don't remember it (and didn't have it bookmarked). Any additional Openbox info that anyone puts out there, especially for folks who come at it via Lubuntu or by installing LXDE in Ubuntu, could be a good thing, from my point of view. As I recall from running LXDE, there can be a few things to look out for when you choose the Openbox session that you won't see if you've simply added Openbox to Ubuntu.

---

### Post by vasa1 on 2013-09-13
> **sudodus said:**
> Sharing results is valuable for the community :-)
Well, here goes but I'm not really systematic and may have missed something or not written things in a logical order. As I said, this is purely limited to trying out the Openbox session available at the time of logging in on a system running Lubuntu 13.04.

At the outset one can exit an Openbox session by typing **openbox --exit** at a terminal prompt and that gets you back to the login screen. Many changes suggested here may require changing themes back and forth or logging out and back in or possibly a reboot.

After logging in to an Openbox session, a plain grey (#303030) screen is all one gets. To change that to another color, create **~/.config/openbox/autostart** and add this line:
```
xsetroot -solid "#000005"
```
or other color of choice. One can also point to a wallpaper but I didn't go there.

Right-clicking on the screen brings up a menu from which one can choose applications to run. The choice of applications doesn't reflect what you have installed on your system if you've removed some software and added some other software. If you're going to rely on this right-click menu a lot, you'll need to fix that by copying over /etc/xdg/openbox/menu.xml to ~/.config/openbox and modifying it to reflect the software you want to access. I understand there's OBmenu to provide a GUI but again, I didn't go there.

Since I'm already a Lubuntu user, I have **lxpanel** installed and configured the way I like it. To get lxpanel running at startup, add one more line to ~/.config/openbox/autostart so that it looks like:
```
xsetroot -solid "#000005"
lxpanel --profile Lubuntu &
```
Again, since I'm already a Lubuntu user, I have modified ~/.config/openbox/**lubuntu-rc.xml** quite a bit to have the keyboard shortcuts I want. [s]But an Openbox session needs to see just **rc.xml**. I don't know if a logical link would do; for now I copied lubuntu-rc.xml to rc.xml in the same folder.[/s]
*Note that in 14.04, just making a copy of **lubuntu-rc.xml** and calling it **rc.xml** won't do. This is because many of the keyboard shortcuts have command lines with "lxsession-default" in them; they also don't refer to executables directly but to their generic names. So, you'll see "lxsession-default file_manager" in lubuntu-rc.xml but you'll need just "pcmanfm" (or the actual executable for your file manager) in rc.xml. As another example, you'll need "lxterminal" instead of "lxsession-default terminal". In other words, if you're using lubuntu-rc.xml as a starting point for your rc.xml, you'll need to fix lines containing "lxsession-default" if you want the respective keyboard shortcuts to work. * 

Now to the appearance of the panel and applications. I found that my icon theme and gtk theme wasn't effective and that fonts in gtk applications looked bad. The "Openbox" aspect of things was unaffected: in other words, window decorations were unaffected.

Lxappearance (Customize Look and Feel) was unhelpful for changing the "widget" theme and icon theme. I had to make the following edits to various files:
Edit **~/.gtkrc-2.0** to include the following two lines:
```
include "/home/your_username/.themes/gtk_theme_name/gtk-2.0/gtkrc"
gtk-icon-theme-name = "icon_theme_name"
```
Edit ~/.config/gtk-3.0/settings.ini to include 
```
gtk-theme-name = gtk_theme_name
gtk-icon-theme-name = icon_theme_name
```
After doing all this, fonts in the panel and in gtk apps were still a problem: they were much thinner in the Openbox session. (Font appearance in the window decoration were unaffected) To fix that, I added one more line to ~/.config/gtk-3.0/settings.ini:
```
gtk-theme-name = gtk_theme_name
gtk-icon-theme-name = icon_theme_name
gtk-font-name = Comic Sans MS
```
and created **~/.Xresources** with the following content [s](from the bottom of [http://awesome.naquadah.org/wiki/Better_Font_Rendering](http://awesome.naquadah.org/wiki/Better_Font_Rendering)[/s]):
```
! Render setting for cairo -> pango -> gtk
 Xft.dpi:        96
 Xft.antialias:  true
 Xft.hinting:    true
 Xft.rgba:       rgb
 Xft.hintstyle:  hintslight

```Now my Openbox session looks fine.

Overall, I feel there may not be "great" performance gains to users of Lubuntu 13.04 as the Lubuntu session is pretty light to start with but there may be gains for those with older kits. I don't know!

---

### Post by malspa on 2013-09-14
> **vasa1 said:**
> Since I'm already a Lubuntu user, I have **lxpanel** installed and configured the way I like it.
This morning, I stumbled upon this article (from PCLinuxOS Magazine), titled "Openbox - Tint2 vs Lxpanel", which it might be appropriate to mention here: [http://pclosmag.com/html/Issues/201108/page01.html](http://pclosmag.com/html/Issues/201108/page01.html)

**tint2** is a nice option to use for a panel in Openbox; worth checking out, for sure.

Another one of my favorite panels to use in Openbox: **xfce4-panel**.

However, Lubuntu users may prefer to stick with LXPanel if, like vasa1, you've already got it configured to your tastes.

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **Desktop Environments**.*

---

### Post by walterorlin on 2013-09-15
IF you want to edit the openbox menu with a gui you could install obmenu if you wanted to. You can adjust other settings in the openbox configuration manager as normal.

---

### Post by vasa1 on 2013-10-02
Another issue that appeared because I'm not running lxsession*** any more is that stuff copied is lost when the parent app is closed. So I need to have **xclipboard** running to keep track of copied stuff. (xclipboard is less feature-full but lighter than Parcellite and is installed by default in Lubuntu.)

*** this post by Julien Lavergne mentions that lxsession makes a clipboard manager unnecessary: [https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000393.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000393.html)

After trying out xclipboard and clipit, I've settled on **xfce4-clipman**.

---

### Post by vasa1 on 2013-10-13
Here's a detailed, and fairly recent, blog on setting up Openbox on Ubuntu: [Install Openbox On Ubuntu 13.04 & 13.10]("http://ndever.net/articles/linux/install-openbox-ubuntu-1304-1310")

---

### Post by sudodus on 2013-10-14
Thanks for sharing this information :-)

---

### Post by vasa1 on 2013-10-14
> **sudodus said:**
> Thanks for sharing this information :-)
You're most welcome. BTW, I appreciate the hard work you're putting into various projects :)

---

### Post by malspa on 2013-10-15
> **vasa1 said:**
> Here's a detailed, and fairly recent, blog on setting up Openbox on Ubuntu: [Install Openbox On Ubuntu 13.04 & 13.10]("http://ndever.net/articles/linux/install-openbox-ubuntu-1304-1310")
Good stuff!

---

### Post by sudodus on 2013-10-15
> **vasa1 said:**
> You're most welcome. BTW, I appreciate the hard work you're putting into various projects :)

You are most welcome too :-)

---

### Post by Rex Bouwense on 2013-10-23
Hi vasa1.  Is there anything here that you can use?
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by vasa1 on 2013-10-23
> **Rex Bouwense said:**
> Hi vasa1.  Is there anything here that you can use?
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)
Essential reading :)

---

### Post by Melodie on 2013-11-14
Hi,

If you are not running lxsession you need to run openbox-session. I don't know much yet about how Lubuntu is setup. (ie: when selecting "openbox" in Lightdm, does it start openbox-session?)  In Openbox distributions I use: Archlinux, Ubuntu, PCLinuxOS when I used it a while ago, are setup with Openbox only and a few additional components which make it act as a real desktop. The main component for this purpose is openbox-menu (I put up a ppa for it, and a set of configurations I also provide for Ubuntu). 

I will soon announce on the forums an Ubuntu Remix having for name "Bento", which will be provided as RC, because it still needs testing. However many versions have been uploaded since a little more than one year, and only once a while a feedback was provided about some things to be improved.
You can read about one of them done a few months ago here, just to have an idea:
[Bento2 - OBUbuntu Remix presentation](http://forum.linuxvillage.org/index.php?topic=248.0)

The boot of the live is much nicer now and the background is changed. The user applications are a bit different also. I have not yet tried to install lubuntu-destkop to a Bento install to see how it would go, but that could be an interesting experience. :)

Let me know if you are interested?

---

### Post by vasa1 on 2013-11-14
> **Melodie said:**
> ...
If you are not running lxsession you need to run openbox-session. I don't know much yet about how Lubuntu is setup. (ie: when selecting "openbox" in Lightdm, does it start openbox-session?)  ...
Thank you for responding :)
I will check whether openbox-session runs by default or not and get back to you.

---

### Post by vasa1 on 2013-11-15
I ran the following command in both Lubuntu and Openbox sessions and grepped for "session":
```
[12:23 PM] ~/Desktop $ grep session ob-session-processes.txt 
root      3313   957  0 10:12 ?        00:00:00 lightdm --session-child 12 25
vasa1     3400  3360  0 10:12 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch /usr/bin/openbox-sessio
vasa1     3403     1  0 10:12 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch /usr/bin/openbox-session
vasa1     3404     1  0 10:12 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
vasa1     3435     1  0 10:12 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
[12:23 PM] ~/Desktop $ grep session lx-session-processes.txt 
root      1118   957  0 07:05 ?        00:00:00 lightdm --session-child 12 19
vasa1     1220  1169  0 07:06 ?        00:00:00 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-FIyUcTDjPh
vasa1     1252  1169  0 07:06 ?        00:00:00 upstart-dbus-bridge --daemon --session --user --bus-name session
vasa1     1253  1169  0 07:06 ?        00:00:00 /usr/bin/lxsession -s Lubuntu -e LXDE
vasa1     1320  1169  0 07:06 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
[12:24 PM] ~/Desktop $ 

```I don't quite know what the output means, but I did not explicitly run openbox-session. I just chose Openbox at the time of login.

---

### Post by vasa1 on 2013-12-21
This maybe of interest to some users of Openbox:
[debian testing oddity]("http://icculus.org/pipermail/openbox/2013-December/008378.html")

---

### Post by vasa1 on 2014-01-11
[http://urukrama.wordpress.com/2012/06/30/autostart-applications-in-openbox-3-5/](http://urukrama.wordpress.com/2012/06/30/autostart-applications-in-openbox-3-5/) explains why more than one .desktop file for the same application maybe seen when in an Openbox session. I got that from here: [&#8220;OnlyShowIn&#8221; and &#8220;NotShowIn&#8221; not being obeyed in Openbox session?]("http://askubuntu.com/a/403865/25656")

---

### Post by vasa1 on 2014-01-15
> **malspa said:**
> This morning, I stumbled upon this article (from PCLinuxOS Magazine), titled "Openbox - Tint2 vs Lxpanel", which it might be appropriate to mention here: [http://pclosmag.com/html/Issues/201108/page01.html](http://pclosmag.com/html/Issues/201108/page01.html)

**tint2** is a nice option to use for a panel in Openbox; worth checking out, for sure.
...
Checking it out and I may end up preferring it. The link is really informative too. One thing it doesn't mention is how to reload tint2's config file (*~/.config/tint2/tint2rc*) after modifying it: run **killall -SIGUSR1 tint2**.

---

### Post by vasa1 on 2014-01-18
[Here's a useful thread by stinkeye]("http://ubuntuforums.org/showthread.php?t=2197247&p=12889961#post12889961") on the right-click menu (and you can safely ignore my posts in that thread).
Then there's this to make the right-click menu appear without needing to right-click on the desktop: [http://ubuntuforums.org/showthread.php?t=2200202&p=12903409#post12903409](http://ubuntuforums.org/showthread.php?t=2200202&p=12903409#post12903409)

---

### Post by vasa1 on 2014-01-24
> **vasa1 said:**
> Another issue that appeared because I'm not running lxsession*** any more is that stuff copied is lost when the parent app is closed. So I need to have **xclipboard** running to keep track of copied stuff. (xclipboard is less feature-full but lighter than Parcellite and is installed by default in Lubuntu.)

*** this post by Julien Lavergne mentions that lxsession makes a clipboard manager unnecessary: [https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000393.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-February/000393.html)

I installed **clipit** and ran it with the **-d** option; that seems to do the job as far as remembering copied stuff after the parent app is closed in a pure Openbox session.

**Edit** on 20140208: I found *clipit -d* to be a little unpredictable in my hands :( . I'll just have to remember to keep the parent application open.

---

### Post by vasa1 on 2014-02-03
See stinkeye's post ([http://ubuntuforums.org/showthread.php?t=2202961&p=12918246#post12918246](http://ubuntuforums.org/showthread.php?t=2202961&p=12918246#post12918246)) for how to use "Software and Sources": *gksudo software-properties-gtk* worked for me.

---

### Post by vasa1 on 2014-02-23
I've come to the conclusion that *~/.themes/theme_name/gtk-3.0/settings.ini* doesn't function in an Openbox session. I don't know if I'm right but to change things, I need to edit *~/.themes/theme_name/gtk-3.0/gtk.css* or *~/.themes/theme_name/gtk-3.0/gtk-widgets.css* directly.

---

### Post by sammiev on 2014-02-23
Hi vasa1, at this time are you running openbox off deb or rpm? Seems you been doing a little testing.

---

### Post by vasa1 on 2014-02-24
> **sammiev said:**
> Hi vasa1, at this time are you running openbox off deb or rpm? Seems you been doing a little testing.
At this time all I have is standard Lubuntu 13.10 which offers an Openbox session at the time of login. So anyone who has Lubuntu 13.10 can just login in to an Openbox session instead of the default Lubuntu (LXDE) session.

The initial experience is quite "unfriendly" --- just a dark screen. So this thread is all about getting past that ;)

I'll ask a mod to fix the title to read Guide to using Openbox session in Lubuntu. That should make things clearer, I hope.

BTW, it's quite lonely as an Openbox user now that stinkeye has done a runner :(

---

### Post by Bucky Ball on 2014-02-24
> **vasa1 said:**
> 
I'll ask a mod to fix the title to read Guide to using Openbox session in Lubuntu. That should make things clearer, I hope.



Done. Be aware that although it is only the title on the first post that changes, the new title will be the one that is picked up in searches and used when it is in the thread list.

---

### Post by vasa1 on 2014-02-24
> **Bucky Ball said:**
> Done. Be aware that although it is only the title on the first post that changes, the new title will be the one that is picked up in searches and used when it is in the thread list.
Thanks! What shows up in the thread's list and searches is what I wanted. Maybe now there'll be a few more eyeballs :)

---

### Post by ibjsb4 on 2014-03-30
I wish to try OpenBox no-desktop, but do not want it having any mixed action with my current DE.  So I wish to put it on a 10G partition and was wondering if you had any tips, maybe other needed packages?

---

### Post by sudodus on 2014-03-30
You can always try from the low end starting from the Ubuntu mini.iso and in the basic text version install openbox (or fluxbox or some other window manager with a light foot-print). Then add what you want ... or what people will recommend in the following posts ...

---

### Post by ibjsb4 on 2014-03-30
I hope the recommends do not start, this is about openbox no-desktop.

---

### Post by sudodus on 2014-03-30
Do you mean

```
sudo apt-get --no-install-recommends openbox
```

to get it as light as possible?

I meant 'human recommends' - suggestions from users of openbox like *vasa1*.

---

### Post by sammiev on 2014-03-30
I have done openbox using the mini.iso and select what menus you want in your openbox. Take your time and choose wisely, you can also add to the openbox menu with a little work. There was really good post I found in this thread, so it's all here.

---

### Post by vasa1 on 2014-03-30
> **ibjsb4 said:**
> I wish to try OpenBox no-desktop, but do not want it having any mixed action with my current DE.  So I wish to put it on a 10G partition and was wondering if you had any tips, maybe other needed packages?
Hi, I started this thread with the specific context of logging into the Openbox session provided to people who have installed regular Lubuntu. Even in such a case, there could be complications arising from editing ~/.gtkrc-2.0 and the other gtk files I wrote about. The settings put down there would interfere with how the Lubuntu session would look if one goes from an Openbox session back to a Lubuntu session.

Of course, once I got used to the Openbox session I found little to no need to go back to the Lubuntu session. Sometimes, I'd go back just to see if I could help someone else who has difficulty with the Lubuntu session.

*I don't know about how to have an Openbox session starting with a minimal CD or .iso.*

---

### Post by ibjsb4 on 2014-03-31
Update:

Set up a 10G partition with lubuntu-core and Openbox.  First thing I have to figure out is why Openbox will not boot :(  Worked fine on 14o4 gnome, but no booty in 14o4 Lu.  Probably need an entry in lightdm conf.  Anyhow I got this far today and ready to put it down for a while :)

---

### Post by ibjsb4 on 2014-03-31
Turns out I was not happy with that install; so I went with a standalone openbox install and no other desktop and I also did not want lightdm (just startx).  So I have built the basic openbox system with:

mini.iso 12o4
openbox
obconf
xinit
xserver.xorg
and a few app's

The optional app's I have installed do not show in menu.  Looks like I need "menumaker" for this.

Also need a panel; I'm thinking either py or lx panel.

[COLOR=#ff0000]Edit:[/COLOR][COLOR=#ff0000][/COLOR]

Installed lxpanel, working nice and the panel main menu shows all installed apps.  Added icons.  Have plenty of themes to choose from.

If I read this right, I can change my r-click menu into a static menu.

[https://wiki.archlinux.org/index.php/openbox#Static](https://wiki.archlinux.org/index.php/openbox#Static)

Need to find some examples of menu.xml.

---

### Post by ibjsb4 on 2014-03-31
Thanks to the post in this thread I have a very good start.  Some more packages added, some tweaks, it turns out to be not that hard when presented with the proper information.  I am surprising happy with Openbox.  Thanks again :)

---

### Post by sammiev on 2014-03-31
> **ibjsb4 said:**
> Thanks to the post in this thread I have a very good start.  Some more packages added, some tweaks, it turns out to be not that hard when presented with the proper information.  I am surprising happy with Openbox.  Thanks again :)

WoW you have come along way in the last 12 hrs. :D

---

### Post by vasa1 on 2014-03-31
> **ibjsb4 said:**
> ...
Need to find some examples of menu.xml.
Here's mine (simple, no nesting):
```
<?xml version="1.0" encoding="UTF-8"?>

<openbox_menu xmlns="http://openbox.org/"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://openbox.org/
                file:///usr/share/openbox/menu.xsd">

<menu id="root-menu" label="Openbox 3">
  <item label="Des_ktop">
    <action name="Execute"><execute>exo-open /home/vasa1/Desktop</execute></action>
  </item>
  <item label="Downloads">
    <action name="Execute"><execute>exo-open /home/vasa1/Downloads</execute></action>
  </item>
  <item label="Openbox">
    <action name="Execute"><execute>exo-open /home/vasa1/.config/openbox</execute></action>
  </item>
  <separator />
  <item label="Solitaire">
    <action name="Execute"><execute>sol</execute></action>
  </item>
  <item label="Composer">
    <action name="Execute"><execute>/home/vasa1/seamonkey2/seamonkey/seamonkey -edit</execute></action>
  </item>
  <item label="TaskManager">
    <action name="Execute"><execute>lxtask</execute></action>
  </item>
  <item label="Gmail">
    <action name="Execute"><execute>/opt/google/chrome/google-chrome https://mail.google.com</execute></action>
  </item>
  <item label="Calc">
    <action name="Execute"><execute>calc</execute></action>
  </item>
  <separator />
  <item label="Reconfig_ure">
    <action name="Reconfigure" />
  </item>
  <separator />
  <item label="Exit">
    <action name="Exit" />
  </item>
</menu>

</openbox_menu>

```Obviously, people will want their own access (accelerator) keys. So, instead of pressing **u** to reconfigure, having *Re_configure* would make **c** the key to press (provided it doesn't conflict with other access keys).

%%%%%%%%%%%%%%%%%%%

Nice to know you're getting on well!

I think I mentioned it before, but with vanilla Openbox, you may have trouble with remembering the clipboard contents when you close the source app *before* pasting into the target app.

So I have xclipboard set to autostart and have modified the <applications> section of **rc.xml** to start xclipboard "iconified" and to *not* appear in the taskbar by means of:

    <application class="XClipboard" name="xclipboard">
      <skip_taskbar>yes</skip_taskbar>
      <iconic>yes</iconic>
    </application>

And here is my current *~/.config/openbox/autostart*:

```
xsetroot -solid "#000005"
(sleep 2s && tint2) &
(sleep 2s && xfce4-power-manager) &
(sleep 2s && nmcli con up id "DSL connection 1") &
(sleep 10s && /home/vasa1/.dropbox-dist/dropbox) &
(sleep 5s && lxpanel) &
(sleep 5s && conky) &
(sleep 5s && udisksctl mount -b /dev/sdb1) &
(sleep 30s && /home/vasa1/bin/cpu-usage-alert) &
(sleep 5s && xclipboard) &

```


Of course, if the user's clipboard needs are more complex, a heavier clipboard manager such as clipit could be used.

---

### Post by ibjsb4 on 2014-04-01
Thanks again vasa1.  I have not install power-manager; are you on a laptop and does Openbox and dropbox play nice?

[COLOR=#ff0000]Note:[/COLOR]  I now have two installs on this box to compare.  A core build of Lu and standalone Ob.  Out of the starting gate Ob is a bit faster, but both need more packages.

---

### Post by vasa1 on 2014-04-01
> **ibjsb4 said:**
> Thanks again vasa1.  I have not install power-manager; are you on a laptop and does Openbox and dropbox play nice?

[COLOR=#ff0000]Note:[/COLOR]  I now have two installs on this box to compare.  A core build of Lu and standalone Ob.  Out of the starting gate Ob is a bit faster, but both need more packages.
There will be quite a few differences because my starting point is a regular Lubuntu 13.10 install which has more packages by default, some of which may be useful, some maybe unnecessary.

xfce's power manager is included in the standard Lubuntu install.

Yes, my system is a laptop, Dell Inspiron 1545 Core2Duo with 4GB RAM and lots of free space.

I installed Dropbox direct from the dropbox.com site and haven't seen any difference in its behavior when I run a Lubuntu session and when I run the Openbox session.

As you pointed out, switching gtk themes is a bit fidgety but now I'm settled and don't miss the DE.

There's a lot to explore in rc.xml and you can set up all sorts of keyboard shortcuts including aerosnap and how to open apps at a specific location on the screen and with defined sizes and with or without window decorations, etc, etc, etc.

---

### Post by ibjsb4 on 2014-04-02
When I installed the package "gksu" I notice it also installing gconf files, so I installed gconf-editor to see whats up.


So I now have gocnf-editor running with one (and only one) package in it, gksu, funny :)

---

### Post by ibjsb4 on 2014-04-03
Here's my findings (keep in mind I'm on a very old box).


Boot time to desktop (both running same app's):
Lubuntu-core with lightdm = 26sec
Standalone Openbox with startx = 22sec


I think this is because lubuntu just has more startup programs.


I cannot see any performance difference when running apps (runs fast), although openbox uses less ram.


Both installs are still lacking necessary packages and will be added to in the weeks to come, but right now I'm leaning towards the core build of lubuntu.  It has the little things done that can be added to openbox, but lacking from the start.


Makes me think this is about to go full circle and end up back at Ob no-desktop on Lu :)

---

### Post by ibjsb4 on 2014-04-04
Well this has turned out to be quite an adventure.  I am really, really impressed with Openbox and will continue to explore Openbox as a possible replacement of my gnome-session.  Although running it without a desktop does not seem to fit my needs.  I find lxde or lubuntu-core better suited for me.


Again I thank all for the input (got me off to a really good start)  ..  good travles  :)

---

### Post by vasa1 on 2014-10-31
Setting the background with xsetroot doesn't work with compton. One needs to use hsetroot instead.

References:
[http://superuser.com/questions/786734/compton-background-color](http://superuser.com/questions/786734/compton-background-color)
[https://github.com/chjj/compton/issues/162](https://github.com/chjj/compton/issues/162)

---

### Post by vasa1 on 2014-11-12
It's quite possible that it becomes difficult to remember which keybinds do what in rc.xml and which keybinds are still available. To ease things a bit, I cleaned up my rc.xml by adding explanatory comments at the end of lines beginning with **<keybind key=** instead of having comments above each keybind. Then, ```
$ grep "keybind key=" rc.xml > ~/Desktop/obkeys
```gives me a plain text file which I can reference more easily (and sort).

---

### Post by vasa1 on 2014-11-18
Thanks to [Lubuntu , Openbox , Change default icon in window title bar.]("http://ubuntuforums.org/showthread.php?t=2250384"), I've decided to try fbpanel (in the repos) instead of tint2. Briefly, the windows of some programs and some "child" windows of other programs don't display distinctive icons. Instead a generic Openbox icon is seen in the tint2 panel and in the window title bar. Apparently, this issue isn't seen when using using fbpanel.

Here's a link to an old but detailed thread on how to install Openbox/fbpanel on Puppy Linux: [Openbox/Fbpanel, How to set it all up.]("http://www.murga-linux.com/puppy/viewtopic.php?t=68200") I'm going to use that as a guide.

I got it going but I had to comment out a plugin related to volume. Leaving that in caused fbpanel to sulk as evidenced by the pgrep output:```
10:49 AM ~ $ fbpanel
Creating profile 'default' at /home/vasa1/.config/fbpanel/default
Using /usr/share/fbpanel/default as template
volume: can't open /dev/mixer
HINT: Do you have ALSA-OSS emulation loaded?
HINT: Check out for 'snd-mixer-oss' kernel module loaded.
HINT: Or disable 'volume' plugin at ~/.config/fbpanel/default.
fbpanel: can't start plugin volume
10:49 AM ~ $ pgrep fbpanel
10:51 AM ~ $ 
```
Now to remove stuff I don't need or that I already have in my conky:)

Yikes: just noticed the "default" Openbox icon still appears!

Edit: I'll give fbpanel a rest and go back to tint2.

---

### Post by vasa1 on 2014-11-20
I can't remember if I linked to this before but here's an epic how-to about the right-click menu: [http://forum.lxde.org/viewtopic.php?f=24&t=31525](http://forum.lxde.org/viewtopic.php?f=24&t=31525)

---

### Post by vasa1 on 2014-12-03
lxlinux.com now has a page about fbpanel: [http://lxlinux.com/fbpanel.html](http://lxlinux.com/fbpanel.html)

---

### Post by vasa1 on 2014-12-31
I was using *clipit -d* as a minimal clipboard utility but I just found that I could use *lxclipboard* instead. It's something that's part of Lubuntu and it is what is used in a regular Lubuntu session. *lxclipboard* works just as well in the Openbox session but, because I'm not running lxsession, I need to launch it via my Openbox autostart (instead of *clipit -d*).

---

### Post by Melodie on 2015-07-27
Hello vasa1,

Out of curiosity, this year I tried to create a custom Openbox configuration in Lubuntu in Virtualbox, using my favorite tools openbox-menu and obsession (now both available in the official repositories), and the usual set of openbox/xml files which are provided in Bento Openbox, but I failed with the lubuntu rc.xml file regularly reloaded from somewhere in the system, at each new session.

I tried one thing, another, and finally gave up and went back to work on the Bento Openbox project, without a clue on what is setup that made me fail. 

I have read the full thread from the beginning here, and that is a very nice exchange of experimentations and teachings. There is one of your tips which I'll try in my current system, (Bento on 15.04) because the fonts aren't bad, but might be even better. 

Also, if you find the fonts not good enough in Openbox, which not install the package ttfautohint which can help improve them, additonnally to libcairo/libpango packages?

---

### Post by vasa1 on 2015-07-27
> **Melodie said:**
> Hello vasa1,

Out of curiosity, this year I tried to create a custom Openbox configuration in Lubuntu in Virtualbox, using my favorite tools openbox-menu and obsession (now both available in the official repositories), and the usual set of openbox/xml files which are provided in Bento Openbox, but I failed with the lubuntu rc.xml file regularly reloaded from somewhere in the system, at each new session.

I tried one thing, another, and finally gave up and went back to work on the Bento Openbox project, without a clue on what is setup that made me fail. 

Hi, I'm guessing that as long as you log into a Lubuntu session, lubuntu-rc.xml **will** be used. If you log into the Openbox session, there needs to be just an **rc.xml** file in ~/.config/openbox.

It's been a very long time since I last seriously used the Lubuntu session. I've gotten used to the plain Openbox session (no desktop environment). But then my needs are relatively simple. 

As regards the right-click menu, I've set up *~/.config/openbox/menu.xml* and *~/.config/openbox/menu.xml* just the way I like them and I hardly ever install "new" software to the extent of requiring a dynamic menu. (In case of "an emergency", I have a toggle for lxpanel (thanks yetiman64!) in my openbox right-click menu.) So I don't have need of things like dmenu or even openbox-menu.

> I have read the full thread from the beginning here, and that is a very nice exchange of experimentations and teachings. There is one of your tips which I'll try in my current system, (Bento on 15.04) because the fonts aren't bad, but might be even better. 

Also, if you find the fonts not good enough in Openbox, which not install the package ttfautohint which can help improve them, additonnally to libcairo/libpango packages?

As far as the appearance of fonts, I'm happy now but I will keep a note of ttfautohint.

One issue I haven't managed to sort out is [the appearance of icons in the title bar]("http://ubuntuforums.org/showthread.php?t=2250384") in an Openbox session! For some reason, certain applications such as gnome-disks, gpaint, and mtpaint or the dialog windows of certain applications such as Geany are represented by a "generic" Openbox icon. The same behavior carries over to the tint2 panel. But of course that's not a deal-breaker :)

---

### Post by malspa on 2015-08-04
> **vasa1 said:**
> I got it going but I had to comment out a plugin related to volume. Leaving that in caused fbpanel to sulk as evidenced by the pgrep output

vasa1, I got the same output with fbpanel in Openbox in Lubuntu 14.04, so I also commented out the volume plugin. But, how to get a working volume icon for fbpanel, then? The volume plugin works fine for me in another installation (Debian Jessie), but not in Lubuntu.

---

### Post by malspa on 2015-08-05
> **malspa said:**
> But, how to get a working volume icon for fbpanel, then?


```
$ fbpanel
volume: can't open /dev/mixer
HINT: Do you have ALSA-OSS emulation loaded?
HINT: Check out for 'snd-mixer-oss' kernel module loaded.
HINT: Or disable 'volume' plugin at ~/.config/fbpanel/default.
fbpanel: can't start plugin volume
```

Okay, here's what worked for me, for fbpanel in Openbox in Lubuntu 14.04:

- Commented out the volume plugin in ~/.config/fbpanel/default.
- Installed volumeicon-alsa.
- Added the following to ~/.config/openbox/autostart:
```
volumeicon &
```
- Logged out and back into Openbox.

---

### Post by vasa1 on 2015-08-05
> **malspa said:**
> ...
Okay, here's what worked for me, for fbpanel in Openbox in Lubuntu 14.04:

- Commented out the volume plugin in ~/.config/fbpanel/default.
- Installed volumeicon-alsa.
- Added the following to ~/.config/openbox/autostart:
```
volumeicon &
```
- Logged out and back into Openbox.
@malspa, if you have time could you please look at the last para in [http://ubuntuforums.org/showthread.php?t=2173126&p=13328387#post13328387](http://ubuntuforums.org/showthread.php?t=2173126&p=13328387#post13328387). One of the reasons I tried fbpanel was to see if I could get actual icons to appear in the panel rather than the generic Openbox icon. But both fbpanel and tint2 behaved the same: only generic icons for certain apps and certain dialog windows. This is in the Openbox session. I don't log into Lubuntu anymore.

---

### Post by malspa on 2015-08-05
> **vasa1 said:**
> @malspa, if you have time could you please look at the last para in [http://ubuntuforums.org/showthread.php?t=2173126&p=13328387#post13328387](http://ubuntuforums.org/showthread.php?t=2173126&p=13328387#post13328387). One of the reasons I tried fbpanel was to see if I could get actual icons to appear in the panel rather than the generic Openbox icon. But both fbpanel and tint2 behaved the same: only generic icons for certain apps and certain dialog windows. This is in the Openbox session. I don't log into Lubuntu anymore.

For most of the apps I use, the icons work correctly, on the window title bar as well as on the panel (fbpanel). I've noticed only a few apps where I get the generic icon -- Disks, mtpaint, not much else. So, that isn't much of an issue here.

For Openbox in Lubuntu 14.04, I think I'll stick with fbpanel, even though I normally use tint2 in Openbox these days.

One thing I miss from logging into the Lubuntu session is being able to have different wallpapers on different workspaces.

Setting up Openbox in Lubuntu, for me it mostly involves setting up the menu (I added obmenu for easier menu editing), choosing and setting up something to handle wallpapers (I went with Nitrogen), and choosing and setting up a panel. A few odds and ends after all that.

Anybody trying Openbox: Save your config files! Especially the stuff in the ~/.config/openbox/ directory, but also stuff like tint2rc. These files can help make things go a lot more quickly and smoothly next time you're setting up Openbox, even if you have to edit them a little bit for the new installation. To me, this is one of the benefits of Openbox, being able to use copies of old config files to quickly set up a new Openbox installation.

---

### Post by vasa1 on 2015-08-05
> **malspa said:**
> For most of the apps I use, the icons work correctly, on the window title bar as well as on the panel (fbpanel). I've noticed only a few apps where I get the generic icon -- Disks, mtpaint, not much else. So, that isn't much of an issue here.

Well, having the generic icon isn't a serious problem but I was wondering if you managed to get the real icons to display.

> **malspa said:**
> Anybody trying Openbox: Save your config files! Especially the stuff in the ~/.config/openbox/ directory, but also stuff like tint2rc. These files can help make things go a lot more quickly and smoothly next time you're setting up Openbox, even if you have to edit them a little bit for the new installation. To me, this is one of the benefits of Openbox, being able to use copies of old config files to quickly set up a new Openbox installation.
Another file I backup is *themerc* and that's because I have my own 1589 byte minimal theme: *~/.themes/openbox_theme_name/openbox-3/themerc*.

---

### Post by malspa on 2015-09-13
> **vasa1 said:**
> Well, having the generic icon isn't a serious problem but I was wondering if you managed to get the real icons to display.
Sorry, vasa1, I hadn't gone back to try to get the real icons to display, mainly because the icons in question are for apps that I really don't use, or rarely use.

---

### Post by Melodie on 2015-10-02
> **vasa1 said:**
> Hi, I'm guessing that as long as you log into a Lubuntu session, lubuntu-rc.xml **will** be used. If you log into the Openbox session, there needs to be just an **rc.xml** file in ~/.config/openbox.

It's been a very long time since I last seriously used the Lubuntu session. I've gotten used to the plain Openbox session (no desktop environment). But then my needs are relatively simple. 

It was an Openbox session. I think I have tried that in a Trusty Lubuntu edition. (Not totally sure now). The default lubuntu-rc.xml kept being back. ( I don't want to really argue about that, but just to say, I am quite stubborn and tried different things until I got enough, especially as Bento Openbox was already working fine).

> As regards the right-click menu, I've set up *~/.config/openbox/menu.xml* and *~/.config/openbox/menu.xml* just the way I like them and I hardly ever install "new" software to the extent of requiring a dynamic menu. (In case of "an emergency", I have a toggle for lxpanel (thanks yetiman64!) in my openbox right-click menu.) So I don't have need of things like dmenu or even openbox-menu.

Well just saying, in case it can be useful : openbox-menu does not need to be launched in persistent mode. It can also generate a new menu by invoking it in the console. (I think other programs do it anyway, well if you want to try… )

> As far as the appearance of fonts, I'm happy now but I will keep a note of ttfautohint.

Sure!

> One issue I haven't managed to sort out is [the appearance of icons in the title bar]("http://ubuntuforums.org/showthread.php?t=2250384") in an Openbox session! For some reason, certain applications such as gnome-disks, gpaint, and mtpaint or the dialog windows of certain applications such as Geany are represented by a "generic" Openbox icon. The same behavior carries over to the tint2 panel. But of course that's not a deal-breaker :)

I don't have gnome-disks, gpaint nor mtpaint, but Geany and several others do have their own icon in the top left part of the handle of the window. It could be your Openbox theme? I am using, uh let me see… "Imagine": 
[http://box-look.org/content/show.php/IMAGINE+OPENBOX?content=156640](http://box-look.org/content/show.php/IMAGINE+OPENBOX?content=156640)

My favorite is "flat carbon".

---

### Post by vasa1 on 2015-10-07
My latest keybind:```
    <keybind key="Menu">        # middle-click
      <action name="Execute"><command>xdotool click 2</command></action>
    </keybind>

```My laptop doesn't have a "middle" mouse button and I don't use the Menu key otherwise.

---

### Post by vasa1 on 2015-10-09
I came across this in the [BunsenLabs forum]("https://forums.bunsenlabs.org/viewtopic.php?id=238"): [obamenu is a free open source utility that automagically creates menus for openbox]("http://rmoe.anukis.de/obamenu.html"). I don't install/uninstall stuff frequently and so it's not something I'll be using but someone else may find it useful:> obamenu is written in standard Python, should run with any Python > 2.5 standard installation and needs no extras or dependencies. 

---

### Post by vasa1 on 2015-10-26
A negative according to some users, is that Openbox offers a limited "restore" feature.

damo@BunsenLabs has posted a Bash script on [github]("https://github.com/capn-damo/snapping") that uses xdotool & wmctrl to extend one's options:
```
Scripts for window snapping
Based on ideas in a script found at
http://icculus.org/pipermail/openbox/2013-January/007772.html
Written by damo damo@bunsenlabs.org October 2015
The script snaps a window to left or right halves of screen, or top and bottom,
using X window properties for getting and storing values.
Left, right, top, or bottom screen margins can be specified (negative values allowed);
Works with dual monitors - windows will snap to edges of monitor they are on;
Honours user-defined Openbox left and right screen margins;
Works with decorated and undecorated windows, and windows with no borders;
Doesn't cover panels at top,bottom, desktop left or desktop right.
REQUIRES: xdotool, wmctrl
TODO: Account for _NET_WORKAREA with top/bottom snapping if panel only
```

To restore a window, just repeat the immediately previous shortcut used to snap the window.

---

### Post by vasa1 on 2016-04-20
Openbox in 16.04 is version 3.6.1. One useful feature is that you can now specify where the right-click menu should **always** appear. The default is based on wherever the mouse pointer is.

```
    
<keybind key="W-space">        # Openbox root (right-click) menu
    <action name="ShowMenu">
      <position>
        <x>550</x>
        <y>35</y>
      </position>
        <menu>root-menu</menu>
    </action>
</keybind>

```will position the top left corner of the root menu 550 px to the right of the top left corner of the screen and 35 px down.

---

### Post by vasa1 on 2016-05-26
Bumping this to keep this thread open and to share [a keybind I just came across]("http://crunchbang.org/forums/viewtopic.php?pid=325206#p325206"). What it does is to minimize all open windows except the one in focus:```
    <keybind key="W-H">        # hide other windows
      <action name="ToggleShowDesktop"/>
      <action name="Raise"/>
      <action name="Focus"/>
    </keybind>

```Of course, the user may want a keybind other than W-H.

---

