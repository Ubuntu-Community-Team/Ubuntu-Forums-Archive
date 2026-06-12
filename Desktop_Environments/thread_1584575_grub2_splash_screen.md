---
title: "grub2 splash screen"
date: 2010-09-29
forum: Desktop Environments
---

### Post by debasishg on 2010-09-29
i am trying to change the grub2 splash image but its not happening. its showing the default screen, “Chainload" is not there. while hunting around, found that need to change 05_debian_theme from
```
for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga}
```
to
```
for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Plasma-lamp.{png,tga}
```
but 05_debian_theme does not have these types of entry
```

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/grub/moreblue-orbit-grub.tga"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi
....

```

totally confused, i am not an advanced user in linux .. also looking for the default location for wallpapers.

---

### Post by debasishg on 2010-09-30
bump......

---

### Post by psusi on 2010-09-30
What version of Ubuntu are you running?  That isn't what mine looks like.  Did you upgrade?  It seems something has modified that file so you might want to reinstall the grub-pc package to get it to where it is supposed to be.

---

### Post by drs305 on 2010-09-30
> **debasishg said:**
> totally confused, i am not an advanced user in linux .. also looking for the default location for wallpapers.

The good news is that you can't find the original reference because they made the entry simpler to understand.

You found the correct line to edit:
> 
WALLPAPER="/usr/share/images/grub/moreblue-orbit-grub.tga"


Just change the path and filename to point to the image you want to use.
Examples:
WALLPAPER="/home/drs305/Desktop/super_splash.png"
or 
WALLPAPER="/usr/share/images/grub/Moraine_Lake_17092005.tga"

The default wallpapers are located in /usr/share/images/grub

Run "sudo update-grub" after saving the changes you make to /etc/grub.d/05_debian_theme.

---

### Post by debasishg on 2010-09-30
@psusi.. i am using 10.04 upgraded to studio. thats corrent even most of tutorials contains a diff file that i have found in the net.

@drs.. i have tried to change the file name even pasting a pic and pointing to that pic, its not working. a wild guess is in my mind that we need to change the value for **f** here
```

f=/usr/share/desktop-base/grub_background.sh

```
again, as i am with grub2, hence it should be
```
sudo update grub2
``` and unfortunately .. i have also tried with grub and grub2

---

### Post by psusi on 2010-09-30
There is no update command.  You want sudo update-grub.

---

### Post by debasishg on 2010-09-30
yes .. it is ... sudo update-grub2 or grub

---

### Post by psusi on 2010-09-30
That's what I just said.  YOU said sudo update grub.  No dash.

---

### Post by debasishg on 2010-09-30
dear psusi .. no personal offence pl... would appreaciate if you suggest me what to do with my 05_debian_theme rather than tickling with spelling mistake.

as YOU said that this is not matched with your one also.

regards.

---

### Post by drs305 on 2010-09-30
> **debasishg said:**
> @drs.. i have tried to change the file name even pasting a pic and pointing to that pic, its not working. a wild guess is in my mind that we need to change the value for **f** here
```

f=/usr/share/desktop-base/grub_background.sh

```
again, as i am with grub2, hence it should be
```
sudo update grub2
``` and unfortunately .. i have also tried with grub and grub2

*update-grub* is the Grub 2 stub for "grub-mkconfig -o /boot/grub/grub.cfg" and will update the Grub 2 configuration files.

As far a "f", the 05_debian_theme script:
In a default Ubuntu installation, /usr/share/desktop-base/grub-background.sh does not exist. Therefore in a default install the script fails the first test and moves on to "else".
In that case, if you specify a file in the WALLPAPER section, it should be used.

You can check your own /usr/share/desktop-base folder of Ubuntu Studio to see if grub_background.sh exists. I haven't seen the contents of *grub_background.sh* so I don't know what it directs grub 2 to use.

