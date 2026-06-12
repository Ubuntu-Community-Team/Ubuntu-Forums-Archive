---
title: "How-To use RemoteApp, local Win7 KVM or Virtual Box  for hybrid desktop environment"
date: 2012-05-17
forum: Desktop Environments
---

### Post by bmullan on 2012-05-17
I thought I'd pass on this useful information to Ubuntu users.

This write-up is in reference to use of two things:
[LIST=1]
[*]Microsoft's [[COLOR="Blue"]_RemoteApp_[/COLOR]]("http://technet.microsoft.com/en-us/library/cc755055.aspx") capability
[*][[COLOR="Blue"]_FreeRDP_[/COLOR]]("http://www.freerdp.com/") (open source tool that now supports RemoteApp)
[/LIST]
I'm sure there are a lot of people like myself that have their machines either setup to dual boot (Linux/Windows) or run a Windows KVM or VirtualBox type setup so they can get access & use some Windows app that their job etc requires at some time.  

Although the KVM/VirtualBox is more convenient than Dual Boot... you still deal with both the Ubuntu/Linux & Windows "full" desktops so I thought I'd see if there was just a way to run the Windows KVM or VirtualBox guest minimized and use FreeRDP to create some Linux Desktop launchers so I could just bring up any Windows App I wanted whenever I needed it.

Sticky part was that most people _think_ that RemoteApp's requires a Windows 2008 Server and Windows 2008 Server requires another Microsoft license from the Windows 7 license I already own.   Then also, to run RemoteApp on Windows 2008 Server you have to configure Terminal Services... which is another license.

I learned recently that certain versions of Windows XP, Windows 7, Vista, etc can all be configured to support RemoteApp without Terminal Services required.

First, I learned how to do it the hard way through using regedit & adding quite a few registry entries.

However, I later learned a much easier way using a tool described at this site:
[[COLOR="Blue"]_http://sites.google.com/site/kimknight/remoteapptool_[/COLOR]]("http://sites.google.com/site/kimknight/remoteapptool")

So I took my CD copy of Windows 7 Ultimate (Enterprise works too) and installed it using KVM onto my Ubuntu PC.

After installing the Win7, I installed all my other Windows related apps onto that KVM Windows VM.

Then I installed the above remoteapptool using the instructions in the above URL.

Since I am only using my own Win7 license, my own licensed applications and only using RemoteApp for my personal use I can't see any problem doing this or that it violates any licenses.

Anyway I used the above tool to setup all the installed Windows applications as "remoteapp", I also created Launcher Icon's on my Ubuntu Desktop with the launcher command being the required FreeRDP command line for each app.

It works great and now I just have only my Ubuntu Desktop with all the applications available that I need from either Linux or Windows that I can launch, resize, move around etc.

Thought this might be something others might find useful as well.

FYI... FreeRDP is already in the Ubuntu Repositories.. and that one works but it is not the latest update.  If you want that then I'd suggest either finding someone who is packaging the latest/greatest and use their PPA or just download and install FreeRDP using the instructions found on their Wiki here:

[[COLOR="Blue"]_https://github.com/FreeRDP/FreeRDP/wiki/Compilation_[/COLOR]]("https://github.com/FreeRDP/FreeRDP/wiki/Compilation")

Brian

---

