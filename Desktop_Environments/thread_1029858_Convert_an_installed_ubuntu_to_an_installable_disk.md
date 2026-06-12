---
title: "Convert an installed ubuntu to an installable disk"
date: 2009-01-03
forum: Desktop Environments
---

### Post by Uji-Wu on 2009-01-03
Hi!

I worked my ubuntu very hard with visual custiomization and additionnal softwares. I would like to use all those new settings i made in a newly made ubuntu install disk so i can reuse the same desktop config on diferant computers. Using Ultimate edition 2, based on hardy herron, with all updates common to this day. I guess that the whole setup is now over 4 gigs... so if i could remove what might be of no use without altering either the currently installed linux, nor the future installation disk's integrity... Like, making a selective convertion...

I just thought something as making a simple backup of the whole disk, but i am scared that some, mayby all computers i would try it other than my own would have missing settings all around and mayby not even boot at all... So backupping isnt enough....

About windows stuff.. I used to copy a backup of my computer on a laptop and it worked, installing all new needed generic drivers... Or did i have some wierd set of folders named with numbers with all drivers inside that appeared by mystical forces out of my sight that i did copy in the /system32/drivers folder....... Yet... It was working nicely.

It wouldnt have worked moving from an amd to an intel... I suspect generation differances to be a cause of failure too........ If i could get some software to detect and replace chipset files while copying the backup to a drive that'd probably solve the problem... And allow to put a fully customized windows on another computer without building an unattended edition whitch seems to be a roar of efforts.

So... If that'd be possible with linux... That'd be sweet......... Yet.... To be concidered  that it would need to make grub installed even if it was a backup..... And stuff like inserting new o-s lines that could be installed on other computers like grub so goodly does while installing a classique ubuntu live cd....

So yeah... Some way to integrate all changes to an installation disc? From an installed ubuntu filese to an installation cd that'd be same-as the public installation live cd?

Thanx.

Léonard-Raoul Leporteur [MFHSBTJ31183]

---

### Post by logos34 on 2009-01-04
as long as it's no bigger than a dvd-size (4.4. gb), you could use Remastersys:

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by 2hot6ft2 on 2009-01-04
> **logos34 said:**
> as long as it's no bigger than a dvd-size (4.4. gb), you could use Remastersys:

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)
If you're close to getting it all on 1 dvd using that but a little bit over after clearing out the trash and ```
sudo apt-get autoremove
``` then you could make a file with all the software you have currently installed using the method below and then use it to restore any apps you remove so it will fit on the dvd after reinstalling the system.
> **handydan918 said:**
> Okay, this should be in the wiki, or something. It's so simple, yet so powerful.


```
sudo dpkg --get-selections
```


```
sudo dpkg --get-selections > softwarelist
```
At this point in the proceedings, you hose your system and reinstall, and then...

```
dpkg --set-selections < softwarelist
```


```
apt-get dselect-upgrade
```

Enjoy.That should make it work with just the apps you uninstall to reinstall.

Did that make any sense?

---

### Post by Uji-Wu on 2009-01-04
My current ubu is near 11.6 gigas, round 280 000 files.
On the remastersys page, they link to an how-to: [http://www.remastersys.klikit-linux.com/capink.html](http://www.remastersys.klikit-linux.com/capink.html) .
They says that it is possible to host a 2gb top fileset to a 700 mb cd using the squashFS filesystem instead of ext2.... (with possible trial and errors) ... This probably means that i could host a 10gb fileset on a 4.4gb dvd right?

Also... 2hot6ft2, you spoke interresting stuff... Do you mean that i could make most extra softwares like, auto install on first network connection?

- Yet.. Today i had some problems using the repositories with update/synapic.. Posted a thread in the installation/upgrade forum section about that.... Like, some softwares i use or not canot upgrade, the repositories seems like hacked or so.... The original files might have been replaced with malicious files... Anyway i couldnt have made my upgrade without removing those other softwares..... 

I guess i'll have to take a few days to make my live cd, waiting for the repos to be fixed..........

- I'll probably keep chatting in this thread until my live cd is released :) wil be quite good for anyone wanting to render the same process :)

Also, if the result is appropriate, i guess i could offer the resulting iso to the ubuntu team? So that they take what is good for a further release? (just finetunings and artwork but yet... :P )

Thanx for the help thought!


-Lucien Lavoie

---

### Post by logos34 on 2009-01-04
You might also consider combining 2hot6ft2 excellent suggestion with **AptOnCD**:

basically run 

sudo dpkg --get-selections > packagelist

then use [AptOnCD]("http://aptoncd.sourceforge.net/doc-manual.html") to backup to dvd all your deb packages in /var/cache/apt/archives.

Now get rid of them to save space:

sudo apt-get clean

That will significantly reduce the size of your compressed remastersys image.

Run remastersys and make your dvd.

Then when you reinstall you will add the aptoncd dvd as a software repository.  Run the restore function, which will copy everything back to /var/cache/apt/archives.

Now run

dpkg --set-selections < packagelist

which will look for the pkgs on your hard disk first and install them from there

or simply

sudo dpkg -i /var/cache/apt/archives/*.deb

(you could also install the aptoncd 'metapackage' which has all the other backed-up pkgs as dependancies)


So basically you'll have a Remastersys dvd and an AptOnCD dvd--a perfect image of your system on one disc, and the installed apps, programs and updates on another disc, which you simply add after restoration, without the need to download everything all over again.

---

