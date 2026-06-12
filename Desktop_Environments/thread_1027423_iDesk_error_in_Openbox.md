---
title: "iDesk error in Openbox"
date: 2009-01-01
forum: Desktop Environments
---

### Post by Terraman on 2009-01-01
Hi all,

I am trying to run iDesk in my machine (see specs in signature) with Openbox as WM. Apparently it has some errors.
I quote the next message when I run idesk in terminal:
"terminate called after throwing an instance of'std::ios_base::failure' what(): basic_filebuf::underflow error reading file
Aborted"

This is my .ideskrc file in $HOME:

table Config
 FontName: tahoma
 FontSize: 8
 FontColor: #ffffff
 ToolTip.FontSize: 9
 ToolTip.FontName: gothic
 ToolTip.ForeColor: #0000FF
 ToolTip.BackColor: #FFFFFF
 ToolTip.CaptionOnHover: true
 ToolTip.CaptionPlacement: right
 Locked: false
 Transparency: 100
 Shadow: true
 ShadowColor: #000000
 ShadowX: 1
 ShadowY: 2
 Bold: false
 ClickDelay: 300
 IconSnap: true
 SnapWidth: 55
 SnapHeight: 100
 SnapOrigin: BottomRight
 SnapShadow: true
 SnapShadowTrans: 200
 CaptionOnHover: false
 FillStyle: FillHLine
 Background.File:
 Background.Delay: 20
 Background.Source: /home/herman/.wallpaper
 Background.Mode: Scale
 Background.Color: #C2CCFF
end
table Actions
 Lock: right doubleClk
 Drag: left hold
 EndDrag: left singleClk
 Execute[0]: left doubleClk
end

The next file is my icon file in .idesktop directoy in $HOME.

table Icon
   Caption: File Manager
   Command: pcmanfm
   Icon: /usr/share/fbpanel/images/file-manager.png
   X: 100
   Y: 50
end

Can someone help me?

Thanks in advance!

---

### Post by Terraman on 2009-01-06
Someone?

---

### Post by Terraman on 2009-01-09
Anybody?

---

### Post by urukrama on 2009-01-09
According to [this thread]("http://easynux.org/forum/viewtopic.php?id=158") (on a French forum) this problem can be solved if you have both a Command[0] and Command[1] line (instead of having just a Command line) in your icon file (as explained on the [Wiki]("http://idesk.sourceforge.net/wiki/index.php/Idesk-usage")). Perhaps that helps you as well.

Since you only specify Execute[0] in your ideskrc and don't have an Execute[1] option, perhaps only changing the Command to Command[0] might do. It shouldn't be necessary, but it could be worth a try.

I don't use idesk, otherwise I'd experiment with it myself.

---

### Post by Terraman on 2009-01-09
urukrama,

I have followed your suggestion, unfortunately it is still showing the same message.

PS: nice Openbox Guide, it has been extremely helpful so far.

---

### Post by Terraman on 2009-01-12
Nobody?:idea:

---

### Post by kerry_s on 2009-01-12
i would try starting again, remove everything(uninstall: sudo apt-get remove --purge idesk), reinstall it(sudo apt-get install idesk), than copy the files(cp /usr/share/idesk/idesrc ~/.ideskrc (i think?)), create the folder(mkdir ~/.idesktop), don't put nothing in it yet. just start it up(idesk &), than kill it(killall idesk), than do your thing.

you know pcmanfm does desktop icons?
put "pcmanfm -d &" in your startup, makes it run as a daemon(aka:faster), than turn on the desktop support, go to /usr/share/applications, copy & paste what ever programs you want to ~/Desktop. it's very simple.

---

### Post by Terraman on 2009-01-14
> **kerry_s said:**
> i would try starting again, remove everything(uninstall: sudo apt-get remove --purge idesk), reinstall it(sudo apt-get install idesk), than copy the files(cp /usr/share/idesk/idesrc ~/.ideskrc (i think?)), create the folder(mkdir ~/.idesktop), don't put nothing in it yet. just start it up(idesk &), than kill it(killall idesk), than do your thing.

