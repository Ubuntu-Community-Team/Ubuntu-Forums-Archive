---
title: "Problems in EQuake"
date: 2005-05-23
forum: Gaming &amp; Leisure
---

### Post by Muiske on 2005-05-23
Hello everyone! 

I'm new on this forum, and I'm also new with Linux (and Ubuntu). I'm learning all there is to learn, but in the meantime I'm having some troubles, and I would certainly appreciate some help from more experienced users. Ok, so what's the problem?

1 - I cannot install the original quake. 

I did everything according to [http://www.tldp.org/HOWTO/Quake-HOWTO.html](http://www.tldp.org/HOWTO/Quake-HOWTO.html), but when I try to execute glquake or quake.x11 it stops with the error "segmentation fault". Strange, since running Equake actually IS possible.... 
Anyone?

2 - Equake.

First of all, I have the original games and I copied the *.pak files to the /id1 directory. However, I cannot play episodes 2 till 5. Do I need to 'tell'  the program that the paks are there? If so, how?

Then, the sound doesn't work. ALSA is installed.. and the sound works, but not in quake. Do I have to change something?

Another problem. When I exit EQuake, I get this error:

/dev/dsp: Broken pipe
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x2a00002
  Serial number of failed request:  1153
  Current serial number in output stream:  1155

X is stretched and distorted. It gets back to normal when I change the resolution and then turn it back on the original value, but it would be nice if this problem could be avoided. Anyone?

Thanks.

---

### Post by phen on 2005-06-07
dont know about quake, but for equake, there is a simple solution to your sound problem:

there is a "glx" file in the run/ directory. It can be used to start fuhquake. there are also other scripts alike.

you have to add some lines for the sound to work. my "glx" script is below:

```

# Force 48k Hz in quakeworld
echo "fuhquake.svga 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "fuhquake-gl.glx 0 0 direct" > /proc/asound/card0/pcm0p/oss

# Disable recording for quakeworld
echo "fuhquake-gl.glx 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "fuhquake.svga 0 0 disable" > /proc/asound/card0/pcm0c/oss

echo "fuhquake.svga 0 0 disable" > /proc/asound/card0/pcm1c/oss
echo "fuhquake-gl.glx 0 0 disable" > /proc/asound/card0/pcm1c/oss

#export LD_PRELOAD=/lib/libpthread.so.0

cd ../
./fuhquake-gl.glx -current -fullscreen -conwidth 320 -conheight 240 -particles 8192 -ruleset smackdown +cfg_load opengl.cfg +cfg_load phen.cfg -norjscripts -gamma 0.9

``` 



the first six "echo" lines are new. The "export" line is commented out, because otherwise my installation didn't run.

hope this helps!

kai

---

### Post by Muiske on 2005-06-13
[QUOTE=phen]dont know about quake, but for equake, there is a simple solution to your sound problem:

there is a "glx" file in the run/ directory. It can be used to start fuhquake. there are also other scripts alike.

you have to add some lines for the sound to work. my "glx" script is below:

```

# Force 48k Hz in quakeworld
echo "fuhquake.svga 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "fuhquake-gl.glx 0 0 direct" > /proc/asound/card0/pcm0p/oss

# Disable recording for quakeworld
echo "fuhquake-gl.glx 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "fuhquake.svga 0 0 disable" > /proc/asound/card0/pcm0c/oss

echo "fuhquake.svga 0 0 disable" > /proc/asound/card0/pcm1c/oss
echo "fuhquake-gl.glx 0 0 disable" > /proc/asound/card0/pcm1c/oss

#export LD_PRELOAD=/lib/libpthread.so.0

cd ../
./fuhquake-gl.glx -current -fullscreen -conwidth 320 -conheight 240 -particles 8192 -ruleset smackdown +cfg_load opengl.cfg +cfg_load phen.cfg -norjscripts -gamma 0.9

``` 



the first six "echo" lines are new. The "export" line is commented out, because otherwise my installation didn't run.

hope this helps!

kai[/QUOTE]


Thanks kai,
I'll try this asap.

---

