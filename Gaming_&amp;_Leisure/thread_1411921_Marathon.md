---
title: "Marathon"
date: 2010-02-20
forum: Gaming &amp; Leisure
---

### Post by NovaWasp on 2010-02-20
I see a lot of requests for a single player first person shooter.

I've got Marathon up and running in 9.10 32 bit.

You can get the engine, AlephOne, from here:

[http://source.bungie.org/index.php/Main_Page](http://source.bungie.org/index.php/Main_Page)

You'll need a few dependencies:

```

sudo aptitude install libsdl1.2-dev libsdl-image1.2-dev libsdl-net1.2-dev bcp libsmpeg-dev libmad0-dev libsndfile1-dev libvorbis-dev libspeex-dev libasound2-dev libgl1-mesa-dev liblua50-dev lua50 
```

From the AlephOne-20100218 directory run:

```

./configure --enable-opengl --enable-mad --enable-sndfile --enable-vorbis --enable-lua --disable-speex 
```

then ```

sudo checkinstall

```

Now you're installed but you need the Scenarios (M1A1, Marathon 2, Marathon Infinity):

[http://alephone.cebix.net](http://alephone.cebix.net)

Unzip the scenario directories to the /usr/local/share/AlephOne/

Then you can put a script in your home folder with 

```

#! /bin/sh
export ALEPHONE_DATA=/usr/local/share/AlephOne:/usr/local/share/AlephOne/AlephOne-M1A1-1.0
/usr/local/bin/alephone $*

```

This will launch M1A1 (Marathon).

Have fun.

---

