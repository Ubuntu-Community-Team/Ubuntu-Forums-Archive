---
title: "su, gksu stopped working"
date: 2009-05-27
forum: General Help
---

### Post by rsullivan25 on 2009-05-27
I have a problem that recently started and I don't know how or why.  I was hoping someone could help.

I have Hardy installed on a Dell vostro 200 - it's a work computer.  Recently I can't seem do elevate my priviledges to do any admin stuff.  when I sudo or su - it asks for a password, but just hangs there after I give it.

Similarly, when I launch an app like synaptic or network admin that requires admin priviledges, when I give it the root password, the icon changes to the "working" icon for a minute then disappears and I don't see the application I want to work with.

Also, yesterday I found out that if I lock my screen, I can't unlock it - I get the same problem - I enter my password and it just sits there.

I can use root access if I log in to recovery mode - I was able to use this to update (wine was the only update at the time).

I did a fsck because I thought that might be the problem, however that turned out fine, yet I still can't do anything that requires admin priviledges.

also, the first time I try to browse the network I get a DBus error, however it works if I try again a second time.

I read a few things about how if you change the hostname on 127.0.0.1 that similar issues appear however my hostname hasn't changed and is correct.

One last thing which may be related - when I can see the network, I can't connect to the computers by name - I have to do it by IP. I used to be able to connect to other ubuntu computers by name but not anymore.

I have a feeling these are all related because everything was working fine until a few days ago.

any suggestions or help is appreciated.

Thanks in advance!

---

### Post by VMC on 2009-05-27
I've had that in the past, but don't know how I fixed iit. It's been a while now.

If you try and start using a Terminal maybe there will be infomation there. Like so:

> vmc@vmc-desktop:~$ gksu nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:3397): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:3397): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:3397): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

The first WARNING I got while using the gui. The others I got after I closed it.

Also, what were you doing a few days ago that started all this. Another thing I've tried was to temporarily create a new user and see if that works. Then you will know, it's in your home folder somewhere.

---

### Post by _Purple_ on 2009-05-27
Did you check if you are added to the admin group? You can check that by typing in terminal
```
groups
```

---

### Post by rsullivan25 on 2009-05-27
> **VMC said:**
> I've had that in the past, but don't know how I fixed iit. It's been a while now.

If you try and start using a Terminal maybe there will be infomation there. Like so:



The first WARNING I got while using the gui. The others I got after I closed it.

Also, what were you doing a few days ago that started all this. Another thing I've tried was to temporarily create a new user and see if that works. Then you will know, it's in your home folder somewhere.

I tried this, however I have the same issue - when I enter the root password it just sits there, therefore there are no further messages

---

### Post by rsullivan25 on 2009-05-27
> **_Purple_ said:**
> Did you check if you are added to the admin group? You can check that by typing in terminal
```
groups
```

I am member of root, adm and admin

---

### Post by rsullivan25 on 2009-05-27
something else.

I just tried to reboot and it wasn't able to complete.  

In particular a bunch of services take a looooong time to end:

avahi-daemon timed out
vmware, clamav and bind all take a long time to end. It's like they are waiting for something. I just sat here for aat least 5 minutes watching the computer attempt to shutdown.

---

### Post by rsullivan25 on 2009-05-27
Wait found another thing.

When I try to view network settings (via system ->administration ->network) it takes a long time to show anything in any of the windows.

It finally did after about 30 seconds and when I went to authenticate (with admin password) it took a long time, then I got a window "Failed to authenticate".  When this window popped up, my computer locked up.

I don't understand what's happening - this computer has been fine since I first installed ubuntu over a year ago, these things just started happening recently.

---

### Post by Bender2k14 on 2009-05-27
Because you have a bunch of seemingly unrelated and odd behavior, are you sure that there is not some hardware problem?  Does everything work on when you boot using the LiveCD?

---

### Post by rsullivan25 on 2009-05-28
I found my problem

I don't know why it was causing problems but I removed vmware from the startup and things are fine now.

I noticed that vmware player modules were taking a long time to start and stop, so I logged into the recovery mode and removed it from /etc/init.d (moved it actually in case that wasn't the problem) and my booting speed has increased, I can sudo and gksu and browse the network again.

So if anyone else is having issues, and have vmware player - see if this will work for you.

For anyone that provided suggestions - thanks for your help!

---

### Post by YQ002lc2 on 2009-05-30
Hello all,

I have a similar problem. Whenever I do sudo nautilus, gksudo nautilus, gksu nautilus, I get similar messages.

They all look something like this: 

** (nautilus:30563): WARNING **: Unable to add monitor: Operation not supported

The number changes everytime, but it's always the same message.

Then there's usually something like this when I close nautilus:

--- Hash table keys for warning below:
--> file:///root

(nautilus:31018): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:31018): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

The list of hash table keys changes depending on what browse while it's open.

---

### Post by YQ002lc2 on 2009-05-31
I posted a thread before I found this one. Please keep an eye on this one, too. 
[http://ubuntuforums.org/showthread.php?t=1174145&highlight=unable+add+monitor](http://ubuntuforums.org/showthread.php?t=1174145&highlight=unable+add+monitor)

Thanks,

jpinson

---

### Post by Bender2k14 on 2009-06-01
> **jpinson said:**
> The number changes everytime, but it's always the same message.

The number is the Process ID (PID), which is a unique number given to each process.

---

