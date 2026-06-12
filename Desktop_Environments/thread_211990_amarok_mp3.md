---
title: "amarok mp3"
date: 2006-07-09
forum: Desktop Environments
---

### Post by 7he on 2006-07-09
Hi everybody!

since the last update of some codecs (about 2 days ago) Amarok can't play mp3 anymore although the default ubuntu multimedia reader can!
When I open Amarok, I get the following warning:


[COLOR="Sienna"]The xine-engine claims it cannot play MP3 files.
You may want to choose a different engine from the Configure Dialog, or examine the installation of the multimedia-framework that the current engine uses.
You may find useful information in the FAQ section of the amaroK HandBook.[/COLOR]

If I understand, Amarok uses xine-engine to play mp3 and xine can't play them . Am I wrong?
Can someone explain me how to make it possible playing mp3 in Amarok?

Thank you very much

---

### Post by dexter on 2006-07-09
Do you have amarok-xine installed ? This is the xine engine for amarok. You can check using Synaptic Packet Manager under System, Administration.

---

### Post by FredB on 2006-07-09
> **7he said:**
> Hi everybody!

since the last update of some codecs (about 2 days ago) Amarok can't play mp3 anymore although the default ubuntu multimedia reader can!
When I open Amarok, I get the following warning:


[COLOR=Sienna]The xine-engine claims it cannot play MP3 files.
You may want to choose a different engine from the Configure Dialog, or examine the installation of the multimedia-framework that the current engine uses.
You may find useful information in the FAQ section of the amaroK HandBook.[/COLOR]

If I understand, Amarok uses xine-engine to play mp3 and xine can't play them . Am I wrong?
Can someone explain me how to make it possible playing mp3 in Amarok?

Thank you very much

Install libxine-extracodecs, in multiverse repository.

---

### Post by 7he on 2006-07-09
> **dexter said:**
> Do you have amarok-xine installed ? This is the xine engine for amarok. You can check using Synaptic Packet Manager under System, Administration.

Thanks for you quick answer!

I just checked, it is installed


2 days ago, everything worked perfect, but till last update, amarok can't play mp3 anymore... :-(

another idea?

---

### Post by 7he on 2006-07-09
> **FredB said:**
> Install libxine-extracodecslibxine-extracodecs, in multiverse repository.

Those codecs are allready installed:
when I type: [COLOR="Sienna"]sudo apt-get install libxine-extracodecs[/COLOR],  

I got the following message:
[COLOR="Sienna"]Reading package lists... Done
Building dependency tree... Done
libxine-extracodecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]

Thanks for your help!

problem still not resolved, another idea ? ;-)

---

### Post by FredB on 2006-07-09
erh... My mind is empty... No other ideas :(

Sorry :-k

---

### Post by 7he on 2006-07-09
> **FredB said:**
> erh... My mind is empty... No other ideas :(

Sorry :-k  --> no problem! ;-)

Is it possible to undo an upgrade, and how can I perform this? 
I worked perfectly 2 days ago,  so, if I uninstall the updates it should work, no?

thanks!

---

### Post by Jucato on 2006-07-09
you can try removing the Amarok 1.4.1 repository, then uninstalling amarok (amarok-xine and kubuntu-destkop will be uninstalled with it), then reinstalling kubuntu-desktop to reinstall amarok and amarok-xine. amarok-engines might also be installed, but it can be safely removed later. 

I'm just not sure why the upgrade would cause that to happen. I have not encoutered such a problem. probably because I have a Kubuntu installation (but currently using GNOME).

---

### Post by Thund3rstruck on 2006-07-09
Though this may not help, have you tried to run Amarok as root (ie: sudo amarok)? After this upgrade I had a similar issue where amarok crashed consistently when it tried to add anything to the database, play songs, etc. I ran it as root and everything worked. I guess I need to look at the permissions in the path where the database is stored (I think /usr/lib/share or something)

---

### Post by 7he on 2006-07-09
> **Thund3rstruck said:**
> Though this may not help, have you tried to run Amarok as root (ie: sudo amarok)? After this upgrade I had a similar issue where amarok crashed consistently when it tried to add anything to the database, play songs, etc. I ran it as root and everything worked. I guess I need to look at the permissions in the path where the database is stored (I think /usr/lib/share or something)

running amarok as root does'nt change anything ...

---

### Post by 7he on 2006-07-09
> **Fenyx said:**
> you can try removing the Amarok 1.4.1 repository, then uninstalling amarok (amarok-xine and kubuntu-destkop will be uninstalled with it), then reinstalling kubuntu-desktop to reinstall amarok and amarok-xine. amarok-engines might also be installed, but it can be safely removed later. 

I'm just not sure why the upgrade would cause that to happen. I have not encoutered such a problem. probably because I have a Kubuntu installation (but currently using GNOME).

I did uninstall amarok by doing:
[COLOR="Sienna"]sudo apt-get remove amarok[/COLOR]
The shell told me that xine would be uninstalled too.

Then I reinstalled amarok.
I noticed that the version installed on my computer now is 1.3.9

Do I have to add something in my sources.list file ?  Do I have to do an update ?  how ? ...

Thanks for spending time helping me!

---

### Post by Thund3rstruck on 2006-07-09
So is the version you have now working? If you are going to want to upgrade to 1.4.1 again, you'll need to add the amarok repository into sources.list but don't do that unless you've completely removed the previous one.

---

### Post by 7he on 2006-07-09
> **Thund3rstruck said:**
> So is the version you have now working? If you are going to want to upgrade to 1.4.1 again, you'll need to add the amarok repository into sources.list but don't do that unless you've completely removed the previous one.

allright,  so

to uninstall I do 
[COLOR="Sienna"]sudo apt-get remove amarok[/COLOR]

then I add an amarol repository in my sources.list file [COLOR="Red"]can someone give me one?[/COLOR]
then I do 
[COLOR="Sienna"]sudo apt-get update[/COLOR]
then
[COLOR="Sienna"]sudo apt-get install amarok [/COLOR]

is it correct?

Thanks for helping another noob ;-)

