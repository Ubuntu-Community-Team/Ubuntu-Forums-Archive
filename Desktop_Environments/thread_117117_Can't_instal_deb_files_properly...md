---
title: "Can't instal deb files properly.."
date: 2006-01-14
forum: Desktop Environments
---

### Post by pfabrikant on 2006-01-14
Hey,
following some advice I got from this wonderful forum I installed a deb.sh file unto my computer using the command line:
sh /directory/where/the/file/is/name of file_deb.sh
and everything unpacked properly into the destination folder.
Then I used the command line
sudo dpkg -i /location/of/destination/directory/*.deb
At that point the console started working with full power ahead untill it got stuck on some specific file, reporting:                        

Errors were encountered while processing:
 /home/pfabrikant/Desktop/Openoffice/DEBS/openoffice.org-debian-menus_2.0.0-3_all.deb

I tried downloading the deb.sh file twice from the internet but the same error repeated itself. What can I do to work this proroblem out ? can I make the system ignore this one debian package which is trouble some ?
Thanks !

---

### Post by bonzodog on 2006-01-14
what was the error? somewhere in there it gives details of the errors. It's possible you are trying to install a openoffice built exclusively for debian, which means the package hasn't been built against the ubuntu tree, which differs slightly.

---

### Post by taurus on 2006-01-14
I assume you know you can install OpenOffice v2.0 for Ubuntu with apt-get!!!

---

### Post by pfabrikant on 2006-01-14
yes, but the openoffice english version is giving me a lot of trouble with the hebrew typing.

there was no error messsage except the ' errors were encountered while processing..
Is there anyway to solve this debian root thing ?

---

### Post by aysiu on 2006-01-14
Can't you just [enable the Universe repositories](http://www.psychocats.net/linux/sources.php) and then ```
sudo apt-get update
sudo apt-get install openoffice.org-l10n-he
```?

---

### Post by pfabrikant on 2006-01-14
What's universe repositories ? and how do I enable them ?
Is that an 1.1 version of openoffice ? It has terrible bugs :(
I don't think they have the new 2.0 hebrew version with an apt-get installation option..

---

### Post by aysiu on 2006-01-14
[QUOTE=pfabrikant]What's universe repositories ? and how do I enable them ?[/quote] I linked to the instructions... that's what the underline means, even though it's a black underline, probably.

> Is that an 1.1 version of openoffice ? It has terrible bugs :(
I don't think they have the new 2.0 hebrew version with an apt-get installation option.. You're probably right... yeah, that is the 1.1 version. Nevertheless, the Universe repositories are a good thing to have.

Right now I'm downloading the .deb.sh file to see if I can play around with it and get it installed...

---

### Post by aysiu on 2006-01-14
Okay.
I got it working... sort of.

So you have the .deb.sh downloaded to your desktop.
Right-click on it and select **Properties**. Then, go to the **Permissions** tab and click **execute**--the one that's next to **owner**. Close Properties.

Then double-click on the OOo_2.0_linux_install_he_deb.sh and select "Run in terminal."

You'll be prompted to unpack it to /var/tmp/unpack_openofficeorg
Press **Enter** to do so.

This is where I got stuck. So there are a bunch of README files in there, but they're all in Hebrew, so I can't read them. There are also a bunch of .deb files, but I can't imagine you'd want to ```
sudo dpkg -i blahblahblah.deb
``` for each one of them...

---

### Post by greenpenguin on 2006-01-14
```
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe
```
In your /etc/apt/sources.list there should be two lines like these, but commented out (# in front).  Uncomment (remove the #) or paste those lines at the end.  Then sudo apt-get update and try again...

Hope that helps :)

---

### Post by pfabrikant on 2006-01-16
Thanks, but more trouble ahead..
I got to the sources.list but it's a read only gedit file so I can't delete the # at the beginning of the rows you pruposed..
What can I do ?

---

### Post by JAwuku on 2006-01-16
Try opening up a terminal and you can use** nano**.

Type:
> sudo nano /etc/apt/sources.list

which brings up the screen with the sources list.

Go down to the part which says "## Uncomment the following two lines to add software from the 'universe' ## repository."

and remove the #'s on the two lines of code below.

for example in my own /etc/apt/sources.list

> deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

Secondly, go down to the bottom 2 lines and remove the #'s:

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

save with Ctrl-O and exit with Ctrl-X

then run

> sudo apt-get update

then you're done.

---

