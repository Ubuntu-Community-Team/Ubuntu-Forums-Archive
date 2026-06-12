---
title: "[SOLVED] Update Manager Problem"
date: 2008-12-25
forum: General Help
---

### Post by greenco on 2008-12-25
I recently purchased a XPS M1530 laptop from DELL, with Ububtu 8.04 installed. When I run the Update Manager I keep getting a message that tells me that " Not all updates can be installed " and suggests that I run a "Partial Upgrade", to install as many updates as possible. It also shows a list of several things that could cause the problem.

Is there anyway to find out what the problem/s is? I suspect that it is becaused DELL installed their version of Ubuntu 8.04. Any help will be greatly appreciated.

---

### Post by balaknair on 2008-12-25
Hello.
We'll need to know what error message you're seeing to be able to help you.
In the meantime I can only guess what the cause is.

Most likely cause: Broken packages.
Are you getting an error message that mentions 'broken packages'?

If yes, try this-

Open Synaptics package manager(System menu> Administration> Synaptic).

If you get an error and can't open it, open a terminal window(Applications menu> Accessories> Terminal) and type in
```
sudo dpkg --configure -a
```

Now try to open synaptic again.

Once it opens, in the left-hand pane, select 'Custom Filters' from the list at the bottom of the pane. Then select 'Broken Packages'. The right hand pane should now list any broken packages.

Now to fix the broken packages, Synaptic toolbar> Edit> Fix Broken packages

If this doesn't fix the errors, post the contents of the error message here and we'll try to help you out.

---

### Post by greenco on 2008-12-25
My Synaptic works great. I only get the error message when using the update manager. I used your suggestion to find any broken packages and there are none listed.

Here is a link to a screenshot about the message:

