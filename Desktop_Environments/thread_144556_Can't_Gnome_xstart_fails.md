---
title: "Can't Gnome xstart fails"
date: 2006-03-14
forum: Desktop Environments
---

### Post by stabface on 2006-03-14
Hi, 

 I got into work today and used. automatix to update my system. It told me to restart after it was finished so I did.   and when i brings up the Gnome login screen I get this error that says GDM could not write to your authorization file. blah blah get your admin. 

for some reason when i try to login i can also pick GDM_failsafe.Xterm.destop
but i pick gnome and try to login and it give me the error. 

it asks me if i want to set either gnome or GDM_failsafe as default every time i try to login. but it gives me the error and logs me out. i can't even get to failsafe terminal from run level2. 

right now i am in gnome running as root i got here from starting failsafe kernal from grub. it says that maybe my file is full but i df and got this 

[HTML]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb1              3842376   3837372         0 100% /
tmpfs                   388276         0    388276   0% /dev/shm
tmpfs                   388276     12588    375688   4% /lib/modules/2.6.12-10-386/volatile
/dev/hdb3             70769848   9387860  57787044  14% /home
/dev/hda2             20472848    516864  19955984   3% /media/hda2
[/HTML]

not sure what is up i foudn this thread but it didn't help [http://www.ubuntuforums.org/showthread.php?t=98738%22](http://www.ubuntuforums.org/showthread.php?t=98738%22)

---

### Post by stabface on 2006-03-14
I just tried to delete .Iceauthority

not sure that was the way to go but i can't get it back either

---

### Post by stabface on 2006-03-14
for some reason it says my /tmp dir is full looking at the folder in Konqueror the /tmp folder has a red plug on the folder not sure what that means

---

### Post by rjwood on 2006-03-14
it helps to know the proper error message. It will be in your /var/log/ directory.

---

### Post by Ramses de Norre on 2006-03-14
Looks like your / is full..
If you get in root shell you can delete or move some files.
To find out where space is used: ```
du -xm /|sort -rn|less
```

---

### Post by stabface on 2006-03-14
hmmm actually that would make sense because this happened after i installed those new programs

i did what you said and this is what is game me

3689    /
2680    /usr
1343    /usr/lib
1032    /usr/share
773     /var
637     /var/cache
633     /var/cache/apt
620     /var/cache/apt/archives
191     /usr/lib/openoffice2
185     /usr/share/doc
180     /usr/bin
176     /usr/lib/vmware
135     /lib
122     /var/lib
119     /usr/lib/openoffice2/program
101     /usr/share/fonts
96      /usr/share/fonts/truetype
92      /lib/modules
86      /usr/lib/j2re1.5-sun
84      /usr/lib/j2re1.5-sun/lib
83      /usr/share/locale
67      /usr/src
66      /usr/lib/vmware/modules

---

### Post by Ramses de Norre on 2006-03-14
```
sudo apt-cache clean
```
this will empty your apt cache (all the installed .deb's are there with no use)

---

### Post by stabface on 2006-03-14
i just went to system > admin > disks and / is indeed full i feel stupid not seeing this before

---

### Post by stabface on 2006-03-14
hmmm, 
root@punk:~# sudo apt-cache clean
E: Invalid operation clean

---

### Post by Ramses de Norre on 2006-03-14
```
sudo apt-get clean
```
sorry :)

---

### Post by stabface on 2006-03-14
That gave me about 600mb of space now, but what should i do to fix this problem Ubuntu set my partitiosn for me my / is a little under 4 gigs i thought that should be enough

---

### Post by Ramses de Norre on 2006-03-14
Enlarge the partition or move some things to another partition/hard disk..
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")
Take a look at that.

---

### Post by stabface on 2006-03-14
thanks it did the trick i am back in run level 2 and login in under a good user that isn't root.

---

### Post by stabface on 2006-03-14
I have a new problem now though, when i was trying to fix my problem I deleted that file and i think it made it s i don't have access to any of the root features like before with the password when i try update manager i get this error

[HTML]Failed to run users-admin as user root:
 Unable to copy the user's Xauthorization file.[/HTML]

---

### Post by Ramses de Norre on 2006-03-14
```
sudo mv ~/.Xauthority ~/Xauthority.bak
```
Then restart X (ctrl+alt+del).
If it doesn't work: set the moved file back ;)

---

### Post by stabface on 2006-03-14
that did the trick. damn this has been a rough day

---

### Post by stabface on 2006-03-14
i have / and /home as there own paritions , but the / still got full what can I move from / to /home and not get in trouble?

---

### Post by ububaba on 2006-04-09
[QUOTE=Ramses de Norre]```
sudo apt-get clean
```
sorry :)[/QUOTE]

Sorry. Does not work for me. Get a message saying [B][COLOR="Red"][I]E: Invalid operation clean
[/I][/COLOR][/B] Any suggestions on how can one clean up then?

---

### Post by Ramses de Norre on 2006-04-09
sudo apt-get clean works for me and is described in the man pages.. so I'm sure it's the right command.

---

