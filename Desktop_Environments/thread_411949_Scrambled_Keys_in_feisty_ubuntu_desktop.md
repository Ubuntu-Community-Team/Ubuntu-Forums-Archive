---
title: "Scrambled Keys in feisty ubuntu desktop"
date: 2007-04-17
forum: Desktop Environments
---

### Post by long.in.the.tooth on 2007-04-17
Hello,

I installed a fresh server last week from the lightweight text install CD.  (I had some RAID stuff to set up, and the website said that was the best way to go)

ubuntu-desktop and dependencies all got installed manually via apt-get.

When I connect to the server using vnc and gdm/gome/ubuntu desktop, the keys all come out scrambled. specifically, 'asdf' becomes 'abfh', or 'qwerty' becomes 'c.gvn<?>' where <?> is some special key I haven't figured out yet.

If I set the window manager to ratpoison, the keys flow through vnc just fine, so I'm pretty sure that the problem is with gnome.

Unfortunately, I don't have access to the server, so I can't plug  a monitor and keyboard in.

I've run dpkg --reconfigure xserver-xorg a few times, with no luck.  
Here is the relevant portion of my xorg.conf:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

All quite vanilla, as far as I can tell...

Where in /etc/gdm would I look for keyboard stuff?

Any other ideas?  Should I take this question to a different list or forum?

---

### Post by Xiphias256 on 2007-04-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/108928](https://bugs.launchpad.net/ubuntu/+bug/108928) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same problem as you do. Made any progress??
I live in Norway and use the no layout.
Also made a bug-report of this on launchpad.

Some configs on my system.

$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "no", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "no", "", ""

$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [gb,no]
 model = generic
 options = [grp grp:alts_toggle]
 overrideSettings = true

Why does it say layouts gb,no?? I only have Norwegian defined.


xorg.conf
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "no"
EndSection

---

### Post by long.in.the.tooth on 2007-04-23
No luck for me, yet.  I've been using ratpoison as a window manager for now, and it's been okay.

I suspect that you might be okay with twm or some other lightweight wm.  I'd be interested to see if kde would work as well.

Couldn't get xprop to work, but the kbd section for me looks like this:

# gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model =
 overrideSettings = true
 options = []

I'm running on a Dell PowerEdge.  How about you?

---

### Post by Xiphias256 on 2007-04-23
I'm running feisty on my fileserver that is assembled with many leftover parts :)
Asus CUBX w/ PIII 700MHz 512MB ram, Matrox millennium II gfx....
It's frustrating, since 6.10 was rock sollid. No issues.

---

### Post by jtonk on 2007-04-23
same problem here,

asdf is abfh....... when I start vnc in twm no problem as soon as I start gnome-session I get this error:

Window manager warning: Log lever 32: could not find XKB extension.

normal display runs fine, only VNC gives me some problems

 layouts = [us  intl]
 model = generic
 options = [grp grp:alts_toggle]
 overrideSettings = true

any ideas??


regards

Jasper

---

### Post by allyn on 2007-04-25
same problem here with tightvncserver.  :-(

very frustrating.

so far no luck.  i did notice that vnc4server does NOT have the problem, but i can't use it because gnome-session is broken with vnc4server.  if the problem is truly with gnome and not vnc, then that would make sense.

---

### Post by allyn on 2007-04-25
i verified that when starting vncserver without gnome, the keyboard works fine, but if i then start gnome-session, everything is scrambled.  so the problem appears to be gnome, not vnc as i originally guessed.

---

### Post by fourthirtysix on 2007-04-26
i've been following this issue since i am having the same problem. it seems to be referred to as the "abfh" problem since that is what people get when they type "asdf"

i upgraded two computers to feisty at the same time, and i only have the gnome keyboard abfh problem on a headless machine that I use tightvnc to connect to.  i never had a problem running the exact same configuration with edgy.

i tried playing around with keyboard and language settings in gnome a little bit, but nothing seemed to help.

i hope someone can track this problem down. i will attempt to look into more this weekend.

if anyone solves the problem, please post the answer here. i am tracking what appears to be the same problem in a number of threads/posts:

[http://ubuntuforums.org/showthread.php?p=2523097](http://ubuntuforums.org/showthread.php?p=2523097)

[http://ubuntuforums.org/showthread.php?p=2517629](http://ubuntuforums.org/showthread.php?p=2517629)

[http://ubuntuforums.org/showthread.php?t=233613](http://ubuntuforums.org/showthread.php?t=233613)

[http://ubuntuforums.org/showthread.php?t=420179](http://ubuntuforums.org/showthread.php?t=420179)

---

### Post by benjackson on 2007-04-30
I have the same problem with vncserver and gnome since upgrading to feisty. Everything works fine in my other window managers so i've had to resort to using kde which is a shame as i prefer gnome. In case it helps to solve the bug I'm using a P3 with an ABIT BE6 motherboard and the old configs i kept were the ones for cups, apache, samba and login details. I saw someone say he'd solved the problem by pressing the restore keyboard defaults (accessed through the gnome-control-panel) but that didn't solve anything for me.

---

### Post by Mayfoev on 2007-05-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/108928](https://bugs.launchpad.net/ubuntu/+bug/108928) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have just posted on the bug report a temporary & ugly fix :
see comments 8 and 9 of 
[https://bugs.launchpad.net/ubuntu/+bug/108928](https://bugs.launchpad.net/ubuntu/+bug/108928)

---

### Post by corny on 2007-06-11
I had the same issue. Freshly installed Feisty (with Gnome) as vserver guest on a Debian Etch host. Accessing session from Dapper clients with vncviewer.
No matter what vnc server running (vncserver or vnc4server) i had allways the keyboard mismatch.
I had also the initial question of gnome asking if X or Gnome keyboard layout should be used. But both options ended up in keyboard mismatch.

Labananas ugly hack was the solution for me: [http://ubuntuforums.org/showpost.php?p=2539412&postcount=4](http://ubuntuforums.org/showpost.php?p=2539412&postcount=4)

---

### Post by m4dsc1 on 2008-02-13
> **corny said:**
> I had the same issue. Freshly installed Feisty (with Gnome) as vserver guest on a Debian Etch host. Accessing session from Dapper clients with vncviewer.
No matter what vnc server running (vncserver or vnc4server) i had allways the keyboard mismatch.
I had also the initial question of gnome asking if X or Gnome keyboard layout should be used. But both options ended up in keyboard mismatch.

Labananas ugly hack was the solution for me: [http://ubuntuforums.org/showpost.php?p=2539412&postcount=4](http://ubuntuforums.org/showpost.php?p=2539412&postcount=4)

Same problem, same resolution.  Try the keyboard layout hack listed.  I posted my experience in quoted thread.  US-105 now working.

---

