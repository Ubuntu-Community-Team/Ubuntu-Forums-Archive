---
title: "how can i start Tor"
date: 2006-09-03
forum: Desktop Environments
---

### Post by guest5 on 2006-09-03
this is my second day of actually running Kubuntu.  i have manaaged to get most of the things i need, codex, programs, &c., and with a little help from you people i'v been pointed in nothing but the right direction, however, i cannot seem to get Tor to startup.  

i have gone into 'system settings', 'system services'. and checked the box 'start during boot', but the program remains 'not running'.

what am i doing wrong?\\

g5

---

### Post by guest5 on 2006-09-03
well, scratching head, Tor did start one time, but i cannot get it to start again.  this is wierd.

any suggestions???

---

### Post by Dr. Nick on 2006-09-03
simply run 

tor 

from a command line and make sure its not generating any errors.

---

### Post by guest5 on 2006-09-03
i would just simply start tor from the command line if i knew how, but this is only my 2nd day with linux, and i need help.

there must be some way to have wireless start without having to go in and start it manually when i boot.  this might be causing tor to not initiate on startup too, but i don't know why tor won't start after i am connected, but it won't.

how do i start tor from the command line please?

---

### Post by Dr. Nick on 2006-09-03
just open a Konsole and type

tor

and it should start, or give you a error message telling you why it cant.

---

### Post by peabody on 2006-09-03
> **guest5 said:**
> i would just simply start tor from the command line if i knew how, but this is only my 2nd day with linux, and i need help.

there must be some way to have wireless start without having to go in and start it manually when i boot.  this might be causing tor to not initiate on startup too, but i don't know why tor won't start after i am connected, but it won't.

how do i start tor from the command line please?

You're definitely right.  If your network isn't working tor will try to start and then fail and you'll unfortunately need to start it manually.  What model wireless card do you have?  Is it natively supported or did you need to use ndiswrapper?

---

### Post by guest5 on 2006-09-03
hadmadder@ubuntu:~$ tor
Sep 03 11:26:49.800 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Sep 03 11:26:49.804 [warn] /var/lib/tor is not owned by this UID (1000). You must fix this to proceed.
Sep 03 11:26:49.804 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Sep 03 11:26:49.804 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
hadmadder@ubuntu:~$


I am using a native supported card, linksys wmp54g

both var/lib and var/run are innacessable

---

### Post by peabody on 2006-09-03
> **guest5 said:**
> hadmadder@ubuntu:~$ tor
Sep 03 11:26:49.800 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Sep 03 11:26:49.804 [warn] /var/lib/tor is not owned by this UID (1000). You must fix this to proceed.
Sep 03 11:26:49.804 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Sep 03 11:26:49.804 [err] init_from_config(): Acting on config options left us in a broken state. Dying.
hadmadder@ubuntu:~$


I am using a native supported card, linksys wmp54g

both var/lib and var/run are innacessable

It's because you weren't told to start it as root, sorry about that, try:

```

sudo tor

```

At the terminal.  It's odd that a natively supported card doesn't start at boot.

---

### Post by guest5 on 2006-09-03
hadmadder@ubuntu:/$ sudo tor
Password:
Sep 03 12:15:16.238 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Sep 03 12:15:16.337 [warn] /var/lib/tor is not owned by this UID (0). You must fix this to proceed.
Sep 03 12:15:16.337 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Sep 03 12:15:16.337 [err] init_from_config(): Acting on config options left us in a broken state. Dying.


upon search for tor reveals both var/lib and var/run are 'innaccessable'

i also find this to be the case running kdesu konqueror.

thanx for hanging in here with me

---

### Post by guest5 on 2006-09-03
looking at the log files i find:

Sep 03 09:40:53.463 [warn] You are running Tor version 0.1.0.16, which will not work with this network.
Please use one of 0.1.0.18,0.1.1.23,0.1.2.1-alpha.

well, can i just uninstall the current tor version and get this app at the command line rather than from adept?

thanx again to be sure

---

### Post by Dr. Nick on 2006-09-03
Im using tor 0.1.0.16 which is the latest in the ubuntu repos.

I thought you might get that error, On some installations of tor I have gotten that aswell, I will post the exact commands to fix it in a minute. I can susessfully run tor without using sudo.

---

### Post by Dr. Nick on 2006-09-03
OK this is the command that i ran to fix it

