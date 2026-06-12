---
title: "Broken Upgrade No GUI"
date: 2009-01-27
forum: General Help
---

### Post by StevoDevo on 2009-01-27
Hi All,

I am in serious **[SIZE="4"][COLOR="Red"]PANIC[/COLOR][/SIZE]** mode. I started out trying to upgrade my Kubuntu 
7.??.? distro to whatever is current 8.04.1 or something isn't it? I used the Adaptec GUI tool and selected the version upgrade button and it dutifuly downloaded all the packages and provided a report of what would be replaced, removed, upgraded and instaled. Well I simply trusted that, as I have never had a problem doing this before.

Choose to install and probably somewhere here I think is a warning to back up my data. Well, what data? I don't store anything mission critical on the partition which contains my root. The /home is on a seperate partition, and theres nowhere to back it upto anyhow, unless I start burning numerous DVDs. I don't want to do that do I? No. Installing a version upgrade shouldn't do anything whatever to my /home partition should it?. 

OOOOooooOOOOPS!! :oops: As fate would have it the install went to about 77 percent of the way through and just froze. Well, I left it go like that for hours, to see if it would regain conciousness. Finally I gave up and shut it down. It gave a warning that the install was incomplete and that the system might be unstable. It also said something about resuming, but there didn't actualy appear to be any button or link to opt for any resumption, however nice that may be. I tried to restart Adaptec to find a resume / repeair option, but it refused to start, It gave a message but I foolishly didn't write it down, as it didn't make much sense (except that it coudn't get some resource and I was unfamiliar with what that was).

Figuring that the system was currently still stable (until I rebooted at least), I choose to make the most of my time. As I had work I needed to do with software on that system. That was two days ago. Tonight I finaly reached a point, where I had a memory freeze up while selecting some text in Knotes and running Firefox. The pointer was still free but wouldn't click or select anything. The keyboard failed to respond (so no usefull interaction here). CTRL+ALT+BKSPCE? Nope! CTRL+ALT+DEL? Nope! Here goes then. Time for a reboot and the cold hard truth.

Ok the bootup seemed fairly normal, I didn't bother to hide the graphical splash screen and read the output, but i made it to the login and the login graphic seemed a little different with a blue fade. Tried to login as usual into a KDE sesion and was told "Could not start up kstartupconfig. Check your installation" DAMN! I hope this isn't serious. 

Well, I tried out a couple of the other Desktop Enviros / Windows Managers to see if I could get my foot in the door. Gnome complains "The files that contain your prefferance settings are currently in use, You might be logged into a session from another computer... You can continue to use the current session... Do you want to continue?".

Well I continue and the next message I get complains that it "couldn't resolve the address..." And it gives a gnome config folder "/home/myaccount/.gconf", which is reffered to in the "file: /etc/gconf/2/path. Could not make the directory /home/myaccount/.gconf; No such file or directory."

OH XXXXXXXX !!!NO!!! That looks like my /home is wiped out.

Closing that dialog restarts the graphical login. 

Found that I could start up the Afterstep WM. Tried using Konquerer and after a few nasty messages about not being able to save files or retreive settings, it actualy starts but the parent window is completely blank except for the menu/tool bar and navigation field they are there but the work space is blank. It complains: Could not find mime type aplication/octet-stream. 

Other apps don't start and I can't get a shell up. The file-open dialog in Konqueror opens and I use the dropdown list to see the defalt navigation points. "Desktop /" "Documents /" and "Home /" but no file system and the all just return "/" into the navigation box and complain "Protocol not supported   file"

I am on the edge of my seat and hoping that the file system and data is all still there, but the GUI can't acces it. Well I get a prompt by loging into one from the login screen and cd /home.
Ok!... "ls"... Nothing there. "sudo mount /dev/sda2 /home"... Ok!
 "ls"... Aaha!! There it is. Thats me right there. /home is where the heart is and I am /home at last. All my data seems to be intact. Now I must change my undies, then try to fix a broken distro. Then I must put a backup system in place. :)

