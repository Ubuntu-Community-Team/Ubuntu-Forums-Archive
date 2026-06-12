---
title: "gEdit starting porblems"
date: 2009-04-14
forum: General Help
---

### Post by AwesomeTux on 2009-04-14
Hello,

I am running Ubuntu 8.10 and I am having a problem, that I find really mind-boggling.

When I _try_ to open gEdit -- via Application > Accessories > Text Editor or command-line gedit -- nothing happens. But, when trying again to open it, it opens, I have to click on Text Editor twice each time I want to open gEdit. Also, when in gEdit, going to Edit > Preferences does the same thing, click it once nothing happens, click it again and then it opens.

I have these packages install gedit -> 2.24.2-0ubuntu1, gedit-common -> 2.24.2-0ubuntu1, gedit-plugins -> 2.22.4-0ubuntu2

I'd tried reinstalling, I've tried completely removing them, with configuration files.

PLEASE HELP!

---

### Post by dcstar on 2009-04-14
> **AwesomeTux said:**
> Hello,

I am running Ubuntu 8.10 and I am having a problem, that I find really mind-boggling.

When I _try_ to open gEdit -- via Application > Accessories > Text Editor or command-line gedit -- nothing happens. But, when trying again to open it, it opens, I have to click on Text Editor twice each time I want to open gEdit. Also, when in gEdit, going to Edit > Preferences does the same thing, click it once nothing happens, click it again and then it opens.

I have these packages install gedit -> 2.24.2-0ubuntu1, gedit-common -> 2.24.2-0ubuntu1, gedit-plugins -> 2.22.4-0ubuntu2

I'd tried reinstalling, I've tried completely removing them, with configuration files.

PLEASE HELP!

Open a terminal, enter "gedit" and tell us of any messages that appear.

---

### Post by AwesomeTux on 2009-04-14
> **dcstar said:**
> Open a terminal, enter "gedit" and tell us of any messages that appear.

Nothing appears. I can then open another terminal and enter gedit again, and it will open. In the System Monitor, it shows it as running, like it normally would, but there is no window open. Until I click Text Editor again of course, then it opens the window.

Could it have something to do with zenity?

---

### Post by anurag_envyinc on 2009-04-14
Try reinstalling again and Ctrl-Alt-Backspace.
Then goto Terminal or Alt+f2 and type sudo gedit.
If it doesn't open, it might be a bug. 
But, still, why use gEdit, why not Vim or Cream or Emacs??

Cheers,
anurag_envyinc

---

### Post by AwesomeTux on 2009-04-14
> **anurag_envyinc said:**
> Try reinstalling again and Ctrl-Alt-Backspace.
Then goto Terminal or Alt+f2 and type sudo gedit.
If it doesn't open, it might be a bug. 
But, still, why use gEdit, why not Vim or Cream or Emacs??

Cheers,
anurag_envyinc

Isn't Vim a terminal program? I think Cream and Emacs are too ugly to use, and not light weight enough.

Plus, gEdit should work, I don't just wanna totally stop using it because it just doesn't work well enough for some reason, everything should work, especially when it worked before, and for everyone else.

---

### Post by AwesomeTux on 2009-04-14
Alright, I hit Ctrl+Alt+Backspace, then Ctrl+Alt+F2, and entered gedit, I got this.

jacobwb@jacob-ubuntu:~$ gedit
Invalid MIT-MAGIC-COOKIE-1 key

(gedit:6804): Gtk-WARNING **: cannot open display:

---

### Post by codeseer on 2009-04-14
Magic cookies are bad, mmk.

Have you been tinkering with your sudoers file?

Did you look at the log files?

---

### Post by AwesomeTux on 2009-04-14
> **codeseer said:**
> Magic cookies are bad, mmk.

Have you been tinkering with your sudoers file?

Did you look at the log files?

Actually, I messed with the dependencies of my operating system; GTK+, xServer, X.Org, the whole bit. I got everything working but gEdit.

So what do I need to do? Where do I need to go? What files do I have to edit?

---

### Post by codeseer on 2009-04-14
> **AwesomeTux said:**
> Actually, I messed with the dependencies of my operating system; GTK+, xServer, X.Org, the whole bit. I got everything working but gEdit.

So what do I need to do? Where do I need to go? What files do I have to edit?

I've looked around a bit on the issue. It seems that some people have had success from deleting the .Xauthority and .ICEauthority files from their home directory and restarting. I'd give it a go, but I'd also make backups of them just in case.

The logs are under System->Administration->System Logs

You could also try 'tail -F /var/log/messages' in the terminal while trying to get gedit working.

---

### Post by AwesomeTux on 2009-04-14
> **codeseer said:**
> I've looked around a bit on the issue. It seems that some people have had success from deleting the .Xauthority and .ICEauthority files from their home directory and restarting. I'd give it a go, but I'd also make backups of them just in case.

The logs are under System->Administration->System Logs

Didn't work. No problems, no anything. But gEdit is still broken.

Is it having problems gaining root privileges to access the display? Is that what I'm looking at here?

---

### Post by codeseer on 2009-04-14
That would be my guess from what I've read so far. I'm wondering how it all happened.

---

### Post by AwesomeTux on 2009-04-14
This is what I get when running "tail -F /var/log/messages"

```
Apr 14 17:37:19 jacob-ubuntu kernel: [   32.482908] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 14 17:37:19 jacob-ubuntu kernel: [   32.483991] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.19  Fri Apr  3 12:24:24 PST 2009
Apr 14 17:37:20 jacob-ubuntu kernel: [   32.871060] agpgart-amd64 0000:00:00.0: AGP 3.1 bridge
Apr 14 17:37:20 jacob-ubuntu kernel: [   32.871075] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
Apr 14 17:37:20 jacob-ubuntu kernel: [   32.873077] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
Apr 14 17:37:31 jacob-ubuntu pulseaudio[5795]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 14 17:37:31 jacob-ubuntu pulseaudio[5797]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 14 17:37:31 jacob-ubuntu pulseaudio[5797]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 14 17:37:31 jacob-ubuntu pulseaudio[5797]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Apr 14 17:37:31 jacob-ubuntu pulseaudio[5797]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
```

