---
title: "Making Gkrellm Transparent in KDE 4x"
date: 2010-12-19
forum: Desktop Environments
---

### Post by Laysan_A on 2010-12-19
Hi,
I'm a fan of Gkrellm. I'm also a fan of KDE. Unfortunately, though Gkrellm and KDE get along very nicely in a general way, there are two issues with it that I needed fixed, and want to share with the community (so hopefully some one else won't have to spend hours scouring the internet). The first issue (which is really secondary to this post) has to do with support for sensor output in Gkrellm, and it applies to all Ubuntu derivatives. I will be very brief about this. The second issue, and the main reason for this post, is that KDE 4x doesn't support transparent themes in Gkrellm. The non-transparent themes in Gkrellm are nice, in their way, but the general taste in looks is moving toward the transparent  look - esp. for utilities, like plasmoids, applets, and docks. Who doesn't like the look of a nice transparent widget? So, I'm going to share what I discovered about how to enable transparent themes on Gkrellm and KDE 4.[COLOR=Red]  **AND ASK FOR HELP WITH A PROBLEM FURTHER DOWN THE PAGE.**[/COLOR] ;)

First, though, about the sensors. Libsensors is THE program for gathering sensor data for use in various applets. Some few (mostly older) sensors have their output sent to a system file, where it can be picked-up and used by the system, but the best way to get sensor data, especially for newer sensor chips, is directly from libsensor.

