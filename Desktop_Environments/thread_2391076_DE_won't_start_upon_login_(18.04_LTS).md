---
title: "DE won't start upon login (18.04 LTS)"
date: 2018-05-05
forum: Desktop Environments
---

### Post by nvx on 2018-05-05
When I try to log in via the LightDM GTK+ Greeter, I end up with a blank screen and a mouse cursor. If I log in in the text mode (e.g. in TTY1), the following error is displayed before the prompt is shown:
```
Unable to connect to X server
```
but when I then run
```
startx
```
the DE starts up without any problems.

The strange thing is that the other user on the same machine can log in via the Greeter just fine. What could be causing this?

Could you please point me to the right configuration file which I should compare between my and the other user's account? There are quite a lot of them in various folders and I -- being relatively new to Linux -- am hesitant to change things so that I do not accidentally make the situation even worse than it is.

Thanks.

---

### Post by Xian on 2018-05-05
Remove or rename your $HOME/.Xauthority file and reboot. 

Any change?

---

### Post by nvx on 2018-05-06
Xian,

Thank you for your response; however, removing the .Xauthority file and rebooting did not help. When I tried to log in via the LightDM GTK+ Greeter, again the DE did not start (only a blank screen with the mouse cursor was visible).

---

### Post by Xian on 2018-05-06
Before we go further -- let's first eliminate there's a user specific issue.

Rename your $HOME/.config folder to something like $HOME/.config_bak
Reboot the computer.

[I]I could just ask you to remove a specific file like $HOME/.config/dconf/user[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]But's let do the full shot just to make certain.[/I]

Any change?

---

### Post by nvx on 2018-05-06
I am sorry to say this but, unfortunately, what you proposed did not help (no change at all in terms of logging in via the Greeter). :(

Just a side note: the problem started occurring after an OS upgrade (16.04 --> 18.04) so maybe this information might be useful to you...?

---

### Post by Xian on 2018-05-06
it's not your user config --- so let's move to the possibility that either:


[LIST]
[*]There was a package installation issue during the upgrade
[*]Or an issue with the lightdm package itself
[/LIST]

First lets check the system for incomplete package installs:

```
sudo apt-get update --fix-missing
sudo dpkg --configure -a
sudo apt-get -f install

```

If no pkgs are reinstalled with that command ... move on to:

```
sudo apt-get purge lightdm
sudo apt-get install lightdm
sudo dpkg-reconfigure lightdm
```[COLOR=#222222][FONT=Verdana]
Reboot the system.[/FONT][/COLOR]

---

### Post by nvx on 2018-05-07
Thanks again for the tips, but I am afraid that none of them solved the problem. As for the first three commands (incomplete packages), nothing was reinstalled. Purging and reinstalling LightDM went fine; however, I am still seeing a blank screen and the mouse cursor when I try to log in via the Greeter.

Since reinstalling the whole OS is quite a lot of hassle, it seems that I will have to get used to logging in via TTY1 and starting the DE manually... ;)

---

