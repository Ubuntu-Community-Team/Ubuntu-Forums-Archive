---
title: "How do I open the packages?"
date: 2006-01-27
forum: Desktop Environments
---

### Post by El Kabong on 2006-01-27
Hey guys, I got another question for ya...

I did everything that is involved here:

[Ubuntu Forums Link]("http://ubuntuforums.org/showthread.php?t=121657")

I edited my source list, and then did "sudo apt-get update" in the command prompt.  I then went to the synaptics program and updated a whole lotta stuff. However, I don't know how to open all the programs that I updated. For instance, in the Communication (universe) tab of synaptic, I got the "smsclient" program. However, I don't know where to go to run that now that I've installed it? Thanks a ton ahead of time for any help!

---

### Post by aysiu on 2006-01-27
Go to Applications > Accessories > Terminal and type ```
man smsclient
```

Not all applications are graphical. Some are terminal-based ones.

---

### Post by El Kabong on 2006-01-27
does that open the manual for it? Thanks for the quick reply, by the way

---

### Post by aysiu on 2006-01-27
[QUOTE=El Kabong]does that open the manual for it? Thanks for the quick reply, by the way[/QUOTE] Yes.

Generally, I've found when you install stuff through Synaptic or apt-get, one of four things happens, depending on the application and how it's packaged:

1. After installation, a menu entry is created for it with an easily clickable icon that launches the application.

2. The menu entry isn't created right away, but if you run the *killall gnome-panel* command, the menu's refreshed and the entry appears.

3. The menu entry never appears, but you can create one with the command, which is usually the same name as the application.

4. There is no menu entry, and it's not easy to create one, as the application itself is not graphical--it's entirely run from the terminal.

---

### Post by El Kabong on 2006-01-27
okay, I tried the man smsclient command, and it said "no manual entry for smsclient."

should I try the killall gnome-panel command? What exactly does that do?

---

### Post by aysiu on 2006-01-27
I hate it when there's no man page, especially since smsclient *is* a command-line utility.

Try this:
[http://www.smsclient.org/](http://www.smsclient.org/)

---

### Post by GeneralZod on 2006-01-27
[QUOTE=El Kabong]okay, I tried the man smsclient command, and it said "no manual entry for smsclient."
[/QUOTE]

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=smsclient&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=smsclient&version=breezy&arch=i386)

Looks like it doesn't come with a man page (naughty!) and has an executable that differs from the package name (slightly naughty!)

Try
```

sms_client

```

instead.

> 
should I try the killall gnome-panel command? What exactly does that do?

No, that won't be necessary - as Aysiu has noted, it's a CLI app and these very, very rarely have menu entries.  Explanation (disclaimer: from someone who knows little of GNOME!) follows.

You've probably noticed that in Windows, when you've installed something, then it's visible in the Start Menu as a soon as you open the menu the next time.  This should be the case in GNOME, but apparently sometimes it goes wrong and you have to restart the gnome-panel (which contains the equivalent of the Start Menu) in order to force it to take stock of what applications are installed and add any menu entries that it missed last time.

---

### Post by El Kabong on 2006-01-27
okay, new but related question... I used synaptic to get the package for Snes9x, which is an SNES emulator. How do I find that to use that? I'd like for it to be in the applications menu, but if not than it's okay. Thanks again for the replies!

---

### Post by GeneralZod on 2006-01-27
[QUOTE=El Kabong]okay, new but related question... I used synaptic to get the package for Snes9x, which is an SNES emulator. How do I find that to use that? I'd like for it to be in the applications menu, but if not than it's okay. Thanks again for the replies![/QUOTE]

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=snes9x-x&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=snes9x-x&version=breezy&arch=i386)

The executable is called

```

snes9x

```

It looks like the developers have not included a menu entry.

---

### Post by aysiu on 2006-01-27
[QUOTE=El Kabong]okay, new but related question... I used synaptic to get the package for Snes9x, which is an SNES emulator. How do I find that to use that? I'd like for it to be in the applications menu, but if not than it's okay. Thanks again for the replies![/QUOTE] Once you've obtained a Super Nintendo ROM, right-click on the ROM and select open with and the command ```
snes9x
```

---

### Post by El Kabong on 2006-01-27
okay, do I have to put the command in the file where the application is actually located, or can I just put it in as soon as I open up terminal?

---

