---
title: "Rather Simple .ICEauthority question"
date: 2010-11-15
forum: Desktop Environments
---

### Post by miserly-martyred on 2010-11-15
So I took the time to read some other threads about this, but my solution has not been met.

I have had an issue changing my "normal" user account password and I was stupid / impatient enough to change it with root instead of myself personally.

Thus the abovementioned file is owned by root and I am completely unable to log in to any GUI whatsoever.

I am looking for the command to reboot to a root shell prompt and run something similar to the following.

sudo chown $user:$user /home/username/.ICEauthority

sudo chmod 644 /home/username/.ICEauthority


BUT - my issue is that I do not know how to run "as me" from root.  I need to use root's power to change a file to be accessed by someone else.  This command I found seems to reflect upon the one doing it, rather then somebody else:

I feel like if I run that straight from root, it will not mod my private, separate account.

b/c when I do it, it states that the .ICEauthority file does not exist.

I think I ran:  su myusername

and it gave me:  myusername@mycomputername root:/$

or so ... indicating, in my mind, that it wasn't really JUST my private acct.

I just need to make my private user .ICEauthority file bound my my private user permissions again, instead of by root's

Any cmd suggestions?

---

### Post by tom4everitt on 2010-11-15
> **miserly-martyred said:**
> So I took the time to read some other threads about this, but my solution has not been met.

I have had an issue changing my "normal" user account password and I was stupid / impatient enough to change it with root instead of myself personally.

Thus the abovementioned file is owned by root and I am completely unable to log in to any GUI whatsoever.

I am looking for the command to reboot to a root shell prompt and run something similar to the following.

sudo chown $user:$user /home/username/.ICEauthority

sudo chmod 644 /home/username/.ICEauthority


Substitute $user to your real username in the chown command. Assuming your username is "bob", you should run:

```

sudo chown bob:bob /home/username/.ICEauthority

```

to have .ICEauthority be owned by bob.

---

### Post by miserly-martyred on 2010-11-15
I appreciate the help but when I tried exactly the following it didn't work:

(assuming uName = khaos)

[as root]: sudo chown khaos:khaos /home/khaos/.ICEauthority


it says that it cannot update the file because "no such file or directory"



{ I only did it as root b/c my GUI failed and I had to reboot to a root prompt in Ubuntu Recovery cmd mode }

I get the feeling that my usage of code in that manner may be botching it, but I pretty much have 0 affinity for coding / command line ... mostly

---

### Post by tom4everitt on 2010-11-15
Hmm, you could try to create an .ICEauthority file then:

touch /home/khaos/.ICEauthority

and then change owner if necessary (with the chown command, as before).

---

### Post by tom4everitt on 2010-11-15
BTW, just as you said in your first post, running

```

su username

```

will turn you into that user. The reason it still says root is that /root is your current directory.

What happens if you do that, and then do:

```

start gdm

```

---

### Post by mcduck on 2010-11-15
> **miserly-martyred said:**
> I appreciate the help but when I tried exactly the following it didn't work:

(assuming uName = khaos)

[as root]: sudo chown khaos:khaos /home/khaos/.ICEauthority


it says that it cannot update the file because "no such file or directory"



{ I only did it as root b/c my GUI failed and I had to reboot to a root prompt in Ubuntu Recovery cmd mode }

I get the feeling that my usage of code in that manner may be botching it, but I pretty much have 0 affinity for coding / command line ... mostly
The error message is telling you that it can't find the file you are trying to chown. Either it doesn't exist, or you mistyped something.

Also, if you are already root (or logged in the recovery mode) you don't need to use "sudo".

---

### Post by miserly-martyred on 2010-11-15
The Results of tom's advice:

(assuming khaos = uName and bot = machine name)

root@bot:~# su khaos

khaos@bot:/root$ start gdm

