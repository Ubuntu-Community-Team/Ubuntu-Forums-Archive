---
title: "Change the name of the Applications menu"
date: 2010-09-29
forum: Desktop Environments
---

### Post by crf on 2010-09-29
How do I change the name of the Applications menu?

What I tried, with no result:

*1)
copied /usr/share/desktop-directories/X-GNOME-Menu-Applications.directory
to ~/.local/share/desktop-directories/X-GNOME-Menu-Applications.directory

and edited
Name=Applications
to
Name=Apps

*2)
edited /usr/share/desktop-directories/X-GNOME-Menu-Applications.directory
to change Applications to Apps.

*3)
copied /usr/share/desktop-directories/X-Gnome-Menu-Applications.directory to /usr/local/share/desktop-directories/X-Gnome-Menu-Applications.directory

*4)
edited /etc/xdg/menus/applications.menu and changed <Name>Applications</Name> to <Name>Apps</Name>

----

Should any of these things I tried have worked?

---

### Post by crf on 2010-09-29
In my alacarte it's now called "Apps". Which isn't really progress ...

---

### Post by hhh on 2010-09-29
[http://www.flyninja.net/?p=888](http://www.flyninja.net/?p=888)

HTH

---

### Post by crf on 2010-09-30
Rebuilding the program I guess is an option ...

I wonder if it is possible to edit one of the language files to effect the change? (I use en_CA)

I'll investigate that ...

---

### Post by crf on 2010-09-30
It worked !
[IMG]https://doc-04-9k-docs.googleusercontent.com/docs/secure/mjpajctd8op2m5opdpaakeudfes7dr98/429v3e626jld6mhkab530k60grio4mbc/1285848000000/07843713603537685338/07843713603537685338/0B5FXtHrNOWfPNmE1NjVhOTEtYjQxNy00OWI5LThiZWMtNzhhOGMzOTY0MGUw?nonce=713u4c0q6hdms&user=07843713603537685338&hash=m4mj2jp63celnod70h9m2plh58joc9ra[/IMG]

---

### Post by crf on 2010-09-30
What I did:
*1)
Downloaded [en_CA.po]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/lucid/gnome-panel/lucid/annotate/head%3A/po/en_CA.po") for lucid's gnome-panel from bazaar.launchpad.net

*2) Using Gedit (easiest), located the right msgid and changed the msgstr from Applications to Apps:

#: ../gnome-panel/panel-menu-bar.c:183
msgid "Applications"
msgstr "Apps"

*3) ran msgfmt (in terminal) on the saved edited po file to create a mo file.

*4) Saved a backup of /usr/share/locale-langpack/en_CA/LC_MESSAGES/gnome-panel-2.0.mo, then replaced it with the new mo file, after appropriately renaming it.

*5) Logged out and back in

---

### Post by crf on 2012-03-07
Some changes:
Download location for the Oneiric: [po files for gnome-panel]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/oneiric/gnome-panel/oneiric/files/212/po").

The locale file we wish to replace with an edited version: (I'm using an en_CA locale, but you'll want to match whatever locale you're using.)
/usr/share/locale/en_CA/LC_MESSAGES/gnome-panel-3.0.mo

---