If you don't have this file, then I suspect is the problem is one of the following:
[LIST]
[*]Improper path or filename or punctuation
[*]Incompatiable file format
[*]Grub 2 is not being updated properly (you should see a message adding the image when 'sudo udpate-grub' is executed.
[/LIST]

---

### Post by debasishg on 2010-09-30
thanks drs, again edited the 05_debian_theme and checked whether path is inconsistant or not.. its fine. not aware of file format and even no comments on last suspect.

attaching the execution for update-grub
```

debasish@debasish:~$ sudo gedit /etc/grub.d/05_debian_theme
[sudo] password for debasish: 
debasish@debasish:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

ps. just for your info, might help you to catch something. i have re-executed the grub-pc and ugrade-from-grub-legacy. while rebooting, splash screen has been displayed @1200x800 (just a guess) which was not before, i had to edit the resolution manually to display the whole thing visible.

---

### Post by drs305 on 2010-09-30
Here is what the terminal will show if the wallpaper is found (earth.png):
> 
drs305@homebuilt:~$ sudo update-grub
Generating grub.cfg ...
Found background image: earth.png
Found linux image: /boot/vmlinuz-2.6.32-25-generic
...


If you post the section of the 05_debian_theme script perhaps we can see something.

Here is what mine looks like:
> 
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
# WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  WALLPAPER="/home/drs305/Desktop/grub_images/earth.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi


---

### Post by debasishg on 2010-09-30
sure drs, here i am posting my 05_debian_theme
```

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/grub/windbuchencom.tga"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi

```

and 
```

debasish@debasish:~$ sudo gedit /etc/grub.d/05_debian_theme
[sudo] password for debasish: 
debasish@debasish:~$ ls /usr/share/images/grub
050817-N-3488C-028.tga                  Glasses_800_edit.tga
2006-02-15_Piping.tga                   Hortensia-1.tga
Aesculus_hippocastanum_fruit.tga        Lake_mapourika_NZ.tga
Apollo_17_The_Last_Moon_Shot_Edit1.tga  Moraine_Lake_17092005.tga
B-1B_over_the_pacific_ocean.tga         Plasma-lamp.tga
BonsaiTridentMaple.tga                  Sparkler.tga
Flower_jtca001.tga                      TulipStair_QueensHouse_Greenwich.tga
Fly-Angel.tga                           Windbuchencom.tga
debasish@debasish:~$

```

another wild thought .. shall i copy above images to /usr/share/desktop-base

---

### Post by drs305 on 2010-09-30
This will be simple. 

Windbuchencom.tga  is not equal to windbuchencom.tga

Linux is case sensitive. Change the case, update grub and it should work for you.

---

### Post by debasishg on 2010-09-30
thanks DRS ..... its working and i was looking for here and there ... thanks again to correct me .. 

another req for you ... pl see if you could help on this

[http://ubuntuforums.org/showthread.php?t=1583935](http://ubuntuforums.org/showthread.php?t=1583935)

---

### Post by Cavsfan on 2010-09-30
**drs305** is the one you want to help you with GRUB2!  I noticed you are dual booting and in my signature is a way to 
make your grub2 screen more manageable and maintenance free. **drs305** has it listed at the bottom of his GRUB2 tutorial.
Check it out when you have time. :P

---

### Post by drs305 on 2010-09-30
> **debasishg said:**
> thanks DRS ..... its working and i was looking for here and there ... thanks again to correct me .. 

another req for you ... pl see if you could help on this

[http://ubuntuforums.org/showthread.php?t=1583935](http://ubuntuforums.org/showthread.php?t=1583935)

You are welcome. 

When you are finished with this thread, would you please mark it SOLVED with the Thread Tool link to the top right of the first post? Thanks.

I will take a look at your other post.

---

### Post by debasishg on 2010-09-30
@cav .. priority given to hunt all links given in drs's siggy .. :)

@drs .. was looking for edit option to mark this [solved].. thanks again to correct me ... it has been done.

---

### Post by Cavsfan on 2010-09-30
> **debasishg said:**
> @cav .. priority given to hunt all links given in drs's siggy .. :)

@drs .. was looking for edit option to mark this [solved].. thanks again to correct me ... it has been done.

I totally understand and when you get to **drs305**'s **Grub 2 Basics** link in his signature you will see my 
tut. at the bottom of step 19 - Links. :)

---

### Post by debasishg on 2010-09-30
;) 

will surely do that .. let me coloured my fingers with G2 so that i can send you paint... ;)

---

### Post by Ballzac on 2010-10-28
I'm having a similar problem. Strangely, my 05_debian_theme has a slight difference. Where dbasishg has

```
source /usr/lib/grub/grub-mkconfig_lib
```

I have

```
. /usr/lib/grub/grub-mkconfig_lib
```

I haven't been able to get the background image to show, so I tried editing the above line to match dbasishg's. When I do this, and then run update-grub, I get

```
/etc/grub.d/05_debian_theme: 3: source: not found
```

even though I can find grub-mkconfig_lib in the file structure and open it manually. I don't actually know what this line does, but obviously something is different here if I'm getting this error. I also don't know why mine was slightly different.

I'm using 10.10 if that makes a difference. Any help appreciated :)

---

### Post by drs305 on 2010-10-28
> **Ballzac said:**
> I'm having a similar problem. Strangely, my 05_debian_theme has a slight difference. 

Yes, that is what I have now as well, so the ". /usr/lib..." is not your problem.

When you run "update-grub" does it show "Found background image..."? If not then the most likely problem is the path or filename. Are you sure your path is correct in the "WALLPAPER=" and is the file a .png, .jpg (8-bit only) or .tga file?


Do you have a /usr/share/desktop-base/grub_background.sh file? Normally it's not there and the "WALLPAPER" line sets the background image.

Is 05_debian_theme executable? Have you run "sudo update-grub"?

Is the "GRUB_TERMINAL=console" mode uncommented in /etc/default/grub?

Is the image in RGB format (non-indexed)?

---

### Post by Ballzac on 2010-10-28
> **drs305 said:**
> 
When you run "update-grub" does it show "Found background image..."? 
No. This is all I get
```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdc1
done

```


> **drs305 said:**
>  Are you sure your path is correct in the "WALLPAPER=" and is the file a .png, .jpg (8-bit only) or .tga file?
At the moment I'm just using
```
WALLPAPER="/usr/share/images/grub/Plasma-lamp.tga"
```
and will make my own one later if I can get one of these to work.
```
gimp /usr/share/images/grub/Plasma-lamp.tga
```
causes the expected image to open up in gimp. I installed SUM at some stage and have tried changing color depth and other settings on that to see if anything helps. I now have it back on 640x480 and 8 bits.

> **drs305 said:**
> 
Do you have a /usr/share/desktop-base/grub_background.sh file? 
```
cd /usr/share/desktop-base/
bash: cd: /usr/share/desktop-base/: No such file or directory
```


> **drs305 said:**
> 
Is 05_debian_theme executable?
Yes.

> **drs305 said:**
> 
Have you run "sudo update-grub"?

Yes.


> **drs305 said:**
> 
Is the "GRUB_TERMINAL=console" mode uncommented in /etc/default/grub?

Yes.


> **drs305 said:**
> 
Is the image in RGB format (non-indexed)?
I have no idea. How do I find this out? I assume that the file is in whatever format it needs to be, because it was from a set specifically designed for use as a background for grub.



Thanks for the help :KS

---

### Post by Cavsfan on 2010-10-28
I had to create this directory myself when I did a clean install of Maverick.

```
/usr/share/desktop-base/
```And you have to do it with root privileges.

And occasionally I have had to edit my image with Gimp and then click on **Image** and then **Scale Image**. 
I didn't really edit it, but by doing this, grub recognized the picture.

Then you can move it (or before hand) to the above directory if that is what your
**/etc/grub.d/05_debian_theme** file points to.

Hope this helps. :)

---

### Post by Ballzac on 2010-10-28
What's the purpose of creating this directory? The file still won't be in it, and drs305's reasoning that, without this file, the WALLPAPER image should be used, seems reasonable to me.

Thanks for the input :)

---

### Post by Cavsfan on 2010-10-28
> **Ballzac said:**
> What's the purpose of creating this directory? The file still won't be in it, and drs305's reasoning that, without this file, the WALLPAPER image should be used, seems reasonable to me.

Thanks for the input :)
I just thought that is the place where your **/etc/grub.d/05_debian_theme** points to.

The picture needs to be in whatever directory it does point to.
The **05_debian_theme** file is what tells grub which picture to use.

There may be a problem with grub2 as the last post I seen drs305 said "Yes, that is what I have now as well, so the ". /usr/lib..." is not your problem."

I guess you may as well wait on drs305 to get back with you as if anyone can fix it, he can.

I just thought I would throw in my 2 cents and try to help.

---

### Post by drs305 on 2010-10-28
The section of the 05_debian_theme we are discussing is
> 
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
.....
fi

The script directs that *grub_background.sh* be used if it exists, which by default it doesn't. 

Otherwise, use "moreblue-orbit-grub.png". By default in Ubuntu, this wallpaper also doesn't exist. 

If the user places an existing wallpaper address/filename in this line, that wallpaper will be used if it is of the proper format. In my 05_, the wallpaper line looks like this:
> 
WALLPAPER="/mnt/mydata/backgrounds/earth.png"


Since *Ballzac* is using one of the grub2_splashimages. I'll assume the images are in the default download location and the wallpaper line in this case should be:
> 
WALLPAPER="/usr/share/images/grub/Plasma-lamp.tga"


I added *Balzac's* wallpaper line to my 05_debian_theme script and it ran correctly after I installed *grub2-splashimages*.

Perhaps StartUp-Manager changed the script in some way. Since it appears you have considered my original questions perhaps you should just attach your 05 script so we can take a look at it.

As far as the format of the image, if it was downloaded from the repositories and not modified it complies with the formatting required.

---

### Post by Ballzac on 2010-10-28
I've messed around so much with the file in various attempts to get it working but, unless I've erred somewhere in recovering the backup, this is the original one I started with, with only the wallpaper line changed. It seems to me that, in addition to the "." instead of "source" in line 3, there is also an extra for loop in the "usable backgrounds" section (when comparing to dbasishg's example).

```
#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/grub/Plasma-lamp.tga"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
use_bg=false
for output in ${GRUB_TERMINAL_OUTPUT}; do
  if [ "$output" = "gfxterm" ] ; then
    for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
      if is_path_readable_by_grub $i ; then 
        bg=$i
        case ${bg} in
          *.png)		reader=png ;;
          *.tga)		reader=tga ;;
          *.jpg|*.jpeg)	reader=jpeg ;;
        esac
        if test -e /boot/grub/${reader}.mod ; then
          echo "Found background image: `basename ${bg}`" >&2
          use_bg=true
          break
        fi
      fi
    done
    break
  fi
