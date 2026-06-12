---
title: "How to get balloon tip alerts for nearly dying hard drives with Xubuntu"
date: 2009-01-05
forum: General Help
---

### Post by rjmoerland on 2009-01-05
[IMG]http://img255.imageshack.us/img255/6136/smartdwarning2vr7.jpg[/IMG]

Well, hello there! I'd like to share some information on how to get notifications (balloon tips) when your hard disk is about to die. Yes, I know about smart-notifier in the repositories, but I simply dislike interpreters running full time as semi-daemons for a relatively simple script. If you *do* like it, no problem of course, but this mini how-to is then not for you and our ways part here. 

You will need to type in some commands, though I've tried to keep it to the minimum. Still here? Good, then let's get started. First, you'll need a proper way to assess the overall health of your drive(s). There is a very good suite of tools available called smartmontools. Fire up synaptic. When the **smartmontools **package is selected for installation, by default a mail server will be installed as well. I personally don't like this, and to avoid it go to *Settings->Preferences* and then the *General *tab. Unselect *Consider recommended packages as dependencies* and click *OK*. Then, search and select the **smartmontools **package for installation. After selecting smartmontools, search and select **libnotify-bin** for installation. When all is installed, you might want to check *Consider recommended packages as dependencies* again afterwards. Close Synaptic. 

**Alternative:** Press Alt+F2. This will open a dialog box with a single line. Here, type 
```

gksudo aptitude install smartmontools libnotify-bin --without-recommends

```
You might want to check *Run in a terminal* to see the progress. If you *do* install the mail server, you can receive an e-mail when a drive is about to fail. I will not go into how to configure the mail server though.

You can check your hard disk's health in various ways, which is discussed here: [http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/]("http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/") and here: [http://www.linuxjournal.com/article/6983]("http://www.linuxjournal.com/article/6983"). I will not go into the details of the on-line testing capabilities, as we will be using a program that runs in the background that does it for us, **smartd**. **smartd** can also be configured thoroughly, but - at least on Xubuntu intrepid and jaunty (alpha) - comes with a configuration file that simply monitors all attached hard disks. If this is not working for you, please check out the [smartmontools' documentation]("http://smartmontools.sourceforge.net/doc.html"). Now, I would have expected that installing the daemon (**smartd**) and Synaptic ensuring that the start-up script (**/etc/init.d/smartmontools**) is launched, **smartd** would actually start. Not so... We will have to edit another file to actually let the **smartd** daemon start. For the following, you'll need to start a text editor with root rights. One possibility is to press Alt+F2. This will open a dialog box with a single line. Here, type 
```

gksudo mousepad

```
to open mousepad with root rights (it will warn you with a red bar on top of the screen if you succeeded). Open the file **/etc/default/smartmontools** and remove the # from the line
```

#start_smartd=yes

```
Save the file and exit mousepad. Press Alt+F2 and type
```

gksudo /etc/init.d/smartmontools restart

```
Now **smartd** will really be started.

You have also installed **notify-send**, a small application that you can use to send any message and make it pop up as a balloon tip. Press Alt+F2 and enter 
```

notify-send "A balloon tip" "With some text"

```
into the text box. If all is well, you will see a balloon tip popping up on your desktop. 8)

