---
title: "General folders/partitions"
date: 2005-07-10
forum: Desktop Environments
---

### Post by Terracotta on 2005-07-10
Hye,
I've been looking a while for a way to mount partitions in every acount at the same place, for example a partition to store music in, that would be /home/logged_acount/music, I know I can cd to maps using ~/Music, but when I installed kubuntu, I tried to make it mount a partition to ~/music, and the installer didn't like my idea very much :s. Is there a way to do this clean (instead of manually creating a music folder in every acount and manually mounting the partition every time). The idea is, I sometimes have to create a new acount, and doing everything all over again every time, seems like a lot of work to me.
Terracotta

---

### Post by adwait on 2005-07-10
The folder to which you want to mount a drive must always be present. A new home folder is created for every user, so you might want to try mounting your music folder to some other location...like /mnt/music maybe. And give each user proper permissions to access the folder..

---

### Post by Terracotta on 2005-07-10
Thanks for your very fast reaction, but can't I somehow, make it create a folder /home/newacount/music when creating a new user? I just can't imagine that that isn't possible. 

edit: Could it be that that's what the /usr file is for?? (I've been wondering about that)
for example if I create a /usr/music file will every acount than have a music folder in his/her home folder??

---

### Post by adwait on 2005-07-13
No thats not what the usr folder is for..... :) . It is used to store system wide settings..... I believe :)

---

### Post by Terracotta on 2005-07-16
then does anybody know how to do this? I'm quite positiv it can be done, I just don't have a clue?

---

### Post by z_pod on 2005-07-16
[QUOTE=Terracotta]then does anybody know how to do this? I'm quite positiv it can be done, I just don't have a clue?[/QUOTE]

I don't know if it helps but I set a shared reiserfs partition in /etc/fstab:

/dev/hdd4       /mnt/shared     reiserfs rw        0       0

All users can acces, read and write there (of course you can revoke write access if you want).

---

### Post by poptones on 2005-07-16
I think the issue is giving each user a "music" folder... correct?

Simple: put a link there.

If you have a folder /mnt/music and you want a "music" folder in the user account, rather than putting a folder there put a link to it. Open a command window and type this:

ln -s /mnt/music ./music

You will see "music" appear in a different color. When you open nautilus you'll see a folder called "music" with a link symbol attached to it. When you click the folder it will open the "music" folder at /mnt/music. You can do this as many times in as many home directories as you like.

To make a default folder "music" in **every** new user's folder (this won't affect existing users) type the following:

cd /etc/skel
sudo ln -s /mnt/music ./music

That makes "music" folder part of the default desktop template.

---

### Post by Terracotta on 2005-07-16
thanks, it's not exactly what I was looking for, but it will most certainly do for the time being :-), tag balsho sposibo poptones (at least I've been told that's thank you very much in Russian, :p). In a few months I'll have more time to do the research to find how what I was looking for is done, and I'll post it then.

---

### Post by Terracotta on 2005-07-18
mmm, strange, I've done what poptones suggested, but I don't have any permissions but the read permission :s, although I'm the sudo user, how can I change this???
Tx

---

### Post by poptones on 2005-07-18
Can you run synaptic? Accessing those folders with write access takes the same permissions. Perhaps the directory is write protected?
Try this: 

sudo chmod 700 /etc/skel

Then see if the rest works

---

### Post by Terracotta on 2005-07-18
Why do I need root access to write to those drives??? i can acces kynaptic but then I have to give my password, the meaning of all this is that I can rip my music on this drive. Just to let you know, I did that chmod thing, it gave no response, but it didn't complain either. I'm still unable to write on the drive, I just need to change the write access, but I don't know how/where ...
Thanks for your kind replies btw :-)

---

