---
title: "&quot;you are not the owner so you can't change these permissions&quot;"
date: 2009-04-21
forum: General Help
---

### Post by DesiArnez6 on 2009-04-21
Well, I am the owner of all three profiles on my system. However, I wanted to clear up the Desktop on "Profile 1" and move an Open Office Doc file to the Desktop of "Profile 2"

So I logged into profile 1

then did this more or less:
$ cd /home/profile1/Desktop/

then

$ sudo mv file.odt /home/profile2/Desktop
$ <password>

then everything seemed fine file no longer on Desktop of Profile 1, so i logged out, then logged into profile 2

And now "file.odt" is on the desktop of Profile 2 instead of Profile 1 (Just as I wanted...,,.except).

file.odt has an orange locked symbol and is now read only.

I tried to use the gui to modify permissions but it say that since I'm not the owner I can't change these permissions.

So how do I change the owner to Profile 2 of this file.

(Since its only an odt file Its not system) All I could find on here was how dangerous to alter permissions on system files. I just want to be able to use my second profile to read my Docs. please help. 

I am sure there is some command line solution here.

---

### Post by Anthon on 2009-04-21
You can either change the permissions on the file so everyone can read/write it:
  sudo chmod 666 file.odt
or change the owner
  sudo chown profile2username file.odt

---

### Post by mikewhatever on 2009-04-21
You can modify the permissions of that particular file with the following command, if you prefer CLI: **sudo chmod 770 file.odt**. It's short and to the point.
You can also use the file browser running with admin privileges, just hit alt+f2 and type **gksudo nautilus**.s
If, however, you plan to use many file across your profiles, it may be wise to create a group (let's say it's named profiles) and add both users to that group. You can do that under System->Admin->Users and Groups.

---

### Post by DesiArnez6 on 2009-04-21
Thanks a million, worked fine, I chose the second option. (Just out of curiosity, chmod 666 is always the number to use to enable all users to read and write?
 And then I assume this would be reversible later If one were to then type in the second chown option, that the earlier chmod changes would be undone and now profile 2 would be the owner with everyone else back to read only?

---

### Post by Anthon on 2009-04-21
666 is octal for a bit setting of 110110110 which translates to Read Write Execute for user, group and (all) others respectivly (the other post suggested 770 which set execute permissions which is not necessary *and* would require for the two users to be in the same group, which IIRC is no longer true for most modern Linuxes (as a new group is created per user).

The chmod changes are different from the chown options. If you do the chown after the chmod, still everyone with access to the directory can change and modify that file. You would have to do:
  chmod 640 
to make it read-only for groupmembers and non-readable by all others

---

### Post by ButchMel on 2012-04-09
> **mikewhatever said:**
> You can also use the file browser running with admin privileges, just hit alt+f2 and type **gksudo nautilus**.s


Ouch... what have I done to my system ? ... Sorry, I'm newbie.  I just wanted to change permissions on a folder and, while highlighting the file in graphich mode I did just this, it asked for my password, and as I entered and okayed, it just disappeared....  My folder is still 'not mine'... (this is on a drive attached to this new Ubuntu server, a drive that was previously external to another Windows machine). 

Have I changed something to my server permissions here ?

---

### Post by oldos2er on 2012-04-09
ButchMel, please start a new thread for your question, this one is three years old.

From the forum's posting guidelines:

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