---

### Post by Jucato on 2006-07-09
You can try using the 1.3.9 version, which is the version that Kubuntu automatically installs, or you could use the 1.4.0 version, which was released just a few days before Dapper's official release. The instructions for Amarok 1.4.0 is here: [http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

The instructions are basically the same as 1.4.3, except that is uses a different repository.

EDIT: the proper steps would be (if you prefer doing it in the command line)
1. sudo apt-get remove amarok
2. take note of what it will remove
3. edit your repository, remove the 1.4.1 repository, or replace it with the 1.4 repository.
4. sudo apt-get update
5. sudo apt-get install amarok (plus anything else that was removed, notably xine related packages)

That should get you back on your feet. 

Hope that helps.

---

### Post by jetpeach on 2006-07-15
I have this exact same problem, I am not positive when it happened but xmms can play mp3s fine, amarok cannot, it brings up a popup asking if I'd like to install mp3 support I click yes nothing happens.  I have all the libraries mentioned in this thread installed.

EDIT: found my problem, although I had libxine-extracodecs installed, I had somehow lost the multiverse repository when editing my sources.conf and it wasn't being updated.  So the version was old and amarok couldn't use it.  It threw me off because I could even remove then reinstall libxine-extracodecs, but what I didn't realize is it wasn't actually checking the web just using the cached package...

---

### Post by Jucato on 2006-07-15
Check if Amarok is using the xine engine (Settings > Configure Amarok > Engine).

---

### Post by jetpeach on 2006-07-17
Yes, it is configured to use the xine engine.  I should have mentioned though that I am running edgy on the machine that stopped working and my other machines are ok (the original poster with the problem presumably has dapper though).  It's strange though, because xmms works to play mp3s for me just not amarok.  And all the configuration stuff seems like it's correct.

See [this thread at amarok forums]("http://amarok.kde.org/forum/index.php/topic,12589.0.html") for more info on my problem.
Any help of course is much appreciated, I'm hoping a patch will soon fix the problem but it has now been there for a couple weeks so just hoping

---

### Post by ctulb on 2006-07-18
I had the very same problem for a couple of days and then it seemed to sort itself out? :confused: I did a reinstall of libxine-extracodecs as suggested which didn't seem to do anything but then as I said everything straightened out.

Don't know if this is much help or not!

---

### Post by 7he on 2006-07-26
Hi !!
I was on hollidays, I just came back tonight!

I don't know if the problem is resolved, but I would like to thank every person who spended time to help!
It's really great to have such a community in the background of ubuntu,  great spirit!   
thank everybody!

7he

---

### Post by 7he on 2006-07-27
problem resolved with latest updates,

Thanks everyone!
enjoy your hollydays!

7he

---

