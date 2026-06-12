---
title: "system-config-printer crashes just when it starts"
date: 2008-12-13
forum: General Help
---

### Post by orlox on 2008-12-13
Hi!

I was just trying to print out a pdf document with evince, and it didn't work. I had my printer configured, but now it doesn't work with evince.

I tried to configure the cups server with gnome's default application, system-config-printer, but the program crashes just when it starts with the following message:
```

pablo@pablo-desktop:~$ system-config-printer
/usr/share/system-config-printer/system-config-printer.py:197: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.xml = gtk.glade.XML(xml, domain = domain)
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 5422, in <module>
    main(configure_printer, change_ppd, devid)
  File "/usr/share/system-config-printer/system-config-printer.py", line 5387, in main
    mainwindow = GUI(configure_printer, change_ppd, devid)
  File "/usr/share/system-config-printer/system-config-printer.py", line 327, in __init__
    self.newPrinterGUI = np = NewPrinterGUI(self)
  File "/usr/share/system-config-printer/system-config-printer.py", line 2649, in __init__
    self.openprinting = cupshelpers.openprinting.OpenPrinting ()
AttributeError: 'module' object has no attribute 'openprinting'
pablo@pablo-desktop:~$ 

```

I don't know if it's just the app that crashes or it has something to do with gnome applications not being able to print documents...I can still print out things directly with cups though...

---

