---
title: "How to update to Firefox 1.0.4?"
date: 2005-05-27
forum: Desktop Environments
---

### Post by joplass on 2005-05-27
How can one update to Firefox 1.0.4 without leaving the old one?  I know there are some issues about the old one lingering in the system and creating havoc.
Thank you,

---

### Post by bored2k on 2005-05-27
Add this two lines to your apt repository [/etc/apt/sources.list]
> deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restricted

```
sudo apt-get update ; sudo apt-get install mozilla-firefox
```

---

### Post by piggyaugu on 2005-05-27
well, you can download the install pack on mozilla's site. and install it.you'll get the 2 version on the same time

btw, i haven't found the 1.0.4 in any repository of apt. you got it??

---

### Post by bored2k on 2005-05-27
[QUOTE=piggyaugu]well, you can download the install pack on mozilla's site. and install it.you'll get the 2 version on the same time

btw, i haven't found the 1.0.4 in any repository of apt. you got it??[/QUOTE]
 It's in the backports. Look at my first post.

---

### Post by Shakie on 2005-05-27
I did exactly what bored2k suggested and it worked fine.

Also though, while looking around the universe synaptic repositories, I found it in there, so you could use synaptic alternativly.

---

### Post by cutOff on 2005-05-27
[QUOTE=bored2k]Add this two lines to your apt repository [/etc/apt/sources.list]


```
sudo apt-get update ; sudo apt-get install mozilla-firefox
```[/QUOTE]
IMHO better to use these not to saturate :wink: 

```
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
```

---

### Post by joplass on 2005-05-27
Ok I upgraded firefox now how can I apply this setting Mike is talking about here so I could add new themes?


------- Additional Comment #3 From Michael R Head 2005-05-14 07:05 UTC [reply] -------

Setting general.useragent.vendorSub to 1.0.4 in about:config seems to let me
access addons.mozilla.org

mike

---

### Post by bored2k on 2005-05-27
[QUOTE=joplass]Ok I upgraded firefox now how can I apply this setting Mike is talking about here so I could add new themes?


------- Additional Comment #3 From Michael R Head 2005-05-14 07:05 UTC [reply] -------

Setting general.useragent.vendorSub to 1.0.4 in about:config seems to let me
access addons.mozilla.org

mike[/QUOTE]
 about:config
general.useragent.vendorSub : 1.0.4

---

### Post by rama on 2005-05-28
Could you clarify the difference between :
1. ubuntu-backports.mirrormax.net
and 
2. backports.ubuntuforums.org/ubp?

---

### Post by NeoChaosX on 2005-05-28
The first is a mirror of the second. The backports people have been encouraging people to use a Backports mirror rather than the main one on UbuntuForums because of the bandwidth usage.

---

### Post by bored2k on 2005-05-28
[QUOTE=rama]Could you clarify the difference between :
1. ubuntu-backports.mirrormax.net
and 
2. backports.ubuntuforums.org/ubp?[/QUOTE]
 They have the same content. Mirrormax is one of the few mirrors that were made to ease server loads. Its advise to use that one.

---

### Post by 23meg on 2005-05-28
here's a question: my distro packed firefox is kind of messed up right now, with some extensions i've installed that i just can't remove (see [this thread](http://www.ubuntuforums.org/showthread.php?t=34254) , and i'd like to see if the official version will be any snappier than the distro packed one on my machine. i'm currently running the backported 1.04; if i install the official package now, will the currently installed extensions appear in it, or do i have a chance to start from scratch? and are there any possible side effects of doing this at all?

---

### Post by bored2k on 2005-05-28
[QUOTE=23meg]here's a question: my distro packed firefox is kind of messed up right now, with some extensions i've installed that i just can't remove (see [this thread](http://www.ubuntuforums.org/showthread.php?t=34254) , and i'd like to see if the official version will be any snappier than the distro packed one on my machine. i'm currently running the backported 1.04; if i install the official package now, will the currently installed extensions appear in it, or do i have a chance to start from scratch? and are there any possible side effects of doing this at all?[/QUOTE]
 They will show. As long as you purge config files. And btw you can just delete extensions and stuff by whipping your user from ~/.mozilla

---

### Post by 23meg on 2005-05-28
i recall that doing that with the warty version, and when (i think) i should have got a dialog to create a new profile, i got a fatal exception error and firefox didn't start, so i've been refraining from deleting the user dir, but alright, i'll try it again.

---

### Post by bored2k on 2005-05-28
[QUOTE=23meg]i recall that doing that with the warty version, and when (i think) i should have got a dialog to create a new profile, i got a fatal exception error and firefox didn't start, so i've been refraining from deleting the user dir, but alright, i'll try it again.[/QUOTE]
 Read the firefox man. There's an option to start firefox with the profile creatr

---

### Post by 23meg on 2005-05-28
right, launched it with the -ProfileManager option and things are fine now, thanks a lot.

---

### Post by graigsmith on 2005-05-28
[QUOTE=23meg]right, launched it with the -ProfileManager option and things are fine now, thanks a lot.[/QUOTE]
 what i did, was download the firefox from mozilla.com. 

and installed it to usr/lib/mozilla-firefox  
it asked me if i wanted to delete the older copy, i said yes.  and it installed, that way every user can have the newest firefox.

---

### Post by bored2k on 2005-05-28
[QUOTE=graigsmith]what i did, was download the firefox from mozilla.com. 

and installed it to usr/lib/mozilla-firefox  
it asked me if i wanted to delete the older copy, i said yes.  and it installed, that way every user can have the newest firefox.[/QUOTE]
 That's mozilla.org ;)

