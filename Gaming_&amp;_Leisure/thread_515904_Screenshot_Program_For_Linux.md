---
title: "Screenshot Program For Linux?"
date: 2007-08-02
forum: Gaming &amp; Leisure
---

### Post by fatsheep on 2007-08-02
I want to do a review of Tremulous and something like FRAPS would be really nice so I could press a button and have a screenshot saved to a certain folder.  And you can't ALT + TAB out of Tremulous either so I'd have to exit each time I took a screenshot with Print screen.  Does such a program exist?

---

### Post by hikaricore on 2007-08-02
[RecordMyDesktop]("http://recordmydesktop.iovar.org/")?

Should be in the universe repos.  ^_^

```
sudo aptitude install gtk-recordmydesktop
```

Otherwise you can get it in this repo for sure:


> # Trevino's Ubuntu Fesity Repository
# Further informations: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0

---

### Post by dannyboy79 on 2007-08-02
if you're talking about an actual "capture of a still image" versus "capturing moving stuff" than all you have to do is hit your Print Screen button on your keyboard, this will bring up a dialog box where to save the .png file and what to name it. that by default takes a pic of the entire screen not just the active window. there's a way to change that but I am not sure off the top of my head.

---

### Post by ajgreeny on 2007-08-02
> that by default takes a pic of the entire screen not just the active window. there's a way to change that but I am not sure off the top of my head.
It's Alt+Print Screen for the active window.

---

### Post by fatsheep on 2007-08-02
> **hikaricore said:**
> [RecordMyDesktop]("http://recordmydesktop.iovar.org/")?

Should be in the universe repos.  ^_^

```
sudo aptitude install gtk-recordmydesktop
```

Otherwise you can get it in this repo for sure:

That's a neat screen capture program but what I was looking for was capturing a still image and saving it to a directory at the push of a button.

> **dannyboy79 said:**
> if you're talking about an actual "capture of a still image" versus "capturing moving stuff" than all you have to do is hit your Print Screen button on your keyboard, this will bring up a dialog box where to save the .png file and what to name it. that by default takes a pic of the entire screen not just the active window. there's a way to change that but I am not sure off the top of my head.

Okay but then I have to close out of Tremulous and click the "Save" button every single time I want to save a screenshot.  What I want to be able to do is go along, find an interesting screenshot, hit a certain button to save that screenshot and then keep on playing.

---

### Post by hikaricore on 2007-08-02
I'm amazed to be honest that Tremulous doesn't have an internal screenshot function.

Most fps games have since back in the day when Doom came out.

---

### Post by jfinkels on 2007-08-02
Try the program 'scrot':```
sudo aptitude install scrot
```and read about it with:```
man scrot
```it has lots of fun functionality.

---

### Post by Nythain on 2007-08-03
scrot is the answer to all your problems... install it... read up on how to use it... and write a simple script for it (you can read the thread "Fluxbox Fast and Cool" for a few different scripts varying from scrot to imagemagick) bind the script to some key you dont ever really use, like oh say pause break, and voila... my script looks like this
```

#!/bin/bash

DIR="${HOME}/screenshots"
DATE="$(date +%Y%m%d@%H%M%S)"
NAME="${DIR}/screenshot-${DATE}.png"
LOG="${DIR}/screenshots.log"

# Check if the dir to store the screenshots exists, else create it: 
if [ ! -d "${DIR}" ]; then mkdir "${DIR}"; fi 

# Screenshot a selected window
if [ "$1" = "win" ]; then import "${NAME}"; fi

# Screenshot the entire screen
if [ "$1" = "scr" ]; then import -window root "${NAME}"; fi

# Screenshot a selected area
if [ "$1" = "area" ]; then import "${NAME}"; fi

if [[ $# = 0 ]]; then
  # Display a warning if no area defined
  echo "No screenshot area has been specified. Screenshot not taken."
  echo "${DATE}: No screenshot area has been defined. Screenshot not taken." >> "${LOG}"
else
  # Save the screenshot in the directory and edit the log
  echo "${NAME}" >> "${LOG}"
fi

```
and i believe requires imagemagick to be installed... i just put that into a text file... named it screenshot and made it executable, dropped it into /usr/bin and bound it to two keys... one for win and one for scr

