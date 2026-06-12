---
title: "uninstall xfce?"
date: 2008-12-16
forum: Desktop Environments
---

### Post by m_a_b on 2008-12-16
I was fooling around this evening and decided to install xfce on my ubuntu distro, so I used synaptic and installed xubuntu-desktop.  It installed 85 packages including things like abiword, thunar, and gnumeric spreadsheet.  Now I decided that I really didn't want to do that, so I went back into synaptic and marked xubuntu-desktop for complete removal, but it did not mark the other 84 packages.

So, does anyone know how to remove all those packages that were installed?  Or at the very least, how to get a list of what was installed so I can go back and remove them one by one?

---

### Post by albinootje on 2008-12-16
> **m_a_b said:**
> Now I decided that I really didn't want to do that, so I went back into synaptic and marked xubuntu-desktop for complete removal, but it did not mark the other 84 packages.

So, does anyone know how to remove all those packages that were installed?  Or at the very least, how to get a list of what was installed so I can go back and remove them one by one?

Since you remove the xubuntu-desktop meta-package, a :
sudo apt-get -d install xubuntu-desktop
should show you the names of the other packages.

---

### Post by frankleeee on 2008-12-16
Make sure you find the distro your running.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by samden on 2008-12-17
I had the same problem myself. I solved it by:
- I went into Synaptic, searched for "xfce" and marked everything containing that phrase for removal. 
- After removing all of those, I then ran "sudo apt-get autoremove" to remove any extra packages that were no longer needed with xfce gone. 
- If you need the space, then run "sudo apt-get clean" - that will remove all the .deb files downloaded during the installation (and during the installation of anything you have done in the past) and may well clear up quite a lot of space on your hard drive. Not essential however.

This got rid of xubuntu pretty well, there may be a few things still hanging round but not much. It did leave behind some applications like AbiWord and Gnumetric, but I actually wanted them, and could easily remove them separately if I didn't want them. I hope this helps.

I have learnt from that - if I ever install a desktop environment again I will use "sudo aptitude install" rather than "apt-get" - aptitude remembers what you have done and will later remove the entire thing if you want rather than just the xubuntu-desktop metapackage.

---

### Post by fareedquraishi on 2008-12-17
7 rapidshare_premium_accounts
 
