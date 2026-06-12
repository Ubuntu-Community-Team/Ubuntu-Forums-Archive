---
title: "Scripting changes to effects"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by Arcnsparc on 2008-01-04
Im using Gutsy on a R60 with compiz for my effects. 
Since Compiz doesn't always get along with other programs I wanted to hotkey it to turn off.  I found a bash command that would do it _metacity --replace_ and that works fine, but then I got greedy and decided to make my VERY FIRST SCRIPT to change the background and the colors & transparency of the top & bottom panels.
I found_ gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/image.ext"_ to change the back ground.

Now I need is the command to change the panel(I think that is what its called, its the top launch bar and the bottom "task-bar" -ish thing, pardon my xp)

Lastly I was hoping a script wouldn't be too hard, it is a text file with the commands to be done similar to GRUB's menu.lst which I worked with a bunch, right?
This is what I have for a script so far, will it work if I assign a hot key to it?

#turn off compiz
metacity --replace

#Change Background to a dark wallpaper
## I don't know if I need these quotes at the end or not either....
#Original Command: gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/image.ext"

gconftool-2 --type string --set /desktop/gnome/background/Light "/home/jake/Documents/Ubuntu/Wallpapers.ext"

#Adjust top and bottom panels to be dark and opaque
#Top Dark

#Top Opaque

#Bottom Dark

#Bottom Opaque

#end



I hope this is going to work, I will do pretty much the opposite to change everything back to the other way I had it.  I really appreciate any feedback as I could understand that this is a pain in the rear question.  Thanks in advance!

---

### Post by Arcnsparc on 2008-01-04
Two more things, sorry...

I thought [U]metacity --compiz[U] would turn compiz back on but it wouldn't so i tried to find another command and found [U]replace --compiz[U] which required me to install the "replace" program, I did that, but as it downloads on my very slow connection i wonder if that was a bad idea...

And second, is there a depot of commands to tweak the interface & looks via script or terminal?

---

### Post by Arcnsparc on 2008-01-04
I just can't stop adding on to this thing can I?  I found that "replace" belongs to  mysql-server-5.0, and is not what i wanted, so im going to uninstall it, nevermind about that thing.

---

### Post by coffen on 2008-01-06
> **Arcnsparc said:**
> I just can't stop adding on to this thing can I?  I found that "replace" belongs to  mysql-server-5.0, and is not what i wanted, so im going to uninstall it, nevermind about that thing.
To turn compiz back on type:
compiz --replace

To turn compiz off and revert to metacity type:
metacity --replace

---

### Post by richardh on 2008-01-06
I tried 'compiz --replace' from a terminal, but lost the window decoration. So I had to do 'metacity --replace' to get back to something sane.

System->Preferences->Appearance->Visual Effects->Custom gets compiz back with my preferences.

So what is the terminal command line that does the same as the above?

---

### Post by Arcnsparc on 2008-01-06
I had a similar problem, Im still working on it but so far I have two good leads.

The first is to use "compiz --replace -all" or something like that.  There is also a way to do it "compiz --replace cube rotate..." et cetera, turning each plugin on individually.  I haven't got that down yet so I am not quite sure.

The second way, which has thus far been a failure is to use DBUS plugin for compiz which is supposed to allow for scripting.  But the download for the tar is down and I cant find the tar anywhere else.

In my script I used this and it works but I dont know why: "compiz --replace &"
something weird with that little ampersand fella.  

Eventually I want to be able to script all of my desktop affects & settings, background, theme, panels, and sounds.  I want to be able to hotkey a whole change so I can switch from a pretty apperance to a functional one, or just to switch between color schemes for what ever mood im in.

I think the ultimate solution will not be a script that directly changes the settings, but instead a script that subsitutes the configuration files for other ones.  Having many config files that arent used all the time, then the script would copy the desired setup file and replace the functioning one. 