At this point I can't sudo startkde, even though I have my /home mounted, it isn't able to resolve the host. Do I now attempt to apt-get -f dist-upgrade or something else? I don't see any resume option.

Any help apreciated thank you.

PS: I think with no host, I won't have internet will I?

---

### Post by carolinason on 2009-01-27
try 
```
sudo aptitude update && aptitude dist-upgrade
```

---

### Post by StevoDevo on 2009-01-27
I should have said "Adept" when i said "Adeptec". Apart from this, I forgot to mention when trying to restart Adept, I got the mesage that another package manager instance is using the database, but I opened the procces table and couldn't find any like Adept, apt-get or aptitude that would access the package database. Can I shut it down or release it manualy? I have gotten KDE back up, as I found that I could run a konsole terminal in one of the window managers, mount the /home partition and then restart X. Then I could log into KDE. But I still have a fairly broken system I think and I still get the same complaint when I try to start Adept. Just had an idea. I will look up Adept and see if there are any special start up parameters. Again, any advice greatly apreciated. Steve.

---

### Post by StevoDevo on 2009-01-27
Ah! Thankyou carolinason I'll give that a go.

---

### Post by carolinason on 2009-01-27
To get rid of adept processes find them by ```
sudo ps -aux | grep -i adept
``` then  ```
sudo kill *pid*
```

I've ran into adept having to many processes running.

I'm assuming that the update manager changed the repos for the Intrepid install and running aptitude show pull from them.

---

### Post by StevoDevo on 2009-01-27
Sorry but that didn't work. It seems I don't have an internet connection on that machine now. It is unable to resolve my-hostname. FWIW the machine is fed by a simple XP internet sharing setup over ethernet with no router. They are both dual boot. I set up the network and internet in windows and I find that linux detects it without a hitch (usualy) during bootup. I don't have a router and I wanted internet on both machines, so I leave XP running on one, with it's inbuilt internet sharing software and boot Kubuntu on the other. Any other ideas? Thanks again Steve.

---

### Post by StevoDevo on 2009-01-27
Didn't see your last message till just a moment ago. Overlap. I didn't try that but i don't think that will help if no internet see?

Tks.

---

### Post by StevoDevo on 2009-01-27
Umm... sorry but it complained about the syntax for ps sugesting '-' was wrong, it listed a process anyway. I tried to kill it but kill complained it couldn't resolve my host. Tried to open Adapt with the same result. Done the same again with ps aux (rather than -aux). It listed a process again. Then kill - no luck.

Cheers Steve

---

### Post by StevoDevo on 2009-01-27
just checking hardware, cables etc.. and reeboot now.

---

### Post by StevoDevo on 2009-01-27
Could I perhaps boot with a live Ubuntu DVD and use mount and chroot to access the broken install? With the live distro I regain the internet and then perhaps I could use the native system to re-start/fix the install with aptitude?

---

### Post by abn91c on 2009-01-27
if you have a wired broadband connection at the prompt do```
sudo dhclient eth0
``` to activate network

---

### Post by carolinason on 2009-01-27
i've crashed during an upgrade and i was able to recover the upgrade by using aptitude or you could use apt-get. 

aptitude, apt-get, adept and synaptic work similar to each other in that they can update the system.  aptitude and apt-get are command line tools. Adept and synaptic are merely gui front ends for apt-get.

> It is unable to resolve my-hostname.
As far as not being able to resolve a hostname i'm confused. If it's the local machine's (linux box) hostname, then the linux box's localhost is not configured and could explain a lot of problems,

this should give you your hostname. ```
echo $HOSTNAME
``` 


if your linux box can't [COLOR="Blue"]resolve[/COLOR] hostnames then it's either not on the network by not having an ip address, the ethernet device is not up or the dns entries are yorked. as abn91c pointed out you can acquire an ip address that way, but if the device isn't up you will get an error message if you tell it to acquire one.

