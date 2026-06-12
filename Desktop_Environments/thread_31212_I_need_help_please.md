---
title: "I need help please"
date: 2005-05-02
forum: Desktop Environments
---

### Post by Zonkle on 2005-05-02
Hi,

I installed Ubuntu I think successfully.

The way I installed Ubuntu is that in Windows XP I deleted a partition, then installed Ubuntu.

The boot loader works great.

Now ..... is this Ubuntu Linux has only like Command Line enviroment ??? Because after I select Ubuntu from the loader, some things happen then Ubuntu asks me for the user name and password (in a Command Line env) that I made during the installation .. after that .... I see my name and after it "~$"  in the command line :| ! is this Ubuntu linux or I did something wrong ??

And how can I have an enviroment more like windows ?

Please tell me.

Thank you very much.

---

### Post by bnutting on 2005-05-02
I don't want to state the obvious but I think that something went wrong with the install. You should be greeted with a graphical login screen. Did do a default install or did you pick the 'server' install?

I've installed Ubuntu on my laptop several times and never had it boot straight to a console. Do you see any 'Failed' messages during boot?

---

### Post by Zonkle on 2005-05-02
Thank you for the very fast reply :)

I installed with the defualt installation ... no server option.

Let's say I messed up .. is there any way to reinstall ?

The "fail" i get is the Synchronization with Ubuntu web site as I remember.

I remember that I got a screen talking about Virtual installation or something.....but i ignored it quickly and quit it :(

Thanks.

---

### Post by huh? on 2005-05-02
sounds like you're booting up in command line mode...try this, boot up, login, and then type "startx" (without the quotes)...
you might also try CLT/ALT/F7 and see what happens
I'm just a newb, so take it for what's its worth
:)

---

### Post by UbuWu on 2005-05-02
If that doesn't work, type ' sudo apt-get install ubuntu-desktop ' and try startx again.

---

### Post by Zonkle on 2005-05-02
Thanks :)

I tried and CTRL + ALT + F7 and nothing happened !

I tried the startx and i some errors :S look here:

[IMG]http://img.photobucket.com/albums/v254/hasanbb/FlexiCam_045.jpg[/IMG]

Is 1.5 GB of space not enough for this Linux ?? because the error on line 132 says no space left of device !

Thank you.

---

### Post by ow50 on 2005-05-02
[QUOTE=Zonkle]Is 1.5 GB of space not enough for this Linux ?? because the error on line 132 says no space left of device![/QUOTE]

I'm not sure, but I think 1.5 GB might not be enough for a full install.

Type "df -T -h" to see your filesystem space usage. See if there's any space left on the filesystem mounted at /.

---

### Post by Zonkle on 2005-05-02
[QUOTE=UbuWu]If that doesn't work, type ' sudo apt-get install ubuntu-desktop ' and try startx again.[/QUOTE]
 Thanks UbuWu,

I tried "sudo apt-get install ubuntu-desktop" , but I get an error that tells me the something interrupted and I have to configure dpkg manually using "dpkg --configure -a", when I try that it tells me that I need to be a super user ! I'm the only account ! ...... what should I do ?

Thank you again :) and thank you all for helping me :(

---

### Post by Zonkle on 2005-05-02
[QUOTE=ow50]I'm not sure, but I think 1.5 GB might not be enough for a full install.

Type "df -T -h" to see your filesystem space usage. See if there's any space left on the filesystem mounted at /.[/QUOTE]
 ow50 thanks,

I tried df -t -h .... but i got empty table, so i tried df alone so I found out that the "/" has used 100% !!! and availble is 0 ! i think that pretty much means that i'm out of space right ? :(

If so .... what can i do ?? how much Ubuntu needs ? why is it taking a lot of space !? more than XP ! .... anyway ... i have another paritition which is "D" (5 gigs)... so now i'm thinking of deleting it too .. 

But now how can I delete Ubuntu to reinstall it with a bigger space ???
If i delete it i will have 10 gigs of unused space - so maybe i will take some to windows...

Ahh man ..... can you please help me guys :( ?

Thank you very much.

---

### Post by Zonkle on 2005-05-02
Hey ow50 ;),

This is what I got when I tried df :

[IMG]http://img.photobucket.com/albums/v254/hasanbb/FlexiCam_046.jpg[/IMG]

---

### Post by WildTangent on 2005-05-02
1.5 GB is definately not enough for ubuntu, i think it requires 2 GB or more

-Wild

---

### Post by ow50 on 2005-05-02
If you have some partitioning software on your windows, I'd recommend you do some partitioning there. There might even be a builtin partitioner on Windows XP, I don't remember anymore. Then during install just assign them to your desired locations.

I still don't know how much space Ubuntu needs, but I'd recommend at minimum:
5 GB for /
1 GB for /home
1 GB for swap

But that depends on how much space you have and how you plan to fill your disks. Use the search and you'll find plenty of topics on pre-install partitioning advice.

As an example, my disk usage:
5.5 GB at /
719 MB at /home
50  GB at /home/osmo/Documents

---

### Post by Zonkle on 2005-05-02
Thanks all for bearing with me :)

