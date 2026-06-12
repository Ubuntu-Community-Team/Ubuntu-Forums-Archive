---
title: "TUTORIAL: Return to Castle Wolfenstein WITH sound under PulseAudio"
date: 2010-07-18
forum: Gaming &amp; Leisure
---

### Post by thanius on 2010-07-18
I've had some trouble getting Wolfenstein to groan with german accents under Lucid Lynx, so I thought I might help others getting the sound to work without the need to uninstall PulseAudio.

1. **Install RTCW** using [the normal instructions]("http://zerowing.idsoftware.com/linux/wolf/"), preferably updating the game to the latest binary

2. Since RTCW still uses OSS for its sound we need to **give it permissions for it** to use the emulation under ALSA. Open up a new terminal and input the following:

```
# gksudo gedit /etc/init.d/redirect_oss
```

[INDENT]Enter the following into the new file and save:[/INDENT]

```
# Return to Castle Wolfenstein
 
echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
echo "wolfsp.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "wolfmp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
echo "wolfmp.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss"

```

[INDENT]It is possible the that *disable* options (disable capture/microphone) aren't necessary, but some applications and games need this off apparently.[/INDENT]

3. **Give the file executable permissions**:

```
# sudo chmod +x /etc/init.d/redirect_oss
```

4. **Update the startup scripts** so that the above script executes every boot:

```
sudo update-rc.d redirect_oss defaults
```

5. **Edit or create a new launcher script** for RTCW so that we can **temporarily disable PulseAudio** when running the game, I used *wolf* in the game directory:

```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory
  cd "/PATH_TO_WOLFENSTEIN_INSTALLATION/"
  pasuspender ./wolfsp.x86 $*
  exit $? 
```

[INDENT]Change *wolfsp.x86* to *wolfmp.x86* in a seperate launcher script to make the sound work under multiplayer.[/INDENT]

6. Give the *wolf* script executable permissions if it doesn't have them already:

```
# chmod +x /PATH_TO_WOLFENSTEIN_INSTALLATION/***wolf***
```

7. Enjoy! Here's an updated icon:

[ATTACH]163822[/ATTACH]

---

