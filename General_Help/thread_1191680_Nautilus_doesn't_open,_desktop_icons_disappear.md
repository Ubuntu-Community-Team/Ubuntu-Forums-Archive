---
title: "Nautilus doesn't open, desktop icons disappear"
date: 2009-06-19
forum: General Help
---

### Post by 7Lj3)(P38J on 2009-06-19
Folks

Nautilus and all folders can't open despite all my clicks and right-clicks. My desktop icons don't show, despite I go to GCONF and click the "show icons" on nautilus category.

How can I solve this?  I run 9.04.

Also, can't start my Evolution mailer, since it keeps asking for a /usr/bin/evolution password. I have tried all passwords, change passwords, gone to key ring setups, and yet can't solve it. This way I will have to switch to Thunderbird, and I would like to stay only with Gnome stuff for the moment.

How do you expect usual customers to stick with Ubuntu with all these bugs, annoyances and need for workarounds ?
It's a pity since Ubuntu is so great and lovely!  :-(

Thanks in advance for your kind replies.
regards
Carlos in Portugal

---

### Post by ethoxyethaan on 2009-06-19
[LIST=1]
[*]Check Chmod of home directory
[*]NOTE: 2 folowing commands delete all nautilus prefs
[*]rm -dr ~/.nautilus
[*]rm -dr ~/.gconf/apps/nautilus/
[*]Send command: killall nautilus && nautilus
[*]...
[/LIST]

to do this press ctrl+alt+F1 (login):
rm -dr ~/.nautilus
rm -dr ~/.gconf/apps/nautilus/
killall nautilus && nautilus

it could be the the last command says display not found then try:

nautilus --display=:0.0

i never experienced this behavior with Gnome this is more pebkac with result of incorrect configuration or advanced desktop effects or any other graphical intense function.

Evolution:

The reason it asks for a password is because the application is trying to access they keyring to decrypt your passwords used to access the mailserver, you entered this password the first time you started the ubuntu desktop. again this is not a error in ubuntu.

to work around that error remember the password or remove the keyring and remake one.

this is also a result of misconfiguration, its best to ether disable encryption of passwords or to decrypt your passwords after login. 

[Ubuntu Documentation](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=passwords&sa=Search)

---

