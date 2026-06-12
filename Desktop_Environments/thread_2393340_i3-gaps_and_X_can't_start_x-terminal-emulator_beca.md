---
title: "i3-gaps and X: can't start x-terminal-emulator because $DISPLAY is not set"
date: 2018-06-02
forum: Desktop Environments
---

### Post by theologymatters on 2018-06-02
Hi folks,

So I've got a weird situation here. I've installed Ubuntu from the minimal net install image. I started with just the bare minimum install, no extras. I didn't install a DE because I wanted to use i3-gaps.

i3-gaps is not in the repos, so I build it from [Airblader's Github]("https://github.com/Airblader/i3"). Then, I installed X and xinit so I could, run the thing.

I don't have a display manager or login manager. The way I currently have it set up is i3 is started from ~/.xinitrc. This works fine, and i3 loads with i3status on the bottom. But when I hit Super+Return to launch a terminal, it stalls. When I try to launch x-terminal-emulator, I get: 
```
Unable to init server: Could not connect: Connection refused
# Failed to parse arguments: Cannot open display:
```

Assuming this may have to do with not having a terminal emulator installed, I installed xterm. But when I try to launch that, I get a similar error:
```
xterm: Xt error: Can't open display:
xterm: DISPLAY is not set
```

When I try to echo $DISPLAY, I get a blank line. When I try to set the display using export DISPLAY=:0.0, I get all the same errors (except $DISPLAY returns the value I set it to).

I've obviously missed something with my x-server. Any thoughts? I'd rather not install lightdm since I'm only running i3.

FYI: I started this little project (turning a 15 year old laptop into a lean i3 machine) with Arch, which was overkill for what I'm trying to do. I thought the ubuntu minimal install would be easier. And it's been a piece of cake, until this little roadblock.

Any and all help appreciated.

---