The directory **/etc/smartmontools/run.d/** is a placeholder for scripts that are executed when a drive fails. One of them installed by default and is a script to send an e-mail, which is why you need a mail server for this to work. We will add a script to this folder that will notify us on the desktop with a balloon tip. You'll probably feel it coming: we will use **notify-send** to let **smartd** 'talk' to us when something nasty is about to happen. The problem is that **smartd** is running as root, and has no idea of a graphical desktop whatsoever. However, we can work around that, as is shown in the script below. With mousepad (or any other text editor you're comfortable with) create a new file and paste the following script (based on [http://gnome-hacks.org/hacks.html?id=82]("http://gnome-hacks.org/hacks.html?id=82")):
```

#!/bin/bash

# Title to pop up with
title="Hardisk failure imminent! "

# The error report by smartd
errortext="`cat ${1}`"

# Infinite timeout. 
# Needs interaction to go away.
timeout=0

# get pid of graphical session
# Ubuntu users might try gnome-session instead of
# xfce4-session
pids=`pgrep xfce4-session`

# Set DISPLAY variable. Only local screens for now.
# Needs to be exported as well
DISPLAY=:0
export DISPLAY;

# Go through all currently logged on users with an
# XFCE session

for pid in $pids;
do

	# find user having a graphical session
    USER=`grep -z USER= \
        /proc/$pid/environ | sed -e 's/USER=//'`
        
	# Set the XAUTHORITY variable and export it
	XAUTHORITY=/home/$USER/.Xauthority
	export XAUTHORITY

    # Find DBUS session bus for this session.
	# For some reason does not need to be exported
	# but is crucial for functioning

    DBUS_SESSION_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
        /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
        
    # Run notify-send as the user who has display :0
	# other icon (-i option) possibilities are
	# drive-harddisk and face-crying
	# See http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html
	# for a full list.
    sudo -u $USER notify-send -i dialog-warning -t "$timeout" -u critical "$title" "$errortext" 
        
done

```

What the script does is to look for an XFCE session and get the user that owns the session and his/her connection to the D-BUS service. The latter is necessary for notify-send to work. Moreover, notify-send needs to be run as that user, hence the 'sudo -u $USER notify-send'. This should make the script independent of the actually logged in user who runs a graphical session. Furthermore, it sets the time that the balloon tip is displayed to 'infinite', so that it's not likely that you'll miss it. Finally, the '-i dialog-warning' option shows a warning icon with the warning. Other possibilities are listed in the script. 

Save the script as 65smartd-notify in your home folder. Start Thunar and go to your home directory. Right click on 65smartd-notify and select the *Permissions* tab. Check the box that says *Allow this file to run as a program*. Close the window. Then, press Alt+F2 and type:
```

gksudo cp 65smartd-notify /etc/smartmontools/run.d/

```
You have just copied the script to its destination! 

Now, to test this setup we are going to use the built-in test warning that **smartd** can generate. Open mousepad as root (Alt+F2->gksudo mousepad) and open the file /etc/smartd.conf. There will be a lot of lines. Search for the line that is *not* starting with a #, but (usually) with **DEVICESCAN**. It should end with **-M exec /usr/share/smartmontools/smartd-runner**. Append the following to that line:
```

 -M test

```
So that it reads 
```

[...] -M exec /usr/share/smartmontools/smartd-runner -M test

```
Save the file but leave mousepad open. Press Alt+F2. In the box, type 
```

gksudo kill -SIGHUP `pidof smartd`

```
Notice the backticks (`), these are not regular single quotes ('). The above line will signal smartd to re-read the smatrd.conf file. Because of the line **-M test** it will generate a fake warning, which you should see pop up, just like the image at the start of this post. Congrats, remove the **-M test** in smartd.conf (which you still had open, right? ;)) and save the file again, (optionally) delete 65smartd-notify from your home folder and you're done :) 

**How to undo:**
Open Synaptic, search and mark smartmontools for removal. Search and mark libnotify-bin for removal. Apply the changes. 

That's it. Suggestions are welcome, of course!

Cheers,
Robert

---

### Post by rjmoerland on 2009-01-06
New version posted, now works even if XAUTHORITY and DISPLAY environment variables aren't set (as is when smartd is started at boot time).

---

### Post by rjmoerland on 2009-01-08
Posted simplified version with same functionality.

---

### Post by dabl on 2009-01-08
Nice piece of work -- thanks!  :)

---

### Post by rjmoerland on 2009-01-08
> **dabl said:**
> Nice piece of work -- thanks!  :)

You are welcome :)

---

### Post by kevdog on 2009-01-08
Ive never had a hard drive die on me -- Wait...

---

### Post by geneiros on 2009-12-07
hi there,

thanks for the tip...

is there a way to make this work in Kde4?

kdialog --title "title" --passivepopup "message"


thanks...

---

### Post by rjmoerland on 2009-12-12
Hi,

I think that replacing the line

```
sudo -u $USER notify-send -i dialog-warning -t "$timeout" -u critical "$title" "$errortext" 

```

in the 65smartd-notify script with

```

sudo -u $USER kdialog --title "$title" --msgbox "$errortext" 

```
should do the trick. I can't test it at the moment though, as since I upgraded my machine to karmic, I can't log into Kubuntu anymore.

HTH
Robert

---