Im still new to linux, this is month 3 so it may take awhile.  But once I get it all figured out ill post it somewheres and leave links on these threads.  You may also find this one useful; [http://ubuntuforums.org/showthread.php?t=640199](http://ubuntuforums.org/showthread.php?t=640199)

---

### Post by mbeierl on 2008-01-08
Noticed your other thread ([http://ubuntuforums.org/showthread.php?p=4094383](http://ubuntuforums.org/showthread.php?p=4094383)) and thought I might be able to help.  While I'm not sure exactly what all you are trying to do, I'll attempt to fill in a little bit of background info:

metacity: the original window manager from Gnome desktop.  Configuration settings are "remotely" managed using the gconftool-2 command.  You can browse the "keys" that can be set via the gconf-editor command.

Example: You can change the wallpaper picture with the following command:
```
gconftool-2 -t str --set /desktop/gnome/background/picture_filename "/path/to/pic.jpg"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "wallpaper"
```

compiz: an open gl window manager that provides many fancy effects.  Configuration (and causing events to occur) is managed through the dbus plugin (make sure you have this enabled through the settings manager).  It is not easy to browse the settable items, and I have not found a good web reference for what is available.  Some settable item lists can be viewed by using the list function like so:
```
dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/core/screen0 org.freedesktop.compiz.list
```
You can replace the "core" with the name of various plugins, such as "cube", "switcher", "animation", but I'm not sure exactly how the names are determined.

Lastly, emerald: a window "decorator", something fancy that makes pretty title bars, shadows, etc.  I do not know how to "remotely" configure it.

So, ask some more specifics, and maybe we can help get your script written!

---

### Post by Arcnsparc on 2008-01-10
Thanks to some great help I have this one figured out!  

Here is the run down:

Using gconf as my backend I wanted to script changing a compiz profile so I could hit a hotkey(also through gconf) and have my setting change.  If you are using a flat file back end there is some on that here too.  

[http://forum.compiz-fusion.org/showthread.php?t=6511](http://forum.compiz-fusion.org/showthread.php?t=6511)

My personal plan is to add a wallpaper change with this:

gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/jake/Documents/Ubuntu/Wallpapers/water.png"

(yours will have to have the correct path and file name)

Im also going to include an emerald theme change when I can find out how to script it.
Once I have that, scripting Appearance, sounds, and panels should be a breeze!

Then we can have a hotkey completely change the whole shebang!

---

### Post by Arcnsparc on 2008-01-12
Richardh

When you do "compiz --replace" from a terminal I have noticed that the command line doesnt come back to the prompt, then the window decoration goes away once the terminal is closed.  The way I found to avoid this is to just run compiz (alt +F2 "compiz"), when running from the terminal somethings get hung up and when the terminal is closed the window deco gets dumped.   I hope this helped!

---

### Post by Arcnsparc on 2008-01-12
OKAY
So its working, but its sloppy and I know it.  Thats why it is so nice to have a community!  

Here is what I have so far:

```

#Stringing together several scripts to make a bunch of changes to how ubuntu looks!
#This is still a baby so lets give it a little time to look prettier.

###Overview
#You have to do some editing to make this work for your computer.  Using the variables listed below, you can set this script to change many things through gconf.  Make sure that you set the path to 

#Backgrounds:  All of your background images have to kept in the same folder for this to work.  Down where the background is changed make sure the PATH is changed to where your Background folder is.

#Controls: This is what your menu looks like, your scroll bar, and other little nuances.  Fiddle with them under the gnome appearance menu until you find the one that suits your theme.


#Colors: the easiest way to adjust all of the color settings is to do them manually until they are to your liking, and then open the gconf editor by entering "gconf-editor" on the command line of your terminal or with Run.  Navigate to /desktop/gnome/interface/gtk_color_scheme and select edit key.  Copy the value and then you can replace the value for the Color Change below with your new one. 

#Icons: Pretty easy, just put in the name of the icon theme.

#Emerald Theme:  /home/username/.emerald/themes is where they are kept.  You can rename the folder containing a theme to make it easier to work with.

#Compiz: Under the Preferences option on the lower left of the CCSM(compiz config) you can add, remove, and change profiles.  This is useful if you want to have a normal profile, and another that is less of a resource hog for running games or the like.  Thanks to some great help over at the compiz forum, this part will save any changes you made to your profile before switching to the next.  If you wanted to really save on the processing power, you could get rid of the Emerald & Compiz changes and replace them with "metacity --replace &".

#If there is something you dont want to change, you can remove that part of the script, its labeled pretty well

#Those are all of the changes I am doing for now, but you can add another gconftool-2 line like those above and change other options like fonts & font colors, or terminal appearance if you wanted to really dork out.. Just look into the gconf-editor for ideas.





###Variables:
#Make sure all of your variables are valid by checking their names against what you find in the gconf-editor and the appearance menu.  Here I am using a theme, profile, and background all called "red".  
#Emerald Theme:
newtheme="red"

#Compiz Profile:
newprofile="red"

#Background:
newbackground="red"

#Icons:
newicons="Gnome"

#Controls:
newcontrols="Clearlooks"

#Colors:
newcolors="fg_color:#000000000000
bg_color:#dfdfe4e4e8e8
text_color:#000000000000
base_color:#ffffffffffff
selected_fg_color:#ffffffffffff
selected_bg_color:#d7d7555556df
tooltip_fg_color:#000000000000
tooltip_bg_color:#000000000000"






##Background Change
#Key Point here:
#make sure all of your backgrounds are in the same folder and that the path below goes to that folder.

gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/jake/Documents/Ubuntu/Wallpapers/$newbackground"

##Appearance changes
#Colors
gconftool-2 --type string --set /desktop/gnome/interface/gtk_color_scheme "$newcolors"

#Icons
gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "$newicons"

#Controls
gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "$newcontrols"



##Emerald change

if [ -z "$newtheme" ]; then
    echo "Usage: $0 <name of new theme>"
    exit 1
fi

#delete old theme folder
rm -rf ~/.emerald/theme

#copy & paste new theme folder to .emerald
cp -r ~/.emerald/themes/"$newtheme" ~/.emerald/theme

##Compiz Change
#!/bin/bash

# Name of new profile specified above
if [ -z "$newprofile" ]; then
        echo "Usage: $0 <profile>"
        exit 1
fi

# Find the name of the currently active profile
oldprofile=$(grep -m 1 'profile = ' ~/.config/compiz/compizconfig/config | cut -d '=' -f 2 | cut -d ' ' -f 2)
if [ -z "$oldprofile" ]; then
        oldprofile="Default"
fi
#If you already are using the desired compiz profile, the script will exit out here, so if you add to the script add before this line.
if [ "$oldprofile" = "$newprofile" ]; then
        echo "The $newprofile profile is already active."
        exit 0
fi

# Specify name of new profile in compizconfig config file
sed -i -e 's/profile = .*/profile = '"$newprofile"'/' ~/.config/compiz/compizconfig/config

# Fetch data from GConf database about the profile we're about to switch away from, and the new profile we're about to switch to
gconftool-2 --dump /apps/compiz >"${oldprofile}-dump.xml"
gconftool-2 --dump /apps/compizconfig/profiles/"$newprofile" >"${newprofile}-dump.xml"

# Remove stale data from GConf database
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compizconfig/profiles/"$newprofile"

# Swap locations of new <-> old profiles
sleep 3
gconftool-2 --load "${newprofile}-dump.xml" /apps/compiz
gconftool-2 --load "${oldprofile}-dump.xml" /apps/compizconfig/profiles/"$oldprofile"
rm "${newprofile}-dump.xml" "${oldprofile}-dump.xml"

# Restart Compiz & Emerald
emerald --replace &
compiz --replace ccp &


```

It was pointed out to me that the Emerald Change is a nasty thing to have in code.  The "rm -rf" combo is dangerous and not very popular.  Im looking into changing how that is done. 

The other problem I run into is that compiz likes to get the profiles a bit mixed up sometimes, I am trying to figure this out.  It likes to drop effect settings when I switch profiles.  It does this when I switch them manually and may be a bug, or it may be me doing something silly.  I am going to try and work around it by putting a pause in somewheres.

It should be said that the pretty looking Compiz code was not written by me, and that the Emerald code was vastly improved upon by others.  Thanks to the folks at [http://forum.compiz-fusion.org](http://forum.compiz-fusion.org) !

If anybody has any suggestions on how to clean this up or on how to make improvements please let me know!  Thanks again.

---

### Post by Arcnsparc on 2008-01-12
Yeah I am still having problems with Compiz dumping settings.  It defaults most of them but luckily it keeps the animation settings with each profile, which is nice because I think that is what is best for a custom overall theme.  Im trying to solve this mystery for now....

If you use this I would suggest that you get rid of the compiz part until it can be fixed.

---

