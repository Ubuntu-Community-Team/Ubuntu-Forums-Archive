---
title: "Program Windows Randomly Go Dark"
date: 2012-12-22
forum: Desktop Environments
---

### Post by Acharn on 2012-12-22
This is a problem I've had for a long time. I now have reason to suspect it's got something to do with compiz, but their forums don't work. I was able to register, but when I log in I get a message that I'm logged in and then I'm returned to the main page which says I'm not logged in. Anyway, I was able to read their post on how to request support, and one of the things they said might be useful was to include output from the command 'compiz --replace ccp&', so I ran that command. The output contained a bunch of warning and error messages, failed assertions, and one line which said "It should not be possible for you to be here. You should probably file a bug report." When I tried to follow their link to their bugtracker I got a '502 Bad Gateway' error.

The problem is that from time to time the window of the program I'm using, usually Firefox but sometimes totem or calibre, will go dark and is unresponsive. All programs slow down or halt. Windows take a long time to raise when I click on them. After a while, from a few seconds to a few minutes, everything resumes normally. Until the next time it happens. Today I was able to get a terminal open and run 'top' while the browser window was still dark, and the topmost program every time 'top' refreshed was 'compiz.' It was only using 14% of CPU and 1.5% of memory, but I've been watching and it is usually the topmost program for the duration of these events. When the program returns to normal, 'compiz' ceases to be the topmost program.

I'm not sure what to do next. Is there some other place than compiz.org to look for support? To report this possible bug? Would it be a good idea to try uninstalling compiz and reinstalling it? I like the Unity desktop, but I don't really use the compiz effects. This isn't a fatal problem, but it's hugely annoying now that I got my internet connection working right. Does the Unity desktop depend on compiz?

---

### Post by Hylas de Niall on 2012-12-22
> **Acharn said:**
> Does the Unity desktop depend on compiz?

Yes.

I've had this problem a lot in the past, but in my case i simply put it down to the underpowered Atom processor in my netbook struggling.

If you have a similar processor that may be the problem (IMO).

In the end i switched distros to one that wasn't so 'heavy'.

---

### Post by Acharn on 2012-12-22
Thanks for the suggestion. I have an Acer Aspire M-1610, which has only 1GB RAM and an ATI Radeon x1550 graphics card, so I've often blamed the GPU, but today I started looking at log files and there's something going on. I suspect compiz or unity. Mayby I should switch to using a different desktop for a while and see if that helps, but I really like unity. I could try a different distro. I started out with Debian and then moved to FreeBSD, so I could relearn that (the BSD file system is laid out a little differently, some commands have different names of different behaviors). But I like Ubuntu and find it easy to use. At my age I don't want to be bothered with having to read man pages again.

I think I made a terrible choice for the title of this thread. Maybe I should mark this one [SOLVED] and start a new one. I'm surprised that I haven't found a thread talking about getting support for compiz, since their organization seems not to exist any more. Or at least doesn't interface with the public.

---

### Post by grahammechanical on 2012-12-22
Why do you think that this is an issue with Compiz? This going grey of an application window is caused by memory and CPU usage.

I get it when the Ubuntu Software Centre is first loaded and it needs put adverts on the screen. I used to get with Libreoffice when I open two windows and put large documents in them. The window that the second document is loading into goes grey for a little while. This has improved recently.

Compiz is the Compositing Window Manager. So, it will use memory and CPU when we do anything in an application. Even if it is only typing. Applications hold on to memory space that they have claimed just in case it is needed again.

Does Compiz release the memory that is allocated to it after a few minutes of screen inactivity?

Does the memory and CPU usage of Compiz get larger over time?. This used to happen about a year ago. It was noticed by those of us testing the development branch of Ubuntu. And yes it was reported on in this forum and reported as a bug.

I do not see this happening now on my version of 13.04 that I am testing. You can also look in top for something called unity-panel-ser. In the past that had a tendency to use a lot of memory. But it was fixed. And then there is hud-service.

Regards.

---

### Post by Acharn on 2012-12-23
Well, I first started to wonder about compiz yesterday when my browser window went dark for longer than usual. I was able to get top running and noticed that compiz was the topmost program for the whole remaining time the window remained dark. It was only using about 14% of CPO and 1.5% of memory, but it was still the topmost program every time top refreshed. I only have 1GB of RAM, so I had long thought that might be the problem, but top was showing that I still had 80-120MB of memory free during this time. So I started googling compiz, found their web site, went to their fupport forum and read the first item which was a description of the info I should send with a support request. I registered, but every time I tried to log in I got a page with a lot of PHP error messages at the top saying I was logged in, and then was automatically redirected back to the main page which told me I was not logged in. When I went to their wiki and tried to follow the link to their bug reporting site I got a '502 - Bad Gateway' error. All the messages I saw on their forum appeared to be spam, so I infer they do not have a publicly available web site.

Anyway, back to the reason I suspect compiz. One of the things they recommended to gather information was to run the command "compiz --replace ccp&'. When I did that yesterday I had been running the desktop for several hours and the command took several minutes to run. When I did it today I got this:
```

roger@roger-Aspire-M1610:~$ compiz --replace ccp&
[1] 9924
roger@roger-Aspire-M1610:~$ Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
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

(compiz:9924): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
WARN  2012-12-23 13:33:10 unity.libindicator <unknown>:0 Desktop file '/usr/share/app-install/desktop/chromium-browser:chromium-browser.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-12-23 13:33:10 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-12-23 13:33:10 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-12-23 13:33:10 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
ERROR 2012-12-23 13:33:10 unity.glib-gobject <unknown>:0 g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "backlight_mode"
^C
roger@roger-Aspire-M1610:~$ Failed to open VDPAU backend libvdpau_r300.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r300.so: cannot open shared object file: No such file or directory
Failed to open VDPAU backend libvdpau_r300.so: cannot open shared object file: No such file or directory
^C

```
It hung on the 'Setting Update "backlight_mode"' so I hit ^C and then it went on to give me the lines about VDPAU. Yesterday there were more failed assertions and one line to the effect: "you should never have been able to arrive here - probably you should report a bug."

So I wanted to find out more about compiz's current status. It may not be the cause of my problems, but I would like to find out if my setup is OK. Oh, yeah, it's compiz version 0.9.7.9.

---

### Post by Open and Sourced on 2012-12-23
Probably have to reinstall. Compiz does depend on Unity, so make sure to reinstall.

---

### Post by Acharn on 2012-12-24
I think so too, but I'll wait just a bit. Funny thing, since I've run that compiz command twice I haven't had a window go dark on me. I'll wait until it starts happening again.

---

### Post by Acharn on 2012-12-26
I suppose I shouldn't post to a thread I've already marked solved, but today I noticed another possible factor. This time I had top already running when the browser window went dark, and I noticed that the uppermost process was kswapd0, a kernel process that does something with swap space. Although I only have 1GB RAM I have 5GB swap space. When I run top I never see that more than about 700MB is used. Which makes sense to me, because I just don't run a bunch of programs at the same time. I would have thought 1GB RAM is humongous. Heck, my first computer was a Radio Shack Model III with 48K RAM, the max -- tho other 16K was ROM that included the BASIC interpreter (gotta say Bill Gates and Paul Allen were code gods to do that). Anyway, I really want to find out what's the real cause of this problem.

---