ow50, after I delete the paritition "D" and the Ubuntu used space I will have 4.5 Gigs ... is that enough ?

Hmm ..... now Ubuntu is installed .... what should I do to clean it (format it) and I want at the same time to keep my Windows XP !

I mean if I delete the partitions from Windows XP, is the loader will still be able to load windows xp ? and then can I install the ubuntu again ? or what should I do ?

Thank you very much :)

---

### Post by bnutting on 2005-05-02
If you get rid of the 'small' Ubuntu partition and create a larger one when you install Ubuntu it will 'see' that you have Windows installed and add an entry to your GRUB loader. You should be able to boot Windows from it.

I currently have Windows-XP and Ubuntu running on my Laptop without any problems.

Bryan

---

### Post by Zonkle on 2005-05-02
[QUOTE=bnutting]If you get rid of the 'small' Ubuntu partition and create a larger one when you install Ubuntu it will 'see' that you have Windows installed and add an entry to your GRUB loader. You should be able to boot Windows from it.

I currently have Windows-XP and Ubuntu running on my Laptop without any problems.

Bryan[/QUOTE]
 Thanks bnutting :)

So the steps i'm thinking of are :

1- Go Windows XP
2- Delete the Ubuntu Partition
3- Delete the partition "D" (the one i don't want)
4- Reboot with Ubuntu CD and Install

Is that right ? byt these steps I won't lose Win XP ?

BTW, when I'm installing on my laptop the Ubuntu installer is not in the center of the screen :S ... is there anyway to fix that ? .... i can't see the other options like choosing my area and stuff ... can i edit that later anyway ?


I really appreciate your help to me.

Thanks.

---

### Post by ow50 on 2005-05-02
[QUOTE=Zonkle]2- Delete the Ubuntu Partition
3- Delete the partition "D" (the one i don't want)
[/QUOTE]
Combine these two to form one partition if possible and let Ubuntu installer suggest how it wants to fill the space.
[QUOTE=Zonkle]Is that right ? byt these steps I won't lose Win XP ?[/QUOTE]
You won't lose Win XP.

Just in case:
If Grub boot loader somehow doesn't work, you can always return to original windows booting by booting from your Windows CD and issuing commands "fixmbr" and "fixboot" at the recovery console.

---

### Post by Zonkle on 2005-05-02
ow50 , really thanks for the great tip :)

Thanks a lot all of you.

---

### Post by Nu-Buntu on 2005-05-02
Probably not a bad idea to go into Windows first and make a boot floppy just in case!

---

### Post by poofyhairguy on 2005-05-02
[QUOTE=Zonkle]
I tried "sudo apt-get install ubuntu-desktop" , but I get an error that tells me the something interrupted and I have to configure dpkg manually using "dpkg --configure -a", when I try that it tells me that I need to be a super user ! I'm the only account ! ...... what should I do ?
[/QUOTE]

For future reference, whenever something tells you you don't have teh correct permission, put sudo before the line. For example:

sudo dpkg --configure -a

---

### Post by Zonkle on 2005-05-03
Thanks you all very much for the help :)

Now I'm writing from my Ubuntu :)

But there is a problem that Ubutnu is not Detecting the port for me Modem :( However I see the Modem's name in the Device manager(But I don't think it is the real name !) my modem name on Windows XP is HSP56, in Linux I see AC'97 Modem controller , I think there is something wrong right ?. What can I do ?

The way I'm connected now is that I have external Modem U.S Robotics.

Thank you all for your great help :)

---

