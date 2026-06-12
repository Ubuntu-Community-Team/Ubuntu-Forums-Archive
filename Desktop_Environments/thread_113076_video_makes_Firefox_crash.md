---
title: "video makes Firefox crash"
date: 2006-01-05
forum: Desktop Environments
---

### Post by nix4me on 2006-01-05
When I play these 2 videos in order, Firefox crashes.

[ftp://ftp.motorcycle.com/pub/videos/Rolling_Burnout.mpg](ftp://ftp.motorcycle.com/pub/videos/Rolling_Burnout.mpg)
[http://www.motorcycle.com/mo/mcbeware/03_Judgement_Day/Judgement_Day.wmv](http://www.motorcycle.com/mo/mcbeware/03_Judgement_Day/Judgement_Day.wmv)

The first video plays fine in my mplayerplug-in 3.17.  The second video tries to open the dialog box to pick a different player but instead Firefox (1.07 and 1.5) disappears.

Can anyone confim?

click first link, then second link.

nix4me

---

### Post by kairu0 on 2006-01-05
Have you deleted the Totem plugins from /usr/lib/mozilla-firefox/plugins? If not, please do.

---

### Post by nix4me on 2006-01-05
Yes I have.

I am using mplayer and mplayerplug-in because Totem is total crap.

I am able to reproduce this crash 100% of the time.  And it is interesting to note, only Ubuntu exibits this behavior.  It works fine on Debian.

nix4me

---

### Post by kairu0 on 2006-01-05
I can't reproduce your problem here. When I click on the second video, the dialog box opens, I click, and mplayer comes up flawlessly (in an external window.)

---

### Post by nix4me on 2006-01-05
Well I have no idea why its doing it.  I can make it crash 100% of the time.

I have tried reloading firefox 3 times and its not the plugin making it crash.

I am out of ideas.

nix4me

---

### Post by kairu0 on 2006-01-05
I recently upgraded to a newer version of Firefox 1.5 that doesn't have those blank Download progress windows anymore. Maybe we are working with different versions of the browser.

---

### Post by nix4me on 2006-01-05
Where did you get the browser from?

I downloaded mine from the mozilla website a week or two ago.

nix4me

---

### Post by kairu0 on 2006-01-05
Same place, 2 days ago.

---

### Post by nix4me on 2006-01-05
Nope, still crashes.  I just wiped everything mozilla off my system, reinstalled 1.07 from synaptic.  Installed mozilla-mplayer 3.17.  Went to mozilla.org and got new 1.5.  Installed in /opt and linked to my plugins.

Firefox 1.5 still crashes on that second video.  Crashes right when the dialog box pops up.

Firefox 1.07 seems to work now.  Plays the file in mplayer just fine.

nix4me

---

### Post by kairu0 on 2006-01-05
Can you post a directory listing of your plugins directory?

---

### Post by nix4me on 2006-01-05
libnullplugin.so        mplayerplug-in-qt.xpt  mplayerplug-in-wmp.so
mplayerplug-in-gmp.so   mplayerplug-in-rm.so   mplayerplug-in-wmp.xpt
mplayerplug-in-gmp.xpt  mplayerplug-in-rm.xpt  mplayerplug-in.xpt
mplayerplug-in-qt.so    mplayerplug-in.so

nix4me

---

### Post by jrib on 2006-01-05
Do you get any errors when it crashes if you run firefox from a terminal?  Also, if you download these files and play them locally with mplayer, do they play ok?

---

### Post by nix4me on 2006-01-05
This is the error from terminal.


checking to see if we need to make a button
n->url=ftp://ftp.motorcycle.com/pub/videos/Rolling_Burnout.mpg
url=ftp://ftp.motorcycle.com/pub/videos/Rolling_Burnout.mpg
href=(null)
/opt/firefox/run-mozilla.sh: line 131:  6606 Segmentation fault      "$prog" ${1+"$@"}


and yes, the files play fine when i download them.  This only happens when playing clips in Firefox.

nix4me

---

### Post by kairu0 on 2006-01-05
Under Edit -> Preferences -> Downloads -> View and Edit Actions, is MPEG set to open with the mplayer plugin?

---

### Post by nix4me on 2006-01-06
Mpg files play fine in the plugin.  Its the wmv file that causes firefox to crash.

That wmv that i posted does not play in the plugin because the mime type is misconfigured on the webpage.  Properly setup wmv's play fine.

Again, that wmv should, when clicked, should pop up a dialog box asking for a player.  My firefox just crashes.

nix4me

---

### Post by e^e on 2006-01-06
samething happens to me, firefox 1.5 and mplayer-plugin 3.17. Actually It crashes often due to viewing video. :???:

---

### Post by nix4me on 2006-01-06
I wish i could figure out why it does this.  I filed a bug report with mozilla.

nix4me

---

### Post by kairu0 on 2006-01-06
[QUOTE=e^e]samething happens to me, firefox 1.5 and mplayer-plugin 3.17. Actually It crashes often due to viewing video. :???:[/QUOTE]

I can open it successfully with mplayer-plugin 3.11 for the record.

---

### Post by nix4me on 2006-01-06
You mean, you have mplayerplug-in 3.11 installed and the video does not crash Firefox.  That video will not open in mplayerplug-in due to misconfigured mime setting on the webserver.

I am still at a loss.  I wish I could get 10 or so people to try this.

nix4me

---

### Post by kairu0 on 2006-01-06
[QUOTE=nix4me]You mean, you have mplayerplug-in 3.11 installed and the video does not crash Firefox.[/QUOTE]

Yeah, that's what I mean.

---

### Post by nix4me on 2006-01-07
If I un-install mplayerplug-in, Firefox does not crash.

So this is either an Ubuntu problem or possibly an mplayer problem, or gnome problem.

I will keep troubleshooting.

nix4me

---

### Post by codejunkie on 2006-01-07
[QUOTE=nix4me]If I un-install mplayerplug-in, Firefox does not crash.

So this is either an Ubuntu problem or possibly an mplayer problem, or gnome problem.

I will keep troubleshooting.

nix4me[/QUOTE]
i had tons of crashes with firefox and mplayer in my situation what helped was remove the mozilla-mplayer package in synaptic, all the totem plugins from my /usr/lib/mozilla-firefox/plugins directory then i compiled the latest mplayerplugin package from [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/) and instead of installing it systemwide i installed the plugins to my home directory in the ~/.mozilla/plugins dir and haven't had a crash since it's a little extra work but hey it's stable, don't know if this will help or not but i thought i'd add it just incase it does.
and the way i compiled the mplayer plugin is run
```
sudo apt-get build-dep mozilla-mplayer
```
```
sudo apt-get install mozilla-dev
```
extract the package and cd to the mplayerplugin dir and run
```

./configure
make

```
then from inside the mplayer dir run 
```
mkdir ~/.mozilla/plugins
```
if the directory already exists it will give an error just skip this step.
```
cp mplayerplug-in*.so mplayerplug-in*.xpt ~/.mozilla/plugins
```
```
cp mplayerplug-in.conf ~/.mozilla
```

---

### Post by nix4me on 2006-01-07
No joy.  Still crashes.

This is very frustrating.

If I uninstall mplayerplug-in all together, the links work just fine and Firefox does not crash.

Im starting to think this is a Gnome issue in Ubuntu.

nix4me

---

### Post by ryoko on 2006-01-16
In case this is not related sorry for posting off topic, but here goes.

Just to let you know this is not an isolated problem I am getting a similar issue when viewing video of any type.  I can watch video if I don't do anything while watching it.  By that I mean if I go full screen I get an instand crash.  If I hit back or change tabs I get a freeze and firefox gos to 99%cpu usage.  If I just let it play and stop then I can proceed to browse normally.  

Now correct me if I am wrong but to me this error says there is some bug with the gecko engine?

(Gecko:24809): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(Gecko:24809): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE
_CHECK_INSTANCE (instance)' failed

So maybe its a gecko gtk lib problem?

I am running:

FreeBSD barton.flcl.net 6.0-STABLE FreeBSD 6.0-STABLE #0: Fri Dec  9 00:45:13 EST 2005 

mplayerplug-in-3.17
firefox-1.5_5,1
xfce-4.2.3.2
gtk-1.2.10_13
gtk-2.8.9
gtk-engines2-2.6.6_1
gtk-xfce-engine-2.2.8
gtkglarea-1.2.3
gtkglarea-1.99.0_7
gtksourceview-1.4.2
gtkspell2-2.0.11_1
libgtkhtml-2.11.0
mplayer-gtk-esound-0.99.7_7
ocaml-lablgtk-1.2.5_1
ocaml-lablgtk2-2.6.0
py24-gtk-2.8.2
wxgtk2-2.6.2_1
wxgtk2-common-2.6.2


I use XFCE4 when uses gtk, but not Gnome.



Here is some terminal output:

%firefox
checking to see if we need to make a button
n->url=http://stream.qtv.apple.com/qtv/videoc/aaa/http/dres001/dres001_http_300_
ref.mov
url=http://stream.qtv.apple.com/qtv/videoc/aaa/http/dres001/dres001_http_300_ref
.mov
href=(null)
ADDED URL: [http://stream.qtv.apple.com/qtv/videoc/aaa/http/dres001/dres001_http_](http://stream.qtv.apple.com/qtv/videoc/aaa/http/dres001/dres001_http_)
300_300.mov
code: 82
 speed 38400
checking to see if we need to make a button
n->url=http://stream.qtv.apple.com/qtv/videoc/aaa/http/dres001/dres001_http_300_
300.mov
url=http://stream.qtv.apple.com/qtv/videoc/aaa/http/dres001/dres001_http_300_ref
.mov
href=(null)
ADDED URL: [http://a284.g.akamai.net/5/284/2941/4146e830/1a1a1aea59cf389d103eaf23](http://a284.g.akamai.net/5/284/2941/4146e830/1a1a1aea59cf389d103eaf23)
99c728980874d9076ad94675e251c730950837ad167adf4eb1e041a203329a0e82f22185f75ccfff
2f60/dres001_http_300_300.mp4
code: -76
 speed 38400

(Gecko:24809): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(Gecko:24809): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE
_CHECK_INSTANCE (instance)' failed

(Gecko:24809): Gtk-WARNING **: Can't set a parent on a toplevel widget

Segmentation fault (core dumped)
%

---

### Post by rado_london on 2006-01-16
I think it isnt a GNOME issue because the same thing happens when I use XFCE. Sometimes I get Firefox crashed even without watching movies.
This is odd but still Firefox is the best browser. 
By the way do you feel Firefox faster in Windows?

---

### Post by ryoko on 2006-01-16
Hold on there a sec!  The best browser?  Better than ie, but not dillo.  For the features and qualities I am looking for in a browser it is just not number one.  If dillo had a few select features I would not use firefox very much.  Quality is there on dillo, just not fine aged maturity and the benefits of a large fan base.  

Firefox has many more features than dillo, but there is some things it just better.  Cpu, memory foot print, and source/binary usage are way better on dillo.  

I have some complaints about firefox like taking 420MBs and a few hours to build, but the end user's experience is what I call the standard to judge others by.


As for speed differnces based on platform, I think most of the time it doesn't matter.  When I have adblock fully decked out my friends tell me how unbelievably fast  the internet is on my pc.  Without adblock I think the internet is slow no matter what the platform.

---

