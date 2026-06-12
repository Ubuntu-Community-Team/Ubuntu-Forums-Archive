---
title: "[SOLVED] anyone know how to fix a DCOP communications error?"
date: 2007-07-27
forum: Colorado Team - US
---

### Post by Keen101 on 2007-07-27
recently I started receiving DCOP communication errors, whenever I try to launch a KDE program in GNOME. This error screenshot is for kalzium, but is not limited to it.

I get the error, and the the program seems to run fine. It is rather annoying.

here is the massage in text form:

DCOP communications error (kalzium)

could not read network connection list.
/home/andrew/.DCOP_server_omni_0

Please check that the "dcopserver" is running!

---

### Post by bur[n]er on 2007-07-27
just delete that file that it references

---

### Post by kebes on 2007-07-27
> **Keen101 said:**
> DCOP communications erro

I've had that error before. To fix it you just need to delete the files DCOP files. In your home directory there will be files that start with ".DCOP" that you need to delete. There might also be ".ICE" files, too:
```

$ cd ~
$ rm .DCOPserver*
$ rm .ICEauthority*

```

After deleting them, logout or reboot. It's safe to delete those files because KDE recreates them on login.

---

### Post by Keen101 on 2007-07-27
unfortunately none of your suggestions help. I looked. there is no file named .DCOP or anything close to that name.  (and, yes I did look at the hidden files)

my .DCOPserver file is missing.

---

### Post by zir0n on 2007-08-02
I'm also having the same error when i try to start up Amarok. Its looking for that DCOP server. I looked all over for the DCOP files but I also do not have them...

---

### Post by zir0n on 2007-08-02
I just figured it out for my machine. I hope it works for you. What i found happening was that it was trying to create files in my /home/user/.kde folder but since i was running it under a normal user it couldn't get permissions to create files in that directory. So what i did was just changed the owner to the normal user by using the "chown user:group /home/user/.kde" command and all the folders within it and now my Amarok works.

---

### Post by Keen101 on 2007-08-02
huh. well, i guess zir0n  was right. 

I tried what he said worked for him.

for me it was "sudo chown andrew:andrew /home/andrew/.kde"

Cool. it works fine now!

---

### Post by SabrinalovesUbun2 on 2007-09-22
i have a similar problem

what should i do?

I attached a little picture of it

---

### Post by Keen101 on 2007-09-23
umm...  for me it was "sudo chown andrew:andrew /home/andrew/.kde"



Your problem could be different, but maybe not.

so, try opening a terminal... (>Applications >Accessories >Terminal)


then write this out and press enter:

sudo chown sabrina:sabria /home/sabrina/.kde

(assuming your username and home directory are "sabrina")


-Andrew
-keen101

---

### Post by pyroshock on 2007-11-09
Neither of the above solutions work for me and I have the exact same error message.  I removed the ICE file and that didn't work.  I also used the chown command and that didn't work.  Any other ideas?

---

### Post by Keen101 on 2007-11-10
A good general rule for things that give errors is to use Synaptic to re-install them. It has worked in the past for other errors from other programs.


If any other people have this problem, and the above solutions do not work for you, then start your own thread! I am very sure more people will help you that way. I would hate for someone not to be able to solve a problem, because they are asking for help on a solved thread.

best of luck!

---

### Post by PenguinSHT on 2007-12-14
Thanks. It solved my problem so nicely.

---

### Post by lgwwin on 2008-04-07
just restart your computer. it works for me. (I find this trick in ubuntu chinese community.)

---

### Post by flint_ on 2008-05-04
Deleting .kde did the job for me!
:)

Thanks!

Flint

---

### Post by KillerSponge on 2008-08-04
I had to add the recursive option (-R) to the chown command to get it to work, but: it works! Thanks :)

---

### Post by bluesmoke on 2008-10-23
Thank you all, I also fixed it by removing the .kde folder from the home folder. I was having this problem on asus eee 4g (Xandros).
Regards,

---

### Post by one2wonder on 2009-01-18
Removing the .kde folder from my home folder seemed to do the trick.

(I had used the chown command suggested without luck before trying this)

Do other programs use this directory to store information?  Basically I'm asking if this fix could potentially break other stuff.

Thanks,

 - wonder

---

### Post by wlenzenjr on 2009-07-29
Hey guys. This is my first time on the forum, and working w/ Linux - please bare with me :)

I'm trying to sync up an iPod nano (5th gen) to an Asus Eee PC running Ubuntu. I've been checking the forums and am not able to find out how to get the command line to appear so I can try some of the ideas below.

The error says:
There was an error setting up inter-process communications for KDE. The message returned by the system was:
Could not read network connection list.
/home/user/.DCOPserver_asus-805599479__0
Please check that the "dcopserver" program is running!

I am not able to find those files to try and delete them.

What can I do? Thanks for your help everyone!

---

### Post by stwalkerster on 2009-08-15
I ran around in circles looking for what was wrong - turned out I had no space left on my /home partition

Check you have enough disk space if you don't have any luck with the suggested solutions.

---

### Post by tstduke on 2009-11-04
As far as getting k3b to run on karmic. I had to start nautilus from root using sudo then change the permissions of all the folders, subfolders and files in the .kde file located at /home/<username>/.kde
 After I did that k3b ran perfectly from the icon, where as before I had to open a console and run it as root.

---

### Post by dddeee on 2009-11-24
Whenever you have a problem like the DCOP or your mouse or anything, shut down your computer and remove the battery.  This is a reset that fixes everything instantly without having to alter your files.    I had the mouse problem once, the mouse just was non responsive, so I removed the battery and that cleared that up.  Then when the DCOP server error happened to my wireless....I did the same thing, and all the other former wireless connections that filled the wireless box were gone except mine and it connected instantly.
 
Try it before you do anything extreme....remove the battery and wait for 10 sec. and put it back...turn it all on.  DONE!
 
Let me know if this helps anyone.

---

### Post by parisseirios on 2011-03-23
same problem try them all but nothing

---

### Post by Sadiq Huq on 2012-11-25
I ran into 'DCOP communications error' when I tried to compress many folders with *ark* and it carshed..

I solved it by removing the temporary files created by ark in this location ~/.kde/tmp-computerName. You might also see konqueror-crash-blabla.log.
konqueror runs fine now.

---

### Post by wildmanne39 on 2012-11-25
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

