---
title: "&quot;Nautilus cannot handle Computer: locations&quot;"
date: 2008-05-20
forum: Desktop Environments
---

### Post by underworld288 on 2008-05-20
I don't remember exactly when this starting taking place but when I click on Computer on my desktop it tells me "Nautilus cannot handle Computer: locations". It does this for Network and the Trash too. Can someone please help?

---

### Post by VMC on 2008-05-20
> **underworld288 said:**
> I don't remember exactly when this starting taking place but when I click on Computer on my desktop it tells me "Nautilus cannot handle Computer: locations". It does this for Network and the Trash too. Can someone please help?
If you Right-Click what does "Location:" say?

---

### Post by underworld288 on 2008-05-20
I'm sorry, I made a mistake, when I try to open the Computer shortcut on my desktop it says "There is no application installed for this file type". When I try to open it from the start menue, under places, it tells me "Nautilus cannot handle Computer: locations". 

And for your question VMC it say "on the desktop".

---

### Post by VMC on 2008-05-20
> **underworld288 said:**
> I'm sorry, I made a mistake, when I try to open the Computer shortcut on my desktop it says "There is no application installed for this file type". When I try to open it from the start menue, under places, it tells me "Nautilus cannot handle Computer: locations". 

And for your question VMC it say "on the desktop".

That's the one I was referring to. The one on the Desktop. The icon with the name Computer. Mine says this: Location: /home/vmc/Desktop

---

### Post by matt2175 on 2008-05-21
I'm having the same problems but also with cd/dvd cdrom and floppy. I cant get anything to mount

mine is pointing to /home/myname/Desktop

i read that somewhere theres a bug in Nautilus or gfvs? kinda annoying because I need to drag a file over to Windows and I cant...

Kinda disappointed I guess next time I'm just going to have to wait 2 weeks or so before I allow my computer to update.

---

### Post by fmonjaraz on 2008-05-21
Same problem. I can't use my external hard drive either.

---

### Post by bankanidhi on 2008-06-02
This problem is definitely due to gvfs. After installing ubuntu, do not update the gvfs and its component. all other updates can be aplied. Right now it looks there is no solution to this problem. if u have the problem then reintsall ubuntu and update all except gvfs and is component. 

I have tested this after many reinstallations. Now i have updated ubuntu running fine (I have updated everything except gvfs and its componets.)

---

### Post by Sonic Reducer on 2008-06-03
whats up with all these updates recently? my trash applet isn't working, i'm having trouble mounting things, compiz was doing that "white screen when blanked" thing, now i can't open my computer or trash.

seriously, stop "fixing" my software like this. this is bush-league windows stuff

---

### Post by jeffimus on 2008-06-09
This is happening to me too.  Places/Computer brings up the "Nautilus cannot handle computer: locations" error.  The "Computer" shortcut on the desktop doesn't work either, and has a "Location:" value of "home/jeffimus/Desktop". I can't mount USB drives. Basically the system is useless.

Please, does anyone know how to restore gvfs to a working version without reinstalling the OS?

---

### Post by Sonic Reducer on 2008-06-09
> **jeffimus said:**
> This is happening to me too.  Places/Computer brings up the "Nautilus cannot handle computer: locations" error.  The "Computer" shortcut on the desktop doesn't work either, and has a "Location:" value of "home/jeffimus/Desktop". I can't mount USB drives. Basically the system is useless.

Please, does anyone know how to restore gvfs to a working version without reinstalling the OS?