Since 2007 libsensor support has been built out of Gkrellm in Ubuntu (perhaps all of Debian, though I'm unclear on that). From some cursory research on the internet, I discovered that in 2007 libsensors did a major update, and Gkrellm did not. Problems insued. Support for libsensors was dropped in Gkrellm. Even though a patch was produced fairly quickly, support for libsensors in Gkrellm was never re-allowed. There is a bug on this [ here.]("https://bugs.launchpad.net/ubuntu/+source/gkrellm/+bug/688944")

To enable support for libsensors in Gkrellm you have to build Gkrellm from source (EGADS!!) It's really pretty easy with this package and mine went off without a hitch (and I now have WONDERFUL readouts from my atk0110 sensors on my asus mb.). You can find the source package for Gkrellm [ here,]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html") and you can find some easy instructions for building it [ here.]("https://help.ubuntu.com/community/CompilingEasyHowTo")  Piece of cake (really!).
Okay, on to invisibility....

Gkrellm invisibility doesn't happen in KDE 4 (without a little tinkering...).



I discovered the fix by looking for insights in pages  discussing the same problem in conky. I found a good one, and thinking  the same situation might apply to gkrellm, I tried it and IT WORKED! [Here's the original post.]("http://everydaylht.com/howtos/eyecandy/conkykde-transparencymonitoring-remote-machines/")  My gratitude to the author. I'm going to reproduce the process here for  posterity's sake, and because the command has changed slightly with the  location of the plasma-desktop-appletsrc file.  

So, gkrellm  uses fake transparency. It samples the desktop at its coordinates and  reproduces the image as its background. Gkrellm doesn't use the user's  desktop to sample from - it uses the root desktop image - hence the  strange-looking colors I got whenever I tried one of the transparent  themes. 

Okay, so first you need to make your current desktop image your root desktop image. To do this you need to install "feh"  (copy and paste these commands into terminal)


```
sudo apt-get install feh
```After that's done, enter this in terminal:


```
feh --bg-scale "`grep 'wallpaper=' ~/.kde/share/config/plasma-desktop-appletsrc | tail --bytes=+11`"
```Okay,  now it needs to be set-up so that it'll load automatically. The feh  documentation recommends setting this in ~/.xsessionrc (if you don't  have one, make one with kate - and don't forget the dot before the name [IMG]http://kubuntuforums.net/forums/Smileys/classic/wink.gif[/IMG]  [ the expression ~/ is shorthand for your home directory path, /home/username, so the aforementioned path in full would be /home/username/.xsessionrc ]):


```
`cat $HOME/.fehbg`
```That  done, we arrive at a problem.[SIZE=3][COLOR=Red] **I could use some help here,**[/COLOR][/SIZE] if anyone has  any idea how to fix it. It's not a deal-breaker, but it's definitely  inconvenient if you like to change your wallpaper a lot.

The feh  program creates a file called ~/.fehbg to store the actual path of the  image used as 'wallpaper'. Unfortunately, it stores it like this:


```
feh --bg-scale '/home/laysan/Pictures/shadows_1280.jpg_cropped.png'
```The  two single quotes enclosing the path are unfortunately read as part of  the path, so when feh (or if it hands it off to bash or kde) looks for  the image file it can't find it. [IMG]http://kubuntuforums.net/forums/Smileys/classic/sad.gif[/IMG] You get a no such file error in feh. I created a bug report [ here.]("https://bugs.launchpad.net/ubuntu/+source/feh/+bug/691845")

The  only way I know of to fix it (I tried removing various sets of  quotation marks from the original feh command to no avail) is to open  the ~/.fehbg file in kate and remove the two single quotations, so it  looks like this:


```
feh --bg-scale /home/laysan/Pictures/shadows_1280.jpg_cropped.png
```But  you must still do one more thing. You must change the permissions on  ~/.fehbg to root, or the image's path will be overwritten the next time  it's opened (at next login), with the single quotes included. Doing so  fixes the issue in the short term, but when you change desktop images  you'll have to reinstate your user privileges on the file, and re-run  the original command to allow the file to be written to by feh (with the  new image path), then edit the file again to remove the single quotes.  Then you'll have to reset the root permissions (kind of a pain, huh?) 

I'm  not very good with bash, so the easiest way for me to change  permissions on a file or folder is to open dolphin as root, like this:


```
sudo dolphin
```Then  just right-click on the file, select properties, permissions, and  select and change appropriately. By the way, never use a rooted dolphin  for general file management or poking around - close it as soon as you  no longer need it (fair warning..[IMG]http://kubuntuforums.net/forums/Smileys/classic/wink.gif[/IMG] )

So  far, it has been set-up so that every login the current desktop image  is set to X root's desktop. This is because the actual path to the  current plasma desktop image is listed in .fehbg. When the desktop image  changes, the X root desktop image will stay the same (and so the  Gkrellm background) unless the original bash command is re-run to set  the path for the new plasma desktop image in .fehbg.

For me, the  best way to do this was to create a bash script, place it my home  directory (where I wouldn't lose it), and make a menu shortcut for it,  including assigning an icon (so I wouldn't forget what or where it was).

All that's required for this simple script is to open kate and paste this:


```
#!/bin/bash

exec feh --bg-scale "`grep 'wallpaper=' ~/.kde/share/config/plasma-desktop-appletsrc | tail --bytes=+11`"
```Then  save it in your home dir. as whatever name you want, with a .sh  extension. I called mine TransparentGkrellm.sh You can test that it  works by dragging it into an open terminal. If your .fehbg file is still  set to root, you'll get an error message that feh was unable to write  to the .fehbg file. That means it worked as expected. To make  TransparentGkrellm executable, you need to select it in dolphin,  right-click and select properties, and tic make executable. Now you can  click on it and it will run. 

If I knew anything about scripting,  I could automate the entire process of establishing the new root image  and removing the single quotes from the .fehbg file, so the whole  process would require a single click. Unfortunately, establishing the  new image is all I get, for now. (Could use some help here! [IMG]http://kubuntuforums.net/forums/Smileys/classic/wink.gif[/IMG] )

To  put TransparentGkrellm in the menu, open the menu editor (right-click  on the menu icon - or if you're using Lancelot, open the menu and click  on the Lancelot icon in the upper right corner) and decide on a  category. I put mine in settings. Select the category, then select new  item. Type in the name, comment and description (make it descriptive  enough that you will not forget what it does). In the command block  place the full path and name (~/TransparentGkrellm.sh). If you click on  the blank icon image you can choose a nifty icon for it. I chose one  from the settings manager for setting the desktop image  (appropriate...). Click to save the new settings and that's it!

Well...my  two desktop images weren't quite aligned...the root image was set with  bg-scale, which I assume is the same as the scale option in plasma. I  had my plasma desktop set to scale (keep proportions), which ended-up  being slightly different. I changed it to scale and voila, they matched  (If for some reason your desktop doesn't look good in scale mode try  "feh --help", or "man feh" in terminal for some options). Now the issues  are fine-tuning the appearance. One thing I will say about that  concerns the window type. In dock or panel mode (set in gkrellm) the  window stays above normal windows (although you may be able to change  that in special window settings - have to try and see). This is not  desirable, even though it looks better right off the bat, because of the  fake transparency. In normal window mode, even when "no borders" is  selected in the window management dialogue, there is still a shadow  under the window, making it stand out too much for my taste. This, too,  may be addressable in special window settings. The important thing now  is...it works, and without too much trouble.

Edit:

Okay, I  got the results I wanted by setting the window type in gkrellm to be  dock or panel, then selecting to force below other windows in special  window settings in kde.  [Here's the final result.]("http://img837.imageshack.us/img837/5738/desktoptransgkrellm2122.png")  The theme is "invisible-jkx". I found it on some guy's site ([Here it is]("http://www.larsen-b.com/tags/gkrellm")).  Anyway, except for the two invisible themes (black and white) from  kde-look (which don't work for some reason), all the transparent themes  work.

Also, for anyone not very familiar with gkrellm:

You  can change the width of Gkrellm in the gkrellm configuration dialogue (right click  in the little button that appears near the top) in General, Options.

You can change the height of any of the charts by right-clicking on the chart (mine are mostly at 15).

You can change the height of gkrellm (it'll vary considerably depending on the theme) by going to Themes, Options, Scale.

You can also globally change the fonts, also in Themes.

---

### Post by mckooper on 2011-01-27
Here's another option:

There's a nifty kde plugin that lets you set the wallpaper using a script

[http://kde-look.org/content/show.php/Scripted+Image+Wallpaper+Plugin?content=115147](http://kde-look.org/content/show.php/Scripted+Image+Wallpaper+Plugin?content=115147)

Here's the script I'm using which selects a random image from a directory, uses feh to set the root image and then returns the image filename for KDE:

```

#!/bin/bash

_imagedir=/home/user/pictures/desktops/
_image=${_imagedir}$(ls "$_imagedir" | shuf -n1)

feh --bg-max "$_image"
echo "$_image"

```The plugin allows you to run the script on a timer, so every XX minutes you get a new background, the root is updated automatically and gkrellm looks perfect!

FYI, the "--bg-max" feh option seems to correspond nicely to the "Scaled, keep proportions" option in KDE.

---

### Post by Laysan_A on 2011-01-27
Very cool!
(I may not use it - I'm really kind of a stick-in-the-mud, and don't tend to change things much, but it's nice to know it's there). :)

What's your .fehbg file look like, anyway?

---

### Post by mckooper on 2011-01-29
Nothing interesting in .fehbg - don't need it or .xsessionrc!  The root image is automatically set (and updated) by kde through that plugin.

---

### Post by Laysan_A on 2011-01-29
Well, thanks for responding. :)

---

### Post by Frank64 on 2011-08-01
Well I know this is old, but I couldn't try before.

I could not install that plug-in, as there is an error in cmake.

So I just ran the script suggested above and it seems to load the picture, cuz it returns no error and the filename/path.

```
frank12.1@linux-r94t:~/wall> sh wall.sh
/home/frank12.1/wall/image/default-1600x1200.jpg

```

But then I load gkrellm and the picture does not set, it's the normal dark gray default background.

Not sure what I'm missing?

---

### Post by Laysan_A on 2011-08-05
Hi Frank64,

I can't tell from your description whether or not you've done everything, but I'm going to assume you have....

I'm thinking the problem is with this area of my description:

> The feh  program creates a file called ~/.fehbg to store the actual path  of the  image used as 'wallpaper'. Unfortunately, it stores it like  this:


 	Code:
 	feh --bg-scale '/home/laysan/Pictures/shadows_1280.jpg_cropped.png' 
The  two single quotes enclosing the path are unfortunately read  as part of  the path, so when feh (or if it hands it off to bash or kde)  looks for  the image file it can't find it. [IMG]http://kubuntuforums.net/forums/Smileys/classic/sad.gif[/IMG] You get a no such file error in feh. I created a bug report [ here.]("https://bugs.launchpad.net/ubuntu/+source/feh/+bug/691845")

The  only way I know of to fix it (I tried removing various sets of   quotation marks from the original feh command to no avail) is to open   the ~/.fehbg file in kate and remove the two single quotations, so it   looks like this:


 	Code:
 	feh --bg-scale /home/laysan/Pictures/shadows_1280.jpg_cropped.png 
But  you must still do one more thing. You must change the  permissions on  ~/.fehbg to root, or the image's path will be  overwritten the next time  it's opened (at next login), with the single  quotes included. Doing so  fixes the issue in the short term, but when  you change desktop images  you'll have to reinstate your user privileges  on the file, and re-run  the original command to allow the file to be  written to by feh (with the  new image path), then edit the file again  to remove the single quotes.  Then you'll have to reset the root  permissions (kind of a pain, huh?) 

So check your .fehbg file to see if the single quotes around the path are there, and if they are remove them. Then try ```
cat $HOME/.fehbg
``` in terminal to load the image in feh. If it's set-up properly that should give you the proper background for gkrellm. You'll then need to change the permissions on the .fehbg file so it's not written over at your next log in when the x-wallpaper is reset.

Hopefully, I guessed right...

---

### Post by Frank64 on 2011-08-10
Hi laysan, tnx for replying.

Cat loads files? I thought it was just to display on-screen the content of a file.

I did the command

```
frank12.1@linux-r94t:~> cat $HOME/.fehbg
feh  --bg-max /home/frank12.1/wall/image/default-1600x1200.jpg
```

Then loaded gkrellm and no change in background.

Do I need 3D acceleration or openGL or composite or something to be enabled? I am trying this under VBox at the moment.


I have also tried the following command

```
frank12.1@linux-r94t:~> _imagedir=/home/frank12.1/wall/image/
frank12.1@linux-r94t:~> _image=${_imagedir}$(ls "$_imagedir" | shuf -n1)
frank12.1@linux-r94t:~> 
frank12.1@linux-r94t:~> feh --bg-max "$_image"
frank12.1@linux-r94t:~> echo "$_image"
/home/frank12.1/wall/image/default-1600x1200.jpg
frank12.1@linux-r94t:~>

```

It seems to work, I get no error. But loading gkrellm after does not change background.

Am I supposed to tell gkrellm to use this as background? I mean why gkrellm would change background (when it works :)) but not Firefox, KTorrent, K3B and any other application you load?

---

### Post by Laysan_A on 2011-08-13
Hi Frank64,

You'll have to pardon me, you're probably right about the cat command - I don't really know bash at all...

What happens (I'm assuming nothing happens) when you enter (Don't change anything):
```
feh --bg-scale "`grep 'wallpaper=' ~/.kde/share/config/plasma-desktop-appletsrc | tail --bytes=+11`"
```
You may just need to get rid of the bg-max option - try bg-seamless instead (other allowed options can be found in the terminal by entering "feh --help" (no quotes). Bg-max seems not to be a proper option currently. 

Copy your output from the cat command and paste it at the prompt and run it. Something interesting happened to me when I tried: Each word of the path to my image file was parsed as a separate file. Until I put back the original 'file name path' single quotes, feh couldn't find it. So maybe the developer fixed the problem in feh that necessitated all the rigamarole with editing and file permissions - but then that would break the installation as I've described it. However, running the command above should still set the wallpaper initially.

If you're not getting an image, perhaps your path to 'plasma-desktop-appletsrc' is incorrect. You might want to physically verify it. You might also want to verify that the image you have set as your desktop is actually in there. As I recall (I've got too much going on right now to disable my feh set-up and restart), running the initial command should set the image for that session even if it cannot write to the .fehbg file because it's protected - but you could always delete your .fehbg and run it. 

As for the other script you mentioned, that one is for use with the plugin mckooper recommended and I don't know what effect it may be having on your image selection with feh without the plugin installed. But I'm not surprised it doesn't work.

---

### Post by Laysan_A on 2011-09-04
Okay, for those (few) of you who may access this topic looking for guidance, I have a small admission to make. This is going to sound really scatter-brained (in fact it is... I'm scatter-brained.), but it seems that my .xsessionrc isn't working, and it hasn't been working for some months now. 

Understand, this is all a bit hazy to me (scatter-brained, remember?), but some months ago, I seem to recall logging-in and Gkrellm wasn't transparent. I was in the middle of something else (who knows...), so I checked my files really quickly and they were there (I'm sorta' making this up, because I don't absolutely remember doing this - but it feels right, so I'm standing by it), so I went into Lancelot and clicked my menu entry for Transparent Gkrellm (which if you remember points to a script I made and placed in Home, called TransparentGkrellm.sh) and voila! Gkrellm was transparent. So I just opened my KDE System Settings utility and went to the Advanced tab and opened Auto Start, and placed an entry there for TransparentGkrellm.sh (use the Add Script dialog), and set it to run at start-up. Problem solved. The details are hazy, but I'm pretty sure that's how it went down, and I quickly forgot about it entirely (sorry).

I don't have the slightest idea why .xsessionrc isn't working right now. Frankly, I'm not a big tinkerer, I don't have much of a background in programming, and none at all in Linux, so basically, as long as it works I'm happy. This isn't the first time .xsessionrc has stopped working, and if you want to fiddle with it, [here's a thread]("http://ubuntuforums.org/showthread.php?t=1505568") about fixing .xsessionrc from a year or so ago on a Gnome system.

---

