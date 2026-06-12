---
title: "Unity missing Dash and panel"
date: 2013-09-06
forum: Desktop Environments
---

### Post by SuperFreak on 2013-09-06
I usually use cinnamon 1.8 on my Ubuntu desktop, but ran into problems [Here]("http://ubuntuforums.org/showthread.php?t=2171607"). Out of curiousity,after I "fixed" my problem I  tried Unity DE again but find the Dash and left hand panel missing and the screen partially frozen (mouse works but I can't click on anything). I would like to give Unity another try can someone help me out.
Thanks

---

### Post by Bashing-om on 2013-09-06
SuperFreak; Hi !

Commands differ depending on what version is installed. Please to advise the installed version/distro.

[INDENT][INDENT]help us to help you
[/INDENT][/INDENT]

---

### Post by SuperFreak on 2013-09-06
Thanks for replying
Ubuntu 12.04.2 Precise Pangolin  64 bit Desktop Env: Cinnamon 1.8

---

### Post by Bashing-om on 2013-09-06
SuperFreak;
> 
Unity DE again but find the Dash and left hand panel missing and the screen partially frozen (mouse works but I can't click on anything). I would like to give Unity another try


try:
```

sudo dkpg-reconfigure unity

```


[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by SuperFreak on 2013-09-06
david@MainSqueeze:~$ sudo dkpg-reconfigure unity
[sudo] password for david: 
sudo: dkpg-reconfigure: command not found
david@MainSqueeze:~$

---

### Post by Bashing-om on 2013-09-06
SuperFreak; Well ...

The command is correct.. maybe you do not even have unity installed ?

```

dpkg -l unity

```

[INDENT][INDENT]a tale in the telling
[/INDENT][/INDENT]

---

### Post by SuperFreak on 2013-09-06
If I issue this command "unity --replace" dash appears but as soon as I close my session or logoff it is gone on next logon


edit: I should add that when I issue the command there are errors in terminal and terminal does not seem to go back to $

---

### Post by SuperFreak on 2013-09-06
When I log into Ubuntu DE
```
echo $DESKTOP_SESSION
```

yields ```
ubuntu
```

according to [THIS]("http://www.liberiangeek.net/2011/10/how-to-quickly-find-out-if-ubuntu-is-running-unity-3d/")
it indicates that 3D Unity is in use

---

### Post by Bashing-om on 2013-09-06
SuperFreak; Yeah.

That does indicate unity 3D... ok .. lets try this to reset the config files.
Go to a text terminal using alt-ctrl-F1
    Stop LightDM with:
```
 sudo stop lightdm
```
Now terminal code:    
```
sudo dpkg-reconfigure lightdm 
```
to set the default display manager.
Reboot:
```
sudo shutdown -r now
```

[INDENT][INDENT]maybe now ?
[/INDENT][/INDENT]

---

### Post by SuperFreak on 2013-09-06
Still no luck....It is not crucial to get into Unity I can still use Cinnamon but it would be nice

---

### Post by SuperFreak on 2013-09-06
I get temporary use of Unity with command ```
unity --replace
```



But it results in these errors in terminal:
```
david@MainSqueeze:~$ unity --replace
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/david/.compiz/session to /home/david/.compiz-1/session
[LOG]: Copied file /home/david/.compiz/session/1056c6c0b3cf8d7ccd137850318076204900000243660054 to /home/david/.compiz-1/session/1056c6c0b3cf8d7ccd137850318076204900000243660054
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:2819): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
WARN  2013-09-06 22:38:11 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x111d920

WARN  2013-09-06 22:38:11 unity <unknown>:0 Failed to fetch path: No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0x111d920
WARN  2013-09-06 22:38:11 unity <unknown>:0 Unable to fetch children: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x111d920

ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 2
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 3
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 4
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 5
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 6
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 7
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 8
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 9
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 10
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 11
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 12
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 13
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 14
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 15
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 16
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 17
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 18
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 19
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 20
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 21
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 22
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 23
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 24
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 25
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 26
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 27
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 28
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 29
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 30
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 31
ERROR 2013-09-06 22:38:11 unity.glib <unknown>:0 g_hash_table_lookup: assertion `hash_table != NULL' failed
WARN  2013-09-06 22:38:11 unity <unknown>:0 No listener with the specified ID: 32
WARN  2013-09-06 22:38:11 unity <unknown>:0 Failed to fetch type: No such interface `org.ayatana.bamf.window' on object at path /org/ayatana/bamf/window44040197
ERROR 2013-09-06 22:38:11 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
Starting gtk-window-decorator
WARN  2013-09-06 22:38:11 unity.libindicator <unknown>:0 Desktop file '/home/david/Desktop/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct


```

Perhaps that gives some clues?

I am sure I did something in the past that has wrecked Unity but I really don't know what

---

### Post by Bashing-om on 2013-09-06
SuperFreak; Well,

supposed to work .. and we will continue our efforts to get it to work.
Lemme have some time ..see what I can come up with for troubleshooting what file(s) are not holding true.


[INDENT]I will be back much later
[/INDENT]

---

### Post by Bashing-om on 2013-09-06
SuperFreak; 

Re-thought what I had in mind .. I am concerned that wiping the desk top will also remove Cinnamon, not a good thing at this time.

Let me sleep on it .. and see what else I can come up with.

[INDENT][INDENT]haste makes waste
[/INDENT][/INDENT]

---

### Post by SuperFreak on 2013-09-07
Thanks for your caution
I should also note that to solve my issues on the post I linked to at the beginning of this thread(see link post 1), I had to make Nemo the default file manager so Cinnamon worked; not sure if that has any impact on Unity. The problems I had with Cinnamon were very similar to the issues I have now with Unity.

---

### Post by SuperFreak on 2013-09-07
Good Day Bashing-om
I have some good news. I was reading another post about similar troubles with Unity and the OP mentioned Unity 2D worked but not 3D. I hadn't thought of this before but I tried Ubuntu 2D and presto it works fine (I am in it now). From my perspective this is probably adequate for me to try Unity out and get a feel for it. So rather than insist on more help I am letting you off the hook and accepting what I have.
Would Unity 3D not work because I don't have a video card (I use the onboard ivy bridge video on my 3770K chip)?

---

### Post by Kevin_Arnold on 2013-09-07
Try putting it back to Unity 3D and rename your ~/.config folder then log out and back in. If it still doesn't work, just set the folder back and no harm done.

This is what fixed the issue for me.

---

### Post by SuperFreak on 2013-09-07
> **Kevin_Arnold said:**
> Try putting it back to Unity 3D and rename your ~/.config folder then log out and back in. If it still doesn't work, just set the folder back and no harm done.

This is what fixed the issue for me.

Thanks but on logging on again I get a purple screen in Unity 3D with no dash or panel. Logging onto Cinnamon all my settings are gone but Cinnamon functions.
Ended up reverting to old Config file

---

### Post by Bashing-om on 2013-09-07
SuperFreak; Hi !

Yeah, I agree if something is good enough.. best let well enough alone. Having different desk top environments may lead to conflicts (GTK2/3 engines in particular) in themes and icons.
To see if your card and driver support 3D:
```

/usr/lib/nux/unity_support_test -p -f

```
All responses must be yes.
It is also a thought that one may have to change the driver to get 3D support if the card supports 3D.

[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by SuperFreak on 2013-09-07
> **Bashing-om said:**
> SuperFreak; Hi !

Yeah, I agree if something is good enough.. best let well enough alone. Having different desk top environments may lead to conflicts (GTK2/3 engines in particular) in themes and icons.
To see if your card and driver support 3D:
```

/usr/lib/nux/unity_support_test -p -f

```
All responses must be yes.
It is also a thought that one may have to change the driver to get 3D support if the card supports 3D.

[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

All responses were yes.
I am satisfied with using Unity 2D until I install the next LTS at which time I will likely do a clean install which should fix this matter.
I won't mark this as SOLVED as the issue was not really resolved, but thank you for your kind help:neutral:

---

### Post by Bashing-om on 2013-09-07
SuperFreak; Good 'nuff,
I do not advocate closing this thread as "solved"; that would miss-lead others searching for a solution.
It is a long time yet until the next release LTS... if you get to where you want to continue this, I am more than willing to put some more effort into it.

[INDENT][INDENT]in for a penny in for a pound
[/INDENT][/INDENT]

---

### Post by SuperFreak on 2013-09-07
Thanks...for now I think I am OK

---

### Post by Jim_in_Omaha on 2013-09-09
I have had this issue a few times. This is the second time it killed my Unity after a UPDATE took place. For me I run two GTX 470 Nvidia video cards and have dual monitors. So I finally remembered that I have to reinstall the Nvidia drivers to fix the problem. For my system, making sure I back up the xorg.conf before is critical as to the wacky configuration I have set up. The primary card is actually in the secondary slot because I have a giant ProlimaTech cooler on it. I did that because Unity makes the primary card run hot while just using the desktop. I did not like hearing the stock fan cranked up on the video card while doing basic work. I like the cards for OpenCL and CUDA stuff.

---

### Post by sena-akada on 2013-09-09
I would advise installing Bleachbit [http://bleachbit.sourceforge.net/download/linux](http://bleachbit.sourceforge.net/download/linux) and running in via the Terminal with the command ' sudo bleachbit'. Tick everything except wipe space and memory and let it do its thing.

---

