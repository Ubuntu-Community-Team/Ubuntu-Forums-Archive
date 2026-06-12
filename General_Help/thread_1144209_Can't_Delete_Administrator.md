---
title: "Can't Delete Administrator?"
date: 2009-04-30
forum: General Help
---

### Post by jzacsh on 2009-04-30
Hello, trying to delete and re-create particular admin.

I had two administrator users: jon & bob. bob was the original user set-up during installation (just yesterday), and through bob was jon set-up as another admin. I did this all via GUI.

I then tried to delete bob (while logged into jon, obviously), via the "edit users and groups" (accessed via right-click on "switch ..." button on top-right desktop). This seemed to work, i was left with only "root" and "jon". I rebooted, then opened up the same panel and clicked "add+" to recreate a new version of bob - Rec'v a message "bob already exists", surprising (maybe i've been approaching this incorrectly, then?). I looked in /home and found jon and bob folders, though "that's funny". So i did a "sudo rm -rf bob" - and the bob folder went away. So i rebooted.

Now i'm back into jon, and finding i still get "bob already exists" message when I try to add the user. Is there a system file somewhere listing users that I should edit? is it far more complicated then what i think? did i do this wrong all together, and now i'm screwed?

Any help is UBER-appreciated
Thanks in advance!
--
using 9.04

---

### Post by taurus on 2009-04-30
Look in /etc/passwd, /etc/group, & /etc/shadow.

```
cat /etc/passwd
cat /etc/group
sudo cat /etc/shadow
```

---

### Post by kanikilu on 2009-04-30
You can also delete a user, including removing the home directory and other options, all in one step, with **deluser**.

```
man deluser
```

---

### Post by jzacsh on 2009-04-30
> **taurus said:**
> Look in /etc/passwd, /etc/group, & /etc/shadow.

```
cat /etc/passwd
cat /etc/group
sudo cat /etc/shadow
```

the only file of these three that had bob in it was /etc/group (63 lines, bob is on the last line)
vi was acting quirky when i tried to !wq after deleting bob's line round- about:
cat /etc/group | head -62 > ~/temp
sudo cat ~/temp > /etc/group

and get

bash: /etc/group: Permission denied

should I do it some other way??

---

### Post by jzacsh on 2009-04-30
> **kanikilu said:**
> You can also delete a user, including removing the home directory and other options, all in one step, with **deluser**.

```
man deluser
```

oh great, i'll read into it right now, thanks!

---

### Post by _Purple_ on 2009-04-30
You can remove the group bob from System > Administration > Users and Groups and delete it from manage groups.

---

### Post by taurus on 2009-04-30
You probably need the vim-full package or use nano.

```
sudo nano -Bw /etc/group
```

---

### Post by jzacsh on 2009-04-30
$ sudo deluser -remove-all-files bob
[sudo] password for jon: 
/usr/sbin/deluser: The user `bob' does not exist.

?? so does that mean its too late for me to use deluser because i already deleted too much stuff? if so i guess, i need full vim (*i'd rather stick to one editor right now, i'm still learning vi as it is*) 

[U]incase someone else comes across similar situation:
[/U][https://help.ubuntu.com/community/VimHowto](https://help.ubuntu.com/community/VimHowto)
sudo apt-get install vim-full

so i deleted the last line with full vi, then received a "found copy in swap" warning, hit enter at "enter or type command". then "wq!" and vi says:

"/etc/group" E212: Can't open file for writing

---

### Post by Grishka on 2009-04-30
this error comes up because the user folder is not deleted when removing a user. to fix this, simply rename bob's home folder to something else. that will let you create bob user account again. then simply remove the fresh, almost empty bob home folder and rename the backup you've made before to bob.

---

### Post by jzacsh on 2009-04-30
> **Grishka said:**
> this error comes up because the user folder is not deleted when removing a user. to fix this, simply rename bob's home folder to something else. that will let you create bob user account again. then simply remove the fresh, almost empty bob home folder and rename the backup you've made before to bob.

i think you may be misunderstanding what's going on. i do not have any backup of bob's user folder (didn't want one). currently in the /home directory there is only one folder: /home/jon and nothing else.

---

### Post by Grishka on 2009-04-30
> **jzacsh said:**
> i think you may be misunderstanding what's going on. i do not have any backup of bob's user folder (didn't want one). currently in the /home directory there is only one folder: /home/jon and nothing else.

indeed, I seem to have misunderstood your problem. sorry. :)

---

### Post by jzacsh on 2009-05-01
> **taurus said:**
> You probably need the vim-full package or use nano.

```
sudo nano -Bw /etc/group
```

I can't believe I hadn't done this. I'm SUCH a newb.... 

[FONT="Courier New"]**[COLOR="Red"]sudo[/COLOR]** vi /etc/group[/FONT]

thanks for your help everyone. I learned a lot.

---

### Post by kanikilu on 2009-05-01
> **jzacsh said:**
> I can't believe I hadn't done this. I'm SUCH a newb.... 

[FONT="Courier New"]**[COLOR="Red"]sudo[/COLOR]** vi /etc/group[/FONT]

thanks for your help everyone. I learned a lot.

hehe, to paraphrase Homer Simpson: *"**sudo**: The cause of, and solution to, all of life's problems."* :biggrin:

---

