---
title: "Why don't I have the permissions to change this drive?"
date: 2009-01-23
forum: General Help
---

### Post by zero777zero on 2009-01-23
[[IMG]http://img135.imageshack.us/img135/5368/screenshottq9.png[/IMG]](http://img135.imageshack.us/my.php?image=screenshottq9.png)

seriously, i've never had this issue when formatting to NTFS in gparted. yes, i am the sole user on this computer. ubuntu 8.10

---

### Post by Archmage on 2009-01-23
Did you consider to change the permisions?

---

### Post by lykwydchykyn on 2009-01-23
What on earth are you talking about?

---

### Post by taurus on 2009-01-23
Why not just change the ownership of the mount point for that partition from root to your login name?  Then, you can write to that partition anytime you want.  

Just because you don't understand something doesn't mean it sucks.

---

### Post by glotz on 2009-01-23
This thread needs more drama.

---

### Post by zero777zero on 2009-01-23
more drama u say?

isnt ubuntu for human beings? its not like i'm trying to compile code guys, reformatting a partition is something anyone should be able to do and use immediately. either way, i still don't know how to use it. i'll just reformat it back to NTFS, marked this thread as [SOLVED]

---

### Post by LowSky on 2009-01-23
> **zero777zero said:**
> more drama u say?

isnt ubuntu for human beings? its not like i'm trying to compile code guys, reformatting a partition is something anyone should be able to do and use immediately. either way, i still don't know how to use it. i'll just reformat it back to NTFS, marked this thread as [SOLVED]

You didn't solve anything? Just change the ownership to your user name or to everyone. Its a very simple command from a terminal. the picture you show says root owns and and is the only one who can acces it, that need to be changed... It is your fault for setting it up that way.

---

### Post by hyper_ch on 2009-01-23
> **zero777zero said:**
> reformatting a partition is something anyone should be able to do and use immediately.

My mom has never formatted anything, I doubt she even knows what that is and I am quite positive that she would have troubles there ;)

---

### Post by LowSky on 2009-01-23
Hyper_ch is right how many "normal" users even know what format even means.
Most Windows user that come here start shouting "where is my C: drive?" or "how do I get iTunes working"
Do your homework before you try somemthing, don't just assume!

---

### Post by scouser73 on 2009-01-23
Just change permissions.

---

### Post by zero777zero on 2009-01-23
i guess this is more of a gparted complaint than an ubuntu one. i just formatted according to default ext3 settings. when i do the same with ntfs i don't have to add that extra step. its also pretty ridiculous you have to manually unmount the drive before reformatting, especially since they don't even tell you this, you simply get a cryptic error message.

>It is your fault for setting it up that way.
i don't see any option in gparted that deals with permissions when formatting.

>Do your homework before you try somemthing, don't just assume!
spent time on the google before i posted here. anything that was relevant was too cryptic for a noob to understand.

>Just change permissions.
hmmm... wish i could just do this from properties, where it gives permission info. if you could right click it and 'change permissions' then you could enter your root password, that would be great! (maybe something for the devs to consider) now i know this much, to change these permissions i have to use that command_line_thingy but i don't know exactly what i am supposed to input. any advice here is appreciated. i'm trying to be all h@rd(0R3_1337 by kicking NTFS.

---

### Post by taurus on 2009-01-23
Let me repeat this again.  Just because you don't understand something doesn't mean it's "pretty ridiculous".  And if you think it's pretty ridiculous, then do something about it.

---

### Post by glotz on 2009-01-23
Open the frightful terminal. Type in **sudo chown -R yourusername:yourusername /full/path/to/the/partition**

Next time just ask the question.

---

### Post by grndslm on 2009-01-24
You could also type:  sudo nautilus

But pointing and clicking takes a bit more if you're a fast typer, like most Linux users already are.

---