you know pcmanfm does desktop icons?
put "pcmanfm -d &" in your startup, makes it run as a daemon(aka:faster), than turn on the desktop support, go to /usr/share/applications, copy & paste what ever programs you want to ~/Desktop. it's very simple.
kerry_s

When I put "pcmanfm -d &" a message "Files does not exist" por up. However, with "pcmanfm &" there is no message and the file manager is running.

---

### Post by kerry_s on 2009-01-14
> **Terraman said:**
> kerry_s

When I put "pcmanfm -d &" a message "Files does not exist" por up. However, with "pcmanfm &" there is no message and the file manager is running.

yeah, i guess it doesn't work in some wm's, i'm using twm and using the daemon causes a zombie. that's okay it's just slow the first time it's started without it. it's a undocumented setting, so my guess is it's not completely ready. when it does work it's great, pcmanfm starts instantly the first time it's used. works in my jwm setup on my other laptop.

---

### Post by Terraman on 2009-01-15
kerry_s

Ok! But iDesk is showing the same message:
> terminate called after throwing an instance of 'std::ios_base::failure' what(): basic_filebuf::underflow error reading the file


---

### Post by kerry_s on 2009-01-15
> **Terraman said:**
> kerry_s

Ok! But iDesk is showing the same message:

never mind, i just reread everything you see the error in terminal, does the program still run?

---

### Post by Terraman on 2009-01-16
> **kerry_s said:**
> never mind, i just reread everything you see the error in terminal, does the program still run?
kerry_s

Unfortunately, iDesk does not run.

---

### Post by nuvytes on 2009-09-04
Hey all,

I might have a solution for this issue. At least it worked for me! 

I've been getting the exact same response about underflow when trying to run idesk 0.7.5 lately, for no apparent reason. But I'm getting ahead of myself.

When I first installed idesk, I followed the steps in the wiki and all was working fine - I created the .ideskrc file and the .idesktop folder in my home dir just like I was told.
I then proceeded to make a simple launcher icon (I think it was for xterm). Tried running it without an icon, but couldn't get it to work. I then recalled I had some icons in my home/downloads/ dir leftover from my previous experience with fbdesk, so I just picked a random one and copied it to the .idesktop dir, added it to the xterm.lnk and voila! It's all working perfectly.
So then I decided to get another pack of icons. The wiki page for idesk linked to a certain "icons.tar.bz2", so I thought I'd give that a shot. Downloaded the file, and extracted it only to find out that it didn't create a dir called "icons", but used the dir that the archive was in (which was .idesktop at that moment). So I went ahead and created "icons"; in .idesktop, and extracted the .png icons there. Edited xterm.lnk once again, this time pointing to a new icon, and got it running again. All was fine, except for random icon files (.png) being used for my desktop background, with a new one every minute. I later found out that the sample .ideskrc file in the wiki (which I just copied and pasted into my .ideskrc) had the following lines:
```

Background.File: image.jpg
Background.Delay: 1
Background.Source: ~/.idesktop/icons
```

Of course I had no image.jpg, so idesk went looking into my icon dir for desktop backgrounds. Coincidence :D
After giving it a minute of thought, I created a new empty dir named "bg" alongside "icons" and pointed the config file to that. Now, I *don't* think I edited anything else.. that was when I started getting the error message. I might have restarted fluxbox a couple of times.  I tried editing .ideskrc and setting values to none, like the wiki suggested:
```

Background.File:
Background.Delay:
Background.Source:
```

I also tried restoring the original .ideskrc from the wiki, removing the icons dir, etc but all to no avail. Google wasn't of much help on the issue.. and I really didn't want to remove and then install idesk all over again.  So I removed the entire .idesktop dir (I of course made a backup of my precious xterm.lnk) and the .ideskrc file, and launched idesk to see what would happen. Well, it worked; I saw some complaints about not having a .idesktop dir, but with that done idesk ran normally, and created a default icon and a default .ideskrc file. I then restored my xterm.lnk and it's working again. One thing for sure, the idesk wiki could use a little more clarity because this is what the values should look like (created automatically on first launch of idesk):

```

Background.File: None
Background.Delay: 0
Background.Source: None
```

Hope this helps :)

---

