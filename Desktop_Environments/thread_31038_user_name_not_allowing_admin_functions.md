---
title: "user name not allowing admin functions"
date: 2005-05-01
forum: Desktop Environments
---

### Post by supermal on 2005-05-01
Yesterdauy I set up Kubuntu and it all seemed to be working fine, today I went back in  to do some adjustments, but when I try to do anything  using the control panel, that requires administrator mode it simply asks for my password and then returns to the KDE Control Centre splash screen. 
Has any one seen this problem before, it effectivly means I cant work as root. TIA

---

### Post by Gezzer on 2005-05-01
[QUOTE=supermal]Yesterdauy I set up Kubuntu and it all seemed to be working fine, today I went back in  to do some adjustments, but when I try to do anything  using the control panel, that requires administrator mode it simply asks for my password and then returns to the KDE Control Centre splash screen. 
Has any one seen this problem before, it effectivly means I cant work as root. TIA[/QUOTE]

open the konsole and write

sudo kcontrol
press enter
enter password
press enter

this will open the control center in full admin mode ...

---

### Post by supermal on 2005-05-01
Thanks for that

I'd already tried something similar, but got command slightly wrong, when I follow your suggestion I get the following:

error "/var/tmp/kdecache-supermal" is owned by uid 1000 instead of uid 0
Link points to "/var/tmp/kdecache-root"
error communication problem eith kcontrol it probably crashed
supermal@ubuntu:~$ error  "tmp/ksocket-supermal" is owned by uid 1000 instead of uid 0
link points to /tmp/ksocket-root

These few lines are repeate da couple of more times, and nothing has changed, I'll try to get my head around this tommorrow.

---

### Post by supermal on 2005-05-02
I have just watched the verbose boot up messages. There are a couple of problems that are unimportant and one that states
[COLOR=Red]Error[/COLOR] :Temoporary failure in name resolution.
Thats before I even log in as a user.

If I try to boot in recovery mode it asks for the root password, my understanding is this should be the same as my user password, but using this fails just as it does in the gui.
So how do I fix a name resolution problem without root priviliges???????

---

### Post by supermal on 2005-05-02
Further to my ramblings above I am now even more puzzled.

I was looking around for clues and came upon the package manager kynaptic, it demands the root password and should fail as mentioned above, but it returned an error saying authentiaction had failed and to make sure dcopserver was running. Then it ran the kynaptic program anyway. The other stuff still fails though.
 What is the dcopserevr and how can I check it ?

---

### Post by skateboarding on 2005-05-02
I ran into the same problem when I installed kubuntu. I ended up using kcmshell for all the admin stuff. 
From the prompt do
sudo -s
enter password
run kcmshell --list
to see available options

---

### Post by supermal on 2005-05-02
I'll try that now!
At least I've dug out what dcopserver is and how to check it.

---

### Post by supermal on 2005-05-02
Tried skateboarding's suggestion.

In konsole from my user prompt sudo -s took me directly to a root@ubuntu:~# prompt ( no password was asked for)

From there I did run kcmshell --list and got back      bash: run: command not found.

If I go into control centre now and try to run network settings, when I input my password it takes me to the network settings splash screen , but nothing more.

So basically I cannot set up my networking on the built in laptop card or the aditional  wireless network card and I'm typing this on another computer.

---

### Post by GeneralZod on 2005-05-02
[QUOTE=supermal]Tried skateboarding's suggestion.

From there I did run kcmshell --list and got back      bash: run: command not found.
[/QUOTE]

That should be just 

```

 kcmshell --list 

```

not 

```

run kcmshell --list 

```

Hope that helps,
Simon

Edit:

Also, this is a rather serious bug but apparently there is an acceptable workaround.  Check out this thread here, and the thread linked from that thread in the last post:

[http://ubuntuforums.org/showthread.php?t=30893](http://ubuntuforums.org/showthread.php?t=30893)

---

### Post by supermal on 2005-05-02
OK that worked! 
The first two lines are the error lines mentioned above, these are the source of the real problem.

[U][B]Error: "/var/tmp/kdecache-supermal" is owned by uid 1000 instead of 0.
Link points to "/var/tmp/kdecahe-root"[/B][/U]
then a list of all modules available
 Using this list I have ran kcm_knetworkconfmodule and I can now use the network on the laptop, doubtless I will eventually get the wireless card going as well, cos I had a good signal the other night. 

But how do I sort out the original problem as seen above. Maybe one of the other modules will let me sort out the problem,!!
Further help will be most appreciated.

---

### Post by hammett111 on 2005-05-18
If you check this file "kdecache-supermal" of yours you will find that the user has changed from root (uid 0) to you (uid 1000). I'm in the process of sussing out how to chage that now, cause its my sudoers file thats doing it and I can't access sudo commands. Let you know how I go.

---

### Post by coaxx on 2005-05-18
[QUOTE=supermal]OK that worked! 
The first two lines are the error lines mentioned above, these are the source of the real problem.

[U][B]Error: "/var/tmp/kdecache-supermal" is owned by uid 1000 instead of 0.
Link points to "/var/tmp/kdecahe-root"[/B][/U]
then a list of all modules available
 .[/QUOTE]

Same problem here...

I think it occured after I set ACPI Options in Kontrol Panel (I use german version so maybe names differ a bit...;-) ) I played with the Option "Poweroptions"-Notebook-Akku"-"ACPI Einrichtung"-"Hilfsanwendung einrichten"

This option "set -uid root" with "ACPI-Hilfsanwendung". How to roll back this??? 

Hopefully it helps  to solve this problem, otherwise I have to do a complete reinstall. :( (I have no working network anymore)

[update]
It also works if a reinstall the dcoprss package, as I read in this thread [http://www.ubuntuforums.org/showthread.php?t=21839](http://www.ubuntuforums.org/showthread.php?t=21839)
But I have to do it everytime I boot kubunto...
[update off]

[update 2]

Well I dont think, that is has something to do with the /usr/bin/klaptop_acpi_helper mentioned above, I set back the user-rights with chmod a-s. But it has only an effekt on the ACPI controlpanel, not the rest.

[/update 2]

---

