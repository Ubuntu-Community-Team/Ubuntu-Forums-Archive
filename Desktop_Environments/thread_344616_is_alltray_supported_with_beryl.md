---
title: "is alltray supported with beryl?"
date: 2007-01-23
forum: Desktop Environments
---

### Post by tisk on 2007-01-23
I installed beryl and now alltray to minimize some programs that are cluttering my desktop.
I can get alltray to work with metacity, but not with beryl. Is there any way to use both?

thanks for any insights :D

---

### Post by Cyr4x on 2007-01-28
The same problem for me. Any suggestions?

---

### Post by tisk on 2007-01-28
just an update: I haven't got it to work with beryl, but if you install the extension mozztray for thunderbird, you can at least get email to minimize. If you also have the music player icon up you can minimize rhythm box or whatever as well.

---

### Post by nischg on 2007-02-09
I used to have alltray start sunbird when a session was initiated. Since I am using Beryl I no longer have sunbird in the tray. ¿Does any one know a work around so I can have sunbird in the tray with Beryl? There are some addons what I need but only for Win.

---

### Post by maxwellcom on 2007-02-25
same problem here - got beryl to work (w/ xgl and fglrx) and love it, but alltray is now broken.

alltray is such a handy little app (function ought to be built-in for gdm), i'd hate to lose it.

anyone find a solution (other than mozztray)?

thanks

---

### Post by odzx on 2007-03-18
bump

---

### Post by rfdeshon on 2007-04-30
The only way I have found to do this is to change the shortcut to the program that you want to use and preempt it with alltray. For instance, to get thunderbird to work with alltray, right click the icon, click properties and change Command to alltray mozilla-thunderbird. It seems that beryl just prevents the alltray gui from capturing which window you click on, not from alltray actually minimizing programs to the notification area.

EDIT: Unfortunately, my fix makes it so that when you launch the program, it is automatically minimized to the tray.

---

### Post by Ramaddan on 2007-04-30
Hi,

I am not using beryl, but I use AllTray, and AllTray has many great features.

If you go to a Terminal, and type:

> **alltray --help**

It will print out some common options of AllTray.
You can try that, and take a look at the options, as you might really like some of them.

(I will use **gedit** for display purposes)

To change a program's command, just right click the Menu Bar, and then go to the properties
of the program you want to modify, and change the command accordingly.

For example, if you want Gedit to get docked in the Gnome-panel,
without minimizing, you can change the program's command to:
> **alltray --show gedit**

So you just need to add **alltray --show ** in front of the program's command.
The **--show** option instructs AllTray to not minimize the program.

If you want to add a few more whistles, you can also do the following:
> **alltray --show -na gedit**

The **-na** option will remove the **(AllTray)** text that usually comes up in the
title bar when opening a program with AllTray.

Or you can even specify what icon you want to display for the program when it docks
in the gnome-panel, by doing the following:
> **alltray --show -na -i  <path to png> gedit**

Replace **<path to png>** with the path and name of the png icon you want to use.
This will make your program look as if it came with minimize to panel built-in.

You can **try all your commands in the terminal** just to make sure they work properly,
without errors before you pass them to the menu editor, because the menu is not that good
at displaying errors, or whether anything went wrong (I hope that's changed at some point).

Also, as stated above, you can type:
> **alltray --help**

To see all the options available to you. There is even a KDE specific feature
which I did not try out, because I'm using GNOME.

Hope that helps.

**Note: Sometimes with certain programs, things don't work out the way you intended.**

---

### Post by RizSilverthorn on 2007-05-05
That advice works great, especially about the trying it via CLI first.

---

### Post by maxwellcom on 2007-05-05
ramaddan, very helpful- thanks

---

### Post by trifon on 2007-05-14
Actually alltray works almost fine with Beryl, except for the fact that you cannot use it without command parameters. Still I have found two problems (ver. 0.69)
[LIST]
[*]if you use the -na option, then the window has no title at all (instead the title, but without (AllTray) )
[*]especially for mozilla-thunderbird if I start it with "alltray mozilla-thunderbird", then I can not drag-drop messages around folders. Maybe drag-drop has problems for other apps as well, but haven't tried.
[/LIST]
Have you experienced any of these?

---

### Post by tisk on 2007-05-14
the problem is that having to use command parameters takes the effortlessness out of just clicking on a window

---

### Post by Kent84 on 2007-05-28
I experience the same problem (that beryl doesn't like you launching alltray with parameters). So I can't use the "-na" parameter when launching thunderbird. That's only a small price to pay in opinion. Also when un-minimising my thunderbird, the window appears black for a split second before reappearing as normal. This behaviour is different to the normal behaviour when unmaximising others windows.

---

### Post by Ajiah on 2007-06-10
The fix further up worked for me! I just added alltray to the command on the thunderbird icon in my bar, and it worked.

Thanks!

---

### Post by LordKelvan on 2007-06-11
Hey:

I was wondering if there was a way to get alltray to work with wine?  I am using utorrent, and I have this launcher on the desktop to fire it up.  However, if I add "alltray --show" to the front of the command in the launcher so that it now reads:

alltray --show wine path_to_utorrent.exe

the launcher stops working.  Can someone help me?

---

### Post by LordKelvan on 2007-06-11
Rofl, isn't life funny, like 5 min after I posted I found the answer to my problems:

The path to my utorrent.exe has a space in it, and so I just had to escape it, i.e. Program\ Files instead of just Program Files.

Edit:

Credit goes to pt123 at [http://ubuntuforums.org/showthread.php?t=295134&page=4]("http://ubuntuforums.org/showthread.php?t=295134&page=4")

---

### Post by rfurman24 on 2007-06-24
I just added alltray to my Frostwire comand in the application menu and it works like a charm. Thanks.

---

### Post by tisk on 2007-06-24
I think looking back now, I don't use alltray much at all. With beryl I just tend to hide stuff on other workspaces.

---

### Post by starscalling on 2007-07-02
alltray is the pimpieness -  i tend to use it for a few things... though it would be nice if the windows would still show up on the pager correctly while we're at it lol

note: kdocker seems to do just that - just make a menu entry or custom application launcher for the panel.. worx great in beryl here

---

### Post by MeduZa on 2007-09-26
alltray work fine with other applications but not with sunbird.
The first time I used alltray with sunbird works perfectly, when I added few task/events their never start again on the tray
I have the sunbird on my secions (start with the gnome)
this is the error I got on the terminal
> The program 'alltray' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 172 error_code 3 request_code 7 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Any one make it work?

---

### Post by MeduZa on 2007-09-26
ok I got the problem, if I load the sunbird on safe mode, works perfectly on the tray, that means that the problem is an extencion, I remove the BirthdayManager extencion and now is working.
I really don't know if the problem is that, but now is working again

Edit: now sunbird works and start on sysmte tray at startup, but start not minimized and if never minimize to the system tray :S
edit2: fixed, I replaced alltray with kdocker

---

### Post by JoelOl75 on 2008-05-14
There was a bug discussion and it was fixed in a ppa repo...  Add these to your /etc/apt/sources.list

deb [http://ppa.launchpad.net/mtrausch/ubuntu](http://ppa.launchpad.net/mtrausch/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/mtrausch/ubuntu](http://ppa.launchpad.net/mtrausch/ubuntu) hardy main

and 
sudo apt-get update
sudo apt-get upgrade

You can check up on this at [https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583](https://bugs.launchpad.net/ubuntu/+source/alltray/+bug/106583)

---

