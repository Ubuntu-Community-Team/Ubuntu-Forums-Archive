---
title: "[ERROR] Steam installing libgl1-mesa-dri:i386, libgl1-mesa-glx:i386 [STEAM]"
date: 2015-07-24
forum: Gaming &amp; Leisure
---

### Post by jesandresval48 on 2015-07-24
Hello guys, i have a problem with steam, since yesterday i have this problem when i want to initialize it, can anyone help me?
> Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
[sudo] password for jex: 
...............................................................................................E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
Press return to continue: 



I appreciate the help.

EDIT1: I tried unistalling steam... this happened:
> jex@VLsPC:~$ sudo apt-get remove steam
[sudo] password for jex: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
jex@VLsPC:~$ 


So apparently, those files are getting in the way, so i tried to delete them.. but when i try to remove them the option is just disabled, so i can't delete them, what do i do?

---

### Post by Julind on 2015-07-24
On the terminal run
<snip>
and navigate to the file and delete it. Then try uninstalling. What happens after that?
(BTW i think there is no space between **_steam_i1  8n_Translation-en** it should be like this **_steam_i18n_Translation-en** thats why its throwing the error.)

You can also use this command. Shorter.
```
sudo rm "/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i1  8n_Translation-en"
```

---

### Post by jso28972 on 2015-07-25
Yeah, I'm getting the same thing. Can't find a way to fix it.

---

### Post by Julind on 2015-07-25
Check out this thread, especially post #3
[http://ubuntuforums.org/showthread.php?t=2234757](http://ubuntuforums.org/showthread.php?t=2234757)

---

### Post by owen9 on 2015-07-25
hello all,

try
sudo rm -r /var/cache/apt /var/lib/apt/lists

if that doesn't work then sorry but it worked for me.   :-)

---

### Post by jesandresval48 on 2015-07-25
Hi, i fixed the problem!
I did this.
> sudo find /var/cache/apt/ -type f -exec rm -v {} \;
sudo find /var/lib/apt/lists -type f -exec rm -v {} \;

And then.
> sudo apt-get update
I got the solution from a page while looking a what to do, those files were being a real pain that didn't let me do anything with the terminal, just those commands worked and fixed my problem. Thanks for answering though!

---

