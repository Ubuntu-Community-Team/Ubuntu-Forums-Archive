---
title: "compiz-fusion cube with 3d windows"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by luckyd on 2007-06-27
In beryl, there was a plugin called 3d that lifted the windows off the cube when you rotated it, but now in compiz-fusion I can't find that plugin... Does it exist or am I just missing it?

---

### Post by superyounan1 on 2007-06-27
i dont think its implemented yet, i'd be surprised if it doesnt come eventually

---

### Post by AriciU on 2007-06-27
It's not implemented yet.

---

### Post by throwingks on 2007-06-28
[http://compiz.org/Plugins](http://compiz.org/Plugins)

It is called 3D Plugin

---

### Post by amadeus266 on 2007-07-01
How do you install it?

---

### Post by luckyd on 2007-07-02
bump i really want to know how to do this

---

### Post by AriciU on 2007-07-02
It's not yet supported in Fusion. What's so hard to understand? :)

If you really want it then go back to Beryl or the old Compiz.

---

### Post by Billy_McBong on 2007-07-02
[COLOR="Blue"]it says on [this]("http://smspillaz.wordpress.com/2007/07/02/compiz-fusion-community-news-edition-8-for-july-01-2007-were-hoving-above-windows/") compiz fusion blog that this weeks update includes a 3-d window plugin. i cant get it work though, can anyone else?[/COLOR]

---

### Post by andrewsomething on 2007-07-02
> **Billy_McBong said:**
> [COLOR="Blue"]it says on [this]("http://smspillaz.wordpress.com/2007/07/02/compiz-fusion-community-news-edition-8-for-july-01-2007-were-hoving-above-windows/") compiz fusion blog that this weeks update includes a 3-d window plugin. i cant get it work though, can anyone else?[/COLOR]

I'm running version 1:0.5.1+git20070702~3v1ubuntu0 from Trevino's repo, and none of the new features seem to be there yet for me either. Chances are the debs are a couple days behind the source. If you really can't wait, try compiling from the source.

---

### Post by Billy_McBong on 2007-07-02
> **andrewsomething said:**
> I'm running version 1:0.5.1+git20070702~3v1ubuntu0 from Trevino's repo, and none of the new features seem to be there yet for me either. Chances are the debs are a couple days behind the source. If you really can't wait, try compiling from the source.[COLOR="Blue"]
im using that repo too, so were gonna get those effects in a couple of days? awesome:D[/COLOR]

---

### Post by luckyd on 2007-07-04
> **AriciU said:**
> It's not yet supported in Fusion. What's so hard to understand? :).

What's so hard for me to understand is this page [http://forums.opencompositing.org/viewtopic.php?f=19&t=1067&p=8404&hilit=cube+gears#p8404](http://forums.opencompositing.org/viewtopic.php?f=19&t=1067&p=8404&hilit=cube+gears#p8404) which gives a tutorial on how to install the plugin. However when I follow their method I get the following output

> 
convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: No such file or directory
make: *** [build/3d_options.h] Error 127


---

### Post by Vorian on 2007-07-04
first install git
```
sudo apt-get install git git-core
```

then git the plugin
```
git-clone git://anongit.opencompositing.org/fusion/plugins/3d
```

then
```
cd 3d
```

then
```
make && make install
```

you should see this
```
convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h
bcop'ing  : build/3d.xml -> build/3d_options.c
schema    : build/3d.xml -> build/compiz-3d.schema
compiling : 3d.c -> build/3d.lo
compiling : build/3d_options.c -> build/3d_options.lo
linking   : build/lib3d.la
install   : /home/vorian/.compiz/plugins/lib3d.so
install   : /home/vorian/.compiz/metadata/3d.xml
install   : build/compiz-3d.schema
```

then run
```
metacity --replace
```

then
```
compiz --replace
```

In your CCSM you will see the 3d plugin.  Configure to your liking.

---

### Post by jjross on 2007-07-05
I am getting the same thing even after following Vorians directions
```
convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: not found
make: *** [build/3d_options.h] Error 127

```

---

### Post by AndrewGene on 2007-07-05
> **jjross said:**
> I am getting the same thing even after following Vorians directions
```
convert   : 3d.xml.in -> build/3d.xml
bcop'ing  : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: not found
make: *** [build/3d_options.h] Error 127

```

...same here exactly.  I also get this error with the snow plugin...

---

### Post by stepol on 2007-07-05
I did this morning a complete uninstall / install with all compiz-fusion extra's and now I have the 3dplugin and a bunch more . I am using the Trevino-repo , hope this can be of some help for someone .:D

---

### Post by luckyd on 2007-07-05
The 3d plugin was in the trevino-repo?

---

### Post by explemonk on 2007-07-05
> **luckyd said:**
> The 3d plugin was in the trevino-repo?

I just found it in the package **compiz-fusion-plugins-unofficial**.

---

### Post by christhemonkey on 2007-07-05
Theres also a package called compiz-fusion-plugins-unsupported wonder what lovelies are in there......

---

### Post by AriciU on 2007-07-05
> **AndrewGene said:**
> ...same here exactly.  I also get this error with the snow plugin...

You must install bcop (apt-get install compiz-bcop).

However, after installing it and trying to compile i'm getting:

> make && make install
bcop'ing  : build/3d.xml -> build/3d_options.h
bcop'ing  : build/3d.xml -> build/3d_options.c
schema'ing: build/3d.xml -> build/compiz-3d.schemawarning: failed to load external entity "/schemas.xslt"
cannot parse /schemas.xslt
make: *** [build/compiz-3d.schema] Error 4


---

### Post by AriciU on 2007-07-05
Ok, got it to work.

> apt-get install compiz-dev

---

### Post by AndrewGene on 2007-07-06
okay i typed "sudo apt-get install compiz-dev" and then "sudo apt-get install compiz-bcop" and then the snow plugin works.  The 3d plugin still gives me an error.

---

