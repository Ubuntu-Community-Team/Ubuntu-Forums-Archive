---
title: "Error ICEauthority prevents login (12.04 LTS Encrypted HomeFolder)"
date: 2014-09-04
forum: Desktop Environments
---

### Post by aka-John99 on 2014-09-04
I am getting an error when attempting to login
>  could not update ICEauthority file/home/{name}/.ICEauthority 
This is leaving me unable to login to the sytem.

I hope someone is able to help with this. I dont want to act too hastilly  and risk losing a few years worth of information. 

Some Backbround info that may help.
[LIST]
[*] An aged  HomePartition
This sytem is rather unstable at the moment, and I am hoping to transfer it to a new Sytem shortly. That is another issue and if necessry I will start a thread about that.
I have not yet attempted that. So I have NOT been deliberatly changing anything or opening Terminals.
I do as of yesterday have another computer available with Ubuntu now  installed on it. 
[*]Encrypted Home partition
It was initially  set up using the option to encrypt.
The /home directory is in a separate partition, but from this account  as an ordinary user I can not access it. 
[*]I do have a Guest account and one other account that I can log into as normal. 
[*]I have found an apparently related solved thread [SIZE=2]
Thread: [Could not update ICEauthority file]("http://ubuntuforums.org/showthread.php?t=2209849")[/SIZE]  
I am rather a novice with Ubuntu and do not want to make mistakes with this. The information in this home folder is very important to me. 
[*]Backups ?
I do have standard backups  using dejadup, or whatever it is called. I have no idea if that helps with file recovery if necessary. I have used that to recover individualfiles,no ideaifit is much use when whole of the account is not accessble. 
[/LIST]

---

### Post by aka-John99 on 2014-09-04
Update.

I still do not know how to correctly fix this error but it seems to be working again at the moment. 

The initial error would not go away even after repeated re-boots. 
I did however try the rescue option, and ran the disk check from that, and maybe another of the options.
After rebooting Ubuntu started up and allowed me to login without an error message.
No idea if blindly using the error console helped or not.

This is no longer urgent but if anyone does know the correct method of dealing with this error I would be interested in a reply.

[HR][/HR]
Something very odd has happened, and wheter this is coincidence or related to the original fault I have no idea.

My .mozilla folder has apparently been replaced with a fresh .mozilla folder for the Canonnical Firefox Aurora  browser.

The pre existing folder has changed location  the original location all new 
```
/home/{name}/.mozilla
```

What did exist there is now moved to the desktop
```
/home/{name}/Desktop/.mozilla
```
At present it is not working as the launcher scripts have the incorrect paths.
Its rather a complicated setup as I have multiple Firefox versions and profiles. I have  Mozilla versions and Palemon in addition to the canonical one. Properties shows 
```
28,012 items, totalling 5.0 GB
```
It looks to be intact and so should work again once the launching scripts are sorted out.

---

### Post by Bashing-om on 2014-09-04
aka-John99; Well, ........


We see this circumstance often as a result of "sudo'n" where one should not:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

For now you might want to investigate that your files in your /home directory are owned by  you:
ANY files in your /home not grouped and owned by "you" should be investigated to see why not !
Look, simply:
```

ls -al 
```

[INDENT][INDENT]just my bit to try and help
[/INDENT][/INDENT]

---

