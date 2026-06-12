---
title: "[SOLVED] Can't change background wallpapers after updates"
date: 2008-05-31
forum: Desktop Environments
---

### Post by Najmudin on 2008-05-31
Hi
I did some upgrades today on my Hardy desktop, but after finishing the upgrade its not possible to change my desktop background wallpapers , when trying to select another one or clicking on it nothing happens at all , i tryied to delete the "gnome" and "gnome2" files in my home folder and logout then login but that didn't help ,at later time i noticed that i have to click many times "7 or 10" times on a wallpaper to be changed.:confused:
i did the same upgrade on my laptop to make sure and get the same issue also, I'm not sure which upgrade did the damage.
I hope some one can help me to fix it.
Sorry for my english.

---

### Post by Najmudin on 2008-06-01
any one.:roll:

---

### Post by unutbu on 2008-06-01
As an experiment, see if you can set the wallpaper from the command line:
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename <path-to-image>
```

Also check the contents of ~/.gnome2/backgrounds.xml and
~/.gconf/desktop/gnome/background/%gconf.xml.

---

### Post by Najmudin on 2008-06-03
> **unutbu said:**
> As an experiment, see if you can set the wallpaper from the command line:
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename <path-to-image>
```

Also check the contents of ~/.gnome2/backgrounds.xml and
~/.gconf/desktop/gnome/background/%gconf.xml.

Thanks for your reply
I tried what you mentioned but i consider my self not good enough in using the terminal :lolflag: so there was no success trying to set the wallpaper from the command line, i tried to copy paste the path of the wallpaper and put the picture_filename but all get was errors about syntax or something like that, i tried to put the wallpaper ext like png or jpg but without success also ,also i didn't know what to check in the files you mentioned.
anyway i reinstalled Ubuntu on my computer again yesterday, after installing i applied all the available updates and rebooted the system , but what i found is the same problem.
I filled a bug report against this problem, here is the link if any one can help or is having the same issue
[https://bugs.launchpad.net/ubuntu/+bug/236521]("https://bugs.launchpad.net/ubuntu/+bug/236521")
Thanks and best regards:)

---

### Post by unutbu on 2008-06-03
Hi Najmudin, I'm sorry I don't know how to fix your problem -- at least not the GUI part, but if you would like to try the CLI again:

[Open a terminal]("http://www.psychocats.net/ubuntu/terminal"). 
Select and paste
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename 
```
into the terminal -- no need to change anything.
Then open a Nautilus window and navigate to the image you want to use as wallpaper. Click-and-drag the image and drop it on your terminal. The path should show up automatically. Make sure there is a space between "picture_filename" and the path. Press return and see what happens.

If it doesn't work, cut and paste everything in your terminal here (the command and the error message.)

---

### Post by cotiK on 2008-06-03
yeah!! me too

---

### Post by Najmudin on 2008-06-03
Hi unutbu

Thanks again for your help,i don't mind using the terminal but some times i don't understand what to do with the codes like the one you mentioned, but after you explained what to do i can use it, and here is the error:
> najmudin@najmudin-desktop:~$ gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/najmudin/Pictures/Other Wallpapers/3DLinux.png
No value to set for key: `Wallpapers/3DLinux.png'

I hope i paste it correctly:)

---

### Post by cotiK on 2008-06-03
> **unutbu said:**
> As an experiment, see if you can set the wallpaper from the command line:
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename <path-to-image>
```

Also check the contents of ~/.gnome2/backgrounds.xml and
~/.gconf/desktop/gnome/background/%gconf.xml.
I have the same problem as the poster.
I can change the wallpaper as you suggest from the terminal, so the problem is at the gnome-appearance program, right?
ALso i need to thos .xml files for what?]

will there be an update fixing this?

---

### Post by CEB2nd on 2008-06-03
> **unutbu said:**
> Hi Najmudin, I'm sorry I don't know how to fix your problem -- at least not the GUI part, but if you would like to try the CLI again:

[Open a terminal]("http://www.psychocats.net/ubuntu/terminal"). 
Select and paste
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename 
```
into the terminal -- no need to change anything.
Then open a Nautilus window and navigate to the image you want to use as wallpaper. Click-and-drag the image and drop it on your terminal. The path should show up automatically. Make sure there is a space between "picture_filename" and the path. Press return and see what happens.

If it doesn't work, cut and paste everything in your terminal here (the command and the error message.)

