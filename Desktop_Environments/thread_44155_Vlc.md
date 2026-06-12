---
title: "Vlc"
date: 2005-06-24
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-24
VLC is wicked. Simple and does everything (except real media). And it even has a FF plugin :)

And so does Mplayer. The Mplayer one however doesn't work for a number of quicktime files which the VLC one does. But I need the Mplayer one for realmedia streams. 

So, task A is to say "firefox use vlc for everything except real media". And that seems quite hard. It's not urgent tho. 

The larger problem at hand is that open with > VLC for gtk+ says this:

> Could not add application to the application database

You have to open the file from VLC to get it to work. 

Dave's internet research states that:

> I had the same problem and figured out a solution yesterday. The directory .local and its subdirecories in your home directory are owned by root and only that account has read/write rights. So try chown it to your account and chmod it to 700 or something like that. Hope it helps. - [http://www.linuxquestions.org/questions/history/318909](http://www.linuxquestions.org/questions/history/318909) 

and also here: [http://ubuntuforums.org/archive/index.php/t-20588.htm](http://ubuntuforums.org/archive/index.php/t-20588.htm) (last comment)

Something about changing file permissions. That's wrong cos it doesn't work on root either. But most interestingly i can no longer open with > custom command > gedit. i get the same error. A database error. Given mythtv's recent screwings with mySQL could something have happened there? It's incharge of databases right?

---

### Post by intangible on 2005-06-24
Do this:
1. open a terminal
2. type **cd ~;ls -la**
3. make sure nothing is owned by root in your home directory, if it is, you probably need to fix the permissions.
 3a. to fix permissions of directories, use this command **sudo chown -R username directory ** where username is your username, and directory is the directory, for a single file, just do **sudo chown username filename**

Here's an extension to help you out with playing media files from withen Firefox: [https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446)

---

### Post by Dave_is_sexy on 2005-06-24
Thanks that looks cool. I'll probably set it up once I have fixed the other problems as it will be very convenient.  :smile:

EDIT: (keeps it tidier). Only .. is owner by root, which is the parent directory /home i believe. What could be wrong i wonder

---

### Post by WAM on 2005-06-24
Hm... I tried chown -R username .vlc but it still doesn't work. Do I need to reboot or something?

EDIT: Fixed.

1) Right click on a media file you want to open with VLC
2) Click <Properties>
3) Select the <Open With> tab
4) Click the <Add> button
5) Click <Use a custom command> at the bottom
6) Type <vlc> in the box (without brackets).

Done.

---

### Post by Dave_is_sexy on 2005-06-24
Yay  :)

---

### Post by WAM on 2005-06-25
Upon further inspection, the problem (on my box) is that the VLC icon in the Add list has a command of <wxvlc> which for some reason doesn't work, whereas <vlc> works fine.

---

