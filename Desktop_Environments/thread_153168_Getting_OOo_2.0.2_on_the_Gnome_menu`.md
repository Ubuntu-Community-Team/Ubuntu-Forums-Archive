---
title: "Getting OOo 2.0.2 on the Gnome menu`"
date: 2006-03-31
forum: Desktop Environments
---

### Post by dgermann on 2006-03-31
Hi--

Last night I downloaded and installed OOo 2.0.2 from the OOo site and installed it using alien. All went without incident.

Where is the new OOo on my computer? How do I start it? I still have 2.0.1 showing when I start it from the menu.

1. How do I add the new version to the gnome menu?

2. How do I get rid of the old version when I am ready to do that?

Thanks!

---

### Post by Ramses de Norre on 2006-03-31
To find command to use:
sudo updatedb
locate ooffice
and find the right file (probably in /usr/bin/).

How to remove old one:
sudo apt-get remove openoffice.org2

---

### Post by benvdh on 2006-03-31
Hey,

To find out where openoffice is installed, you can use locate. But first you will need to update the locate database. Do this using the following command:

> sudo updatedb

Now it's time to find out where your openoffice executable is located :

> locate ooffice2

When locate has finished searching, you will need to check which executable belongs to which version. To check this, do the following (in this example locate has found an executable in /opt/ooo2/) :

> /opt/ooo2/ooffice2 --version

When you've found out where the new executable is located, use smeg (GNOME menu editor) to add the new menu entry. you can start smeg using the smeg command if it's not in your menu allready. When you've started smeg use 

file > new entry

to add a new entry. Where it says command, enter the complete path to the ooffice executable. 

Kind regards,

Ben

ps. you can probably remove the old openoffice package using synaptic

---

### Post by ariel on 2006-03-31
I also succeeded in installing ooo 2.0.2 via alien. However the locate / updatedb trick didn't work for me. I had to find the new installation location manually; it was done in:

               /opt/openoffice.org2.0

Not sure if this is required, but I changed the owner of the folder and its contents:

   chown your_user_name:your_user_name /opt/openoffice.org2.0 -R

Then, to functionally replace the old 2.0.1 installation with the new one, I simply did:

               sudo gedit /usr/bin/ooo-wrapper2

And comment out the following two lines
  my $SystemInstallDir = '/usr/lib/openoffice2';
  my $OOO_BUILDVERSION = '2.0.1';

and put instead:

  my $SystemInstallDir = '/opt/openoffice.org2.0';
  my $OOO_BUILDVERSION = '2.0.2';

Worked like a charm for me. All Gnome menus, and also all nautilus and firefox associations were preserved (i.e., double click in a .doc file, and ooo 2.0.2 opens).

I think it might not be safe to remove the old version, you may break the above associations. It might be better to leave it there dormant, and do a clean Dapper install a couple of months from now. At least that is my plan :-)

Hope this helps!
Ariel

---

### Post by dgermann on 2006-04-01
Ramses de Norre, benvdh, and ariel--

Thank you each for your help. It is good to have good people like you to turn to.

ariel, how did you find your installation, finally? I used locate, even combining it with grep and either found nothing or hundreds of hits.

In any case, editing the ooo-wrapper2 did the trick for me as well. I may try uninstalling the old one just to see, since I have so much time in building the system I have, I would hate to do a clean install when the new Ubuntu 6.10 comes out!

I am glad to have that reference to smeg--it will be helpful for other things.

I did not chown anything and it seems to be running OK for an ordinary user.

Thanks folks! You're tops! Rarely do people give such detailed and to-the-point answers as you did.

---

### Post by dgermann on 2006-04-01
OIC. In the Applications Editor Menu I had not before noticed that I could add a new item.

More importantly, it looks like I should have chosen the freedesktop installer instead of the one for debian. That might have kept us all from this exercise, do you suppose?

Thanks, again!

---

### Post by ariel on 2006-04-02
I downloaded the official "Linux x86, without JRE" version from the OOo site. After unpacking it you will find a folder full of .rpms; then I used alien to convert them all to .deb's. After following the procedure described above to "integrate" the new openoffice in my desktop, I didn't have to change my default menus at all.

Regards,
Ariel

---

### Post by dgermann on 2006-04-02
Thanks, Ariel!

---

### Post by dgermann on 2006-04-03
OK, a quick follow-up and a question.

On a second computer I tried uninstalling, via Synaptic, all of OOo. Then I installed using the alien method.

There were no menus at all for OOo. I created two of them for Writer and Calc so that is working.

But, when I click on a file in nautilus, it says it cannot read the file. Anybody know how to get that working?

Thanks!

---

### Post by dgermann on 2006-04-03
OK, I found it.

Find a file of the type you want to open with the application, in this case, a .odt file or a .ods file.

Right click on the file, choose properties, go to the open with tab.

Choose the file or click add to find the right file. Choose add a couple of times and then close. 

Voila! There it is!

---

