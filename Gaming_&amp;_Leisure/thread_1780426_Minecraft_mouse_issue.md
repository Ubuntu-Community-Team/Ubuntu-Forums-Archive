---
title: "Minecraft mouse issue"
date: 2011-06-12
forum: Gaming &amp; Leisure
---

### Post by ulnarstyloid on 2011-06-12
I think this may be an issue with mouse input as opposed to java-- what happens when I load Minecraft is everything loads and renders perfectly, but I spawn with my mouse stuck straight down.  I can spin, sort of, mine, place blocks, and move.  I just can't look round.
The problem remains in all 3 USB ports, and with two different mice.
I'm running Ubuntu 10.10 on a HP laptop, and am using xserver-xorg-video-radeon as opposed to fglrx.  (Prior to switching, Minecraft wouldn't run at all.)
I've also updated the lwjgl files and everything.
I'm still learning my way round Ubuntu-- I know there's probably some sort of readout I could get through the terminal that would provide a major clue, but I'm not sure what it'd be.
Thanks in advance!

---

### Post by desktorp on 2011-06-12
Some will say it doesn't matter, but are you using OpenJDK or the official Oracle/Sun JRE?  Mojang recommends the official one.

Also, not sure about Minecraft and joystick/gamepad inputs, but do you happen to have a gamepad sitting on the floor with a dpad/analog stick being pressed?  I had this happen once when I had *mysterious* mouse problems in GTA3.  Felt pretty dumb for a minute, but no one saw me do it.

---

### Post by ulnarstyloid on 2011-06-12
> **desktorp said:**
> Some will say it doesn't matter, but are you using OpenJDK or the official Oracle/Sun JRE?  Mojang recommends the official one.

Also, not sure about Minecraft any joystick/gamepad inputs, but you don't by chance, have a gamepad sitting on the floor with a dpad being pressed, do you?  I had this happen once when I had *mysterious* mouse problems in GTA3.  Felt pretty dumb for a minute, but no one saw me do it.

I'm opening it with the official Sun JRE, but I think I may have OpenJDK installed also-- should I try removing those packages?
And nah, I don't have a gamepad or anything.  I do have a tablet for art and whatnot, but it's not plugged in.

---

### Post by desktorp on 2011-06-13
Typically it's not a big deal for OpenJDK to exist alongside Sun's JRE, but some people choose to remove it anyhow, just to make sure it's nice and dead.  It's worth a shot anyhow.  If you *know* you're telling it to run using Sun's JRE, it's probably not a problem with OpenJDK.  I honestly don't know a ton about using the terminal to get decent error output.  I do this for Wine error reporting sometimes, but I typically never see any extra output after launching Minecraft, if I do it from the terminal.  I suppose mine is working properly though, so that's another thing that's worth a shot.

Dunno if you just do java -jar minecraft.jar or if you use Mojang's suggested string.. I just do it the plain way because I haven't had any (noticeable) memory problems.  Sorry it's not being quickly resolved.  It sounds like a weird problem.

---

