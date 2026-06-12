---
title: "Totaly remove LimeWire ?"
date: 2006-02-14
forum: Desktop Environments
---

### Post by r4ik on 2006-02-14
How do i completely remove LimeWire i have tried;

sudo rm -r Limewire

And;

sudo rm -rf /opt/LimeWire

sudo rm /usr/bin/runLime.sh

sudo rm /usr/share/applications/LimeWire.desktop

Wich removes the icon nice and easely but when i do a "search" there are still 57 files left wich i cannot remove.
Any suggestions please ?

---

### Post by cstudent on 2006-02-14
[QUOTE=r4ik]How do i completely remove LimeWire i have tried;

sudo rm -r Limewire

And;

sudo rm -rf /opt/LimeWire

sudo rm /usr/bin/runLime.sh

sudo rm /usr/share/applications/LimeWire.desktop

Wich removes the icon nice and easely but when i do a "search" there are still 57 files left wich i cannot remove.
Any suggestions please ?[/QUOTE]


Did you check the .LimeWire directory in your home folder?

---

### Post by Ramses de Norre on 2006-02-14
Where are those files? Are they from the program itself or things like logs etc?
How did you install it?

---

### Post by r4ik on 2006-02-14
I did check my homefolder nothing there and i installed it manualy.
This is what its all about,

 /usr/share/ubuntu-docs/gnome/menus/C/limewire.xml
/usr/share/ubuntu-docs/generic/faqguide/en_AU/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/en_AU/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/C/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/C/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/da/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/da/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/cs/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/cs/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/pt_BR/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/pt_BR/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/es/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/es/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/fa/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/fa/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/fi/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/fi/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/fr/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/fr/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/he/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/he/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/id/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/id/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/it/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/it/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/mk/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/mk/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/nl/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/nl/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/pl/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/pl/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/pt/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/pt/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/sr/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/sr/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/sv/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/sv/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/tl/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/tl/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/ast/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/ast/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/ca/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/ca/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/de/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/de/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/hu/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/hu/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/lt/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/lt/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/nb/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/nb/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/ro/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/ro/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/sk/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/sk/sample/runLime.sh_limewire
/usr/share/ubuntu-docs/generic/faqguide/uk/sample/LimeWire.desktop_limewire
/usr/share/ubuntu-docs/generic/faqguide/uk/sample/runLime.sh_limewire

---

### Post by Ramses de Norre on 2006-02-14
If I'm not mistaking those are just help files, if so you can just delete them if you wish to. But check out first, I'm not entirely sure (and I to want to be the reason for you to end up with error messages).

---

### Post by r4ik on 2006-02-14
Thanks for your reply but i cannot simly wack those in the bin,
access denied.

---

### Post by cstudent on 2006-02-14
Looks like they may be related to something else with documentation. I don't think I would worry with them.

---

### Post by Ramses de Norre on 2006-02-14
The files are owned by root, that's why you can't just delete them (sudo rm will do the job). But when they aren't bothering you I wont delete them neither, they wont do no harm but taking a few kB (MB?) of your hardisk space.

---

### Post by r4ik on 2006-02-14
I am a "in control-freak' but when opened this one up i it scared me a bit.
Where does al this limewire chips installs itself to ?
These "leftover" files are not harmless at all because when i install Frostwire it starts where Limewire left.
When i delete/remove something i wont it to be gone.. period.
But it is beyond my capabillity (for now that is...)
Thanks for your reply's

file:///usr/share/ubuntu-docs/gnome/menus/C/limewire.xml


