---
title: "Start a command in &quot;startup application preferences&quot; in silent mode so gui is hidden"
date: 2021-05-24
forum: Desktop Environments
---

### Post by triplemaya on 2021-05-24
I put paprefs in startup application preferences but I don't want to see the PulseAudio Preferences gui each time.
Similar problem. I put synapse in startup application preferences but again I don't want to see the interface when I log in, only when I press ctrl space.

---

### Post by yetimon_64 on 2021-05-25
Having just looked at "man paprefs" is seems that there are no built in options to "start minimized/hidden". Probably because it is a program that does not need to "run in the background" and it is generally used "on demand".

If you really need to start such a program at startup and have it minimized I'd suggest you **install devilspie2** and **put it in startup applications as well** as paprefs. I have the devilspie2 config folder set up in $HOME/.config/devilspie2 and inside that folder I store the ".lua" scripts for each devilspie2 action required. It can be installed from a terminal with "**sudo apt install devilspie2**" (or you can use whichever GUI installer app you prefer).

After installing devilspie2 make a directory for devilspie2 configuration files/lua scripts.
```
mkdir $HOME/.config/devilspie2
```

The startup command for devilspie2 in startup applications would look like...
```
devilspie2 --folder  /home/"put-your-username-here"/.config/devilspie2
```
Replace "put-your-username-here" with your actual user account name.

The script in $HOME/.config/devilspie2 for minimizing the paprefs window which I've called "paprefs.lua"...
```
if get_window_name()=="PulseAudio Preferences" then
    debug_print "Pulseaudio Preferences Window"
    minimize()
end
```

Now if you log out and back in again devilspie2 will start at log in and when paprefs tries to open it will be automatically minimized by the devispie2 program running in the background.

As I had both devilspie2 and paprefs installed here it was very easy to add a paprefs start up entry and a devilspie2 lua script named $HOME/.config/devilspie2/paprefs.lua. Every time I log out and back in paprefs is open but minimized to the bottom panel's "window buttons". Though once in a desktop session if paprefs is stopped and then restarted it will always restart minimized if devilspie2 is running.

The same set up could be used for synapse I would guess though I can't test that here. I won't install it to test as it brings in zeitgeist packages as well. When the synapse window opens you could try noting the window title and creating a new lua script in $HOME/.config/devilspie2 called synapse.lua. Change both the "get_window_name" and the "debug_print" lines to suit the synapse window title and save as eg. "synapse.lua". Then add a startup entry for it as well.

Good luck, yeti. :)

---