### Post by albinootje on 2008-12-13
Do you get any errors when you try to configure the printer via
[http://localhost:631/](http://localhost:631/) ?

---

### Post by orlox on 2008-12-13
noup. Configuring CUPS with the web gui works perfect. That's how I printed test pages to see if it worked properly...I printed the document finally using acroread, but I dislike that program because it's too slow and would like things working on evince...Also, I would like to restore the system-config-printer...

---

### Post by albinootje on 2008-12-13
Okay, good to know this!

One thing you can do is to use "strace".
Like : strace system-config-printer
That will likely produce a lot of text, but i forgot how to filter it.
It might give you more insight about the exact problem than those cryptic python error messages.

---

### Post by orlox on 2008-12-13
well, that gave me a lot of output!

can't figure right now how to put all that into a log, but these are the las lines that I guess are the most usefull...Aaaa, an another comment, before the thing crashes, the window opens, but it only shows the borders of gnome windows and then it closes before showing anything...

```

fstat64(11, {st_mode=S_IFREG|0755, st_size=219782, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6833000
read(11, "#!/usr/bin/env python\n\n## system"..., 4096) = 4096
read(11, "lection()\n        model_from, ro"..., 4096) = 4096
read(11, ", \n\n                        \"lbl"..., 4096) = 4096
read(11, " (self.btnNew)\n        self.tool"..., 4096) = 4096
read(11, "lumn (col)\n        sel = self.tv"..., 4096) = 4096
read(11, "                                "..., 4096) = 4096
read(11, "s_iconview.resize_children ()\n  "..., 4096) = 4096
read(11, "       if object.discovered:\n   "..., 4096) = 4096
read(11, "     self.chkServerBrowse, self."..., 4096) = 4096
read(11, "con_theme_get_default ()\n       "..., 4096) = 4096
read(11, "self.cmbServername.set_model(sto"..., 4096) = 4096
read(11, "\n\n    def reconnect (self):\n    "..., 4096) = 4096
read(11, "\n            self.tvPUsers.get_m"..., 4096) = 4096
read(11, "   # keep name as reminder that "..., 4096) = 4096
read(11, "                dialog.format_se"..., 4096) = 4096
read(11, "\n            # Update our copy o"..., 4096) = 4096
read(11, "ustom_testpage):\n               "..., 4096) = 4096
read(11, "o \"\n                            "..., 4096) = 4096
read(11, "ver_side_options[option.name] = "..., 4096) = 4096
read(11, "ontrol\n            self.rbtnPAll"..., 4096) = 4096
read(11, "Slot\":\n                    self."..., 4096) = 4096
read(11, " %s\" % (name, newname))\n        "..., 4096) = 4096
read(11, "t_text ())\n        self.populate"..., 4096) = 4096
read(11, "#####################\n    ### Se"..., 4096) = 4096
read(11, "                TEXT_start_firew"..., 4096) = 4096
read(11, "elf.changed = set()\n        self"..., 4096) = 4096
read(11, "ext\', 0)\n\n        # SMB browser\n"..., 4096) = 4096
read(11, "dPrinters\n        combobox.set_m"..., 4096) = 4096
read(11, "  ppddict = self.ppds.getInfoFro"..., 4096) = 4096
read(11, "t waiting:\n                waiti"..., 4096) = 4096
read(11, "  self.moveClassMembers(self.tvN"..., 4096) = 4096
read(11, "GET\", \"/printers/%s.ppd\" % resg["..., 4096) = 4096
read(11, "          else:\n                "..., 4096) = 4096
read(11, "                                "..., 4096) = 4096
read(11, ".get_selected()\n            self"..., 4096) = 4096
read(11, " Problem executing command.\n    "..., 4096) = 4096
read(11, "l\n                        device"..., 4096) = 4096
read(11, "                                "..., 4096) = 4096
read(11, "bugging ():\n                debu"..., 4096) = 4096
read(11, "                if self.expandin"..., 4096) = 4096
read(11, "b.smbc.SERVER:\n                #"..., 4096) = 4096
read(11, "  self.SMBBrowseDialog.hide()\n\n "..., 4096) = 4096
read(11, "rowseOk.set_sensitive(False)\n   "..., 4096) = 4096
read(11, "w()\n        uri = dict.get(\'prin"..., 4096) = 4096
read(11, "alues\n                          "..., 4096) = 4096
read(11, ", optionvalues in (\n            "..., 4096) = 4096
read(11, ")\n            if len (printers) "..., 4096) = 4096
read(11, "\n\n    # PPD from foomatic\n\n    d"..., 4096) = 4096
read(11, "odel)\n\n        self.on_tvNPDrive"..., 4096) = 4096
read(11, "pportcontact_extra\n             "..., 4096) = 4096
read(11, "pen the PPD file.\n              "..., 4096) = 4096
read(11, "r\"):\n            name = self.ent"..., 4096) = 4096
read(11, "ng it to a\n                    #"..., 4096) = 4096
read(11, "                         _(\"Prin"..., 4096) = 2694
write(2, "    ", 4    )                     = 4
write(2, "mainwindow = GUI(configure_print"..., 55mainwindow = GUI(configure_printer, change_ppd, devid)
) = 55
close(11)                               = 0
munmap(0xb6833000, 4096)                = 0
open("/usr/share/system-config-printer/system-config-printer.py", O_RDONLY|O_LARGEFILE) = 11
write(2, "  File \"/usr/share/system-config"..., 90  File "/usr/share/system-config-printer/system-config-printer.py", line 327, in __init__
) = 90
fstat64(11, {st_mode=S_IFREG|0755, st_size=219782, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6833000
read(11, "#!/usr/bin/env python\n\n## system"..., 4096) = 4096
read(11, "lection()\n        model_from, ro"..., 4096) = 4096
read(11, ", \n\n                        \"lbl"..., 4096) = 4096
read(11, " (self.btnNew)\n        self.tool"..., 4096) = 4096
write(2, "    ", 4    )                     = 4
write(2, "self.newPrinterGUI = np = NewPri"..., 46self.newPrinterGUI = np = NewPrinterGUI(self)
) = 46
close(11)                               = 0
munmap(0xb6833000, 4096)                = 0
open("/usr/share/system-config-printer/system-config-printer.py", O_RDONLY|O_LARGEFILE) = 11
write(2, "  File \"/usr/share/system-config"..., 91  File "/usr/share/system-config-printer/system-config-printer.py", line 2649, in __init__
) = 91
fstat64(11, {st_mode=S_IFREG|0755, st_size=219782, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6833000
read(11, "#!/usr/bin/env python\n\n## system"..., 4096) = 4096
read(11, "lection()\n        model_from, ro"..., 4096) = 4096
read(11, ", \n\n                        \"lbl"..., 4096) = 4096
read(11, " (self.btnNew)\n        self.tool"..., 4096) = 4096
read(11, "lumn (col)\n        sel = self.tv"..., 4096) = 4096
read(11, "                                "..., 4096) = 4096
read(11, "s_iconview.resize_children ()\n  "..., 4096) = 4096
read(11, "       if object.discovered:\n   "..., 4096) = 4096
read(11, "     self.chkServerBrowse, self."..., 4096) = 4096
read(11, "con_theme_get_default ()\n       "..., 4096) = 4096
read(11, "self.cmbServername.set_model(sto"..., 4096) = 4096
read(11, "\n\n    def reconnect (self):\n    "..., 4096) = 4096
read(11, "\n            self.tvPUsers.get_m"..., 4096) = 4096
read(11, "   # keep name as reminder that "..., 4096) = 4096
read(11, "                dialog.format_se"..., 4096) = 4096
read(11, "\n            # Update our copy o"..., 4096) = 4096
read(11, "ustom_testpage):\n               "..., 4096) = 4096
read(11, "o \"\n                            "..., 4096) = 4096
read(11, "ver_side_options[option.name] = "..., 4096) = 4096
read(11, "ontrol\n            self.rbtnPAll"..., 4096) = 4096
read(11, "Slot\":\n                    self."..., 4096) = 4096
read(11, " %s\" % (name, newname))\n        "..., 4096) = 4096
read(11, "t_text ())\n        self.populate"..., 4096) = 4096
read(11, "#####################\n    ### Se"..., 4096) = 4096
read(11, "                TEXT_start_firew"..., 4096) = 4096
read(11, "elf.changed = set()\n        self"..., 4096) = 4096
write(2, "    ", 4    )                     = 4
write(2, "self.openprinting = cupshelpers."..., 61self.openprinting = cupshelpers.openprinting.OpenPrinting ()
) = 61
close(11)                               = 0
munmap(0xb6833000, 4096)                = 0
write(2, "AttributeError", 14AttributeError)          = 14
write(2, ": ", 2: )                       = 2
write(2, "\'module\' object has no attribute"..., 47'module' object has no attribute 'openprinting') = 47
write(2, "\n", 1
)                       = 1
rt_sigaction(SIGINT, {SIG_DFL}, {0x80fb730, [], 0}, 8) = 0
exit_group(1)                           = ?
Process 9930 detached

```

---

### Post by albinootje on 2008-12-13
What gives reinstalling the package where it's from ? 

sudo apt-get install --reinstall system-config-printer-gnome

---

### Post by orlox on 2008-12-21
It still crashes after reinstalling :(...

I don't even get to see the gui start now

---

### Post by rene8 on 2009-01-29
I have the same problem... I've been using hardy for a while on my personal computer, and just installed it at work... and the system-config-printer just died as orlox describes. It died first when trying to delete a printer which I wrongly put into 'local printers', when it was already listed as a remote printer on our local net.

I hope someone can help us on this!
Than you.

---

### Post by albinootje on 2009-01-29
> **rene8 said:**
> I have the same problem... I've been using hardy for a while on my personal computer, and just installed it at work... and the system-config-printer just died as orlox describes. It died first when trying to delete a printer which I wrongly put into 'local printers', when it was already listed as a remote printer on our local net.


Can you search on [http://launchpad.net](http://launchpad.net) whether a bug was already filed ?
See also : [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by rene8 on 2009-01-30
> Can you search on [http://launchpad.net](http://launchpad.net) whether a bug was already filed ?
See also : [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

Thanks for that; but I honestly don't know if my problem is really a bug, since I think it has something to do with remote printers: when doing 'strace system-config-printer' it stops after the next line:
```
connect(13, {sa_family=AF_INET, sin_port=htons(631), sin_addr=inet_addr("148.214.40.143")}, 16
```
That IP is NOT our printing-server... after a few minutes, system-config-printer actually resumes, but crashes again if ever it comes up to that line.

I tried (when it resumed) trying to change the server location on 'Goto Server', but it crashed again; I reproduce last lines given by strace:
```
read(4, "\5\1m\16(\16$\0\\\0\0\0\0\2\240\3\0\0\0\0~\3t\1\30\0\27"..., 4096) = 32
read(4, 0x8352b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
stat64("/usr/share/locale/en_US.UTF8/LC_MESSAGES/system-config-printer.mo", 0xbfd84e08) = -1 ENOENT (No such file or directory)
stat64("/usr/share/locale-langpack/en_US.UTF8/LC_MESSAGES/system-config-printer.mo", 0xbfd84e08) = -1 ENOENT (No such file or directory)
stat64("/usr/share/locale/en_US/LC_MESSAGES/system-config-printer.mo", 0xbfd84e08) = -1 ENOENT (No such file or directory)
stat64("/usr/share/locale-langpack/en_US/LC_MESSAGES/system-config-printer.mo", 0xbfd84e08) = -1 ENOENT (No such file or directory)
stat64("/usr/share/locale/en.UTF8/LC_MESSAGES/system-config-printer.mo", 0xbfd84e08) = -1 ENOENT (No such file or directory)
stat64("/usr/share/locale-langpack/en.UTF8/LC_MESSAGES/system-config-printer.mo", 0xbfd84e08) = -1 ENOENT (No such file or directory)
stat64("/usr/share/locale/en/LC_MESSAGES/system-config-printer.mo", 0xbfd84e08) = -1 ENOENT (No such file or directory)
stat64("/usr/share/locale-langpack/en/LC_MESSAGES/system-config-printer.mo", 0xbfd84e08) = -1 ENOENT (No such file or directory)
select(5, [4], [4], NULL, NULL)         = 1 (out [4])
writev(4, [{"\n\7\2\0\347\1\240\3\31\0\v\0\\\0\0\0\0\0\30\0\22\0\0\0"..., 60}], 1) = 60
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\22\0n\16\347\1\240\3\347\1\240\3\0\336\335\10\310\36\266"..., 4096) = 256
read(4, 0x8352b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(5, [4], [4], NULL, NULL)         = 1 (out [4])
writev(4, [{"(\0\4\0\205\0\240\3\\\0\0\0\0\0\0\0", 16}], 1) = 16
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\1\1q\16\0\0\0\0\205\0\240\3+\2\30\0}s\33\10\340\336\335"..., 4096) = 32
read(4, 0x8352b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(5, [4], [4], NULL, NULL)         = 1 (out [4])
writev(4, [{"(\0\4\0\205\0\240\3\\\0\0\0\0\0\0\0", 16}], 1) = 16
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\34\257q\16\347\1\240\3x\0\0\0-\16$\0\0\31\t\10\20c \10"..., 4096) = 96
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\1\1r\16\0\0\0\0\205\0\240\3+\2\30\0}s\33\10\340\336\335"..., 4096) = 32
read(4, 0x8352b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
uname({sys="Linux", node="mizar.astro.ugto.mx", ...}) = 0
select(5, [4], [4], NULL, NULL)         = 1 (out [4])
writev(4, [{"\1\30\r\0\301\2\240\3\\\0\0\0\0\0\0\0\231\0]\0\0\0\1\0"..., 856}], 1) = 856
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\241 r\16\205\0\240\3\5\1\0\0\6\1\0\0-\16$\0\0\0\0\0\0"..., 4096) = 32
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\34\36u\16\301\2\240\3\n\1\0\0/\16$\0\0\257\35\10\330\304"..., 4096) = 544
read(4, 0x8352b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(5, [4], [4], NULL, NULL)         = 1 (out [4])
writev(4, [{"(\0\4\0\205\0\240\3\\\0\0\0\0\0\0\0", 16}], 1) = 16
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\241 \215\16\205\0\240\3\5\1\0\0\6\1\0\0/\16$\0\0\0\0\0"..., 4096) = 32
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\1\1\216\16\0\0\0\0\205\0\240\3+\2\30\0}s\33\10\340\336"..., 4096) = 32
read(4, 0x8352b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
select(5, [4], [4], NULL, NULL)         = 1 (out [4])
writev(4, [{"(\0\4\0\205\0\240\3\\\0\0\0\0\0\0\0", 16}], 1) = 16
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\34\257\216\16\347\1\240\3x\0\0\0000\16$\0\0\31\t\10\20"..., 4096) = 32
select(5, [4], [], NULL, NULL)          = 1 (in [4])
read(4, "\1\1\217\16\0\0\0\0\205\0\240\3+\2\30\0}s\33\10\340\336"..., 4096) = 32
read(4, 0x8352b84, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
clone(child_stack=0xb63854c4, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb6385bd8, {entry_number:6, base_addr:0xb6385b90, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb6385bd8) = 10749
futex(0x85eb090, 0x81 /* FUTEX_??? */, 1) = 1
futex(0x855e7b8, 0x81 /* FUTEX_??? */, 1) = 1
futex(0x855e7b8, 0x80 /* FUTEX_??? */, 2
```

Again it resumed after some minutes, but gives me the next error message whenever I try to configure a printer:
> Option 'sides' has value 'one' and cannot be edited.
And a button appears that says:
> There are conflicting options.
Changes can only be applied after
these conflicts are resolved.

Slipsheet


I tried just printing something from evince, but it crashed too. I neither can configure the printers using Cups, since it tells me either that access is forbidden or that it can't connect.

I hope you can help me and, if this IS a bug, then I'll follow the instructions in your post to file it.
Thanks!

---

### Post by albinootje on 2009-01-30
> **rene8 said:**
> Thanks for that; but I honestly don't know if my problem is really a bug, since I think it has something to do with remote printers

I think that since Ubuntu 8.04 you can use the cups web interface without problems (before that it was disabled) : [http://localhost:631](http://localhost:631)
Can you take a look and see whether the configuration is correct ?
And print a test page ?

And what's the output of :
```

lpq -la

```

---

### Post by albinootje on 2009-01-30
Here are all cups related bugs at launchpad :
[https://bugs.launchpad.net/cups/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=cups](https://bugs.launchpad.net/cups/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=cups)

Your problems with cups look difficult to solve to me, and the lack of answers in this thread might also indicate that that is true.
Filing a bug report gives you a higher chance that Ubuntu developers will look at it.

But.. see also here : [http://cups.org/](http://cups.org/)
--> Bugs & Features
--> User forum

---

### Post by rene8 on 2009-01-30
Before I could actually send any response to your last posts (or check the bug-related forums), I learned that the default network printer was not working since yesterday. After a couple of system-config-printer crashes, I was able to change the default to a working printer, configure it, and print on evince. Now system-config-printer does not crash on start, except when trying to cofigure the not-working printer, which I won't do from now on, of course, lol.

By the way, cups web interface IS working.

I don't know if this crashes are still some kind of bug... for if they are, I'll file the report.

Thank you very much!

---

### Post by sublime78ska on 2009-02-20
This thread helped me solve my problem so I thought I'd post my resolution.  My dhcp server provides hostnames to my devices. I have no dns so I add the hostnames to /etc/hosts.  On one of my laptops, I forgot to update /etc/hosts so the print app was searching the internet for my hostname.  Once I updated /etc/hosts the problem went away.

---

### Post by rene8 on 2009-02-20
Thanks for your post, sublime78ska.
My problem was something pretty similar, since it was a network problem, but the difference is that we do have DNS, so the problem was actually simpler: the config app was trying to look for a device that was down at the time, so it crashed every time it tried to connect with it.
It partially got solved by changing the default printer to a working one, and never occurred again when the device was up again.
So, thank you everyone for your help!

---