Same problem here. I can change the background if I use terminal as you instructed.

---

### Post by unutbu on 2008-06-03
Najmudin, the reason the terminal command did not work for you is because the image you want is in a directory whose name contains a space. To get around this problem, try putting a backslash before the space:

```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/najmudin/Pictures/Other\ Wallpapers/3DLinux.png
```

or use quotation marks:

```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/home/najmudin/Pictures/Other Wallpapers/3DLinux.png"
```

cotiK, CEB2nd: It appears this is a bug in Hardy. Najmudin has opened a bug report (see post #4), and I think that's the best we can do. It wouldn't hurt to post a note there to confirm that the problem is widespread.

---

### Post by Najmudin on 2008-06-03
> **unutbu said:**
> Najmudin, the reason the terminal command did not work for you is because the image you want is in a directory whose name contains a space. To get around this problem, try putting a backslash before the space:

```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename /home/najmudin/Pictures/Other\ Wallpapers/3DLinux.png
```

or use quotation marks:

```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "/home/najmudin/Pictures/Other Wallpapers/3DLinux.png"
```

cotiK, CEB2nd: It appears this is a bug in Hardy. Najmudin has opened a bug report (see post #4), and I think that's the best we can do. It wouldn't hurt to post a note there to confirm that the problem is widespread.

unutbu

I was able to do it this time without errors following your post, but as you know the problem is with the appearance window so we cant select by mouse click.
Anyway thanks for advising cotik and CEB2nd to put a note on the bug report so the developers can look at it, please people do this.
Great help from you unutbu ,i appreciate it.

---

### Post by Najmudin on 2008-06-03
The problem is solved , i just got some updates which solved the problem:guitar:
I'm going to ask for closing my bug report.
Could some one tell me please how mark this thread as SOLVED

---

### Post by CEB2nd on 2008-06-03
Latest updates 6-3-08 didn't help here. I refreshed update manager and it
shows up to date system.

---

### Post by CEB2nd on 2008-06-03
> **Najmudin said:**
> The problem is solved , i just got some updates which solved the problem:guitar:
I'm going to ask for closing my bug report.
Could some one tell me please how mark this thread as SOLVED

Were these pre-release Hardy proposed updates that fixed the problem
for you?  Update Manager shows I have all current important security
and recommended Hardy updates.

---

### Post by Najmudin on 2008-06-03
> **CEB2nd said:**
> Latest updates 6-3-08 didn't help here. I refreshed update manager and it
shows up to date system.

Go to system> administration> software sources> 
try to change the download from to the main server (if its not)
then it will ask you to reload do it , if you didn't get any updates try to reboot your system.
thats what i did to get the updates, i think they include some gnome or xlruner .. i don't remember , but they solved the issue for me.
i hope that helps you.

---

### Post by CEB2nd on 2008-06-03
> **Najmudin said:**
> Go to system> administration> software sources> 
try to change the download from to the main server (if its not)
then it will ask you to reload do it , if you didn't get any updates try to reboot your system.
thats what i did to get the updates, i think they include some gnome or xlruner .. i don't remember , but they solved the issue for me.
i hope that helps you.

I enabled the "pre-released updates Hardy-proposed" in Software Sources Update tab and found Gnome and Compiz updates that fix the problem...and hopefully didn't break something else.:rolleyes:

---

### Post by Najmudin on 2008-06-03
> **CEB2nd said:**
> I enabled the "pre-released updates Hardy-proposed" in Software Sources Update tab and found Gnome and Compiz updates that fix the problem...and hopefully didn't break something else.:rolleyes:

Great I'm so happy for you.:)

---

### Post by mbaker824 on 2008-06-03
> **Najmudin said:**
> Go to system> administration> software sources> 
try to change the download from to the main server (if its not)
then it will ask you to reload do it , if you didn't get any updates try to reboot your system.
thats what i did to get the updates, i think they include some gnome or xlruner .. i don't remember , but they solved the issue for me.
i hope that helps you.

Thanks, that solved it for me too.

Mark

---

### Post by SynapseR on 2008-06-04
If you don't want to use the proposed updates and wait for it to appear in the standard repositories, there is a work-around.
Once you have the change desktop background window open, you can use the arrow keys on the keyboard to navigate between wallpapers.
Clicking on add still works, it's just clicking on the wallpaper that doesn't, so you can add/delete wallpapers and use the keyboard arrow key to change.
Hope this helps in the interim.

---

### Post by Pirolocito on 2009-01-04
try gconf-editor and under desktop->gnome->background->draw backgroud enable it

worked for me

Best regards 

RP

---

### Post by Fitch on 2010-01-11
Is this problem with Karmic as well? or is it that I want to use a web page as the background.

My command is:
gconftool-2 -t string -s /desktop/gnome/background/picture_filename [http://www.ehabich.info/images/synchro/europecrescent.jpg](http://www.ehabich.info/images/synchro/europecrescent.jpg)

which instantly produces the original Ubuntu fawn background.

If I copy the page and put it in my home folder:[[COLOR=blue]__[/COLOR]]("http://www.linuxquestions.org/questions/#")
and do:
[ ]("http://www.linuxquestions.org/questions/#")gconftool-2 -t string -s /desktop/gnome/background/picture_filename /brafferton/europecrescent.jpg

I get the same result....

---

### Post by Fitch on 2010-01-11
My fix:
I use the opefs european crescent as my wallpaper and update it every 30 minutes.

Stage 1:
Open a command line and type:
wget -N -c [http://www.ehabich.info/images/synchro/europecrescent.jpg](http://www.ehabich.info/images/synchro/europecrescent.jpg)
which will download the latest satellite image into your home folder.

Stage 2:
Click on Applications>System Tools>Configuration editor.
Expand desktop and then gnome then background.
Double click on the image filename box and drag the image into the box or type in - in my case - /home/*brafferto*n/europecrescent.jpg 
(change the "brafferton" to whatever your home directory is).
Set picture_options to stretched.
Close the config editor.

Stage 3:
In the command line, type:
crontab -e
I used nano (if this is the first time crontab is used)
Underneath the "# m h  dom mon dow   command" I typed

*/30 *  * * * rm europecrescent.jpg; wget -N -c [http://www.ehabich.info/images/synchro/europecrescent.jpg](http://www.ehabich.info/images/synchro/europecrescent.jpg)

CTRL O to write out
CTRL X to exit

*/30 *  * * * means every 30 minutes of every hour, every day, every week, every month.

There are two commands separated by a semicolon:
The  "rm europecrescent.jpg" removes the old image as wget won't download the file if one already exists.
and the wget is as stage 1.

Sorted!

---

### Post by rapidwiz on 2010-01-20
Try this if you having trouble changing your background via script and cron.

I found this forum with the info.
[http://forums.fedoraforum.org/archive/index.php/t-83656.html](http://forums.fedoraforum.org/archive/index.php/t-83656.html)

Add this to the top of your script

# This function required in order to run gconftool-2 from cron
# ================================================== ====
function export_variables
{
user=$( whoami )
pid=$( pgrep -u $user gnome-panel )

for dbusenv in $pid; do
DBUS_SESSION_BUS_ADDRESS=$( grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ 
| sed -e 's/DBUS_SESSION_BUS_ADDRESS=//' )

data="DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS"
eval " export $data"
done
}
# ================================================== ====
export_variables
# =====
####################################################################

---

### Post by rapidwiz on 2010-01-20
#!/bin/bash 

# This function required in order to run gconftool-2 from cron
# ================================================== ====
function export_variables
{
user=$( whoami )
pid=$( pgrep -u $user gnome-panel )

for dbusenv in $pid; do
DBUS_SESSION_BUS_ADDRESS=$( grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//' )

data="DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS"
eval " export $data"
done
}
# ================================================== ====
export_variables
# =====
####################################################################


ImageDir="/Public/Wallpaper/webilder/Collection/"

COUNT=`find $ImageDir | grep -v .thumbs | grep .jpg  | wc -l`

# --> Create Random Number
((NUM=RANDOM%COUNT))

# Find Image and grep for .jpg twice, one for all .jpg's, second to print line number on .jpg's and grep for the line num
IMG=`find $ImageDir | grep -v .thumbs | grep -v thumb | grep .jpg | grep -n .jpg | grep "^$NUM:" | awk -F ":" {'print $2'}`

echo "$IMG"

/usr/bin/gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$IMG"

/usr/bin/gconftool-2 -t str -set /desktop/gnome/background/picture_options "scaled"

---

### Post by mister_playboy on 2010-01-20
I can't get my background to change.  It doesn't work from the CLI either.  Gnome is set to draw the background in Gconf.

I have no idea what's causing my problem, it just appeared a day or so ago and the only updates I've been getting are Chromium daily builds.

---

