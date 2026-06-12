---
title: "Conky on startup"
date: 2007-03-16
forum: Desktop Effects &amp; Customization
---

### Post by Family_Guy on 2007-03-16
Is there a way to have conky on boot and run? On the same subject, does it need to have the terminal running?

---

### Post by SnackySmores on 2007-03-16
you should try to add conky to the autostarted applications, it is located in the settings menu
take care

it doesn't need to be run from a terminal

---

### Post by Family_Guy on 2007-03-16
I put the command 'conky' in the startup programs list and it started but disappeared after about 1 second.

---

### Post by johnc4510 on 2007-03-16
To have conky autostart on login create a small bash script called .conky_start.sh and save it to your /home.

gedit .conky_start.sh

copy the code below and past into the file. Save and close

#!/bin/bash
sleep 10 && conky;

This would start conky after 10 seconds after you login. The delay can be changed. Some sort of delay is desirable if you autostart beryl as well since conky works best if started after beryl. Not using beryl so I changed it to sleep 2 && conky;  Make sure the script is executable:

chmod a+x .conky_start.sh

Now, add it to your startup programs (menu: system->preferences->session->startup programs).Note, path to script is /home/>your user name/.conky_start.sh

---

### Post by olieviya on 2007-09-14
I have seen people post about having issues with Conky with Beryl/Compiz but I do not have those two installed, so the reason this is not working for me seems to be unaddressed as far as I can see.

So, what I did was I installed Conky like so (I basically followed: [this link]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")):

```

sudo apt-get install conky

zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc

```
Then ran:
```

sudo gedit /etc/X11/xorg.conf

```
Added:

```

Load “dbe”

```
to the section titled Section “Module”.


Then I added it to the Startup, so it would start on boot up.

The problem is it doesn't and if I do run from a terminal "sudo conky" all I get is conky in a window which is not what I want.

I then tried (I removed the other startup I previously tried):

> **johnc4510 said:**
> To have conky autostart on login create a small bash script called .conky_start.sh and save it to your /home.

gedit .conky_start.sh

copy the code below and past into the file. Save and close

#!/bin/bash
sleep 10 && conky;

This would start conky after 10 seconds after you login. The delay can be changed. Some sort of delay is desirable if you autostart beryl as well since conky works best if started after beryl. Not using beryl so I changed it to sleep 2 && conky;  Make sure the script is executable:

chmod a+x .conky_start.sh

Now, add it to your startup programs (menu: system->preferences->session->startup programs).Note, path to script is /home/>your user name/.conky_start.sh


Still no luck, any ideas?

:confused:

---

### Post by oswaldkelso on 2007-09-30
I run debian but this should work.  open the directory:

/home/username/.config/autostart

create files for the applications you want to run. here are mine.

# file called:   "conk.desktop" minus the quotes.
#this is the entry on the file "conky.desktop"

[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=conky
Comment=system viewer
Exec=conky
StartupNotify=false
Terminal=false
Hidden=false

# file called:   "tilda.desktop" minus the quotes.
#this is the entry on the file "tilda.desktop"

[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=tilda
Comment=terminal
Exec=tilda
StartupNotify=false
Terminal=false
Hidden=false


# file called:   "bbrun.desktop" minus the quotes.
#this is the entry on the file "bbrun.desktop"

[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=bbrun
Comment=terminal
Exec=bbrun
StartupNotify=false
Terminal=false
Hidden=false

#NOTE: if you run xfce4 in a terminal you can enter:

code:

xfce4-autostart-editor

# this will give you a nice little gui that is what i used to create the first file the used that as a base the create and edit others.

---

### Post by fululian on 2007-10-09
i just created the script .conky_start.sh

```
#!/bin/bash
sleep 20 && conky
```

an with a sleepy time long enough to let the desktop settle itself i finally got it to work. thanks a lot.

however, conky does blink from time to time, and to solve this i used

[this.]("http://conky.sourceforge.net/faq.html")

hth

---

### Post by steve101101 on 2008-06-15
if you enable a double buffer it wont anymore. also you may be able to decrease your delay. Mine can get down to 2 sec.

---