I would check my tcp/ip setup ```
sudo ifconfig
```
this will list all tcp/ip devices that are running. if you have only one nic, you should see an **lo** and an **eth0** entry. lo should have the ip address of 127.0.0.1 if eth0 has no ip address then use the before mentioned sudo dhclient eth0, if you don't see eth0 then use ```
sudo ifconfig eth0 up
sudo dhclient eth0
```


When I ran Windows internet file sharing, which is routing software, it would sometimes lose the connection to my linux machine and i would have to restart the Windowes Firewall/Internet Connection Sharing (ICS) service. This is much handier than restarting windows.

I would use ping to see if the pc's where talking ethernet.

---

### Post by StevoDevo on 2009-01-28
Thanks abn19c & carolinason, I will try all that.

---

### Post by StevoDevo on 2009-01-28
Incidently in the root directory of the broken system (the ubuntu linux machine), there are three files that I think were put there during the upgrade and they must be start up files as they all start with initrd. There is initrd, initrd.img and initrd.img.old. Can these be replaced in etc, or can .img (that's an image isn't it?) be mounted where they belong, to restore the old (or atleast a working) startup?

And yes carolinason, it is the linux box that isn't able to resolve the hostname.

I will try to fix the network anyhow and run aptitude as above. Thanks again guys! :)

Steve

---

### Post by StevoDevo on 2009-01-28
> **abn91c said:**
> if you have a wired broadband connection at the prompt do```
sudo dhclient eth0
``` to activate network

Ah Hah!! BINGO!! That solves the network problem thanks abn19c. Now I get back to the aptitude update/upgrade stuff...

Now I get: 

lots of Get lines with repository urls (Get:1 - 22)

Then:

"E: dpkg was interupted, you must manualy run 
'dpkg --configure -a' to correct the problem"
"E: Couldn't rebuild package cache"

Just trying that now it seems to be working (returned lots of "setting up..." lines) but it stops at the line Generating Locales... en_AU.UTF.8... 

Come to think of it, I'm prety sure that's where it froze up on the first attempt in Adept. That is obviously my Australian locale file. And to think... the day before yesterday was Australia Day too. ;) 

Any ideas guys? 

Regards Stevo

---

### Post by StevoDevo on 2009-01-28
Now I realise that strewn through out the results from my dpkg command are numerous complaints:

"perl: warning: setting locale failed"
"perl: warning: Please check that your locale settings
               
             LANGUAGE = (unset),
             LC_ALL = (unset),
             LANG = en_AU.UTF-8"

      are supported and installed on your system"
"perl: warning: Falling back to the standard locale ("C")."


I check those environment variables and they are as shown. I assume the first two should probably be set to something. 

Dont tell me Ubuntu is racist against us Aussies... I'ts not about the bloody cricket is it? ;)

---

### Post by StevoDevo on 2009-01-28
> **StevoDevo said:**
> Could I perhaps boot with a live Ubuntu DVD and use mount and chroot to access the broken install? With the live distro I regain the internet and then perhaps I could use the native system to re-start/fix the install with aptitude?
Didn't mention it at the time but I tried this and it failed (forget why). I dropped that aproach to try fixing the internet and working from the broken install. When I got to using dpkg, I had a look at the man page and noticed that it can be told to use a different path as root. I am thinking that I could boot my Ubuntu 8.04 DVD and then I would have no problems with locales, environment variables and other parts of the system that are broken when I try to boot the installed system. Then I could Mount my drives "/" and "/home", then try that "dpkg --configure -a" command again but with the options set to define a new root.

I don't know if i should try this,but I am presently stuck again.

Cheers Stevo.

---

### Post by carolinason on 2009-01-28
I've never had to chroot except for installing Gentoo. 

Aptitude or apt-get has usually repaired my installs. If **dpkg --configure -a** didn't correct the problem I would take the easy road and reinstall from scratch. 

Error messages that fly by the screen I usually just take a note and try and notice if something serious is up. Usually it's meant that I need some package, but it was no big deal to linux. Unless the process prematurely halts, the install succeeded.

---

### Post by StevoDevo on 2009-01-29
Solved.

[Here's the fix.]("http://ubuntuforums.org/showpost.php?p=5495181&postcount=35")

Thanks All. :KS

---