/usr/share/ubuntu-docs/gnome/menus/C/about-me.xml
/usr/share/ubuntu-docs/gnome/menus/C/accessories.xml
/usr/share/ubuntu-docs/gnome/menus/C/acro-read.xml
/usr/share/ubuntu-docs/gnome/menus/C/administration.xml
/usr/share/ubuntu-docs/gnome/menus/C/amule.xml
/usr/share/ubuntu-docs/gnome/menus/C/archive-man.xml
/usr/share/ubuntu-docs/gnome/menus/C/assistive-technology-preferences.xml
/usr/share/ubuntu-docs/gnome/menus/C/azureus.xml
/usr/share/ubuntu-docs/gnome/menus/C/boot.xml
/usr/share/ubuntu-docs/gnome/menus/C/calculator.xml
/usr/share/ubuntu-docs/gnome/menus/C/character-map.xml
/usr/share/ubuntu-docs/gnome/menus/C/desktop-background.xml
/usr/share/ubuntu-docs/gnome/menus/C/desktop-preferences.xml
/usr/share/ubuntu-docs/gnome/menus/C/device-manager.xml
/usr/share/ubuntu-docs/gnome/menus/C/dictionary.xml
/usr/share/ubuntu-docs/gnome/menus/C/disks.xml
/usr/share/ubuntu-docs/gnome/menus/C/downloader-x.xml
/usr/share/ubuntu-docs/gnome/menus/C/file-management.xml
/usr/share/ubuntu-docs/gnome/menus/C/firefox.xml
/usr/share/ubuntu-docs/gnome/menus/C/firestarter-firewall-tool.xml
/usr/share/ubuntu-docs/gnome/menus/C/font.xml
/usr/share/ubuntu-docs/gnome/menus/C/games.xml
/usr/share/ubuntu-docs/gnome/menus/C/gconf.xml
/usr/share/ubuntu-docs/gnome/menus/C/gftp.xml
/usr/share/ubuntu-docs/gnome/menus/C/gnomeappinstall.xml
/usr/share/ubuntu-docs/gnome/menus/C/graphics.xml
/usr/share/ubuntu-docs/gnome/menus/C/inkscape.xml
/usr/share/ubuntu-docs/gnome/menus/C/internet.xml
/usr/share/ubuntu-docs/gnome/menus/C/keyboard.xml
/usr/share/ubuntu-docs/gnome/menus/C/keyboard-shortcuts.xml
/usr/share/ubuntu-docs/gnome/menus/C/limewire.xml
/usr/share/ubuntu-docs/gnome/menus/C/login-screen-setup.xml
/usr/share/ubuntu-docs/gnome/menus/C/logout.xml
/usr/share/ubuntu-docs/gnome/menus/C/menu-editor.xml
/usr/share/ubuntu-docs/gnome/menus/C/menus-and-toolbars.xml
/usr/share/ubuntu-docs/gnome/menus/C/mouse.xml
/usr/share/ubuntu-docs/gnome/menus/C/multimedia-systems-selector.xml
/usr/share/ubuntu-docs/gnome/menus/C/networking.xml
/usr/share/ubuntu-docs/gnome/menus/C/network-proxy.xml
/usr/share/ubuntu-docs/gnome/menus/C/nvu.xml
/usr/share/ubuntu-docs/gnome/menus/C/open-office.xml
/usr/share/ubuntu-docs/gnome/menus/C/palmos-devices.xml
/usr/share/ubuntu-docs/gnome/menus/C/preferred-applications.xml
/usr/share/ubuntu-docs/gnome/menus/C/printing.xml
/usr/share/ubuntu-docs/gnome/menus/C/qtparted.xml
/usr/share/ubuntu-docs/gnome/menus/C/realplayer.xml
/usr/share/ubuntu-docs/gnome/menus/C/remote-desktop.xml
/usr/share/ubuntu-docs/gnome/menus/C/removable-drives-and-media.xml
/usr/share/ubuntu-docs/gnome/menus/C/route-planner.xml
/usr/share/ubuntu-docs/gnome/menus/C/screen-resolution.xml
/usr/share/ubuntu-docs/gnome/menus/C/screensaver.xml
/usr/share/ubuntu-docs/gnome/menus/C/scribus.xml
/usr/share/ubuntu-docs/gnome/menus/C/services.xml
/usr/share/ubuntu-docs/gnome/menus/C/sessions.xml
/usr/share/ubuntu-docs/gnome/menus/C/shared-folders.xml
/usr/share/ubuntu-docs/gnome/menus/C/skype.xml
/usr/share/ubuntu-docs/gnome/menus/C/sound.xml
/usr/share/ubuntu-docs/gnome/menus/C/soundandvideo.xml
/usr/share/ubuntu-docs/gnome/menus/C/synaptic.xml
/usr/share/ubuntu-docs/gnome/menus/C/systemtools.xml
/usr/share/ubuntu-docs/gnome/menus/C/terminal.xml
/usr/share/ubuntu-docs/gnome/menus/C/text-editor.xml
/usr/share/ubuntu-docs/gnome/menus/C/theme.xml
/usr/share/ubuntu-docs/gnome/menus/C/time-date.xml
/usr/share/ubuntu-docs/gnome/menus/C/ubuntu-update-manager.xml
/usr/share/ubuntu-docs/gnome/menus/C/users.xml
/usr/share/ubuntu-docs/gnome/menus/C/users-groups.xml
/usr/share/ubuntu-docs/gnome/menus/C/windows.xml
/usr/share/ubuntu-docs/gnome/menus/C/xine.xml
/usr/share/ubuntu-docs/gnome/menus/C/xmms.xml

---

### Post by r4ik on 2006-02-14
I have been thinking about this and here are several other threads about this topic ending in silence.
So i am calling for help here once again because the subject is not answered.
Anyone please ?

---

### Post by Ramses de Norre on 2006-02-14
What are you asking now? Like we said, it are probably help files, settings,... which may be shared by more programs then only limewire (frostwire seems to be other program using them then). If they aren't causing any problems I'd just leave them there.

---

### Post by r4ik on 2006-02-14
Lets not get upset here no need to.
The question remains simply if you do a fresh limewire install it starts of asking several questions about connection speed wich files you want to share  bla bla.
Once is it has been removed totaly, Frostwire is suposed to do the same.
That is what i want.

---

### Post by Ramses de Norre on 2006-02-14
I'm not getting upset at all, sorry if it seemed but english is not my native language. Not so easy to express:)
I don't know the solution to your problem..

---

### Post by r4ik on 2006-02-14
No problem it is not mine either :)
Pas de probleme.
Geen probleem.

---

