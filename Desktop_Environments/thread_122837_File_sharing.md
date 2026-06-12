---
title: "File sharing"
date: 2006-01-28
forum: Desktop Environments
---

### Post by seakiwi on 2006-01-28
I need some basic help with how to set up file sharing on my home network.  My host machine is running XP Home and is on dial up (always on), connected to my Kubuntu machine via a switch, and also to my other XP Home machine.  Host machine using ICS to get the other two online. All is working well. 

The only thing I haven't been able to figure out yet is how to "see" my Windows Workgroup from my machine, and how to set up file sharing between the three machines.

I suspect Samba is what I should be using for this, but I checked out the online help guide and it was WAY over my non-geek head! 

Is there a simpler way for me to do this, or failing that how can I set up ftp between the machines? I have next to no knowledge on ftp either. I pretty much only need the ability to send files to the workgroup machines, and have them be able to send files to me. We dont need access to each other's drives and really don't even need access to shared folders - just a way to shoot a file across quickly.

If anyone can walk me through this I'd appreciate it. 

TIA!  :)

---

### Post by christhemonkey on 2006-01-28
I have the same problem!
IMHO, Samba is what i think we should be using, but i dont know.

---

### Post by Neeko on 2006-01-28
Yes, Samba will allow you to connect to your Windows shares from Kubuntu.

In Konqueror (3.4.3) there is a 'Starting Point' called 'Network folders'. A wizard will assist you in adding Windows shares or connecting to an ftp server.

Firstly though, have you made sure all your pcs are on the same IP network? Can you ping your Kubuntu box from both your Windows boxes?

---

### Post by christhemonkey on 2006-01-28
I can ping both my pcs
But i am not using Kubuntu and i cant see this wizard.

---

### Post by Neeko on 2006-01-28
If you're not using Kubuntu - or a similar KDE desktop - then that wont work. 

Samba sounds tricky to configure buts its not really, it has a web interface which makes things a bit easier. 

When installed you can connect to samba to configure it, from a web browser like Firefox, by entering: 127.0.0.1:901 or localhost:901 or your-pcs-ip-address:901 in the address bar.

---

### Post by christhemonkey on 2006-01-28
cheers will let you know as soon as i find my laptop....:s

---

### Post by cmongini on 2006-01-28
i have the same problem (only 2 computers the ubuntu and a windows). samba is installed on the ubuntu, the computers can ping each other, share an internet connection, but i couldn´t open the adresses you suggested with the browser.....

[QUOTE=Neeko]When installed you can connect to samba to configure it, from a web browser like Firefox, by entering: 127.0.0.1:901 or localhost:901 or your-pcs-ip-address:901 in the address bar.[/QUOTE]

the answer was: no response from the server in all the three cases
what could it be?thanks!

---

### Post by Jason_25 on 2006-01-28
That's because you don't have swat installed.  It's the web interface for configuring samba.  Just an FYI, network browsing may not work correctly since you are using microsoft ICS.  But you should still be able to connect to your windows computer's shares with the address like this
//(machine name)/ . Sorry I don't know the graphical way to do this from KDE but at the command line you can always type
smbclient //(machine name)/(share name) and then the share password (blank if none).

If you want windows computers to see your shares, then you need to configure samba.  A little involved but works great when your done.  I recommend using webmin for that.  You can find it in the repos along with the samba plugin for it.

---

### Post by seakiwi on 2006-01-28
[QUOTE=Jason_25]That's because you don't have swat installed.  It's the web interface for configuring samba.  Just an FYI, network browsing may not work correctly since you are using microsoft ICS.  But you should still be able to connect to your windows computer's shares with the address like this
//(machine name)/ . Sorry I don't know the graphical way to do this from KDE but at the command line you can always type
smbclient //(machine name)/(share name) and then the share password (blank if none).

If you want windows computers to see your shares, then you need to configure samba.  A little involved but works great when your done.  I recommend using webmin for that.  You can find it in the repos along with the samba plugin for it.[/QUOTE]

OK, I think this is what I need to set up but I have no clue how to do this. As I said before I did read through the samba manual on the samba site but it went right over my head. I also checked out webmin - I admit I didn't spend too much time reading up on that, but I'm not sure I understand how that works either.

If you have the time and can be bothered helping out an idiot, would you mind giving me a few step by step instructions for how to set samba up? I assume the Windows machines also need samba installed - would it be installed by default or would I have to go hunt it down for those machines?

I'm learning heaps but at this point I'm totally clueless about the networking side of things.

Thanks for your help!

---

### Post by Jason_25 on 2006-01-28
Samba is "long" for SMB.  Short message block.  It's the file sharing protocol used by        windows.  So of course your windows computers need nothing extra.  Do you require that the windows computers access your ubuntu computer or do you just need the opposite?  You can just use what I posted earlier to connect from ubuntu to windows.  

If you need help on setting up samba to share your ubuntu computer, I can post my smb.conf that is set up for anonymous (no password) file sharing between the computers on my network.  But be prepared for a little head beating if you decide to go this route.

---

### Post by seakiwi on 2006-01-28
OK, all I really need to be able to do is shoot files from one machine to the other occasionally, but I'd need the ability to do it in both directions ie: send files **to **the Windows machines and receive files **from** them. Up until now we haven't even needed this as we've been able to do it via Gaim/ICQ. I'm using Gaim and the Windows machines use ICQ - which all worked perfectly until recently. For some unknown reason file transfers **from **the Windows machines now no longer work using that system. I can still send files to them via Gaim. No idea what that's about unless there's been some kind of protocol change with ICQ or something.

So, to summarise - we don't need access to each other's files or drives. We just need a way to send/receive files.