[http://www.home.comcast.net/~flt-simmer/Message.jpg]("http://www.home.comcast.net/%7Eflt-simmer/Message.jpg")

I hope it helps!

Edit:

When I click on the button to run the partial update, I end up with this message:

[http://home.comcast.net/~flt-simmer/Package.jpg]("http://home.comcast.net/%7Eflt-simmer/Package.jpg")

When I look this module up in the Synaptic Package Manager it is listed as being installed. If I elect to remove it it also wants to remove several Ubuntu Generic Packages. It scared me off until I learn more of what it is telling me.

---

### Post by balaknair on 2008-12-25
OK

You can do the updates through with this command in terminal

sudo apt-get install -f

After all possible updates are installed, check if any packages are left 'un-updated'.

If a previous aborted update resulted in corrupted files being saved in the cache, removing those packages from cache will fix the issue.
Hit alt-F2--> type in *gksudo nautilus /var/cache/apt/archives*===> This opens a file browser window with root privileges in the folder where the apt installer stores packages---> find the packages which could not be updated/installed and delete them. Now try running Update manager again.

Note: This does not uninstall any packages, it merely removes any files which may be uninstallable or corrupted upon download.

---

### Post by greenco on 2008-12-25
Look at reply #3 for the added link and info!


I ran the terminal command to install the updates and after it finished this is what it printed:

coleman@dell-desktop:~$ sudo apt-get install -f
[sudo] password for coleman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 139 not upgraded.
coleman@dell-desktop:~$ 
0
When I looked at the cache folder, it has over 900 items in it. What do I need to look for to determine which ones that did not update? There is a folder name " Partial " in the cache folder, but it is empty.

---

### Post by balaknair on 2008-12-25
Did you do 

sudo dpkg --configure -a

before

sudo apt-get install -f  


You can safely delete all the files in the cache/archives
(or simply do *sudo apt-get clean* in a terminal). The only issue you'd have is that if you had to reinstall any apps you have already installed, at a later date, you would have to download them again from the repositories or from the DVD. Not an issue if you have a reasonably fast internet connection.

These steps ought to clear up issues caused by the first two reasons given in the screenshot you've posted. Reasons 3 and 4, I'm not so sure.

PS: can you install any new apps?

---

### Post by balaknair on 2008-12-25
Don't uninstall it, just delete the file named

linux-ubuntu-modules-2.6.24-22-generic.deb in the /var/cache/apt/archives folder.

Now in System menu> Administration> Software sorces---> set the 'Download from' as 'Main Server'.
Now try updating again.


For some reason, the Update manager cannot authenticate this file and refuses to install it(maybe it was corrupted on download?).

You can also manually download the file from the Ubuntu archives, and paste it into the /var/cache/apt/archives folder yourself.

[http://packages.ubuntu.com/hardy-updates/amd64/linux-ubuntu-modules-2.6.24-22-generic/download](http://packages.ubuntu.com/hardy-updates/amd64/linux-ubuntu-modules-2.6.24-22-generic/download)

You'll need to use gksudo nautilus for all this. After copying the manually downloaded file into the folder, type in a terminal
sudo apt-get update
sudo apt-get upgrade

to try updating again.

---

### Post by greenco on 2008-12-25
No, I did not run      sudo dpkg --configure -a    first. Here is the result of running it first.

coleman@dell-desktop:~$ sudo dpkg --configure -a
[sudo] password for coleman: 
coleman@dell-desktop:~$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 139 not upgraded.
coleman@dell-desktop:~$

Yes I can install new packages.

I don't want to delete the archives and have to install them again. I have fought too many battles, getting some of them installed! Most of the items in the archive folder are " DEB " files. It will be easier to live with the error message than installing the modules again.

Thanks for your help.

---

### Post by balaknair on 2008-12-25
Try what I've suggested in Post # 7--> don't clear the cache, now that you know which package is causing the trouble, just delete that one package- **linux-ubuntu-modules-2.6.24-22-generic.deb**- apt will download it again from the server, or you can manually download it from packages.ubuntu.com using the link given.
As long as it is in the cache, apt will not try a fresh download.

---

### Post by greenco on 2008-12-25
**Problem is still with me!  When I thought it was fixed, I was using my PC and not my laptop**.

Thanks balaknair!!
That seems to have corrected the problem. Here is the result of your suggestion:

coleman@coleman-desktop:~$ sudo dpkg --configure -a
[sudo] password for coleman: 
coleman@coleman-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
coleman@coleman-desktop:~$ 

I ran the update manager and I did not get the error screen!!

Thanks for your help

---

### Post by balaknair on 2008-12-25
Excellent.
Glad to have been able to help.

Happy holidays. :D

PS: could you mark the thread as solved(at the top of the page- Thread tools> solved)
Thanks.

---

### Post by greenco on 2008-12-26
I must have been tired last night when I said that the problem was solved. When I got home last night and checked the forum, to see if I had anymore help, I was using my PC and not my laptop.

I just ran the suggestions and they DID NOT fix the problem. Here is the results of the commands:

coleman@dell-desktop:~$ sudo dpkg --configure -a
[sudo] password for coleman: 
coleman@dell-desktop:~$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 139 not upgraded.
coleman@dell-desktop:~$ 

I have some programs installed, that was not added with "Synaptic", and I had rather not go through that process again. I usually end up having to reinstall Ubuntu, to fix my mistakes. It will be easier for me to ignore the error, than it will to reinstall all of my packages again. 
Thanks

---

### Post by balaknair on 2008-12-26
Sorry to hear that.

Could you try what I've suggested in post # 7 and then run update manager.
I think that will fix this issue.

Wishing you luck

---

### Post by greenco on 2008-12-26
I deleted the only Linux DEB folder, that was there. I downloaded "  linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb  " and put it in the folder. The problem is still there!

Next question: **Where did the deleted deb folder go**? It is not in the trash basket. Do I have more than one "Trash Baskets"?

Here is the results of the terminal commands

coleman@dell-desktop:~$ sudo apt-get update
[sudo] password for coleman: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                       
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Fetched 2B in 1s (2B/s)  
Reading package lists... Done
coleman@dell-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils f-spot language-support-writing-en libbind9-30
  libisccc30 libisccfg30 linux-backports-modules-hardy
  linux-backports-modules-hardy-generic linux-headers-generic
  linux-image-generic openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-filter-binfilter openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-br openoffice.org-help-cs
  openoffice.org-help-da openoffice.org-help-de openoffice.org-help-dz
  openoffice.org-help-en-gb openoffice.org-help-en-us openoffice.org-help-es
  openoffice.org-help-et openoffice.org-help-eu openoffice.org-help-fr
  openoffice.org-help-gl openoffice.org-help-hi-in openoffice.org-help-hu
  openoffice.org-help-it openoffice.org-help-ja openoffice.org-help-km
  openoffice.org-help-ko openoffice.org-help-nl openoffice.org-help-pl
  openoffice.org-help-pt openoffice.org-help-pt-br openoffice.org-help-ru
  openoffice.org-help-sl openoffice.org-help-sv openoffice.org-help-zh-cn
  openoffice.org-help-zh-tw openoffice.org-impress openoffice.org-l10n-af
  openoffice.org-l10n-ar openoffice.org-l10n-as-in openoffice.org-l10n-be-by
  openoffice.org-l10n-bg openoffice.org-l10n-bn openoffice.org-l10n-br
  openoffice.org-l10n-bs openoffice.org-l10n-ca openoffice.org-l10n-cs
  openoffice.org-l10n-cy openoffice.org-l10n-da openoffice.org-l10n-de
  openoffice.org-l10n-dz openoffice.org-l10n-el openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-l10n-eo openoffice.org-l10n-es
  openoffice.org-l10n-et openoffice.org-l10n-eu openoffice.org-l10n-fa
  openoffice.org-l10n-fi openoffice.org-l10n-fr openoffice.org-l10n-ga
  openoffice.org-l10n-gl openoffice.org-l10n-gu-in openoffice.org-l10n-he
  openoffice.org-l10n-hi-in openoffice.org-l10n-hr openoffice.org-l10n-hu
  openoffice.org-l10n-it openoffice.org-l10n-ja openoffice.org-l10n-ka
  openoffice.org-l10n-km openoffice.org-l10n-kn openoffice.org-l10n-ko
  openoffice.org-l10n-ku openoffice.org-l10n-lo openoffice.org-l10n-lt
  openoffice.org-l10n-lv openoffice.org-l10n-mk openoffice.org-l10n-ml-in
  openoffice.org-l10n-nb openoffice.org-l10n-ne openoffice.org-l10n-nl
  openoffice.org-l10n-nn openoffice.org-l10n-nr openoffice.org-l10n-ns
  openoffice.org-l10n-or-in openoffice.org-l10n-pa-in openoffice.org-l10n-pl
  openoffice.org-l10n-pt openoffice.org-l10n-pt-br openoffice.org-l10n-ro
  openoffice.org-l10n-ru openoffice.org-l10n-rw openoffice.org-l10n-sk
  openoffice.org-l10n-sl openoffice.org-l10n-sr openoffice.org-l10n-ss
  openoffice.org-l10n-st openoffice.org-l10n-sv openoffice.org-l10n-sw
  openoffice.org-l10n-ta-in openoffice.org-l10n-te-in openoffice.org-l10n-tg
  openoffice.org-l10n-th openoffice.org-l10n-ti-er openoffice.org-l10n-tn
  openoffice.org-l10n-tr openoffice.org-l10n-ts openoffice.org-l10n-uk
  openoffice.org-l10n-ur-in openoffice.org-l10n-uz openoffice.org-l10n-ve
  openoffice.org-l10n-vi openoffice.org-l10n-xh openoffice.org-l10n-zh-cn
  openoffice.org-l10n-zh-tw openoffice.org-l10n-zu openoffice.org-math
  openoffice.org-officebean openoffice.org-style-human openoffice.org-voikko
  openoffice.org-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 139 not upgraded.
coleman@dell-desktop:~$ 

Nothing has changed and I still get the message!

---

### Post by balaknair on 2008-12-26
I've just been hunting through Launchpad for related bug reports.

This might be relevant-

[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/51048](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/51048)

This is what worked here.
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by balaknair on 2008-12-26
Another possibility is it could be a broken package on the repositories(in which case it'll get resolved within a day or two when the repos are updated).

If nothing seems to work, perhaps you should file a bug on [launchpad]("https://launchpad.net/")

Include the nature of the error, and also the output of sudo apt-get update and upgrade

---

### Post by zika on 2008-12-26
Sorry if I am writing something that was already written or done:

open Synaptic
click on Reload
click on Mark all upgrades
click on Apply
answer 'Yes' to question about unautentificated packages (You are using launchpad's openoffice packages ... which are not autentificated ...)

What bothers me is the fact that unautentificated is kernel ... so beware and do not take my advice for granted.

It is essential to do this through Synaptic, not the other way ...

---

### Post by balaknair on 2008-12-26
> **zika said:**
> 
What bothers me is the fact that unautentificated is kernel ... so beware and do not take my advice for granted.


Yep, that's exactly the trouble. The kernel modules package is what doesn't feel right.

@greenco
But Zika's comment also made me think of something else. 

1) You did say you modified quite a bit of stuff and did some installs outside of Synaptic, and that makes me wonder if the kernel has been patched, or is a custom kernel(not the generic kernel).

Type uname -r in a terminal to get the kernel version. and see if it's 2.6.24-x-generic

2) As Zika pointed out you have ppa.launchpad repos. Dell uses the launchpad ppa-s to host its modified packages. It could be any of those as well(as you mentioned earlier). The file name would however reflect that however(like linux-headers-lum-2.6.24-22-386_2.6.24-22.35Dell1_i386.deb)

I'm not sure if that could cause this sort of error.

I'd personally try something like editing sources.list, but given that you've put in a lot of custom installs and don't want to lose that, in your case I suggest that you try launchpad, since the folks hanging out there will have a much better idea, and if it's a new bug, it'll be brought to the developers' and package maintainers' attention so they can roll out a fix.

PS: just wanted to clarify- clearing the apt cache will not affect the installed programs, and especially not those installed by means other than synaptic. It's just the place where synaptic stores all the files downloaded from the repositories, sort of like a folder full of setup.exe files. And only the files for packages installed via Synaptic will be stored there.

---

### Post by greenco on 2008-12-26
Thanks zika!!!!

That did the trick. The warnings scared me and I am not afraid of anything, but I let it do the changes.

Thanks a million to both of you

---

### Post by zika on 2008-12-26
> **greenco said:**
> Thanks zika!!!!

That did the trick. The warnings scared me and I am not afraid of anything, but I let it do the changes.

Thanks a million to both of you

Not at all. You can click on Thanks button bellow my message ... ;)

I'm glad my 2 cents could be of value to somebody.

---

### Post by greenco on 2008-12-26
Thanks zika, your suggestion did the trick. All of those warnings scared me and I am not afraid of anything. I got brave and let it do the updates and now the error message is gone, when I run the Update Manager.

Thanks a million to both of you for helping me get this fixed!!!!

---

### Post by balaknair on 2008-12-26
Great to know you got it fixed.
:D

---

### Post by Amiduffer on 2008-12-27
Thank you very much for this thread. Update Manager had problems due to a power outage when updating and many problems subsequently such as the web browser no longer working. After doing what balaknair suggested back at the start of the thread, it was fixed.

---

