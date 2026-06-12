---
title: "Getting kmfl to work"
date: 2007-01-13
forum: Desktop Environments
---

### Post by edonnelly on 2007-01-13
I am using Ubuntu 6.10 and the default Gnome environment. I have installed kmfl (keyboard mapping for linux), and it appears within SCIM, so as far as I can tell, both kmfl and SCIM are installed and working. 

What doesn't work, however, is when I try to install a keyboard. I open the SCIM utility, select IMEngine and KMFL. I then select "install" to install a keyboard, choose one of many different ".kmn" keyboard mapping files, and every time I get the error "Failed to load the keyboard file!" with no further information. I get this error on every kmn file I try.

Is anyone using this program and does anyone have any advice for me on where to go from here?

---

### Post by Fredo on 2007-01-16
At least the install guide states that the scim utility based installation is currently broken. But there is a way to install the keyboards manually.

> Keyboards can be installed by copying a compiled keyboard (*.kmfl) or the keyboard source (*.kmn) to the ~/.scim/kmfl directory (you may have to create this directory). The icon for the keyboard should be copy to ~/.scim/kmfl/icons/. There is also a kmfl keyboard management section in the scim-setup utility (this is currently broken). Right-click on the scim tray icon and se

---

### Post by edonnelly on 2007-01-21
Thank you for the reply. Unfortunately, nothing happens when I try to manually install a keyboard. I've only tried source (.kmn) files because that's all I have, but I've tried several without any luck at all.

---

### Post by Jara on 2007-12-03
I wonder if there is someone who have had something to do with KMN files, originally coded for Tavultesoft Keyman, in Ubuntu Gutsy Gibbon. More specifically, I would like to get them run in a non-English (Czech) environment. That is exactly what I can't. The current version of KMFL implemented in the SCIM is supposed to decode the Keyman rules irrespective of the underlying keyboard setting. You can choose either mnemonic or positional mode in the KMN header but whichever I use, the result is all the same: some of the keys do not respond. I tried to make use of the key constants (e.g. [K_EQUAL] etc.) but it did not help either. I only discovered that the mapping of the particular keys is messed up, following, rather improperly, more or less the Czech keyboard layout (with the positional mode on !). The deadkeys are troublesome too: they are dead indeed. Whatever address I try, they do not respond, produce no character.

I would not like to switch to the English keyboard which might be a way out of the trouble. I would rather stick to my current local setting (Czech) as it allows me type English as well, switching between Czech and Greek keyboard. I mean polytonic (ancient) Greek.

Did you come across a similar problem? Did you find a solution to it? I will be happy to know.

---