the only way i can see to fix it (if you didn't already lock the version that came installed) is to go back and lock the original version.

.:EDIT:. didn't work

---

### Post by VMC on 2008-06-09
This is strange. Mine works okay. But I don't have compiz or 3d turned on. I wonder if that has something to do with it.

I do havea Nautilus search error reported elsewhere.

---

### Post by sjordan on 2008-06-12
I turned off compiz-fusion, restarted and the problem remains.  I even downgraded my gvfs packages but it didn't change anything. :(

---

### Post by Sonic Reducer on 2008-06-12
> **sjordan said:**
> I turned off compiz-fusion, restarted and the problem remains.  I even downgraded my gvfs packages but it didn't change anything. :(

i'm beginning to think it's not GVFS, but something dependent on it. i locked the "stock" versions of the GVFS files on my desktop and can still run regular updates with everything working.

meanwhile, i revert back to the stock GVFS files on my laptop and still no luck.

all i can tell you guys is that once you update the entire computer without locking GVFS you are screwed. it might not be GVFS thats doing it, but if you update GVFS something else gets fuxxored

---

### Post by jeffimus on 2008-06-12
> **Sonic Reducer said:**
> the only way i can see to fix it (if you didn't already lock the version that came installed) is to go back and lock the original version.

.:EDIT:. didn't work

Thanks for trying, Sonic. Your information is helpful, if only to tell me how bad the problem is. I shall carry on waiting for a miracle.

---

### Post by Sonic Reducer on 2008-06-12
> **jeffimus said:**
> Thanks for trying, Sonic. Your information is helpful, if only to tell me how bad the problem is. I shall carry on waiting for a miracle.

i'm actually thinking about APTonCD and reinstalling hardy for my laptop. it's the only thing i can think of to fix this.

does aptoncd care if i run it on my desktop and install the packages onto my laptop? i don't want it to save the packages preconfigured for my desktop, because my laptop's processor is a completely different architecture

---

### Post by Terrycymru on 2008-06-13
Just to add to the comments. Everything has been working OK for me. However, I wanted to delete a file in usr/share/opera and as usual used sudo nautilus but hit the error "Nautilus cannot handle computer: locations". This is presumably a permissions issue. The only directory accessible is root>Desktop!

Here is what happened at terminal in case it means something to anyone:
```

[sudo] password for user: 
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6833): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6833): WARNING **: bookmark uri is file:///root/Desktop, but expected file:///root

--- Hash table keys for warning below:
--> file:///

(nautilus:6833): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6833): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown 
```

---

### Post by Terrycymru on 2008-06-13
This bit may be the problem (or just a symptom of something else?):

**WARNING **: bookmark uri is file:///root/Desktop, but expected file:///root**

Anyone know how to fix it?

---

### Post by John_T on 2008-06-15
I'm having what I think is the same problem. At first I thought it was only my newly upgraded to hardy machine, but I've since realised my wife's 7.10 machine has the same issue.

Here's the issue.
Go to Places>Network"
I get a list of machines on the LAN, no problem. (The hostname is "mythty" in this case)
When I double click on of the machine's icon, it's shares are listed correctly. This is shown in the pic below.  

[IMG]http://img214.imageshack.us/img214/928/nautilussharesuy0.png[/IMG]

I then double click on the share I want (in this case "ourmusic", and instead of opening it in nautilus (as had been happening previously for several months), I get:

[IMG]http://img171.imageshack.us/img171/6900/nautiluserrorap0.png[/IMG]


_A few notes:_
[LIST]
[*]If I address machines by IP address, it works.  But this is no good for the various machines around the place that are already setup to use host name.
[*]I've tried a complete samba / smbfs reinstall, to no avail
[*]I tried the rollback described in [this thread]("http://ubuntuforums.org/showpost.php?p=5161469&postcount=15"), with no success.
[/LIST]

I'd be really interested in hearing if this is what other people are seeing, and where to go from here.

---

### Post by asoare on 2008-06-27
> **jeffimus said:**
> This is happening to me too.  Places/Computer brings up the "Nautilus cannot handle computer: locations" error.  The "Computer" shortcut on the desktop doesn't work either, and has a "Location:" value of "home/jeffimus/Desktop". I can't mount USB drives. Basically the system is useless.

You can mount them from the command line, you make a directory in /media and then *sudo mount /dev/sdb1 /media/directory_created*

(/dev/sdb1 is, in my case, the removable storage)

> **jeffimus said:**
> Please, does anyone know how to restore gvfs to a working version without reinstalling the OS?

I had the same problems and today I installed gvfs from [GNOME official sources]("ftp://ftp.gnome.org/pub/gnome/sources/gvfs/0.99/") and a couple of my problems are fixed: trash applet is working fine, no more "Nautilus cannot handle Computer: locations" error, CD/DVD Creator Works fine, however I still don't have automount with removable storage and my other partitions don't show up in Places. At least we're on the right track.

---

### Post by sjordan on 2008-07-04
> **asoare said:**
> I had the same problems and today I installed gvfs from [GNOME official sources]("ftp://ftp.gnome.org/pub/gnome/sources/gvfs/0.99/") and a couple of my problems are fixed: trash applet is working fine, no more "Nautilus cannot handle Computer: locations" error, CD/DVD Creator Works fine, however I still don't have automount with removable storage and my other partitions don't show up in Places. At least we're on the right track.

Installing from source fixed most or all of my problems! Thanks

---

### Post by Der_Xte_Mensch on 2008-07-06
hey guys and girls... i have the same problem. installing from source fixed most of my problems (trash, computer, cd creator), but i still can't go to "network". and then there are in my file browser on the left side both the button "new" (for the cd, i have in my drive) and the button cdrom0, which doesn't work ("mount: /dev/hda doesn't exist"). i think, i just can ignore this error, because i can access my cd's by the other button, but nonetheless it's strange...

if you have solutions to fix the rest of my problems, please tell me ;-)

---

### Post by k2chris1983 on 2008-07-11
I also had the same problem, which I have no clue what happen or what caused it. I also updated to the latest version of "gvfs" at [ftp://ftp.gnome.org/pub/gnome/sources/gvfs/]("ftp://ftp.gnome.org/pub/gnome/sources/gvfs/")... 

Now my menu "Places" work: Computer, CD-ROM, Network and so on.

Thanks Asoare!

---

### Post by nowshining on 2008-07-15
i've had too many problems and had it with hardy - gutsy worked fine & I thought Hardy would be more stable for me due to the LTS tag, however it seems that that TAG is a fake, it's the worst version of Ubuntu I used so far.

For that, however those who have problems and want to try the gvfs from the gnome.org site, won't have to compile as here is a deb for it, just install and reboot. It works, but ur other troubles won't go away..

However my only diff. this time is going to gnome from kubuntu to hardy and going back to gutsy to the gnome..

again Hardy sucks for me. Yes feisty was fine, too. lolz...

---

### Post by Halibutt on 2008-08-26
> **k2chris1983 said:**
> I also had the same problem, which I have no clue what happen or what caused it. I also updated to the latest version of "gvfs" at [ftp://ftp.gnome.org/pub/gnome/sources/gvfs/]("ftp://ftp.gnome.org/pub/gnome/sources/gvfs/")... 

Now my menu "Places" work: Computer, CD-ROM, Network and so on.

Well, now I can see the trash, though I still can't open it (no error though). Also, all of my desktop's content disappeared, can't right-click it, even files saved to it do not show up. Finally, after installing all of the required components and dependencies my "Places" still don't work - this time showing up a different error ("Can't open file:///home/halibutt/Dokumenty" No default action; or something along those lines, my Ubuntu's in Polish). 

BTW, all the files are still there, as I can navigate to desktop through the console, but no files show up on the desktop.

Any idea how to set this right? Anyone willing to help a newbie? :)

BTW, It's horrible, but from my experience Windows XP is more stable and more safe than Ubuntu (sic!). Such automatic update packages are as bad as viruses...

---

### Post by raphaelmarcomini on 2008-10-03
I had the same problem using this package. Nautilus was uninstalled and now i am not able to reinstall it gives the following message:
Pendency: gvfs-backends but will not be installed

My system is in portuguese, so i had to translate the message

---

### Post by Prinssimikko on 2008-12-17
> **sjordan said:**
> Installing from source fixed most or all of my problems! Thanks

Yes! After a long searching this worked for me as well! thanks a lot!

---

### Post by phiphi on 2009-02-03
What seems to help is:
sudo mv /usr/local /usr/local.old && sudo mkdir /usr/local

Undo would be:
sudo rm -r /usr/local && mv /usr/local.old /usr/local

I found it on Launchpad and it helped someone who asked me for help.

---

### Post by Otu on 2009-02-06
Ok, now every problem is gone overnight o_O i didnt do anything about them and now everything is as they should be, except the little thing that gnome/nautlius/whatever is saying that my storage hdd is picture CD, not big deal.

---

### Post by RGPerson on 2009-02-16
> **nowshining said:**
> 
For that, however those who have problems and want to try the gvfs from the gnome.org site, won't have to compile as here is a deb for it, just install and reboot. It works, but ur other troubles won't go away..
.


Thanks but we tried this after noticing we couldn't open Computer anymore.  Got the same error as what started this thread.  I tried this deb file, but at first it said it needed dependencies and I'd have to run a command from the Terminal. I did and it kept saying it was removing Nautilus stuff.  We rebooted.  We ran the deb again and it didn't give any errors.

But we still can't go to Places and get anywhere.  I'd tell you the error, but my husband installed PCManFM and now that's what's defaulting.  Under Places, I see Home Folder, Desktop, Documents, Music, Pictures, Videos and then cdrom0 and cdrom1 and then Search for Files and Recent Documents.

We only have one CDRom drive.  

I'd really like to get this back without reinstalling everything. Again.  But I'm downloading a new CD just in case.

Gabrielle

---

### Post by RGPerson on 2009-02-17
Well found a partial solution in another thread ([http://ubuntuforums.org/showthread.php?t=644877](http://ubuntuforums.org/showthread.php?t=644877)) by goodling "reinstall Nautilus".  It said to put this command in Terminal: sudo aptitude install ubuntu-desktop.

I did that and said Yes to all the prompts and Nautilus is back!  Mostly.

We can open anything in Places and it shows up just fine.  

What we can't do is see our Trash or add icons to the Desktop.  I could live with the Trash problem if only I knew where the Trash was located in File Browswer so we could browse to it and empty it now and then.  As for the icons, I can add them to the panel so that's a so-so workaround.  They're small there with no text to remind you what they stand for. 

So, major problem resolved.  Minor ones still exist.  Would still like some help if someone could offer it.

Gabrielle

---

### Post by GnuSense on 2009-02-21
Gag, I'm using the LTS version of Hardy and I tripped over this bug when trying to give support to a Gnome user.  Unbelievable. My suggestion is to install konqueror (or thunar or pcmanfm or mc or just about any other file manager), Konqueror's kioslaves work fine. I'm hoping a future upgrade will fix the bug, but then, I probably won't notice since I never use Nautilus, always seemed to me a bass-ackwards file manager, though I understand it finally has tabs in 8.10.

---

### Post by samsom on 2009-02-27
> **RGPerson said:**
> Well found a partial solution in another thread ([http://ubuntuforums.org/showthread.php?t=644877](http://ubuntuforums.org/showthread.php?t=644877)) by goodling "reinstall Nautilus".  It said to put this command in Terminal: sudo aptitude install ubuntu-desktop.

I did that and said Yes to all the prompts and Nautilus is back!  Mostly.

We can open anything in Places and it shows up just fine.  

What we can't do is see our Trash or add icons to the Desktop.  I could live with the Trash problem if only I knew where the Trash was located in File Browswer so we could browse to it and empty it now and then.  As for the icons, I can add them to the panel so that's a so-so workaround.  They're small there with no text to remind you what they stand for. 

So, major problem resolved.  Minor ones still exist.  Would still like some help if someone could offer it.

Gabrielle

Heres the absolute path to your trash. You can just clear it from the terminal.

 cd ~/.local/share/Trash


I am a Ubuntu newbie as well and am having the same problem. Am I right in thinking that Nautilus not working means that I cannot access the filing system in a GUI mode, but it should work fine if I access it from the terminal?

---

### Post by GnuSense on 2009-02-27
> **samsom said:**
> 
I am a Ubuntu newbie as well and am having the same problem. Am I right in thinking that Nautilus not working means that I cannot access the filing system in a GUI mode, but it should work fine if I access it from the terminal?

Like I said in the post above, you can access all that stuff from any other GUI file manager as well as the command line, but not Nautilus because it is broken (for now).  

$
sudo apt-get install konqueror thunar dolphin krusader xfe pcmanfm  emelfm2 rox-filer

I prefer EACH of those file managers to nautilus, even when it is working as advertised...especially in the brain-dead spatial mode, Dog, what a piece...really, the worst file manager since Eazel, it seems like it is designed by sadists for masochists, but I guess that's why it took me 10 months of using Hardy to realize it was broken.

You can even access the files in your trash can from nautilus.  Just enter /home/USERNAME/.local/share/Trash in the location bar.

---

### Post by samsom on 2009-02-28
I was checking launchpad.net and realised that my problem was not due to an update but because I had installed glib a couple of days ago. So if anyone else has done the same, there is a solution posted there which worked for me. Here goes...hope it works for you as well.



"I just finished helping someone with this issue. It turned out to be caused by an install of glib and gvfs in /usr/local . For everyone having this problem, see if it still happens after 'sudo mv /usr/local /usr/local.old & sudo mkdir /usr/local'."

---

### Post by GnuSense on 2009-02-28
I wish I could say it worked for me.  Do you have to log out Samson?

---

### Post by RGPerson on 2009-03-01
I lied. Sort of.  I don't know if this is a lingering problem with Nautilus or a new one. 

We can get every place except Network.  I'm still working the kinks out of samba (and stuck doing it) but I used to see my domain listed there even though I couldn't connect past that.  Now I see the familiar 

Nautilus cannot handle network: locations.

And now my computer will also not mount audio CDs.  Data CDs in the same drive don't have a problem.

Grrr.

And oh, but we did get to our trash and got our desktop icons back.  Wish I could remember where I found the solution to that.  It was about something not closing down after logouts.  It was hanging up.  Dang. Sorry.

Gabrielle

---

### Post by rjellinek on 2009-03-20
One solution: If you've installed upgraded (and non-repository) versions of glib (i.e. past 2.16.x) recently, or  a recent non-repository version of gtk+ (which relies on the later versions of glib), go to the source directory that you installed them from and:

```
sudo make uninstall
```


Hope this helps some people.

Robert

---

### Post by Qwertie on 2009-03-22
I have this problem too. I simply restarted my computer one day, after which I couldn't reach any of my Windows partitions (I notice the /mnt folder is empty and /media only contains floppies and cdroms), and Places | Computer gives the error

(empty title bar)
**Couldn't display "computer:".**
Nautilus cannot handle computer: locations.

Is there some expert that can suggest which of the proposed solutions on this thread is likely to work? Does anyone know the cause?

Note: I'm using Ubuntu 8.04.1

---

### Post by cajunlibra on 2009-04-19
I have had the same problem for about 2 weeks now. Running Jaunty from a fresh install, the kernal had an error and was unable to come out of suspend. The error was reported but from that point on, I have been unable to mount any other drives. It worked prior to closing my laptop lid, when I opened it back up, it wouldn't wake up and on restart, I was notified of this seriuos kernel error.

---

### Post by Gforce20 on 2009-04-26
> **Qwertie said:**
> I have this problem too. I simply restarted my computer one day, after which I couldn't reach any of my Windows partitions (I notice the /mnt folder is empty and /media only contains floppies and cdroms), and Places | Computer gives the error

(empty title bar)
**Couldn't display "computer:".**
Nautilus cannot handle computer: locations.

Is there some expert that can suggest which of the proposed solutions on this thread is likely to work? Does anyone know the cause?

Note: I'm using Ubuntu 8.04.1
I'm having the same problem on Ubuntu 9.04. When, if ever, will this be fixed?

---

### Post by cajunlibra on 2009-04-27
I attempted using fschk in the grub prompt but it didnt help.

What commands should I run to troubleshoot this issue?


Thanks

---

### Post by M_Visser on 2009-04-29
GETTING ALL the unofficial updates fixes the problem

---

### Post by kazza765 on 2009-05-01
I'm having the same problem with Jaunty. Can't open computer, network or trash, and can't mount drives.

Has anyone worked out what causes this? I don't want to go through a reinstall just to have it happen again.

---

### Post by cajunlibra on 2009-05-02
could you clarify what you mean by getting ALL unofficial updates?

I have all of the items under "Ubuntu Software" and "UPdates" checked.  This did not fix my issue.

---

### Post by cajunlibra on 2009-06-21
I installed MountManager and it gives the following errors when I launch it in the terminal:

```
4 records in /etc/fstab were detected. 
[G] DBus interface was created
[G] All devices were recieved
[I] Storage device was detected: "/dev/sr0" 
[I] Storage device was detected: "/dev/sr0" 
[I] Storage device was detected: "/dev/sda5" 
[I] Storage device was detected: "/dev/sda4" 
[I] Storage device was detected: "/dev/sda3" 
[I] Storage device was detected: "/dev/sda2" 
[I] Storage device was detected: "/dev/sda1" 
[I] Storage device was detected: "/dev/sda" 
[G] Parsing of  "/usr/share/mountmanager/options/common.xml"  was successful 
[G] Parsing of  "/usr/share/mountmanager/options/ntfs-3g.xml"  was successful 
Segmentation fault

```

---

### Post by cajunlibra on 2009-06-21
Am I missing anything?

My sources list:

```
## UBUNTU REPOSITORIES

# deb http://ppa.launchpad.net/ubuntume.team/ubuntu jaunty main # Ubuntu Muslim Edition
# deb-src http://ppa.launchpad.net/ubuntume.team/ubuntu jaunty main # Ubuntu Muslim Edition
## +++ Backports & Proposed (Ubuntu Unstable) +++
## +++ Source Repositories +++
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu jaunty main

## Canonical Partner Repository
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
## PLF REPOSITORY
## +++ Medibuntu +++
deb http://packages.medibuntu.org/ jaunty free non-free

# deb http://deb.mulx.net/ jaunty main


deb http://streaming.stat.iastate.edu/CRAN//bin/linux/ubuntu jaunty/
deb http://dl.google.com/linux/deb/ stable non-free
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/fta/ubuntu jaunty main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main
deb http://www.estamos.de/download/apt stable main
deb-src http://ppa.launchpad.net/synce/ubuntu jaunty main
deb http://ppa.launchpad.net/phylu/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/phylu/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/synce/ubuntu jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse #Added by software-properties
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

# deb http://download.tuxfamily.org/swiftweasel jaunty multiverse
# deb http://ppa.launchpad.net/frederik-elwert/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/frederik-elwert/ppa/ubuntu jaunty main

```

---

### Post by m0rph3us2009 on 2009-06-27
I had this problem after upgrading from jaunty to karmic, solution was simple...

Updated intltool:

```
sudo apt-get install intltool
```

Then installed gvfs from latest source available from the gnome website:

[ftp://ftp.gnome.org/pub/gnome/sources/gvfs/0.99/](ftp://ftp.gnome.org/pub/gnome/sources/gvfs/0.99/)

I can now access computer, trash, network, and my usb drives now automatically mount again instead of having to mount them manually.

m0rph...

---

### Post by cajunlibra on 2009-06-27
I could not find directions on installing gvfs from source.  I went ahead and reinstalled gvfs and related files via Synaptic. Hopefully this works.

---

### Post by mad.max on 2009-07-30
> **samsom said:**
> I was checking launchpad.net and realised that my problem was not due to an update but because I had installed glib a couple of days ago. So if anyone else has done the same, there is a solution posted there which worked for me. Here goes...hope it works for you as well.



"I just finished helping someone with this issue. It turned out to be caused by an install of glib and gvfs in /usr/local . For everyone having this problem, see if it still happens after 'sudo mv /usr/local /usr/local.old & sudo mkdir /usr/local'."


This fixed the problem completely for me :D, after reboot. I did installed glib, and make an update.

---

### Post by cajunlibra on 2009-07-30
This solved my problem as well, but i had to separate the commands by renaming the directory first and then recreating a new one.  It's a shame it took 4 months to find a solution. I did not wnat to have to go through reinstalling again.

---

### Post by nanao on 2009-08-28
The solution given by **samson **solved mine too.

It also gives back my Ubuntu Human Theme which mysteriously disappeared during the course of the problem.. 

Two of my problems that are being solved:
1. removable device not shown on the desktop and nautilus not opening the location "Computer" 
2. disappearance of ubuntu  "**Human**" theme and unrecognized image file format error while starting up the login screen ("[FONT=Courier New]*Cannot recognize the image file format for file /usr/share/gdm/themes/Human/bottom_bar.svg*[/FONT]")

My problem started shortly after I installed gtk and its dependencies (glib, pango, cairo..etc) locally by compiling from the sources.

Now my headache is gone, my theme is back  and  also I am able to browse my usb drives.[IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG]
 Thanks for the solution.  **mad.max** =>** samson**

---

### Post by andoty_jazz on 2009-09-13
> **phiphi said:**
> What seems to help is:
sudo mv /usr/local /usr/local.old && sudo mkdir /usr/local

Undo would be:
sudo rm -r /usr/local && mv /usr/local.old /usr/local

I found it on Launchpad and it helped someone who asked me for help.

I am so happy having found this workaround. Struggling for days now and you just made this thing work like a charm. Thank you so much.

---

### Post by GnuSense on 2009-09-14
None of these seems to do the trick for me. Maybe I needed to log out and log back in again? I don't see why whacking /usr/local would help.  Seems like there must be a more surgical way to go about it since probably only a subdirectory of /usr/local is involved in nautilus.  I figure sooner or later the developers will sort it out and in the meantime I'll continue to use konqueror.

---

### Post by brianbrian on 2009-09-25
> **nanao said:**
> The solution given by **samson **solved mine too.

It also gives back my Ubuntu Human Theme which mysteriously disappeared during the course of the problem.. 

Two of my problems that are being solved:
1. removable device not shown on the desktop and nautilus not opening the location "Computer" 
2. disappearance of ubuntu  "**Human**" theme and unrecognized image file format error while starting up the login screen ("[FONT=Courier New]*Cannot recognize the image file format for file /usr/share/gdm/themes/Human/bottom_bar.svg*[/FONT]")

My problem started shortly after I installed gtk and its dependencies (glib, pango, cairo..etc) locally by compiling from the sources.

Now my headache is gone, my theme is back  and  also I am able to browse my usb drives.[IMG]http://ubuntuforums.org/images/icons/icon14.gif[/IMG]
 Thanks for the solution.  **mad.max** =>** samson**

I had same problem as Nano after installing gtk and it's dependencies.  
1) Removable drives don't auto mount.
2) Unable to access network drives - smb://
    When I type in an smb address manually into Nautilus it opens the file up in gedit.
3) Error after logging in that .svg image file format can't be recognized.
4) Trash can missing

I complied the latest source for svg, now the machine will recognize svg files.  Damn desktop theme is still messed up, when I am navigating menus the current selection is not highlighted.  If I go into the menu screen with Alt + F  I am unable to see what selection I am on.  

After uninstalling glib-2.22.0 there is improvement.  I can now navigate to network devices over smb & the trash can is there.  The menu thing is still messed up.  Uninstalling glib actually caused problems with too many programs that needed the library so I ended up reinstalling it again from source.

After moving all files from /usr/local into a temp folder, this acutally seems to have resolved everything, now Nautilus is working.  Seriously though, there must be a better way of resolving this then axing /usr/local

---

### Post by cgroza on 2009-09-25
Try with Dolphin...see if it works...

---

### Post by Tootoot222 on 2009-10-03
For all of those that removing /usr/local worked for, I've narrowed it down to these files (all within /usr/local/lib/ ) that cause this problem:

```
libgio-2.0.la           libglib-2.0.so.0.2200.1     libgobject-2.0.so.0
libgio-2.0.so           libgmodule-2.0.la           libgobject-2.0.so.0.2200.1
libgio-2.0.so.0         libgmodule-2.0.so           libgthread-2.0.la
libgio-2.0.so.0.2200.1  libgmodule-2.0.so.0         libgthread-2.0.so
libglib-2.0.la          libgmodule-2.0.so.0.2200.1  libgthread-2.0.so.0
libglib-2.0.so          libgobject-2.0.la           libgthread-2.0.so.0.2200.1
libglib-2.0.so.0        libgobject-2.0.so
```

(I may go through them later and see exactly which ones cause the problem)

I put all of these into another directory (using this command: `sudo mkdir /usr/local/lib.old; sudo mv /usr/local/lib/libg* /usr/local/lib.old/` ), and (after logging out and back in again) I was able to open computer:// , network:// , trash:// (etc) locations once again!

---

### Post by brianbrian on 2009-10-04
Thanks for the info Tootoot222.  Out of the examples you listed the only library I recognize that I had installed was  libglib.  Unfortunately I did delete my backup of /usr/local so I don't know what version I had installed.

-Brian

---

### Post by jp_ceegp on 2009-10-28
Hi there after a lot of search i found this post and reduced the Tootoot222's list in:
:KS
libgio-2.0.la
libgio-2.0.so
libgio-2.0.so.0
libgio-2.0.so.0.2200.1
:KS
I did install libglib, glade and COBO in the same day so i don't know which one installed this.  Anyways everything else is in the same location and NAUTILUS works just fine 

TRASH, COMPUTER, NETWORK... 

U just need move this files away from "/usr/local/lib/" and everything its gonna be okay. 

I've tried use the programs and all of them works as well. I hope it help.

CHEERS!

p.s.  If any of you can explain what "libgio" does ill be gratefull.:razz:

---

### Post by Doctor Drive on 2009-11-05
i've removed what jp_ceegp said - the trash icon appeared and USB drives now mount automatically.
But obex:/// network:/// still don't work. And computer:/// can't load.

I've tried to remove all from Tootoot222's list but nothing changed. So there is something else besides
libgio-2.0.la
libgio-2.0.so
libgio-2.0.so.0
libgio-2.0.so.0.2200.1


and it's not

libglib-2.0.so.0.2200.1     libgobject-2.0.so.0
libgmodule-2.0.la           libgobject-2.0.so.0.2200.1
libgmodule-2.0.so           libgthread-2.0.la
libgmodule-2.0.so.0         libgthread-2.0.so
libglib-2.0.la              libgmodule-2.0.so.0.2200.1
libgthread-2.0.so.0
libglib-2.0.so              libgobject-2.0.la           libgthread-2.0.so.0.2200.1
libglib-2.0.so.0            libgobject-2.0.so


I also tried to remove /usr/local/bin/ folder and whole /usr/local/ and it wouldn't help

---

### Post by 5phinX on 2009-11-10
> **rjellinek said:**
> One solution: If you've installed upgraded (and non-repository) versions of glib (i.e. past 2.16.x) recently, or  a recent non-repository version of gtk+ (which relies on the later versions of glib), go to the source directory that you installed them from and:

```
sudo make uninstall
```


Hope this helps some people.

Robert

I had this problem too, until I read this... This really helped...

Thank you

---

### Post by publicout on 2009-12-11
I'm running openbox and had this problem as well (still do I suppose). However when I start nautilus via dbus-launch "computer:" works just fine.

dbus-launch nautilus --no-desktop

---

### Post by djtarki on 2009-12-14
> **samsom said:**
> 

"I just finished helping someone with this issue. It turned out to be caused by an install of glib and gvfs in /usr/local . For everyone having this problem, see if it still happens after 'sudo mv /usr/local /usr/local.old & sudo mkdir /usr/local'."

It also worked for me. Thanks! ;)

---

### Post by booksnmore4you on 2009-12-30
IN my case with 9.10, I had installed glib to compile audacious. Removing it manually as described on page 3 fixed the problem.

---

### Post by Jeet K. Do on 2010-02-01
Also work for me:

 					Originally Posted by **samsom** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6813120#post6813120") 				
 				[I]I was checking launchpad.net and realised that my problem was not due to an update but because I had installed glib a couple of days ago. So if anyone else has done the same, there is a solution posted there which worked for me. Here goes...hope it works for you as well.



"I just finished helping someone with this issue. It turned out to be caused by an install of glib and gvfs in /usr/local . For everyone having this problem, see if it still happens after 'sudo mv /usr/local /usr/local.old & sudo mkdir /usr/local'."

Thanks
[/I]

---

### Post by LazyEyeFIME on 2010-02-15
> **samsom said:**
> I was checking launchpad.net and realised that my problem was not due to an update but because I had installed glib a couple of days ago. So if anyone else has done the same, there is a solution posted there which worked for me. Here goes...hope it works for you as well.



"I just finished helping someone with this issue. It turned out to be caused by an install of glib and gvfs in /usr/local . For everyone having this problem, see if it still happens after 'sudo mv /usr/local /usr/local.old & sudo mkdir /usr/local'."

:D
This works for my too, but in my case I dent have a /usr/local/ directory, I done this:

lazyeye@lazyeye-desktop:~$ sudo mkdir /usr/local
lazyeye@lazyeye-desktop:~$ sudo mv /usr/local /usr/local.old
lazyeye@lazyeye-desktop:~$ sudo mkdir /usr/local

I am using 64 bit Ubuntu 9.10. Yestarday I was tryíng to install GTK+, GLib, Cairo, ATK, etc just to realize an hour later that my system already has them all.

I am learning how to program Linux applications with C language and GTK+ API

---

### Post by leeds55 on 2010-08-18
I've been struggling with this issue for about a week, insisting on trying the suggested solutions roughly in order of perceived impact/my understanding!  Hence, I have

* tried the 'dbus launcher' approach from a terminal ([http://ubuntuforums.org/showpost.php?p=9068539&postcount=9](http://ubuntuforums.org/showpost.php?p=9068539&postcount=9))
* reinstalled both nautilus & gvfs-backends
* tried to compile gvfs from source (hit a problem with required package dbus-1, which I couldn't install through aptitude)
* installed ubuntu-desktop through apt-get

But it looks like glib was the issue for me:

> **rjellinek said:**
> One solution: If you've installed upgraded (and non-repository) versions of glib (i.e. past 2.16.x) recently, or  a recent non-repository version of gtk+ (which relies on the later versions of glib), go to the source directory that you installed them from and:

```
sudo make uninstall
```

Didn't appear to work, unless I needed a reboot first.  Stupidly, I didn't try again after following this suggestion:

> **samsom said:**
> I was checking launchpad.net and realised that my  problem was not due to an update but because I had installed glib a  couple of days ago. So if anyone else has done the same, there is a  solution posted there which worked for me. Here goes...hope it works for  you as well.

"I just finished helping someone with this issue. It turned out to be  caused by an install of glib and gvfs in /usr/local . For everyone  having this problem, see if it still happens after 'sudo mv /usr/local  /usr/local.old & sudo mkdir /usr/local'."

and went straight for a reboot after the /usr/local 'refresh', so either of the above could have done the job...

---

### Post by Golepa on 2010-08-23
Thank you, phiphi. Your solution worked like a charm. [-o<

This has happened quite a few times before. Back then I did not know what was causing it and I couldn't find a fix for it, so I always ended up reinstalling Ubuntu. Now it happened once again and I was very close to throwing my computer through the window.

Seems like I need to be a little bit more active on these forums. ](*,)

---

### Post by seventhsamurai on 2010-10-28
Thank you [rjellinek]("http://ubuntuforums.org/member.php?u=516373")

glib was indeed the issue for me. With your simple solution of ```
sudo make uninstall
``` everything is back to normal! Thank you!

---

### Post by el_guazu on 2010-11-29
Same here... Problem showed after a glib installation from source...

Doing what samson said, will fix nautilus... 

Thks!

---

### Post by c0rrupt0r on 2010-12-02
I am having this same problem and I did install glib from source but I also went and followed these steps and uninstalled it but that did not solve my problem with Nautilus opening computer folder and so on. I am using Ubuntu Studio 10.10

Any help would be great thank you

---

### Post by c0rrupt0r on 2010-12-04
> **RGPerson said:**
> Well found a partial solution in another thread ([http://ubuntuforums.org/showthread.php?t=644877](http://ubuntuforums.org/showthread.php?t=644877)) by goodling "reinstall Nautilus".  It said to put this command in Terminal: sudo aptitude install ubuntu-desktop.

I did that and said Yes to all the prompts and Nautilus is back!  Mostly.

We can open anything in Places and it shows up just fine.  

What we can't do is see our Trash or add icons to the Desktop.  I could live with the Trash problem if only I knew where the Trash was located in File Browswer so we could browse to it and empty it now and then.  As for the icons, I can add them to the panel so that's a so-so workaround.  They're small there with no text to remind you what they stand for. 

So, major problem resolved.  Minor ones still exist.  Would still like some help if someone could offer it.

Gabrielle

Thank you This did the trick for me on Ubuntu studio 10.10 and fixed everything.

---

### Post by amireldor on 2011-04-27
Had this problem after my system froze (10.10) and i had to 'alt+syn rq+REISUB'.

I followed the suggestions here and removed the libgio-2.0.* files from /usr/local/lib to some backup folder. After logging out and logging in again nautilus was working.

It is to be mentioned that I did some install-from-source of glib and some its friends so it might have installed libgio to /usr/local/lib but I'm not sure what exactly I've done to my system.

Oh well, nautilus works and I can access my USB HD :)

---

### Post by lakitu on 2012-03-05
lousygarua: you saved my system my friend. had forgotten i had installed some glib stuff too i think - maybe that was last time the system was borked - anyway, followed your instructions in post #72 & system was saved. thanks man/woman =) very cool.

---