sudo chown *yourusername */var/lib/tor

Try that and then see if tor will start sucessfully without the need for sudo, If it starts right it will not output any text to the konsole.

Their is a howto on here that may help some aswell. 

[http://ubuntuforums.org/showthread.php?t=95527&highlight=howto+tor](http://ubuntuforums.org/showthread.php?t=95527&highlight=howto+tor)

---

### Post by guest5 on 2006-09-03
works like wonderful now.  thank you so much Dr. Nick.  Looks like i have a lot of commands to learn over time.

now if i can just get that wireless to initialize upon boot, but i will live with it till then.  i am truly amazed and believe linux to be coming of age, esp with the advent of vista, you know it's boastful security is such because vista does not permit any non signed drivers at all - spells doom, as even xp will reach it's 8 year standard drop in support soon enough.

---

### Post by Dr. Nick on 2006-09-03
Glad that got it, Do you have a wired ethernet card aswell? I had trouble getting wireless on boot with a wired card. it always went wired first even when thier was no cable plugged in.

---

### Post by guest5 on 2006-09-03
no lan card at all, as i am running an old pc off the neighbor's router in exchange for consulting services - so no conflict there.

I did note that, and this is totally reproducable as i had to do several installs for various reasons:

on install the wireless sees the router but cannot connect till i goto system settings and disable the card, reboot and initialize the wireless:

in fact, this is so reproducable that it is probably a bug.  i tried that based upon wireless issues under xp, and it worked upon each install of both ubuntu and kubuntu alike.

and now - a peerguardian like program hunt...

---

### Post by Dr. Nick on 2006-09-03
[http://forums.phoenixlabs.org/f15-peerguardian-linux.html](http://forums.phoenixlabs.org/f15-peerguardian-linux.html)

been awhile since I messed with it, may work better now though

---

### Post by guest5 on 2006-09-03
Perfect thing to try.  Thanks again Dr Nick for standing in this particular format.

---

### Post by j-strap2 on 2006-09-04
The repository Tor package is obsolete - it is an old, deprecated version of Tor. You should add the repository from the Tor developers to your sources list and install the latest version. Don't run Tor as root, use the correct package where it automatically starts using its own user account.


Instructions:

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian")

---

### Post by guest5 on 2006-09-04
thanks for the responce.  i shall give this a try as well.  looks straight forward enough,

---

### Post by guest5 on 2006-09-04
ok, it's not straightforward enough.

i admit it.  i'm an idiot.

will you tell me exactly what to do.  for ex, i don't know which package to get, the deb or the deb-scr.  

then i don't know if i need to run in the terminal or add this into the repository somehow.

i will learn though.  i will learn.

this is what i did:

hadmadder@ubuntu:~$ [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main
bash: [http://mirror.noreply.org/pub/tor:](http://mirror.noreply.org/pub/tor:) No such file or directory
hadmadder@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
hadmadder@ubuntu:~$

---

### Post by guest5 on 2006-09-04
i got a silly question about updates.  why, if someone has gone to all the trouble to place packages in the package manager, would they not be maintain, such as is the case here with Tor?  I am figuring that this question might be served up to me, seeing as how i am going to install ubuntu on a friends pc this wed and i want to be able to respond correctly.

---

### Post by Dr. Nick on 2006-09-04
> **guest5 said:**
> i got a silly question about updates.  why, if someone has gone to all the trouble to place packages in the package manager, would they not be maintain, such as is the case here with Tor?  I am figuring that this question might be served up to me, seeing as how i am going to install ubuntu on a friends pc this wed and i want to be able to respond correctly.

This question has been tossed around a few times and thier really isnt a good answer to it. sometimes pople submit and then move on to something else and dont maintain what they did. In that case their just has to be a need for the newer version by enough people that someone who knows how to build a package and add it will justify doing it I supose.

---

### Post by Dr. Nick on 2006-09-04
> **guest5 said:**
> ok, it's not straightforward enough.

i admit it.  i'm an idiot.

will you tell me exactly what to do.  for ex, i don't know which package to get, the deb or the deb-scr.  

then i don't know if i need to run in the terminal or add this into the repository somehow.

i will learn though.  i will learn.

this is what i did:

hadmadder@ubuntu:~$ [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main
bash: [http://mirror.noreply.org/pub/tor:](http://mirror.noreply.org/pub/tor:) No such file or directory
hadmadder@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
hadmadder@ubuntu:~$


Add them to the sources.list file. in the link it says add the line to **/etc/apt/sources.list **You most likely only need the deb line, If you are on dapper adding this line to the end of /etc/apt/sources.list should work

```
  deb     http://mirror.noreply.org/pub/tor dapper main
```

then do the sudo apt-get update and sudo apt-get install tor.

I didnt realize that tor was updated, guess I shall try this aswell

---

### Post by Dr. Nick on 2006-09-04
I had to completely uninstall tor since it wouldnt update because of a error message caused by me runnning chown /var/lib/tor

I got the new one installed and it wouldnt work because of ownership erors, I changed owners again and now all I get is 404 in my browser. guess I still need to do a bit to figure it out.

---

### Post by guest5 on 2006-09-04
what a coincidence, the same thing just happened to me, but as i understand it, both lines must be inserted pointing to two (somethings) libraries,

which begs the question, do they also need to be given the permission lines as does the first two lines of code in the file?

---

### Post by guest5 on 2006-09-04
So, for instance, to add universe and multiverse to the Dapper repository for both binary and source packages, change: 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

to: 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe 
 multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe 
 multiverse

to add third party, such as tor, it would be necessary ( wouldn't it ? ) to add 

deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main

deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main restricted universe multiverse
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main restricted universe multiverse


Was the Tor package with universe, or is it with multiverse ? ? or is my thinking just way off base?

---

### Post by peabody on 2006-09-04
> **guest5 said:**
> S
Was the Tor package with universe, or is it with multiverse ? ? or is my thinking just way off base?

I would think universe because I don't believe it has any non-free dependencies.

---

### Post by guest5 on 2006-09-04
i just installed automatix but it doesn't have Tor in the list either.

i was sort of waiting on help because everyone knows more about what not to do waaaay more than i.

accorrding to that page though, only those two lines need be added.  me, i think the maintanence they do is in that file located in /var/lib/tor, which is the list of onion servers, but there may be security updates in other areas...

---

### Post by Dr. Nick on 2006-09-04
you can add the deb-src, but if you dont I dont think it'll hurt at all.

I installed tor from the new repo mentioned earlier and its now the newer version. But when I try and use it as before it doesnt connect.

If i uninstall it and reinstall the old version it works again. It always gives the permission error though until I chown it???

---

### Post by guest5 on 2006-09-04
i don't like running w/o tor.  i can't get it to install following the tor website instructions.  i'm with you Dr Nick, install tor and chown it till someone clues me in on the new updated version...

sure would be nice to see vidalia running under kubuntu - it is very sweet gui

---

### Post by j-strap2 on 2006-09-06
Hmmm, this is a strange problem people are getting with the up-to-date package from the Tor website. I use the Tor website repository and it works fine. I wonder whether something is getting left behind from the deprecated ubuntu version of Tor when it is upgraded.

It might be worth uninstalling the old version of Tor first, checking that all the directories are removed (/var/lib/tor etc.) and then installing the updated version.

Remember also that the Tor website package runs automatically as a service in its own account: you don't need to run Tor manually.

---

### Post by guest5 on 2006-09-06
i thought about that, it's a good point and very logical.  3 files are left, that i know of, after an uninstall.

torcc is one of them too !!, i'm  sure i can just delete them after uninstall - but i didn't do that as i hadn't searched for them at that point - but i thougth i should first ask before deletion - being this is my first go of it w/any linux and all that.


so, let me get this right, installed after entering the lines in the sources.list and everything was golden?

i think i have one additional issue, being new and all, which is that i didn't reasign root permissions after i chown the dir.  still that chown ing takes place somewhere else, because those directories where deleted at uninstall, yet the properties did not seem to return to the root owner.  or it is just me.  i need to know...

thanks again.  tor is good good good.

ps, tor should run automatically even if there is no connection, it will just wait to connect, it won't self terminate.  my firewall, firestarter does the same thing to me, fails to start until i connect wirelessly.  i hope i didn't mess something up ? outpost was my firewall in micro$oft, and it ran when i wasn't connected.  makes me wonder.

---

### Post by Dr. Nick on 2006-09-06
OK, just got mine working correctly. I will post the steps to help hopefully. at this point dont worry about any chown mess.

open a terminal and run

killall tor
sudo killall tor

one of them may say "no process killed" Dont worry about it.

then open synaptic and search for tor, select it and right click and hit "mark for complete removal" That should get rid of the old version if you have it installed, and any leftovers. After a uninstall i no longer had /var/lib/tor

After that just mark it for installation and apply it. I didnt have to do a thing after that. tor started automatically and worked just as prior, just at a new version. With the new version the chown is no longer needed.

I think thats what I did, Ive been messing with it so I may have done something else aswell, but that should work.

---

### Post by guest5 on 2006-09-07
Tor v0.1.0.16 is the version that i got after trying that.  i didn't have to chown it, but do still have to type tor into the console.  The latest stable release is 0.1.1.23.

---

### Post by Dr. Nick on 2006-09-07
you added those lines to your sources.list right? and ran apt-get update or press reload in synaptic? If so you should have gotten the newest.

Open synaptic and search tor, then click it and go to the "package" menu up top and push force version and see if the new version is their.

If not then someting is wrong with the sources.list

With the new version i dont have to start it manually, it starts every boot all by itself

---

### Post by guest5 on 2006-09-08
hello Dr Nick, all,

i figure you're correct about the .list file, and being i want to hook up my micro$oft friends, i thought i'ld start from scratch.  better practice at home first.  to continue, this is what i did and it worked the first time around, a recommended install routine for newbies, imo (from my ubuntu diary):

how to edit a locked file such as sources.list:
 alt+f2, type the command kdesu konqueror

to update tor in the repository add the following two lines to the sources.list file, located at /etc/apt/sources.list

deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) dapper main

install universe repository

install privoxy 
Add the following line to /etc/privoxy/config.
forward-socks4a / localhost:9050 .
comment out logfile and jarfile at the end of sections 1.5, 1.6
edit default to personal preferrence

install firefox and thunderbird and xchm (for .chm micro$oft formats)

install  Easy Ubuntu
wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz)
tar -zxf easyubuntu-3.021.tar.gz
cd easyubuntu
sudo python easyubuntu.in


I want to thank you all for your participation and patience with me, so - thanx goes out to all.

g5

---

### Post by Dr. Nick on 2006-09-10
ill throw this out just incase.

i used to use killall tor then tor to get a new exit node
not that it is a service use these commands instead

sudo /etc/init.d/tor stop
sudo /etc/init.d/tor start

or

sudo /etc/init.d/tor restart

---

### Post by rubengs on 2006-09-12
I made it like this: 

[http://ubuntuforums.org/showthread.php?t=10825&highlight=tor](http://ubuntuforums.org/showthread.php?t=10825&highlight=tor)

---

### Post by Dr. Nick on 2006-09-12
> **rubengs said:**
> I made it like this: 

[http://ubuntuforums.org/showthread.php?t=10825&highlight=tor](http://ubuntuforums.org/showthread.php?t=10825&highlight=tor)


Did you do any modification of your sources.list file? I threw that link out at the begenning of this thread since thats what i initially used. Someone corrected me since that method will install a old tor. Their are instructions in this thread to get the newest ver

---

### Post by rubengs on 2006-09-13
Well, the link points to an old discussion but the instructions apply to dapper and even edgy (I'm running this development version), just follow the guide and you can connect firefox in localhost:8118 or gaim in localhost:9050.

Be sure to enable universe and multiverse in synaptic to have all the necesary source. 

Foxyproxy can help for firefox: 
[https://addons.mozilla.org/firefox/2464/]("https://addons.mozilla.org/firefox/2464/")

---

### Post by Yirimyah on 2006-09-30
Hi. Although I myself am a relative n00b, I have just had the same problem as you with TOR. However, if you are an admin and you check my IP, I am using it. Howto: Go to /var/lib. Rightclick on /tor. In Permissions, set the ownership to your useraccount. 

Please note: You may need to do this as root. To do so, open a terminal and type:

sudo nautilus

Hope this fixes the issue- it did for me!

---

### Post by guest5 on 2006-10-01
Just to let everyone know, 

i've installed using the method I outlined above over a dozen times now on peoples machines with a success rate of 100% -- no errors -- no elevation of privaleges.

I will leave this set to email me in case anyone has any problems with the instructions, in the case I might help.  I am running kubuntu, but this works with ubuntu, just a change of command in order to edit the sources file for ubuntu.

---

