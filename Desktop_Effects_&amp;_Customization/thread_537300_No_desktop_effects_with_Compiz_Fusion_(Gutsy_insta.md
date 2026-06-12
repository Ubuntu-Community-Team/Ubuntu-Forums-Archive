---
title: "No desktop effects with Compiz Fusion (Gutsy install)"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by mdoyle on 2007-08-28
Alright, so I have an install of Gutsy with all the latest updates. Compiz is installed and running. I have the CompizConfig Settings Mananger in my System -> Preferences menu. The effects that I want enabled have a check mark next to them, but none of them work. I'm new to Ubuntu and especially Compiz, just trying to get them to work correctly. Where do I start?

---

### Post by dougfractal on 2007-08-28
> glxinfo | grep direct
> 
compiz --replace  | tee output.txt &

post output.txt

---

### Post by mdoyle on 2007-08-28
For the first one

> direct rendering: Yes

Second

> ~$bash: compiz-replace: command not found

---

### Post by mdoyle on 2007-08-28
Also, from the Appearance Preferences screen, trying to enable Desktop Effect Extra gives me the error "Desktop effects could not be enabled".

I have an Nvidia 9750 with the correct drivers working. Dual monitor with one screen rotated 90 degrees.

---

### Post by duanarmy on 2007-08-29
im kind of having that same problem....I tried to install compiz and it says its already installed...but when i go to -System> Preferences menu CompizConfig Settings Mananger is not in there...any ideas

---

### Post by dougfractal on 2007-08-29
copy & paste a marvelous thing. no typos!!!  Look at my tag, use the mouse ;-)

compiz-replace **!=** compiz --replace

> 
compiz --replace  | tee output.txt &

post output.txt

---

### Post by mdoyle on 2007-08-29
"/usr/bin/compiz: line 777: 23646 Segmentation fault (core dumped) $*"

With nothing in the text file.

---

### Post by dougfractal on 2007-08-29
I need to know more about your setup.
Run this script.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by mdoyle on 2007-08-29
Here it is.

---

### Post by dougfractal on 2007-08-29
remove Treviño's repos from sources.list as gutsy comes with CF.
> 
sudo apt-get --purge remove compiz* libcompizconfig*
sudo apt-get install compiz compizconfig-settings-manager