Nothing I can find wrong in there besides pulseaudio, but that's normal.

---

### Post by codeseer on 2009-04-14
Wish I knew more and could help you further. This just seems like one of those weird occurrences. If it were me, I'd probably start considering creating and testing another user then transferring some files over or reinstalling. Hopefully someone will come by that knows what's going on.

---

### Post by AwesomeTux on 2009-04-14
I just realized. My guest session doesn't work either. WHAT THE HELL?

---

### Post by AwesomeTux on 2009-04-14
Now I got something in the logs:

```
Apr 14 17:59:41 jacob-ubuntu kernel: [ 1375.063368] gedit[6483]: segfault at 58 ip 08099ff9 sp bfa5f7c0 error 4 in gedit[8048000+9a000]
Apr 14 17:59:43 jacob-ubuntu kernel: [ 1377.168953] gedit[6485]: segfault at 58 ip 08099ff9 sp bf8ea650 error 4 in gedit[8048000+9a000]
Apr 14 17:59:46 jacob-ubuntu kernel: [ 1379.637827] gedit[6487]: segfault at 58 ip 08099ff9 sp bfb25080 error 4 in gedit[8048000+9a000]
Apr 14 18:01:32 jacob-ubuntu kernel: [ 1485.696295] gedit[6667]: segfault at 58 ip 08099ff9 sp bfb870e0 error 4 in gedit[8048000+9a000]
Apr 14 18:01:33 jacob-ubuntu kernel: [ 1486.378439] gedit[6669]: segfault at 58 ip 08099ff9 sp bff6ecd0 error 4 in gedit[8048000+9a000]
Apr 14 18:01:35 jacob-ubuntu kernel: [ 1488.771102] gedit[6671]: segfault at 58 ip 08099ff9 sp bfdda340 error 4 in gedit[8048000+9a000]
Apr 14 18:01:36 jacob-ubuntu kernel: [ 1490.028318] gedit[6673]: segfault at 58 ip 08099ff9 sp bf810d70 error 4 in gedit[8048000+9a000]
Apr 14 18:01:46 jacob-ubuntu kernel: [ 1499.624251] gedit[6676]: segfault at 58 ip 08099ff9 sp bffe5800 error 4 in gedit[8048000+9a000]
Apr 14 18:01:51 jacob-ubuntu kernel: [ 1504.752838] gedit[6715]: segfault at 58 ip 08099ff9 sp bfe50680 error 4 in gedit[8048000+9a000]
Apr 14 18:17:08 jacob-ubuntu -- MARK --
```

---

### Post by codeseer on 2009-04-15
> **AwesomeTux said:**
> I just realized. My guest session doesn't work either. WHAT THE HELL?

I'd reinstall. The great thing about Ubuntu is that if something does happen like this, you can reinstall in 20 minutes and, with good backups, you can have everything back in order in under an hour total.

---

### Post by AwesomeTux on 2009-04-16
> **codeseer said:**
> I'd reinstall. The great thing about Ubuntu is that if something does happen like this, you can reinstall in 20 minutes and, with good backups, you can have everything back in order in under an hour total.

Dude, that is the Window$ way around problems. It has to be either 1)missing packages or 2)mis-configured packages/files.

Reinstalling is never an option.

---

### Post by codeseer on 2009-04-16
> **AwesomeTux said:**
> Dude, that is the Window$ way around problems. It has to be either 1)missing packages or 2)mis-configured packages/files.

Reinstalling is never an option.

Alright, then how can we determine what's wrong in a situation like that within an hour's time? We could check the dependencies list and 'reinstall' all (25-27) of those; but how would we know if it was a corrupt or mis-configured configuration file somewhere? Would 'reinstalling' those (25-27) dependencies generate all new configuration files for those outside the user's home directory? I suppose, if one was willing and knowledgeable, they could throw it in a debugger and find the file that way.

---

### Post by AwesomeTux on 2009-04-16
> **codeseer said:**
> Alright, then how can we determine what's wrong in a situation like that within an hour's time? We could check the dependencies list and 'reinstall' all (25-27) of those; but how would we know if it was a corrupt or mis-configured configuration file somewhere? Would 'reinstalling' those (25-27) dependencies generate all new configuration files for those outside the user's home directory? I suppose, if one was willing and knowledgeable, they could throw it in a debugger and find the file that way.

Why does it have to be in an hour's time? I don't mind waiting and working at it.

Yes. And there is surely more than 3229 commands on a normal Ubuntu install, and each of those have 25-27 dependencies, and those dependencies have 30-50 dependencies.

Reinstalling after deleting the configuration files _could_ work, in some cases.

Which worked! :D I deleted every configuration file for gEdit, xServer, X.Org, GTK+, etc., reinstalled all of those, hit Control+Alt+Backspace, let it start GDM, logged in, and ran gedit, it opened, created configuration files, that didn't have anything related it the original configuration files, because it was now running on run level 8(or whatever Ctrl+Alt+F8 is called) and rebooted for good measures.

And I'm happy to say gEdit works great now. But my Guest Session is still broken. But, I'll figure that one out sooner or later. Maybe it would get fixed when I upgrade to Ubuntu 9.04 here soon :)

LATERS!
Thanks everyone!

---

### Post by codeseer on 2009-04-16
lolz. :P

---

