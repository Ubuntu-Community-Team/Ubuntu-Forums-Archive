---
title: "Nautilus freezes when opening home folder"
date: 2006-10-05
forum: Desktop Environments
---

### Post by akurtz on 2006-10-05
I'm relatively new to Ubuntu and am currently running the standard 32-bit distribution of Dapper (6.06).

Recently I have been experiencing trouble with the file manager, Nautilus.  Any time I try to open my home folder, Nautilus opens the window but freezes up before displaying its contents.  I can open other folders without a problem, but as soon as I touch home, it's over.

Force-quitting Nautilus results in it re-launching with my home folder open, which of course freezes the system again.  Rebooting results in the home folder opening again on startup (because it remembers the last windows I had open and "conveniently" re-opens them).  The only temporary remedies I've found are to login using the GNOME "failsafe" session or to delete *~/.gnome2/session* and reboot.  Nautilus will then work properly until I open the home folder again.

The last time I had this problem, deleting *~/.gnome2/session* fixed the problem "permanently" (for a month or so, at least, until it recently started happening again).  This time, however, the problem re-occurs every time I open my home folder.

I don't think it's a problem with a specific file in my home folder because I have no trouble accessing the contents of the home folder via the terminal.  I'm not sure if it's an issue with the file manager (Nautilus), the window manager (Metacity), a corrupt session file, my startup scripts, or what, but I'm nearly at my wit's end.

Please help!

---

### Post by IoCaster on 2006-10-05
Try Alt-F2

```
nautilus --no-desktop --browser%U
```

and navigate to your /home folder.

If it works I'm not sure what it would prove, but it would be a temporary workaround while you sort things out.

---

### Post by akurtz on 2006-10-05
Hmmm...no dice.  The Nautilus window opens to my home folder, but freezes before displaying the contents as before.

Thanks for the suggestion though!

---

### Post by akurtz on 2006-10-06
Anyone else have any suggestions?  Which logs should I be examining (if any)?  Are there any other files I should remove besides *~/.gnome/session* to "start over" with a new, clean login profile?

---

### Post by bluevoodoo1 on 2006-10-07
I am having the same issue.


Got it fixed...
try reading this... 
[http://ubuntuforums.org/showthread.php?t=268170&highlight=nautilus](http://ubuntuforums.org/showthread.php?t=268170&highlight=nautilus)

---

### Post by CatKiller on 2006-10-07
As an alternative to having an illegaly named file in there, you might have buggered up the permssions on your Home folder - making it so that you can't read the contents, hence the crash. Open a terminal and type```
gksudo nautilus
```and browse to your Home folder (/home/akurtz). This will be browsing as root, so permissions shouldn't be a problem. If it displays OK, go back up to /home and right-click on your folder. Go to Properties and then Permissions, and set them to how they should be.

---

### Post by akurtz on 2006-10-08
Thanks so much for pointing out that earlier thread, bluevoodoo1!  It *was* a problem with symbols in filenames.  They were appearing in the terminal with 8-hex-character names such as "BCF41000", so I just did a little ```
mv BCF41000 temp1
``` and so on until they were all renamed.  My home folder is now opening without a hitch!

Thanks also for your suggestion, CatKiller.  The permissions were correct, but I hadn't even considered checking them.

---

### Post by bluevoodoo1 on 2006-10-08
Good good.

---

### Post by elgandoz on 2008-03-03
Hi smart guys, mine is similar but i can't understand what's wrong in my home floder.
I can see everything from another user using Nautilus or using "gksudo nautilus" from my account.
I tried to move all the visibile files, such as pdf, images and documents, but nothing.
When i go in home folder with my account, it freezes!
After some crashes and using the command "Force quit" (it's a traduction, i'm not sure in english is the same), appear a message that suggest me to close the bonobo-activation-server, but this do not affect the nautilus to work properly.
here my folder...
marcoz@RaVeN:~$ dir -a
.               .gnome2               .sane
..              .gnome2_private       Schermata-1.png
.adobe          .gnupg                .scim
.amsn           .googleearth          .screenlets
amsn_received   .gpilotd              .Skype
.aMule          .gstreamer-0.10       .sounds
.aptitude       .gtkrc-1.2-gnome2     .subversion
.autumn         .ICEauthority         .sudo_as_admin_successful
.bluefish       .icons                .synaptic
.cache          .ies4linux            temp
.compiz         Immagini              .themes
.config         Incoming              .thumbnails
.dbus-keyrings  .inkscape             .tilda
Desktop         .java                 tkdnd
Desktop\ Win    .kde                  .tomboy
.dmrc           .local                .Trash
Documenti       .macmenu-tslist       .tremulous
.emerald        .macromedia           .update-manager-core
.esd_auth       .mcop                 .update-notifier
.evolution      .mcoprc               Video
.face           .metacity             .VirtualBox
.filezilla      .moiosms              .w3m
.fontconfig     .mozilla              wallpaper.png
.fonts          .mozilla-thunderbird  .wapi
.galeon         Musica                .wine
.gconf          .nautilus             .Xauthority
.gconfd         .openoffice.org2      .xine
.gdesklets      .picasa               .xsession-errors
.gimp-2.4       Pubblici              Yugma
.gksu.lock      .qt
.gnome          .recently-used.xbel

i don't see any strange character...and everything was workin fine till this morning (i do not install anything).
Somebody can help me?
thanks you all guys..

---