Sounds like Samba is what I need. I haven't touched anything in the Samba setup so far so I have no idea what's involved with that. Anonymous sharing sounds fine - we have no need for passwords.

If you could post your smb.conf that might help ... many thanks!

---

### Post by Jason_25 on 2006-01-28
Here is my file.  Use at your own risk.  It allows no-login anonymous read/write access to the directory in the path.

---

### Post by christhemonkey on 2006-01-29
Have typed that in..now what?

---

### Post by Jason_25 on 2006-01-29
So that file is now in your /etc/samba folder named as smb.conf?

If so

sudo /etc/init.d/samba restart

That will reload the changes.  Make sure you have removed the .txt extension and edited the path in the file to the directory you want to share beforehand.

---

### Post by stig on 2006-01-29
Hi,
I am a newbie, using Ubuntu rather than Kubuntu, and have Ubuntu and Windows computers. I tried to figure out Samba but never got it to work. Then I tried Nautilus Share

[http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil](http://gentoo.ovibes.net/nautilus-share/mediawiki-1.4.4/index.php/Accueil)

and that was very, very easy to set up (even though I know little about computers). I can now view files between the computers regrdless of whether they are Ubuntu or Windows.

What I haven't yet been able to do is to find out how to transfer files from one computer to another. The computers won't let me do this so I guess something has to be done with permissions.

I don't know if you can use Nautilus with Kubuntu or whther there is a Kubuntu equivalent to Nautilus Share.

Good luck with your network!

---

### Post by ubuntujonez on 2006-01-29
i just installed samba from the Ubuntu desktop, with System->Administration->Shared Folders

I tweaked some samba settings in /etc/samba/smb.conf, minor changes like mount read-write and some things that might have already been defaults. The goal was to have it set up like I had it set up before under Fedora Core, but since about 2 years went by, I forgot how to get samba to work. 

Anyway, I was lost in PAM for a while, but the trick to be able to connect to ubuntu smbd with my windows username password (same on both systems) was to:

bash$ sudo smbpasswd -e <username>

and set the password to my unix password.

Now I can copy files from windows (xp) by opening an explorer window typing \\ubuntu-server 

I'm not sure if setting bind/named (not very easy for beginners)up makes it easier or not... 
*time lapse*
\\ipaddress
(\\192.168.1.200)
works too. I'm pretty sure samba (smbd/nmbd) will advertize the name of your server.

Anyway, good luck to you all and I hope this helps. If usernames and passwords are the same across systems you can have "authenticated" read-write filesharing without having to login to samba from windows.

---

### Post by hamil on 2006-01-29
[QUOTE=Jason_25]So that file is now in your /etc/samba folder named as smb.conf?

If so

sudo /etc/init.d/samba restart

That will reload the changes.  Make sure you have removed the .txt extension and edited the path in the file to the directory you want to share beforehand.[/QUOTE]

Hello, bumping into this thread...

I have tried setting up samba, and I have tried with the GUI Swat, but not beeing able to share files between my computers.
Found this thread, and used a modified version of the smb.conf file from this thread.

When I issue the command to restart sambe, I get this output:
```
lasse@njord:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons...                                             [ ok ]
 * Starting Samba daemons..                                              [fail]

```

Anyone have any idea to why??

Brgds

---

### Post by christhemonkey on 2006-01-29
Neither PC can ping each other?
I can see my ubuntu machine in its network dialog, but no others.
When i try going onto mshome workgroup, it says that it cant display the contents of the folder (and the same on my XP machine!)

---

### Post by Jason_25 on 2006-01-29
Network browsing is a tricky thing.

Type 

\\(name of ubuntu computer)

To directly connect to it from a windows computer.

---

### Post by christhemonkey on 2006-01-29
Says
Windows cannot find \\ubuntu

---

### Post by Neeko on 2006-01-29
[QUOTE=christhemonkey]Says
Windows cannot find \\ubuntu[/QUOTE]
Use the ip address of the ubuntu box rather than its hostname, or if you know how you can put an entry in the hosts file on each windows pc. If you know the share name of the folder on the ubuntu box then you can include that too - and map a drive letter to it. 

For example, if your ubuntu box is 192.168.1.10 and the folder is shared as ubuntustuff then in Windows you could enter this is the address bar: 
\\192.168.1.10\ubuntustuff though you would probably want to map a drive so next time the pc is started up the drive will be available.

---

### Post by christhemonkey on 2006-02-01
Ok, now i can see and put stuff onto my ubuntu box from windows :D
How about the other way round? can i put stuff on windows from linux?

---

### Post by anil_robo on 2006-03-06
[quote=Jason_25]Here is my file.  Use at your own risk.  It allows no-login anonymous read/write access to the directory in the path.[/quote] 
Hey it worked!
Cool!

Thanks dude!

But folders with spaces in their names are not shared well... they always show my home directory when I try to access  them from my windows box :(

--Anil

---

### Post by ubuntujonez on 2006-03-12
It's been a while, but I thought I would follow up. 

I don't allow any anonymous, unauthenticated access and I incorrectly assumed that samba could authenticate against my /etc/passwd file. Once I ran the command:

```
$ sudo smbpasswd -a <username>
```
(where <username> is the ubuntu username and the windows username, and both passwords are the same in /etc/passwd file as the windows password)

... after that it was easy. A snap. Read-write access to my Ubunto server. (the family storage array)

:-)

---

### Post by funkenstein on 2006-03-17
[quote=Jason_25]Here is my file.  Use at your own risk.  It allows no-login anonymous read/write access to the directory in the path.[/quote]

\\:D/\\:D/\\:D/WooHoo!!! thanks for that, changed the path and the share name and the "force user" and off I went :-D

---