[http://rapidshare.com/files/172639505/RS1__7rapidshare_premium_accounts.rar](http://rapidshare.com/files/172639505/RS1__7rapidshare_premium_accounts.rar)
 
4001 Business, Sales and Personal Letters 
 
Down Load from this link
[http://rapidshare.com/files/17305444...al.Letters.rar](http://rapidshare.com/files/17305444...al.Letters.rar)
 
Microsoft Access Bible 
 
There are three parts of this huge book, Microsoft Access From beginners to Expert Level

File: Access Bible.part1.rar
DownloadLink: [http://rapidshare.com/files/17404413...ible.part1.rar](http://rapidshare.com/files/17404413...ible.part1.rar)

File: Access Bible.part2.rar
DownloadLink: [http://rapidshare.com/files/17404965...ible.part2.rar](http://rapidshare.com/files/17404965...ible.part2.rar)

File: Access Bible.part3.rar
DownloadLink: [http://rapidshare.com/files/17405337...ible.part3.rar](http://rapidshare.com/files/17405337...ible.part3.rar)
 
Formulas and Functions With Microsoft Excel 2003 

File: Formulas and Functions With Microsoft Excel 2003.part1.rar

[http://rapidshare.com/files/17399480...2003.part1.rar](http://rapidshare.com/files/17399480...2003.part1.rar)

File: Formulas and Functions With Microsoft Excel 2003.part2.rar

DownloadLink: [http://rapidshare.com/files/17402749...2003.part2.rar](http://rapidshare.com/files/17402749...2003.part2.rar)

File: Formulas and Functions With Microsoft Excel 2003.part3.rar

DownloadLink: [http://rapidshare.com/files/17403228...2003.part3.rar](http://rapidshare.com/files/17403228...2003.part3.rar)

File: Formulas and Functions With Microsoft Excel 2003.part4.rar LAST PART

File: Formulas and Functions With Microsoft Excel 2003.part4.rar

DownloadLink: [http://rapidshare.com/files/17403388...2003.part4.rar](http://rapidshare.com/files/17403388...2003.part4.rar)

----------------------------------------------------------------------------------------------

KFC AUTHENTIC RECIPES

Mc DONALDS INCLUDES ALL THESE
Big Mac®
Arch Deluxe®
Big X-tra®
Breakfast Burrito
Cheeseburger
Chicken Fajitas
Chicken McNuggets®
Egg McMuffin®
Filet~o~Fish®
French Fries
Hamburger
McChicken®
McD.L.T.®
McRib® Sandwich
Milkshakes
Quarter Pounder®
Sweer & Sour Dipping Sauce

200 PIZZA RECIPE BOOK

VEDIC MATHEMATIC SECRET

File: Mc Donalds and KFC Recipes.rar
DownloadLink: [http://rapidshare.com/files/17403824...FC_Recipes.rar](http://rapidshare.com/files/17403824...FC_Recipes.rar)
 
--------------------------------
 
BODY LANGUAGE DICTIONARY 
 
 [http://rapidshare.com/files/17398536...Dictionary.pdf](http://rapidshare.com/files/17398536...Dictionary.pdf)  
 
-------------------------------------------------------
 
child reading
Dream Psychology
inequal justice
Homeopathy Pro v1.0.0 build 51010 w fix

All in one Link - Enjoy

File: Homeopathy.rar
DownloadLink: [http://rapidshare.com/files/173971588/Homeopathy.rar](http://rapidshare.com/files/173971588/Homeopathy.rar)
 
=====================
 
1000 hacking tutorials-The Best of 2008 
 
[http://rapidshare.com/files/17305827..._of__2008_.rar](http://rapidshare.com/files/17305827..._of__2008_.rar)
====================================
 
The Emotionally Intelligent Manager - Jossey Bass
Becoming a Strategic Leader Your Role in Your Organizations Enduring Success - Wiley
Everybody Wins The Story and Lessons Behind RE MAX
Getting An Investing Game Plan Creating It Working It Winning It -John Wiley&Sons
living the brand
Crunch Point The 21 Secrets to Succeeding When It Matters Most
Leadership Secrets of the Worlds Most Successful CEOs-Dearborn Financial 
Publishing
Customer_Once_Client_Forever
Hotel_Front_Office_Management_3rd_Edition_-_John_Wiley_and_Sons
The_Essentials_of_the_New_Workplace_A_Guide_to_the_Human_Impact_of_Modern_Working_Practices

these all books are in these two links, Lots to come

[http://rapidshare.com/files/172962944/ebooks1.rar](http://rapidshare.com/files/172962944/ebooks1.rar)
[http://rapidshare.com/files/172962945/ebooks_2.rar](http://rapidshare.com/files/172962945/ebooks_2.rar)
 
================================
 
4001 Business, Sales and Personal Letters 
 

Down Load from this link
[http://rapidshare.com/files/17305444...al.Letters.rar](http://rapidshare.com/files/17305444...al.Letters.rar)

---

### Post by albinootje on 2008-12-17
> **samden said:**
> 
I have learnt from that - if I ever install a desktop environment again I will use "sudo aptitude install" rather than "apt-get" - aptitude remembers what you have done and will later remove the entire thing if you want rather than just the xubuntu-desktop metapackage.

Interesting to know. Thanks. :)

---

### Post by m_a_b on 2008-12-17
technically, I have not yet removed xubuntu-desktop yet.  I canceled out when I saw that it wasn't removing everything.

That psychocat link is freakin' awesome though.  In case anyone cares, here are the 84 packages xubuntu-desktop installs on 8.04 (I extracted these from the psychocats command line)

a2ps
abiword
abiword-common
abiword-plugins
gnumeric-common
gnumeric-gtk
gtk2-engines-xfce
imagemagick
libaiksaurus-1.2-0c2a
libaiksaurus-1.2-data
libaiksaurusgtk-1.2-0c2a
libexo-0.3-0
libgdome2-0
libgdome2-cpp-smart0c2a
libglib2.0-data
libgoffice-0-6
libgoffice-0-6-common
libgsf-gnome-1-114
libgtkmathview0c2a
liblink-grammar4
libots0
libt1-5
libtagc0
libthunar-vfs-1-2
libwpd-stream8c2a
libxfce4mcs-client3
libxfce4mcs-manager3
libxfce4util4
libxfcegui4-4
link-grammar-dictionaries-en
mousepad
mozilla-thunderbird
orage
psutils
python-exo
ristretto
tango-icon-theme
tango-icon-theme-common
thunar
thunar-archive-plugin
thunar-data
thunar-media-tags-plugin
thunar-thumbnailers
thunar-volman
thunderbird
vim-runtime
xfce4-appfinder
xfce4-battery-plugin
xfce4-clipman-plugin
xfce4-cpugraph-plugin
xfce4-dict-plugin
xfce4-fsguard-plugin
xfce4-governor-plugin
xfce4-icon-theme
xfce4-mailwatch-plugin
xfce4-mcs-manager
xfce4-mcs-plugins
xfce4-mcs-plugins-extra
xfce4-mixer
xfce4-mixer-alsa
xfce4-mount-plugin
xfce4-netload-plugin
xfce4-notes-plugin
xfce4-panel
xfce4-places-plugin
xfce4-quicklauncher-plugin
xfce4-screenshooter-plugin
xfce4-session
xfce4-smartbookmark-plugin
xfce4-systemload-plugin
xfce4-terminal
xfce4-utils
xfce4-verve-plugin
xfce4-weather-plugin
xfce4-xkb-plugin
xfdesktop4
xfdesktop4-data
xfprint4
xfwm4
xfwm4-themes
xubuntu-artwork-usplash
xubuntu-default-settings
xubuntu-desktop
xubuntu-docs

---

