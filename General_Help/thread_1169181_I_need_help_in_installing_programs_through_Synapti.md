---
title: "I need help in installing programs through Synaptic Pachage Manager"
date: 2009-05-24
forum: General Help
---

### Post by KRDouglas on 2009-05-24
Can anyone help me with correcting the problem I caused when did something wrong while installing WINE?  I followed the directions in _*Unbuntu For Non-Geeks *_and still managed to do something wrong.


Every time I follow the System to Administration to Synoptic Package Manager, I get the same message:


Error Occured
E: Malformed line 52 in source list /etc/apt/sources.list (dist parse)
E: The list of sources cannot be read.
Go to the repository dialog to correct the problem
E:_cache->open () failed, please report


I have had my computer for a week and I need to get this problem resolved so that I can download a few Windows programs.


Thanks,


Kevin

---

### Post by alphacrucis2 on 2009-05-24
> **KRDouglas said:**
> Can anyone help me with correcting the problem I caused when did something wrong while installing WINE?  I followed the directions in _*Unbuntu For Non-Geeks *_and still managed to do something wrong.


Every time I follow the System to Administration to Synoptic Package Manager, I get the same message:


Error Occured
E: Malformed line 52 in source list /etc/apt/sources.list (dist parse)
E: The list of sources cannot be read.
Go to the repository dialog to correct the problem
E:_cache->open () failed, please report


I have had my computer for a week and I need to get this problem resolved so that I can download a few Windows programs.


Thanks,


Kevin

Looks like your sources.list file is somehow corrupted. What happens if you try running System - Administration - Software Sources ?


Edit: Kevin - you should probably open a new thread of your own rather than piggybacking on a thread for a different problem. Just sayin..

---

### Post by balloooza on 2009-05-24
well, first off, wine is not a garunteed way to get a windows problem (I mean program lol) to work.

to install wine type
```
sudo apt-get install wine
```
no need for ubuntu for non geeks!!!!

by the way, be carefull, that tutorial obviously had you editing your sources.list, in some crazy way this could be a security problem, either by your mistake, or editing intentionaly done (verrry unlikly, but still a risk)
I would never edit that file unluess you know exactly what it will do, and exactly what you are doing.
I am concerned because ubuntu allready has the wine package intalled, please tell me what ubuntu non-geek had you do to your /etc/apt/sources.list file, and can you post it here...
```
cat /etc/apt/sources.list
```
and highlight the results, then CTRL SHIFT C (copy, in a terminal, this is because CTRL C, the normal copy command, is a commen key combo)

---

### Post by KRDouglas on 2009-05-24
It looks the problems I'm having is Synaptic program manager is worse than I thought..  When follwed the System-Administration-Software Source the following screen came up:

Canonical Supported open source software (main)
Community-maintained open source software (universal)
Proprietary drivers for devices (restricted)
Software restricted by copyright or legal issues.


I also checked the program/remove function and the following came up:

'This is a major failure of your software management system.  Please check for broken package synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with sudo apt-getupdate' and sudo apt-get install f'

Could someone also give the instructions on where I need to go to enter the new commands.  I am new to computers and I could use every little bit of help.

Thanks,

Kevin

---

### Post by ububaba on 2009-05-24
> **philcamlin said:**
> hi im in ubuntu 9.04 and everytime i go to install something  i get 
- dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

how do i fix this i have no idea what it mwans im a beginner so help ? :)

even sudo apt-get update gives me this

Exactly the same problem here. When I feed the above command 
in the terminal it says "Parse error /var/dpkg/updates/0037 near
line 1 new line in field name '#padding'.

The window/page that opens next has #padding in a column on the 
left repeated probably 37 times. 

Can't make head or tail of this.

---

### Post by oldos2er on 2009-05-24
Please copy and paste the output of
```
cat /etc/apt/sources.list
```

---

### Post by ububaba on 2009-05-26
> **oldos2er said:**
> Please copy and paste the output of
```
cat /etc/apt/sources.list
```
Could not follow your request as I was unable to access that file.
Reason being my inability to log in. I am using another OS.

---

### Post by oldos2er on 2009-05-26
> **KRDouglas said:**
> Can anyone help me with correcting the problem I caused when did something wrong while installing WINE?  I followed the directions in _*Unbuntu For Non-Geeks *_and still managed to do something wrong.


Every time I follow the System to Administration to Synoptic Package Manager, I get the same message:


Error Occured
E: Malformed line 52 in source list /etc/apt/sources.list (dist parse)
E: The list of sources cannot be read.
Go to the repository dialog to correct the problem
E:_cache->open () failed, please report
  

 In a terminal, run
```
gksu gedit /etc/apt/sources.list
```
 Click the 'search' menu, 'go to line', type in 52. Add a comment mark # in front of the line. Save and exit the file. Then in a terminal, run
```
sudo apt-get update
```
 If you have any further problems with this, please post back and copy and paste any errors you see.

---