---

### Post by varla on 2005-05-30
i have been following this thread because I want to get firefox 1.0.4 and I have added the two lines in /etc/apt/sources. list
I get an error message when I do sudo apt-get update

Here is the deal (sorry it is a bit long)

Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz)  403 Forbidden
Reading package lists... Done
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by varla on 2005-05-30
[QUOTE=varla]i have been following this thread because I want to get firefox 1.0.4 and I have added the two lines in /etc/apt/sources. list
I get an error message when I do sudo apt-get update

Here is the deal (sorry it is a bit long)

Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz)  403 Forbidden
Reading package lists... Done
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_ubp_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/QUOTE]
 Forgot to ask how can I prevent this?

---

### Post by bored2k on 2005-05-30
[QUOTE=varla]Forgot to ask how can I prevent this?[/QUOTE]
 The backports team has prohibited the use of the main ubuntuforums.org link. YOu need to use mirrors.

[QUOTE=jdong]To make it more clear, accessing backports.ubuntuforums.org will result in a **FORBIDDEN** error.[/QUOTE]

---

### Post by christooss on 2005-05-30
[QUOTE=bored2k]The backports team has prohibited the use of the main ubuntuforums.org link. YOu need to use mirrors.[/QUOTE]
 Why??

---

### Post by cutOff on 2005-05-30
[QUOTE=christooss]Why??[/QUOTE]
[http://ubuntuforums.org/showthread.php?goto=newpost&t=35641](http://ubuntuforums.org/showthread.php?goto=newpost&t=35641)

---

### Post by bhound89 on 2005-06-01
I am using 1.02, and I want to update to 1.04.
my sources.list has the mirrormax links in it, but when I apt-get install mozilla-firefox, it says I have the latest version.  :???: 

help...

---

### Post by christooss on 2005-06-01
[http://www.ubuntuforums.org/showpost.php?p=172105&postcount=30](http://www.ubuntuforums.org/showpost.php?p=172105&postcount=30)

---

### Post by varla on 2005-06-02
[QUOTE=bored2k]The backports team has prohibited the use of the main ubuntuforums.org link. YOu need to use mirrors.[/QUOTE]

Hey thanks for the info, I am going to go and change that.

---

### Post by varla on 2005-06-02
So I went and changed to the mirror site and I still can't access!!
here is the deal:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_dists_main_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_dists_main_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_dists_main_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_dists_main_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_dists_main_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_dists_main_restricted_binary-i386_Packages) - stat (2 No such file or directory)

I know I did something wrong. It is the first time I decide what I write in /etc/apt/sources.list. Usually I always copy what people write in their posts. I think maybe what I wrote in my file is wrong hence the no access or the mirror is already to busy??

here is what I wrote in /etc/apt/sources.list

deb [http://ubuntu-backports.mirrormax.net/dists/hoary-backports](http://ubuntu-backports.mirrormax.net/dists/hoary-backports) main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/dists/hoary-extras](http://ubuntu-backports.mirrormax.net/dists/hoary-extras) main universe multiverse restricted
 

Any inputs??

thanks

---

### Post by ShaneAu on 2005-06-02
[QUOTE=varla]So I went and changed to the mirror site and I still can't access!!
here is the deal:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_dists_main_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_dists_main_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_dists_main_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_dists_main_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_dists_main_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) main/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_dists_main_restricted_binary-i386_Packages) - stat (2 No such file or directory)

I know I did something wrong. It is the first time I decide what I write in /etc/apt/sources.list. Usually I always copy what people write in their posts. I think maybe what I wrote in my file is wrong hence the no access or the mirror is already to busy??

here is what I wrote in /etc/apt/sources.list

deb [http://ubuntu-backports.mirrormax.net/dists/hoary-backports](http://ubuntu-backports.mirrormax.net/dists/hoary-backports) main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/dists/hoary-extras](http://ubuntu-backports.mirrormax.net/dists/hoary-extras) main universe multiverse restricted
 

Any inputs??

thanks[/QUOTE]
 [http://ubuntuforums.org/showpost.php?p=196549&postcount=7](http://ubuntuforums.org/showpost.php?p=196549&postcount=7)

---

### Post by varla on 2005-06-04
[QUOTE=ShaneAu][http://ubuntuforums.org/showpost.php?p=196549&postcount=7](http://ubuntuforums.org/showpost.php?p=196549&postcount=7)[/QUOTE]
 Thanks ShaneAu, 
that resolved my error problem. Now the upgrade gives me a list of packages to be upgraded but certain ones can't be authenticated(is it because it is a mirror site?). Why is there an authentication and also is it ok to install without authentificating?

---

### Post by ShaneAu on 2005-06-04
[QUOTE=varla]Thanks ShaneAu, 
that resolved my error problem. Now the upgrade gives me a list of packages to be upgraded but certain ones can't be authenticated(is it because it is a mirror site?). Why is there an authentication and also is it ok to install without authentificating?[/QUOTE]
 That's fine. Just ignore the authentication warnings. See here:

[http://ubuntuforums.org/showpost.php?p=153996&postcount=6](http://ubuntuforums.org/showpost.php?p=153996&postcount=6)

Ignore jdong's first point... lol. It's out of date.

---

### Post by varla on 2005-06-04
[QUOTE=ShaneAu]That's fine. Just ignore the authentication warnings. See here:

[http://ubuntuforums.org/showpost.php?p=153996&postcount=6](http://ubuntuforums.org/showpost.php?p=153996&postcount=6)

Ignore jdong's first point... lol. It's out of date.[/QUOTE]
 Thanks again 

Cheers!!!

---