start: rejected send message, 1 matching rules; type="method_call", sender=":1.9" (uid=1000 pid=1242 com="start) interface="com.ubuntu.Upstart 0_6.Job" member="start" error num="unset requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

---

### Post by tom4everitt on 2010-11-15
But did you try to create the .ICEauthority file? 

```

su khaos
touch /home/khaos/.ICEauthority

```

Also, you could try to launch gdm as root, and see if that makes a difference:

```

sudo start gdm

```


When something seems to unfixable I usually just reinstall my system though. It is done within an hour, so it is often quicker than actually solving the problem. A good thing is to write down the changes you do to your new system (in a google doc or file in your dropbox or whatever), so that you can redo them the next time you install/upgrade/change distro.
Also, putting your home folder on a separate partition will make reinstallation much smoother.

---

### Post by miserly-martyred on 2010-11-15
so ... I tried the startup gdm and creation advice of the file itself to no avail.

Also, I absolutely cannot risk upgrade or reinstall (upgrade JUST maybe).

If upgrade would fix it, I'd have to do that command line too.

Anyhow I can't reinstall because I have 7000GB of ridiculously important academic, hobby & professional data. (yes I = multimedia guru)

Finally, after trying all aforementioned and recent advice, I got this exact layout upon GUI- (full GDM) bootup:

1
Could not update /home/khaos/.ICEauthority file

2
There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

3
Nautilus could not create the following folders
home/khaos/desktop
home/khaos/.nautilus
Please "create them yourself or give nautilus permission to do so."  (shorthand)

4
language support database incomplete


omfg ... what is WRONG with me ... ugh ...

---

### Post by tom4everitt on 2010-11-15
Okay. I understand your data is important. There are pretty straight forward ways of getting your data out, however: 

1. Make yourself a live cd/live usb (see [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) for instructions ). Once booted into the livecd you can access your hard drive under Places, and thereby moving your data to an external hard drive, burning it to dvd or uploading it to a cloud service. 

2. You can also do it from the command line, it's pretty straight forward if you have an external hard drive. Tell me if you need guidance with that. 

Either way is backing up your data a pretty good idea! I would even suggest you do that before you try to fix your computer in any other way, but that is your choice of course. 


As for the error messages you received:

number 1: 
```

sudo chown khaos:khaos /home/khaos/.ICEauthority
su khaos
chmod 777 /home/khaos/.ICEauthority

```
should give anyone permission to modify your .ICEauthority file.

Number 2
not sure

Number 3
```

su khaos (if you didn't do that already)
mkdir /home/khaos/Desktop
mkdir /home/khaos/.nautilus

```
will create the missing folders. 


Number 4
probably not that severe.

---

### Post by tom4everitt on 2010-11-15
Just struck me, the problem is probably the ownership/permissions with your home folder *itself*. That's the only reasonable explanation, as I see it. Try:

```

sudo chown -R khaos:khaos /home/khaos
chmod 755 /home/khaos

```

---

### Post by miserly-martyred on 2010-11-16
[ - @tom4everitt - ]

I sincerely appreciate your effort.  You obviously have ridiculously profound knowledge in these areas and that is not only respectable but also excellent for this forum.

I am thankful for your patience and efforts to a REAL dedicated solution but to be a bad news bringer I must also admit that the most recent bit of advice you gave was only partially successful.

I was able to get into "a" khaos directory, but it was not my real one and it had none of my files.

additionally, the theme was totally incorrect, and the language database error was present again.

further, "gksudo nautilus" does not work

BUT my hdd is at the EXACT prev. capacity, thus file integrity has been maintained for my personal content.

any further suggestions you may have would be greatly appreciated.

---

### Post by tom4everitt on 2010-11-16
Okay, so at least it meant some progress then.

Normally, your home directory has the same name as your user account. It is not necessary to set it up that way though. You should look in /home to see if there are other folders there (apart from khaos), and if they contain your files. 

The other possibility is that your home folder was put on a different hard drive/partition that is no longer mounted correctly. If you think this is possible, go through the different partitions (under Places) and see if any of them contain your files. 

Basically, I just want to know where your files have gone :)



When you say that the theme is incorrect, does that mean it is just different, or that it is malfunctioning?

---

### Post by miserly-martyred on 2010-11-16
So, like I said, my GUI and file browser don't work well when I log in to the system.  As before, the HDD capacity & free space seem to show that my stuff is still there though.

I had to try multiple boot discs to browse but I still couldn't locate any of my data.

Many things are saying 'access denied' and others simply don't contain my stuff.

I think you may be right about the fact that my account directory is mis-mounted.  I dunno much about error correction for that though.

---

### Post by tom4everitt on 2010-11-17
When in the live cd, starting nautilus (the file browswer) with
```

gksu nautilus

```
should get rid of the access denied problem.

I would also suggest you use a search function. Surely you know the name of some of your files? Also, make sure you look through all partitions.


Mounting is a pretty big area (too big for me to describe in detail here). But basically your hard drive is divided into partitions. When your system boots, the "main" partition is *mounted* at '/', the *root* of the file tree. 

During boot, other partitions can be add to the file tree. For example another partition might be mounted on '/home'. That means everything under /home will be on this newly mounted partition. If no partition is mounted on /home, everything under /home will be on the original "main" partition. 

Also, when you plug in an external hard drive or CD, they are mounted to folders under /media. (Look in /media before and after plugging in something, and you will see.)

The mounting that should take place during boot is defined in a file called /etc/fstab. [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)


This might a side track, but it's useful to understand anyhow.

---

### Post by miserly-martyred on 2010-11-18
after you reminded me of the "gksudo nautilus" I took it upon myself to meddle a bit.

1- I simply booted the machine to the login interface.
2a- I logged in to the "quazi-user" account of mine that had none of my data.
2b- Gksudo'd into the root account file browser
3- Then I saw the Ubuntu company's shortcut stating "Access-your-private-data.desktop." - within my khaos account main page
4- When I clicked I was denied access b/c it was an 'untrusted source'
5- I then wormed my way in with gEdit and executed the "exec" in it's code lines.
6- It led me here: "/usr/bin/ecryptfs-mount-private". - And I entered my new private password I had changed to.
7- I then proceeded to locate my data right where it should have been but it had obviously been previously locked by encryption after " I " mounted " Me " improperly without the encryption mask virtualized, thus my account wasn't really "me".
8- While I had this terminal & file browser up I used the root account to revert my khaos account back to it's original password.

and after a reboot ...

-->  :) now everything works :)

---

### Post by miserly-martyred on 2010-11-18
Thanks everybody for the useful contributions ;)

good to have...

---

### Post by miserly-martyred on 2010-11-18
> **miserly-martyred said:**
> Thanks everybody for the useful contributions ;)

good to have...



and apologies for what was obviously a blatant growing misnomer...

NOT SO SIMPLE ... lol

---

### Post by tom4everitt on 2010-11-19
Haha, no, a little trickier than expected :P

---