done

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi
```

You suggest that SUM may be interfering with the settings. While this may be true, I had problems before installing it, so it can't have caused the initial problem. I should also mention that, out of desparation, I tried installing burg themes to see if that would override whatever settings I had that were not working. Alas, no. I still just get a black background with white writing on the grub menu.

I'm sure SUM will be easy to uninstall, and I'll do it if need be, but I'm not sure how to do a clean uninstall of burg, as it required making a lot of adjustments that I didn't understand (I just followed an online guide).

---

### Post by Cavsfan on 2010-10-29
Try this in terminal
**cd /usr/share/images/grub/**
and make sure Plasma-lamp.tga exists.
Enter **sudo update-grub2** (update-grub is the same thing) and if it lists your picture, you should be good to go.

And I would be patient as I have tried a lot of things trying to fix stuff and ended up 
doing a clean install because I messed my system up so bad!

EDIT: also if the picture does show up and it is dark those colors may be too dark to be able to read. (the ones below the image name)
On a lighter background I use these 2 color combinations:
[B]COLOR_NORMAL="light-cyan/black"
COLOR_HIGHLIGHT="white/black"[/B]
You just want to make sure and not change the 2nd color from black as that will make the line transparent 
and you will not see anything.

---

### Post by drs305 on 2010-10-29
I don't see a problem with your file as posted. I've attached my lucid files if you would like to try using my 05_debian_theme and /etc/default/grub files to see if they work for you. They use the default location for "Plasma-lamp.tga"

If you would like to try them, save them to your Desktop and then run the following commands. They will rename your existing files and make the renamed 05 file non-executable. The default menu entry is the first one (0).

```
sudo -i
mv /etc/default/grub /etc/default/grub.old
mv /etc/grub.d/05_debian_theme /etc/grub.d/05_debian_theme.old && chmod -x /etc/grub.d/05_debian_theme.old
cp ~/Desktop/grub /etc/default/ && cp ~/Desktop/05_debian_theme /etc/grub.d/ && chmod +x /etc/grub.d/05_debian_theme
update-grub
exit
```

---

### Post by Ballzac on 2010-10-29
Thanks for your continued help but, unfortunately, still no dice. It might be about time to give up. I'd really like to be able to change grub's appearance, but realistically, it IS just cosmetics for a screen that I see for a couple of seconds when I reboot. There's only so much time that I (and presumably you guys) can afford to invest in it.

And just for clarification, I checked that my 05_debian_theme had been renamed, and yours had been copied to the appropriate location, and also the the permission had been changed to allow execution, yet the image is not found when I update-grub.

---

### Post by drs305 on 2010-10-29
I'm sorry we aren't able to get this resolved. I don't know if once having burg on the system changed something or not. It's been a puzzle and I don't mind trying to solve these puzzles. 

Sometimes Grub just wins..... but I'll be glad to continue should you have any more questions or ideas.

---

### Post by Ballzac on 2010-10-29
...and just as I was about to give up: SUCCESS

I was looking through your 05_debian_theme to see if there were a lot of differences to mine. I noticed that your wallpaper was /usr/.../earth.png or something like that. I might have misunderstood you, but I thought you were saying that it was already pointing to Plasma-lamp.tga. I changed it to the appropriate wallpaper and it worked. Obviously there WAS something wrong with my 05_debian_theme originally. Not sure what it was, but glad it's working now, and I can play around with it a bit. Thanks heaps for all the help. :) :) :)

---

### Post by Cavsfan on 2010-10-30
> **Ballzac said:**
> ...and just as I was about to give up: SUCCESS

I was looking through your 05_debian_theme to see if there were a lot of differences to mine. I noticed that your wallpaper was /usr/.../earth.png or something like that. I might have misunderstood you, but I thought you were saying that it was already pointing to Plasma-lamp.tga. I changed it to the appropriate wallpaper and it worked. Obviously there WAS something wrong with my 05_debian_theme originally. Not sure what it was, but glad it's working now, and I can play around with it a bit. Thanks heaps for all the help. :) :) :)
That is great!!! :)   Glad you got it working as mysteries are no fun! **drs305** can always figure this stuff out.
It's just that there are so many things involved and if one of them is out of place, nothing works. Glad you didn't give up!!!

---

