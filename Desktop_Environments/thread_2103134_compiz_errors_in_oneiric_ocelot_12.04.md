---
title: "compiz errors in oneiric ocelot 12.04"
date: 2013-01-09
forum: Desktop Environments
---

### Post by Acharn on 2013-01-09
I've been having problems with program windows turning dark and unrepsonsive since I first started using the unity desktop -- when was that, 11.10? At first I thought it might be connected with hard disk problems I was having. More recently, while waiting to be able to resume using my browser, I had enough time to get a terminal started and start 'top'. I found that for the time the window remained dark the topmost running program was 'compiz.' Since than I've found that another program that seems to be associated with the problem is 'kswapd0', which is a part of the kernel, and 'plugin-container', which is part of Firefox. I only have 1GB of RAM (seems like that ought to be plenty, but...) but the 5GB swapfile i originally set up never seems to use more than about 500MB. I'm using An Acer Aspire M-1610 with ATI Radeon x1550 graphics card. The thing that really bothers me is that compiz does not seem to have a site I can report bugs at, and I definitely think I should. They used to have a site at [www.compiz.org](www.compiz.org), and the initial sticky post on their user forum offers some advice on information to include when reporting a problem. The forum is broken, although there are some posts which look like all spam. Following one of their recommendations I ran the command 'compiz --replace ccp&':
```
roger@roger-Aspire-M1610:~$ Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1a00cb9

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x44000ba

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

(compiz:12425): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x4e00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x4e00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2013-01-09 17:32:17 unity.libindicator <unknown>:0 Desktop file '/usr/share/app-install/desktop/chromium-browser:chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-01-09 17:32:17 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-01-09 17:32:17 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2013-01-09 17:32:17 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
ERROR 2013-01-09 17:32:18 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "backlight_mode"
Setting Update "icon_size"
^C

```
The command stuck on the last command after about five minutes, and I terminated it after about twenty. I'm especially bothered by those "this should never happen" warnings.

OK, so my questions are these: Should I report a bug, and, if so, where? Should I try to replace 'compiz'? If so, how? Should I use apt-get through the console, would it be better to use the Ubuntu Software Center, or the Synaptic Package Manages? Is it likely I could just run "sudo apt-get reinstall compiz"?

---

### Post by grahammechanical on 2013-01-09
Can you please clarify what version of Ubuntu you are using. The thread title is inaccurate.

If you are still using 11.10 then it would be best to upgrade to 12.04 as a lot of development work has been done on Compiz in the last year.

I have 1GB RAM and in older version of Ubuntu I got the greying of application windows as either CPU or memory resources were used to the maximum. But not with more up to date version of Ubuntu. On my 12.10 Compiz never uses  more than 9% CPU or 8% memory and CPU useage quickly drops.

The place to report bugs is Launchpad

[https://launchpad.net/ubuntu]("https://launchpad.net/ubuntu")

[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

Regards.

---

### Post by Acharn on 2013-01-09
Whoops! My bad. The version I'm using is 12.04, Precise Pangolin. Can't think why I got the name wrong. OK, I'd be amenable to upgrading to 12.10 -- certainly less scary than trying to reinstall compiz -- but the current .iso is too large to fit on a CD. My Lite-on DVD burner worked fine under Windows XP, but it doesn't see BLANK DVDs under Ununtu. Even the DVDs I used it to burn. I've been planning to get a new one but as cheap as they are I can't afford it this month. Maybe next month. I've got the image, and I could mount it with AcetoneISO, but I don't know if that would work. I do have 12.04 on a CD (that version was just small enough), so I suppose if things go wrong I can reinstall 12.04. 

Interesting that you get such low CPU usage. I was just looking at top (the browser window has greyed out a couple of times while I've been writing this) and compiz is only using 14% of CPU while the window is greyed out but firefox and plugin-container are using 30-40% each when the browser is operating.

The reason the "this should not happen" warnings scared me so much is because they are so much like a technique which Brian Kernighan recommended in his book, Software Tools (1976). I think it was in the chapter on writing an editor like ed.

---

