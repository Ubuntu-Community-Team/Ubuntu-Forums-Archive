---
title: "Script to replace compiz with metacity during gaming."
date: 2008-07-23
forum: Gaming &amp; Leisure
---

### Post by ad_267 on 2008-07-23
I have problems running full screen games with compiz (games will be randomly minimized and I lose control) so I wrote this script. It's pretty basic but I still thought it might be useful for someone else. All it does is runs "metacity --replace," executes the commands given to it and then runs "compiz --replace."

Installation:

Open a terminal and enter:
```
gksu gedit /usr/games/playgame
```
I put mine in /usr/games but it can be anywhere in your path, eg /usr/bin or ~/bin

Enter:
```

#!/bin/bash

if [ $# -lt 1 ]; then
	echo "Usage: playgame game_name game_options" 1>&2
	exit
fi

# Replace compiz with metacity to prevent issues
metacity --replace &

# Run game
$@

# Replace metacity with compiz
compiz --replace

```

Save that and close gedit then in the terminal enter:
```
sudo chmod +x /usr/games/playgame
```

Now run alacarte or right click on your menu and select edit menus. Find the launchers for any games you want to use this with and right click and select properties. Where it says "Command:," keep the same command but just put "playgame " in front (without the quotes and with a space after). Eg to play alien arena, the command is "alienarena" which I changed to "playgame alienarena"

Now compiz will be replaced with metacity while you play these games.

Known Issues:
Metacity and compiz handle workspaces differently so if you have a lot of applications spread out on different workspaces and run this they will end up all on the first workspace.

Note:
Don't run "playgame game_name" in a terminal as when you close the terminal this will cause compiz to exit and you will lose your window borders and window management.

---

### Post by ad_267 on 2008-09-05
Also, if you decide to switch back to metacity you can just comment out these two lines as shown so that the games run normally without switching to compiz afterwards. Then you can uncomment them later if you enable compiz again.

```

#metacity --replace &
#compiz --replace

```

---

### Post by Lod on 2008-09-05
Will try it out soon. Does it work with games played with Wine (Crossover games)?

---

### Post by ad_267 on 2008-09-05
> **Lod said:**
> Will try it out soon. Does it work with games played with Wine (Crossover games)?

Yes, I've used this with Counter Strike Source and it improved the quality a lot on my computer.

---

### Post by Lod on 2008-09-05
nice, haven't got time the next few days unfortunately. Another question though :) I'm using emerald, will it close down and restart automatically or do I have to alter the script?

---

### Post by ad_267 on 2008-09-05
I'm using emerald too and yes it closes emerald and then reloads it when compiz loads. In compizconfig-settings-manager I set the "Command" in the Window decoration plugin to "emerald --replace" but I'm not sure if that's needed or not.

---

### Post by Crafty Kisses on 2008-09-05
Nice, this should work pretty well.

---

### Post by airtonix on 2008-09-05
i just use the compiz-icon to switch between openbox/metacity & compiz/emerald.

Its less config in the end...

---

### Post by washeddang on 2008-09-05
Since I use AWN and screenlets, I like to use metacity with compositing. I put together a similar script that checks if compiz is running and switches to metacity with compositing and vice versa:

```
#!/bin/sh
SERVICE=0`pidof compiz.real`

if [ 0`pidof compiz.real` -gt 0 ];
then
    gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
    kill -9 $SERVICE
    sleep 1
    metacity --replace &
else
    gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
    sleep 1
    compiz --replace --ignore-desktop-hints &
fi
exit 0
```

I copied the script to the ~/.gnome2/nautilus-scripts folder so that I can run it from the Scripts menu when I right-click in Nautilus.

---

### Post by nisaky on 2008-09-05
It's all problem in screen saver, not compiz. If you switch screen saver off, all games will work in full-screen and with no problems. Even wine games.

---

### Post by ad_267 on 2008-09-05
> **washeddang said:**
> Since I use AWN and screenlets, I like to use metacity with compositing. I put together a similar script that checks if compiz is running and switches to metacity with compositing and vice versa:

I copied the script to the ~/.gnome2/nautilus-scripts folder so that I can run it from the Scripts menu when I right-click in Nautilus.

Ah ok cool. Yeah I don't think my script works if metacity compositing is enabled as compiz won't replace it. Something like this would need to be used.

---

### Post by ttanev on 2010-10-14
Works beautifully well, thanks! :) 
Tried it on more than two separate Maverick's with lots of games already /including wine games/.

---

### Post by ttanev on 2010-10-18
Thanks for the script, it's just perfect! I'm using an awn too but the latest version doesn't disappear without compositing. 
I tried to put your code inside an bash script that creates your one:
```
#!/bin/bash
#Creating "playgame" script in /usr/games
cat > ~/playgame <<EOF
#!/bin/bash

if [ $# -lt 1 ]; then
    echo "Usage: playgame game_name game_options" 1>&2
    exit
fi

# Replace compiz with metacity to prevent issues
metacity --replace &

# Run game
$@

# Replace metacity with compiz
compiz --replace
EOF
sudo cp ~/playgame /usr/games/
sudo chmod +x /usr/games/playgame

exit
```
but in the end the actual file is missing essential fragments:

> #!/bin/bash

if [ [COLOR=Red]0[/COLOR] -lt 1 ]; then
    echo "Usage: playgame game_name game_options" 1>&2
    exit
fi

# Replace compiz with metacity to prevent issues
metacity --replace &

# Run game
[COLOR=Red]?![/COLOR]

# Replace metacity with compiz
compiz --replaceCan someone suggest a solution to my problem :???:

---

### Post by dethorpe on 2010-10-18
The shell is expanding the special variables $# and $@ before writting out to the file so you get the current values of those variables.

You need to quote the $ char to print an actual $, so change to (note the \ before the $'s):

if [ \$# -lt 1 ]; then
.
.
\$@

---

### Post by ttanev on 2010-10-18
> **dethorpe said:**
> The shell is expanding the special variables $# and $@ before writting out to the file so you get the current values of those variables.

You need to quote the $ char to print an actual $, so change to (note the \ before the $'s):

if [ \$# -lt 1 ]; then
.
.
\$@
You will have to excuse my ignorance. At first I didn't got it but with some searching about "quote the $ char" found more expanded answer here - [http://tldp.orthe g/LDP/Bash-Beginners-Guide/html/sect_03_03.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html")
Thank you! :)

---

### Post by ttanev on 2010-10-24
I was just curious - is it possible to implement in the script functionality to detect whether 3D app is running in fullscreen and if so to automatically switch to metacity ?
That would involve more than a bash script in the equation I guess... :-s

---

