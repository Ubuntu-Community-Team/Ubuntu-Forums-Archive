---
title: "how to install patchs for ut 2004?"
date: 2006-11-28
forum: Gaming &amp; Leisure
---

### Post by holylucifer on 2006-11-28
OKay im on ubuntu dapper drake ,not edgy,

i downloaded the patches for ut 2004, but i have to do some sudo commands or something,nor do i have a clue on how to install the patch, although i feel dissapointed and feel spoilt by windows, although windows is not secure...

Can any of you have installed the linux ut 2004, it would be great of how you did it!

Thanks in advance ill check this later.

---

### Post by holylucifer on 2006-11-28
Please note i got ut 2004 to run and work under ubuntu(and play online,although it seems i got to have audio drivers or something) although its not patched so, all i want is the patches installed and i don't have a clue here,

---

### Post by xopher on 2006-11-28
Check out this site: [http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)

It offers the updates with installers, so you only have to ./filename.run

You probably have to make it executable first though.

And as for the sudo cmd, you only have to run the installer's with sudo if you've installed ut2004 somewhere your user don't have write permissions to.

Cheers

---

### Post by holylucifer on 2006-11-29
Thanks.

---

### Post by _simon_ on 2006-11-29
To patch you just copy paste or drag and drop the individual files.

---

### Post by holylucifer on 2006-11-29
Yeah but it askes for permissions, and i am new to this os.

---

### Post by holylucifer on 2006-11-29
O well i give up , ill play it unpatched, thinking about going back to windows, but this os is peice of cake when it comes to just useing the internet and mail.

---

### Post by User_Program on 2006-11-29
ekk don't leave! :)

This is if you have the unzipped untared ect versions of the patch 
To make it ezer in console type 
> gksudo nautilus
or
> gksu nautilus

Sorry I'm not sure which on (I use KDE) I'm guessing you use Gnome?)

It will ask for a password..most likely it's the password you type in everytime you login to gnome.  It will open up a file manager for you. You will look for usr/local/games in there will be the ut2004 folder.  Take all the files from the untared or unzipped and put them in the appropriate folders.. i/e system files go in the usr/local/games/ut2004/system and so on. This may not be the right path I have mine installed in /home/useraccount/ut2004 so I don't have to mess with this permission stuff nonsense ;) Linux is nice for the security but sometimes it's just alittle to much.

Now if you have the ut2004.megapack-english-2.run from the link that xopher provided all you will have to do is 
> sudo ./ut2004.megapack-english-2.run

Note make sure that file is executable I'm not sure if nautilus has this feature but right click the ut2004.megapack-english-2.run and there maybe a permissions tab or somthing like that that makes it executable. If you can't make it executable in the console
> sudo chmod 766 2004.megapack-english-2.run
or
chmod -R 766 2004.megapack-english-2.run

For give me about these commands because I have been spoiled for far to long with this KDE feature. And I try not to help ppl to much in posts because most the time I just muddle around until it works :) but we have to get you up and running UT because...well it's the best game ever! :)

In the console typing "cd" before the folders name you want to get into moves you to that directory so if you save the 2004.megapack-english-2.run to say /home/user/saves
you would 
> cd /home/user/saves
I think just cd saves will work too.

Go with that and if you have anymore problems I will help yea out!

---

### Post by holylucifer on 2006-11-29
Yes Gnome in the garden, on this ubuntu the speed of ut 2k4, is nice, i can just crank all the graphics settings and textures on max,where on windows it would do the hard drive sound,Playing on demo servers, heh.

---

### Post by holylucifer on 2006-11-29
well i got the mega pack installer to work the easy way by just fricken all arrows on, and double clicked and started up, without this command line bler, And says i don't have ut 2004 installed, where i do.

---

### Post by holylucifer on 2006-11-29
i installed ut 2004 as root,

---

### Post by nalinde on 2006-11-29
@ holylucifer have had all the same problems with ut2004 that you seems to had (problems installing patches and so on..). Well as usually one of your best friends consulting about linux "problems" is Google ;-) and then i found some good stuff!

Anyway found this site that is quite excellent (faq) 
[http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml]("http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml")

make sure to also check out the Linux Gaming FAQ link in the bottom if this page. It's awesome! and if you've got the possibility to enable Fast Write, do that :-) quite performance boost :-D.

Anyone else then me, that got 2004 run better in Ubuntu then in Xp btw?

---

### Post by Tuna-Fish on 2006-11-30
I suggest just uninstalling it and reinstalling it somewhere else to make patching and modding easier. Just make a new folder called games or something in your home folder, then start the ut2004 installer as user (ie DONT sudo), and when it asks where to install put it in the games/ut2004. after that installing patches is just a peace of cake.

---

### Post by macabro22 on 2007-12-13
Shoot, the megapack installer says I don't have utk4 installed here as well!!

Is there a fix for this???

---

