---
title: "Dual screen set up"
date: 2011-05-05
forum: Desktop Environments
---

### Post by szpuni on 2011-05-05
Hello,

I'm looking for a solution to run two different programs let say teminal and vlc on separate monitor on startup.

Did anybody came across that kind of setup?

I know xinit can sent it to different monitors but i don't know if i can use it inside existing X session.

Basicall what i want to do is start ubuntu, and have two applications running on both monitors.

I'm using nvidia card with twin mode with monitors using separate sessions.

Does anybody have any idea how i can achieve this?

Thanks

---

### Post by Cerox Rex on 2011-05-05
What i do atm is to run Ubuntu-classical (no-effects) session and a seperate desktop setup by the nvidia tool. 

Due to some issue with compiz. unity and gnome with compiz running breaks keyboard functonality at second monitor.

Or u can see if u are able to configur your monitors with xrandr, I know that for my setup with nvidia xrandr fails to identify my monitors so its useless for me.

---

### Post by Copper Bezel on 2011-05-05
> Due to some issue with compiz. unity and gnome with compiz running breaks keyboard functonality at second monitor.

It's actually Compiz on 11.04, such that it affects Xubuntu, for instance, as well, but it only applies to some graphics cards, and I don't think that's the OP's problem. (There's a depressing lack of activity on that bug for something six months old and that Shuttleworth has personally commented on as a priority, but it seems unrelated. However, the OP's problem is a different one.)

The only way to position a startup application on the screen is to create a bash script to move it into position after it's launched. That requires using a sleep delay, then using wmctrl to manually reposition the window. The delay should equal the amount of time between the moment you hit enter after typing your password at the login screen to the point that the window is visible on the screen. The wmctrl command would look something like

```
wmctrl -r vlc -e 0,1500,-1,-1,-1
```

where "vlc" represents some part of the window's title, non-case-sensitive; "-e" is the option for a geometry modification; "0" is the window's gravity and shouldn't be changed; "1500" stands in for the desired x value of the window, which you'll have to adjust to your desktop; and the "-1"s indicate that other geometry values should remain unchanged.

You'll need to install wmctrl if you haven't, but it's available in the repositories.

```
sudo apt-get install wmctrl
```

Your final script will look something like

```

#!/bin/bash
sleep 40s;
wmctrl -r vlc -e 0,1300,-1,-1,-1;
wmctrl -r @ -e 0,1600,-1,-1,-1
```

---