and
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
>   Install Compiz-fusion tray icon via .deb
    What is Compiz-fusion tray icon?
          o

            [WWW] [http://tomdryer.com/blog/index.php/2007/08/26/compiz-fusion-tray-icon/](http://tomdryer.com/blog/index.php/2007/08/26/compiz-fusion-tray-icon/)
    *

      Where can I download it?
          o

            [WWW] [https://help.ubuntu.com/community/CompositeManager/CompizFusion?action=AttachFile&do=get&target=fusion-icon_1.0-1_i386.deb](https://help.ubuntu.com/community/CompositeManager/CompizFusion?action=AttachFile&do=get&target=fusion-icon_1.0-1_i386.deb)

Double-click to install the .deb. 

---

### Post by mdoyle on 2007-08-29
Effects still don't work and now i've lost the ability to close windows, minimize and maximize them from the menu bar. And programs that are open dont show up in the bottom panel.

---

### Post by dougfractal on 2007-08-29
forgot to say update repos with **sudo apt-get update  **
> 
sudo apt-get update     #  update the repos
sudo apt-get --purge remove compiz* libcompizconfig*
sudo apt-get install compiz compizconfig-settings-manager


then 
> metacity --replace
compiz --replace

fail that logout/login

---

### Post by mdoyle on 2007-08-29
When doing compiz --replace

"/usr/bin/compiz: line 777: 31072 Segmentation fault     (core dumped) $*"

Even after restart

---

### Post by dougfractal on 2007-08-29
Can I just check this 

grep 3v1deb /etc/apt/sources.list
aptitude search ~icompiz  -F "%20p %10v %10V %20d"

i have 
```
compiz                       1:0.5.2+gi 1:0.5.2+gi OpenGL window and compositing
compiz-core                  1:0.5.2+gi 1:0.5.2+gi OpenGL window and compositing
compiz-fusion-plugins-extra  0.5.2+git2 0.5.2+git2 Collection of extra plugins f
compiz-fusion-plugins-main   0.5.2-0ubu 0.5.2-0ubu Collection of plugins from Op
compiz-gnome                 1:0.5.2+gi 1:0.5.2+gi OpenGL window and compositing
compiz-plugins               1:0.5.2+gi 1:0.5.2+gi OpenGL window and compositing
compizconfig-settings-manage 0.5.2+git2 0.5.2+git2 Compiz configuration settings
libcompizconfig-backend-gcon 0.5.2+git2 0.5.2+git2 Settings library for plugins 
libcompizconfig0             0.5.2-0ubu 0.5.2-0ubu Settings library for plugins 
python-compizconfig          0.5.2-0ubu 0.5.2-0ubu Compiz configuration system b
d
```

---

### Post by mdoyle on 2007-08-29
Mine
 
```
compiz                       1:0.5.2+gi 1:0.5.2+gi OpenGL window and compositing
compiz-core                  1:0.5.2+gi 1:0.5.2+gi OpenGL window and compositing
compiz-fusion-plugins-extra  0.5.2+git2 0.5.2+git2 Collection of extra plugins f
compiz-fusion-plugins-main   0.5.2+git2 0.5.2+git2 Collection of plugins from Op
compiz-gnome                 1:0.5.2+gi 1:0.5.2+gi OpenGL window and compositing
compiz-plugins               1:0.5.2+gi 1:0.5.2+gi OpenGL window and compositing
compizconfig-settings-manage 0.5.2+git2 0.5.2+git2 Compiz configuration settings
libcompizconfig-backend-gcon 0.5.2+git2 0.5.2+git2 Settings library for plugins 
libcompizconfig0             0.5.2+git2 0.5.2+git2 Settings library for plugins 
python-compizconfig          0.5.2+git2 0.5.2+git2 Compiz configuration system b

```

---

### Post by dougfractal on 2007-08-29
Edit:   I've now updated
[COLOR="DimGray"]there's a slight difference
QUOTE:
compiz-fusion-plugins-main   0.5.2-0ubu 0.5.2-0ubu Collection of plugins from Op
 libcompizconfig0             0.5.2-0ubu 0.5.2-0ubu Settings library for plugins 
python-compizconfig          0.5.2-0ubu 0.5.2-0ubu Compiz configuration system b[/COLOR]


and try 
> sudo apt-get install nvidia-glx-new

---

### Post by mdoyle on 2007-08-29
That last command destroyed my xorg.conf file. I had to manually delete a few lines that it added that wouldn't allow my system to boot.

Now, when I do compiz --replace I get

Checking for Xgl: not present
Checking for texture_from_pixmap: present
Checking for no power of two support: present
Checking for Composite extension: present
Checking for nVidia: present
Checking for Xgl: not present

Gdk-ERROR **:The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 338 error_code 181 request_code 157 minor_code 8)

---

### Post by dougfractal on 2007-08-29
> That last command destroyed my xorg.conf file
:-s

nvidia tend to create a backup. + from the ~/Xinfo folder

what did it add to the xorg.conf?

I don't know why it works for me and not you.

Your using    "Xinerama" "1"  
try twinview or 2 seperate screens?

> 

Gdk-ERROR **:The program 'gtk-window-decorator' received an X Window System error.
gtk-window-decorator --replace --sync &

---

### Post by mdoyle on 2007-08-29
I don't remember what it added, I just took a mental note of it then deleted the lines.

Now TwinView is on and it still isn't letting me enable desktop effects.

Edit: Actually TwinView isn't on. I turned it on, restarted X, and it went right back to Xinerama.

---

### Post by mdoyle on 2007-08-29
Ok, I got TwinView to start, Compiz still doesn't work, and now my dual monitors aren't setup correctly anymore. I'm going back to the old xorg.conf file.

I should be able to get Compiz running even though i'm using Xinerama, shouldn't I? I don't get it.

---

### Post by dougfractal on 2007-08-29
> I should be able to get Compiz running even though i'm using Xinerama, shouldn't I? I don't get it.  Yes

It was worth testing.

you could try xgl. I find it better than aiglx, more responsive. but you've got better frame rate than me, so you might not get the popup delay.

for xgl follow  
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

but still CF runs for me on XGL and aiglx

[http://www.nvnews.net/vbulletin/showthread.php?t=96458](http://www.nvnews.net/vbulletin/showthread.php?t=96458)   (a bit dated?)
> 
    $ export DISPLAY=:0

for example. However, if everything goes well, it should be fine to start it from a terminal window.

If you are using a version of compiz that supports the Composite Overlay Window:


    $ gnome-window-decorator &
    $ compiz --replace --use-cow gconf

Otherwise:


    $ gnome-window-decorator &
    $ compiz --replace gconf

At this point, the screen may flicker a bit, then all your windows should reappear. If everything looks good, you can set up compiz to start at X start time via your favorite method.


Common problems:

    * If you get a black screen, be sure you are either using --use-cow option, or set the DisableGLXRootClipping NVIDIA X driver option in your X configuration file.

    * If you are using an old version of compiz and it prints out a message about not being able to bind a pixmap to a texture (or, if you are running it from an X terminal and you just see a blank screen), compiz is most likely incorrectly linked against a Mesa implementation of OpenGL. You should verify compiz is linked against the NVIDIA OpenGL libraries. This can be done by running...


          $ ldd `which compiz`

      ...and ensuring the output contains the library libnvidia-tls.so.1. Only the NVIDIA OpenGL drivers should link in this library, so if you see it, your linking is correct. If not, you will need to rebuild compiz, ensuring it links against the NVIDIA version of libGL.so.

    * If you are using compiz-quinnstorm or a version of compiz from compiz.net and compiz crashes with a segmentation fault on startup, the most likely reason for this also is that it was linked against a Mesa version of libGL.so. Please see the last bullet item for details.

    * If you are not using the Composite Overlay Window, you may get bits of black corruption when moving windows around. This is a known bug we have not yet resolved, but it can be worked around be either upgrading to a version of compiz that supports the Composite Overlay Window, or disabling the sync_to_vblank compiz option.

    * If you are seeing intermittent performance problems such as hickups, setting the __GL_YIELD environment variable to "NOTHING" in compiz's environment may help, e.b. by running...


          $ gnome-window-decorator &
          $ export __GL_YIELD="NOTHING"; compiz --replace --use-cow gconf

      Please be sure that you are not using compiz 's --indirect-rendering option in this case.

---

### Post by dougfractal on 2007-08-29
ccsm
prefences>profile>reset to defaults

---

### Post by mdoyle on 2007-08-29
When ever I run any of those commands I get the same thing I was getting before with compiz --replace.

XGL doesn't load either from the Sessions when I log out and log back in. It gives me an error saying my session lasted less than 10 seconds. And forces me to log in under Gnome again.

I reset all my preferences also, still doesn't do anything.

---

### Post by dougfractal on 2007-08-29
> cat ~/.xsession-errors
cat /var/log/Xorg.1.log

I think it might be a driver thing rather than compiz?
> 
ldd  /usr/bin/compiz.real

---

### Post by mdoyle on 2007-08-30
That first one gave me a list of errors, anyway I can have it output to a text file so that it's easier to post?

The second said that that file doesn't exist.

The third also gave me a huge list that I need to post.

---

### Post by dougfractal on 2007-08-30
> $ ldd /usr/bin/compiz.real
...and ensuring the output contains the library libnvidia-tls.so.1. Only the NVIDIA OpenGL drivers should link in this library, so if you see it, your linking is correct. If not, you will need to rebuild compiz, ensuring it links against the NVIDIA version of libGL.so.

but as you didn't build compiz I guess this wont help.

cat ~/.xsession-errors > errors.txt

you could also try

> sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx nvidia-glx

---

### Post by Meson on 2007-10-21
Hey, what's the status of your problem?  Have you been able to get the Desktop Effects working with Xinerama?  So far I am only able to with TwinView or just declaring two screens with Xinerama off.  Also, I don't really want to use TwinView because my login screen is showing up on the wrong monitor.  Xinerama seems to handle things better.

---

### Post by tmtmy on 2007-10-21
Compiz was working fine for me on feisty but once upgraded to gutsy, compiz fails to work. 

Here's my compiz output:

[HTML]tmtmy@tmtmy:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
[/HTML]

So...where should I start from to get it working again?

---

### Post by Meson on 2007-10-21
I've made made some serious progress.  Are you deadset on using Xinerama?  Have you considered TwinView?  I'm now using TwinView and I am able to get both monitors oriented correctly, login screen on the correct monitor, and desktop effects on both monitors.

---

