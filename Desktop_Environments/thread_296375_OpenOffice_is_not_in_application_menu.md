---
title: "OpenOffice is not in application menu"
date: 2006-11-09
forum: Desktop Environments
---

### Post by HeisanHopp on 2006-11-09
After installing Ooo (Norwegian) OpenOffice are not in the application menu. 
I used the official .tar.gz file (Norwegian).
This is how i installed it (found it in the forum):

sudo apt-get install alien

Open the new (2.0.4) .tar.gz in a temp folder; then open a terminal in the folder that contains the official .rpm's and do:

sudo alien *.rpm (this takes a few minutes)
sudo dpkg -i *.deb

New installation will be done in: /opt/openoffice.org2.0
sudo chown your_user_name:your_user_name /opt/openoffice.org2.0 -R
Then: sudo gedit /usr/bin/ooo-wrapper
And comment out the following two lines
my $SystemInstallDir = '/usr/lib/openoffice2';
my $OOO_BUILDVERSION = '2.0.1';
and put instead:
my $SystemInstallDir = '/opt/openoffice.org2.0';
my $OOO_BUILDVERSION = '2.0.4';

This worked fine, and I can run Ooo from the terminal window...but how can i get it in the menu?

Will be happy for any help

---

### Post by DaveBorealis on 2006-11-09
> **HeisanHopp said:**
> I can run Ooo from the terminal window...but how can i get it in the menu?

Hello,

Assuming that you're using Gnome, right click on the 'Applications' menu, select 'Edit Menus', and that will open the 'Alacart Menu Editor'.  Under 'File' on the menu editor select 'New Entry', and for the command just type in what you've been using on the command line in the terminal, probably '/usr/bin/ooffice -writer %U'.

Best regards,
Dave

---

### Post by HeisanHopp on 2006-11-10
Thanks...it worked:) , but...
If i would like the application to appear for several users, do you know how?

---

