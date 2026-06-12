---
title: "Script to download bing desktops?"
date: 2014-02-03
forum: Desktop Environments
---

### Post by timonoj on 2014-02-03
Hi! Does anyone know of a working script to download bing wallpapers daily? The one for gnome works perfectly, but not for KDE. For KDE I could only find one that requires Suse libraries...
Thanks!

---

### Post by Erik1984 on 2014-02-03
Do you have a link to that script for SUSE? Maybe it's not so hard to modify it so it no longer needs those specific libraries.

---

### Post by timonoj on 2014-02-03
Sure. The script comes in two files. The firs file is for gnome mostly, and if it needs KDE, it calls the second script for setting the wallpaper.
[https://github.com/marguerite/linux-bing-wallpaper](https://github.com/marguerite/linux-bing-wallpaper)

---

### Post by Erik1984 on 2014-02-03
Thanks. I don't know about SUSE but from quickly looking through the script files these lines seem to be specific for SUSE (zypper)

```

test -e /usr/bin/xdotool || sudo zypper --no-refresh install xdotool
test -e /usr/bin/gettext || sudo zypper --no-refresh install gettext-runtime

```

xdotool is also in the Ubuntu repositories as it seems. I can't find gettext-runtime but maybe gettext does the same.

So what you could try is comment out the above two lines and before running the script, do this first:
```
sudo apt-get install xdotool gettext
```

---

### Post by timonoj on 2014-02-03
> **Euroman said:**
> Thanks. I don't know about SUSE but from quickly looking through the script files these lines seem to be specific for SUSE (zypper)

```

test -e /usr/bin/xdotool || sudo zypper --no-refresh install xdotool
test -e /usr/bin/gettext || sudo zypper --no-refresh install gettext-runtime

```

xdotool is also in the Ubuntu repositories as it seems. I can't find gettext-runtime but maybe gettext does the same.

So what you could try is comment out the above two lines and before running the script, do this first:
```
sudo apt-get install xdotool gettext
```

Thanks a lot! I'm not in front of the computer, but I'll give it a shot and report when I can take a look!

---

### Post by Erik1984 on 2014-02-03
I tried it myself now and while it's easy to get around the zypper lines there are more problems. I had to modify both files in several places but it does work after that for my specific setup.

Here you can find my modified files:
[http://pastebin.com/Md0N0xYm](http://pastebin.com/Md0N0xYm)
[http://pastebin.com/GzRsuYdJ](http://pastebin.com/GzRsuYdJ)

btw if you only want this for KDE the script could be greatly simplified and you can cut out all DE determination stuff.

---

### Post by timonoj on 2014-02-03
Hi euroman, thanks a lot for your work.

I just ran it before going to work, and it hanged on
```

timonoj@Timo-PC:~/Pictures/bing$ bash ./bing_wallpaper.sh 
./kde4_set_wallpaper.sh: line 35: warning: here-document at line 23 delimited by end-of-file (wanted `_EOF')

```
I'll try to check that line myself a bit later, and thanks for the help!
Which system do you run on?

---

### Post by Erik1984 on 2014-02-04
I run Kubuntu 13.10. 

The script is really 'hackish', both the original and my additions. For example I changed qdbus to the full path /usr/lib/x86_64-linux-gnu/qt4/bin/qdbus because it won't work on my system otherwise. It's actually quite funny how the wallpaper is changed: first the script looks for the localized name of the "Deskop Shell Scripting Console", then it writes a script file to /tmp, opens the scripting programs and uses xdotool to simulate keypresses... Apparently (I spent some time Googling on how to change the wallpaper via commandline in KDE) this the only way to do this in KDE right now. In past versions of KDE it was possible to simply overwrite the wallpaper file with a cp command, not anymore.

Regarding your error: Maybe pastbin messed up indentation or something. I'll repost that part of the script:
```

js=$(mktemp)
cat > $js <<_EOF
var wallpaper = "$1";
var activity = activities()[0];
activity.currentConfigGroup = new Array("Wallpaper", "image");
activity.writeConfig("wallpaper", wallpaper);
activity.writeConfig("userswallpaper", wallpaper);
activity.reloadConfig();
_EOF

```
You have to make sure there are no trailing spaces after _EOF if I understand that construct correctly: [http://stackoverflow.com/questions/2500436/how-does-cat-eof-work-in-bash](http://stackoverflow.com/questions/2500436/how-does-cat-eof-work-in-bash) If I add a trailing space I get the same error as you quoted.

Regarding the 'hanging' part: That is intentional, I have removed that part myself. bing_wallpaper.sh contains an infinite loop and a sleep command. The script sleeps until the next day to fetch a fresh wallpaper from Bing. Of course that only makes sense if you leave your PC running 24/7 and this script is executed in the background (not occupying a terminal window).

edit: If you use Kate as your text editor it's easy to display trailing spaces: Settings > Configure Kate > Appearance > check "Highlight trailing spaces".

---

### Post by timonoj on 2014-02-04
Hahahaha, very good explanation!

Thanks for the correction, actually I had some tabs at the beginning of each line, it's fixed now. The bing image downloads to the folder correctly. However the hackish part fails. I believe xdotool actually fails to find the correct window, as it remains open and doesn't run the code. Nevermind, it did paste the code into the window, just didn't run and close it. I ran it myself.
It just runs and finishes with no errors, but no changes to the wallpaper:
> Executing script at 2014-02-04 21:39


Runtime: 57ms
Any way to debug this desktop shell? Never actually used it before.

---

### Post by Erik1984 on 2014-02-04
What is your locale (language setting)? It could be that xdotool looks for the wrong window name. The best way to debug the script is to let it echo the variables you are interested in. For example you could put ```
echo $JS_CONSOLE
``` before the xdotool line to see the window title it looks for.

Before I modified the script it failed to properly download and store the wallpapers. The downloaded wallpapers should be in $HOME/Pictures/Bing you can check if there are image files in that directory.

---

### Post by timonoj on 2014-02-05
Hi...so JS_CONSOLE is "Desktop Shell Scripting Console - Plasma Desktop Shell"...Still not sure how to fix this thing. At least here the file downloads correctly with no issues, but the setting as desktop part fails somehow. I think the plasma desktop shell doesn't actually pay attention to the xdotool input, as it doesn't show that it ran the script. But even running it there's no result :/

---

### Post by Erik1984 on 2014-02-06
Sorry to hear that, I really don't know why it doesn't work on your system. Do you have the standard keyboard layout (US international)? If I comment out the xdotool line and manually press ctrl + e (Execute) in the Desktop Shell Scripting Console my wallpaper is changed immediately.

---

### Post by timonoj on 2014-02-06
Well I have a Spanish (ES-ES) layout, although I use the US too. When I press Ctrl + E, it does run, it just doesn't change the wallapaper, nor do anything noticeable :/

---

### Post by Erik1984 on 2014-02-07
Really weird. Maybe your wallpaper settings are different so the script can't change it (just a guess). For what it's worth I made a screenshot of the scripting console and the wallpaper settings.

[[IMG]http://i.imgur.com/QtYDWRPl.png[/IMG]](http://imgur.com/QtYDWRP)

---

