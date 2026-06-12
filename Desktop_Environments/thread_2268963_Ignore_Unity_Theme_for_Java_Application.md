---
title: "Ignore Unity Theme for Java Application"
date: 2015-03-12
forum: Desktop Environments
---

### Post by vni.jamie on 2015-03-12
I have a java application (BlueVue Device Manager) that very poorly adapts to the dark theme I have running in Ubuntu-14.04

The application is opened through a shell script

```
#!/bin/bash

export BVDM_VERSION=1.7.13
export BVDMData=~/DManager


cd $BVDMData
java -cp "*" DMLauncher btConfigPath $BVDMData/cfg/ $@

```

Is there a way I can modify this script so that it doesn't attempt to use the dark theme I have running?

I tried the following to no avail (code adapted from [http://askubuntu.com/questions/8336/how-can-one-make-firefox-ignore-my-gtk-theme-entirely](http://askubuntu.com/questions/8336/how-can-one-make-firefox-ignore-my-gtk-theme-entirely))
```
#!/bin/bash

export BVDM_VERSION=1.7.13
export BVDMData=~/DManager


cd $BVDMData
env GTK2_RC_FILES=/usr/share/themes/Ambiance/gtk-2.0/gtkrc java -cp "*" DMLauncher btConfigPath $BVDMData/cfg/ $@



```

I suspect because my Ubuntu-14.04 LTS is using Unity instead of Gnome?


==============================================
Update:
I found this command to set the default look and feel from the command line when running a java application. ([http://docs.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html](http://docs.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html))
`java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel MyApp`

So I tried it with my startupApplication script

[FONT=Verdana]```
#!/bin/bash[/FONT]

[FONT=Verdana]export BVDM_VERSION=1.7.13[/FONT]
[FONT=Verdana]export BVDMData=~/DManager[/FONT]


[FONT=Verdana]cd $BVDMData[/FONT]
[FONT=Verdana]java [/FONT][FONT=Verdana]-Dswing.defaultlaf=com.sun.java.swing.plaf.metal.MetalLookAndFeel[/FONT][FONT=Verdana] -cp "*" DMLauncher btConfigPath $BVDMData/cfg/ $@[/FONT][FONT=Verdana]
```[/FONT]

This didn't do the trick. I tried a couple other look and feel's (motif, gtk) but none of them seemed to have any affect on how the application was rendered.

---