its called by typing
screenshot scr
for the entire screen
or
screenshot win
for the active window
there are no annoying popups asking to save teh file or anythign that would pull you out of the game so it should work

note: i would highly recommend just going the scrot route though... its much easier and you can find tons of scripts using it on these forums

---

### Post by Qwerty_ on 2007-08-03
> **hikaricore said:**
> I'm amazed to be honest that Tremulous doesn't have an internal screenshot function.

Most fps games have since back in the day when Doom came out.


It does I am pretty sure that f10, f11 or f12 lets you screenshot

If not go into the console (`) and type /bind <key> screenshotjpeg

then when you press that key it will take a screen shot and save it to /home/user/.tremulous/base/screenshots

Also you can Alt+tab trem...

All you have to do is hit Alt+Enter then open up the conolse  and you can take the mouse out of the game.

Hope that helps. Avid trem player.

Might want to take a look at my trem skills programme I ran

[http://www.the1qwerty.com/trem-skills/](http://www.the1qwerty.com/trem-skills/)

Hope everything helps.

---

### Post by dannyboy79 on 2007-08-03
> **fatsheep said:**
> That's a neat screen capture program but what I was looking for was capturing a still image and saving it to a directory at the push of a button.



Okay but then I have to close out of Tremulous and click the "Save" button every single time I want to save a screenshot.  What I want to be able to do is go along, find an interesting screenshot, hit a certain button to save that screenshot and then keep on playing.

As I said, I believe you can change the prefs so that it just names the file for you and stores it in a certain spot. I am nto aware of how to do that but obviously if currently the print screen button can bring up a dialog for where to save it and what to name it than it can be changed somehow.

---

### Post by Sindwiller on 2007-08-03
> 
I'm amazed to be honest that Tremulous doesn't have an internal screenshot function.

Open Console with key "^" (or shift+^ or something like that, really depends on layout, you can also edit your autoexec.cfg)

```
set F12 screenshot
```

Then check in your ./tremulous/base/screenshots directory...

---

### Post by fatsheep on 2007-08-03
oops.. double post...

---

### Post by fatsheep on 2007-08-03
I have used Tremulous' inbuilt screenshot feature but the screens it outputs are far too dark.  I play Tremulous with the Brightness bar all the way up (the only way to play it to be honest.  if I don't turn it all the way up it's pitch black, can't see a thing...) and when I take a screenshot it's as is the Brightness has been turned all the way down. :/

> **Nythain said:**
> ...
i just put that into a text file... named it screenshot and made it executable, dropped it into /usr/bin **and bound it to two keys...** one for win and one for scr

...

How do you bind keys?  I can figure out scrot from the man page but I can't seem to find a good way to bind keys.  Thanks,

- sheep

---

### Post by hikaricore on 2007-08-03
Just a suggestion, save yourself the trouble and use GIMP to change the brightness and contrast of your screenshots.

Using another screenshot program probably will not be any better as they both grab the same image.

---

### Post by fatsheep on 2007-08-03
> **hikaricore said:**
> Just a suggestion, save yourself the trouble and use GIMP to change the brightness and contrast of your screenshots.

Using another screenshot program probably will not be any better as they both grab the same image.

I did that but it still distorts the image and it turns out really ugly.

---

### Post by hikaricore on 2007-08-03
> **fatsheep said:**
> I did that but it still distorts the image and it turns out really ugly.

Sorry I guess I underestimated the extent of the dark images. >.<

Hopefully someone can help you with the keybinding issue and it works out after that.

---

### Post by fatsheep on 2007-08-03
> **hikaricore said:**
> Sorry I guess I underestimated the extent of the dark images. >.<

Hopefully someone can help you with the keybinding issue and it works out after that.

Yea NP.  I just bound scrot to the F2 key using xbindkeys and xbindkeys-config (xbindkeys-config is a life saver).  I will try taking a screenshot inside tremulous now.  I'll post back later.

EDIT: This works outside of tremulous but not inside!  Not even when I run Tremulous in a window...  ??  How do I bind keys so they will work in Tremulous?

---

