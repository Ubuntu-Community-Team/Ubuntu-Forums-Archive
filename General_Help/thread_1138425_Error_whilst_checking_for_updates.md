---
title: "Error whilst checking for updates"
date: 2009-04-26
forum: General Help
---

### Post by calvinps on 2009-04-26
Hello all.

I was checking for updates, then I got this error box with the following message:

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures could not be verified because the public key is not available: NO_PUBKEY CE90D8983E731F79
```There's two things I need to know:


[LIST=1]
[*]The seriousness of the error in terms of security
[*]How I would be able to fix it
[/LIST]
Thanks in advance if you have any solutions :D

---

### Post by calvinps on 2009-04-26
bump

---

### Post by calvinps on 2009-04-26
bump again :|

---

### Post by almikul on 2009-04-26
[list=1][*]Find the GPG key at this address: [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCE90D8983E731F79](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCE90D8983E731F79)
[*]Next, copy the text that starts with "-----BEGIN PGP PUBLIC KEY BLOCK-----" and ends with "-----END PGP PUBLIC KEY BLOCK-----" and save it as a text file. 
[*]Then, go to System->Administration->Software Sources and open tab Authentication. 
[*]Click on Import Key File and select the file you've just saved. 
[*]Then do 'sudo apt-get update' in terminal (or use GUI) and it should not give you any warnings. [/list]

Hope it helps.

---

### Post by PatrikG on 2009-04-26
Had the exact same problems and followed the steps above, and no problems anymore.

Thanks!

---

### Post by calvinps on 2009-05-11
Bump! Another (similar) error just appeared :/

```
GPG error: http://download.virtualbox.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAEGPG error: http://download.virtualbox.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAEFailed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by calvinps on 2009-05-11
Hello?! I have another problem here! :|

---

### Post by calvinps on 2009-05-12
bump

---

### Post by ushills on 2009-05-12
go to the virtual box site and download their gpg key they guide you on the site.

---

### Post by abhiroopb on 2009-05-12
you can use the following command:

```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CE90D8983E731F79

```

You can use this command whenever you add a new repository. This basically authenticaes the repository.

Let me know if it works.

---

### Post by gnyanganga on 2009-07-21
yupp! it works.

---

### Post by bacil on 2009-07-21
whole precedure for futer reference is:

1. ```
 gpg --keyserver keyserver.ubuntu.com --recv 2B7E03A7 
```

you always use last 8 charcter of key

2. ```
 gpg --export --armor 2B7E03A7 | sudo apt-key add - 
```

this actualy import key where it belongs

---

### Post by Toke on 2009-07-23
> toke@Toke-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv CC60BA1F
gpg: requesting key CC60BA1F from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
toke@Toke-laptop:~$ 

I get this when trying to install unknown-horizons.


Are there more than one keyserver?
I am set "for server for denmark"

---

### Post by riverdrums on 2009-08-05
I also have a problem receiving keys from a keyserver. I am behind a firewall at work. Is there a pure http interface to get the public key file?

---

### Post by shiroyoshida on 2009-08-05
Hello, 

I have the same problem as the other users in this thread... I've tried everything previous, more experienced posters have advised and nothing worked. So far I've changed three or four different servers and the error messages are the same when an update is attempted: 

```
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.90.142), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_GB.bz2  Unable to connect to archive.canonical.com http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty-i386/Release.gpg  Unable to connect to archive.canonical.com http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/i18n/Translation-en_GB.bz2  Unable to connect to archive.canonical.com http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/multiverse/binary-amd64/Packages  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


Output from Synaptic Package Manager: 
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/restricted/binary-amd64/Packages  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/universe/binary-amd64/Packages  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/restricted/binary-amd64/Packages  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/universe/binary-amd64/Packages  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/multiverse/binary-amd64/Packages  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/main/binary-amd64/Packages  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/restricted/binary-amd64/Packages  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/universe/binary-amd64/Packages  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/multiverse/binary-amd64/Packages  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/multiverse/binary-amd64/Packages  404 Not Found
Failed to fetch http://archive.canonical.com/ubuntu/dists/jaunty-i386/partner/binary-amd64/Packages  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Output from the terminal: 
shiro@ubuntu:~$ sudo apt-get update
[sudo] password for shiro: 
apt-get: update
Get: 1 http://security.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB
Get: 2 http://gb.archive.ubuntu.com jaunty Release.gpg [189B]                  
Get: 3 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]     
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB    
Get: 4 http://security.ubuntu.com jaunty-security Release [49.6kB]             
Get: 5 http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB [4640B]
Get: 6 http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB [35.2kB] 
Get: 7 http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB [47.5kB]
Get: 8 http://security.ubuntu.com jaunty-security/main Packages [62.3kB]       
Get: 9 http://gb.archive.ubuntu.com jaunty-updates Release.gpg [189B]          
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB   
Get: 10 http://gb.archive.ubuntu.com jaunty Release [74.6kB]                   
Get: 11 http://gb.archive.ubuntu.com jaunty-updates Release [49.6kB]           
Get: 12 http://gb.archive.ubuntu.com jaunty/main Packages [1253kB]             
Get: 13 http://security.ubuntu.com jaunty-security/restricted Packages [2391B] 
Get: 14 http://security.ubuntu.com jaunty-security/main Sources [18.1kB]       
Get: 15 http://security.ubuntu.com jaunty-security/restricted Sources [522B]   
Get: 16 http://security.ubuntu.com jaunty-security/universe Packages [24.6kB]  
Get: 17 http://security.ubuntu.com jaunty-security/universe Sources [5836B]    
Get: 18 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]   
Get: 19 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]    
Get: 20 http://gb.archive.ubuntu.com jaunty/restricted Packages [8848B]        
Get: 21 http://gb.archive.ubuntu.com jaunty/main Sources [555kB]               
Get: 22 http://gb.archive.ubuntu.com jaunty/restricted Sources [3156B]         
Get: 23 http://gb.archive.ubuntu.com jaunty/universe Packages [4757kB]         
Get: 24 http://gb.archive.ubuntu.com jaunty/universe Sources [2375kB]          
Get: 25 http://gb.archive.ubuntu.com jaunty/multiverse Packages [197kB]        
Get: 26 http://gb.archive.ubuntu.com jaunty/multiverse Sources [107kB]         
Get: 27 http://gb.archive.ubuntu.com jaunty-updates/main Packages [129kB]      
Get: 28 http://gb.archive.ubuntu.com jaunty-updates/restricted Packages [2391B]
Get: 29 http://gb.archive.ubuntu.com jaunty-updates/main Sources [39.5kB]      
Get: 30 http://gb.archive.ubuntu.com jaunty-updates/restricted Sources [522B]  
Get: 31 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [43.5kB] 
Get: 32 http://gb.archive.ubuntu.com jaunty-updates/universe Sources [12.1kB]  
Get: 33 http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages [3933B]
Get: 34 http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources [1349B] 
Get: 35 http://archive.canonical.com jaunty Release.gpg [189B]                 
Ign http://archive.canonical.com jaunty/partner Translation-en_GB
Get: 36 http://archive.canonical.com jaunty Release [10.5kB]
Get: 37 http://archive.canonical.com jaunty/partner Packages [3320B]
Get: 38 http://archive.canonical.com jaunty/partner Sources [1555B]
Fetched 9931kB in 1min 45s (94.5kB/s)
Reading package lists... Done
Get: 1 http://gb.archive.ubuntu.com jaunty Release.gpg [189B]
Get: 2 http://gb.archive.ubuntu.com jaunty/main Translation-en_GB [52.6kB]     
Get: 3 http://security.ubuntu.com jaunty-security Release.gpg [189B]           
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB    
Get: 4 http://security.ubuntu.com jaunty-security Release [49.6kB]             
Get: 5 http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB [4640B]
Get: 6 http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB [35.2kB] 
Get: 7 http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB [47.5kB]
Get: 8 http://gb.archive.ubuntu.com jaunty-updates Release.gpg [189B]          
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB   
Get: 9 http://gb.archive.ubuntu.com jaunty Release [74.6kB]                    
Get: 10 http://security.ubuntu.com jaunty-security/main Packages [62.3kB]      
Get: 11 http://gb.archive.ubuntu.com jaunty-updates Release [49.6kB]           
Get: 12 http://gb.archive.ubuntu.com jaunty/main Packages [1251kB]             
Get: 13 http://security.ubuntu.com jaunty-security/restricted Packages [2366B] 
Get: 14 http://security.ubuntu.com jaunty-security/main Sources [18.1kB]       
Get: 15 http://security.ubuntu.com jaunty-security/restricted Sources [522B]   
Get: 16 http://security.ubuntu.com jaunty-security/universe Packages [24.2kB]  
Get: 17 http://security.ubuntu.com jaunty-security/universe Sources [5836B]    
Get: 18 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]   
Get: 19 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]    
Get: 20 http://gb.archive.ubuntu.com jaunty/restricted Packages [8858B]        
Get: 21 http://gb.archive.ubuntu.com jaunty/main Sources [555kB]               
Get: 22 http://gb.archive.ubuntu.com jaunty/restricted Sources [3156B]         
Get: 23 http://gb.archive.ubuntu.com jaunty/universe Packages [4732kB]         
Get: 24 http://gb.archive.ubuntu.com jaunty/universe Sources [2375kB]          
Get: 25 http://gb.archive.ubuntu.com jaunty/multiverse Packages [189kB]        
Get: 26 http://gb.archive.ubuntu.com jaunty/multiverse Sources [107kB]         
Get: 27 http://gb.archive.ubuntu.com jaunty-updates/main Packages [129kB]      
Get: 28 http://gb.archive.ubuntu.com jaunty-updates/restricted Packages [2366B]
Get: 29 http://gb.archive.ubuntu.com jaunty-updates/main Sources [39.5kB]      
Get: 30 http://gb.archive.ubuntu.com jaunty-updates/restricted Sources [522B]  
Get: 31 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [43.1kB] 
Get: 32 http://gb.archive.ubuntu.com jaunty-updates/universe Sources [12.1kB]  
Get: 33 http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages [4118B]
Get: 34 http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources [1349B] 
Get: 35 http://archive.canonical.com jaunty Release.gpg [189B]                 
Ign http://archive.canonical.com jaunty/partner Translation-en_GB
Get: 36 http://archive.canonical.com jaunty Release [10.5kB]
Get: 37 http://archive.canonical.com jaunty/partner Packages [1744B]
Get: 38 http://archive.canonical.com jaunty/partner Sources [1555B]
Fetched 9894kB in 1min 54s (86.5kB/s)
Reading package lists... Done
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/archive.canonical.com_ubuntu_dists_jaunty_main_binary-i386_Packages: No such file
/usr/bin/apt-get: 101: cannot open /var/lib/apt/foreign/lists/archive.canonical.com_ubuntu_dists_jaunty_main_binary-i386_Packages: No such file
Ignoring archive.canonical.com_ubuntu_dists_jaunty_partner_source_Sources
arch_all.list: adding linux-headers-2.6.28-14 all
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_main_source_Sources
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_multiverse_source_Sources
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_source_Sources
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_universe_source_Sources
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_i18n_Translation-en%5fGB
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty_main_source_Sources
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_i18n_Translation-en%5fGB
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_source_Sources
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_i18n_Translation-en%5fGB
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_source_Sources
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_i18n_Translation-en%5fGB
Ignoring gb.archive.ubuntu.com_ubuntu_dists_jaunty_universe_source_Sources
Ignoring security.ubuntu.com_ubuntu_dists_jaunty-security_main_source_Sources
mangle: ia32-libs-tools/mangle.cc:402: void mangle(Archlist&, Renamelist&): Assertion `buf_used > 1' failed.
Aborted

```

For a minute I assumed that this might be my ISP (Virgin Media) who's blocking the updates but even I tried to update the available software packages by using the mirror server they are providing, I got another serving of the above messages. 

Since it's been eight days from my first Ubuntu installation (via Wubi) I have yet to do any research on firewalls for Linux and therefore have none installed. 

I'm running Ubuntu 9.04, 64bit. 

Thank you! :-)

---

### Post by shiroyoshida on 2009-08-17
Well, I seem to have solved the problem on my end so I thought I'd share my solution here in case someone else has the same problem and may benefit from this. 

I read a while ago in this forum that if you have 64-bit Ubuntu installation and you want to install 32-bit apps, you can install the "ia32-libs" package. This worked like a charm for me and has been very helpful so far. 

However, this package has also added a few (to say the least) entries in the Third Part Software repositories list. To disable these entries, you can either manually edit the "sources.list" file which is located in the /etc/apt folder (please make sure you know what you're doing that you have backed up the file first!) or you can simply run the Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) and disable them from there. 

Once you have the Synaptic Manager window open in front of you, navigate to the "Third Party Software" tab and unckeck all entries that contain "i386" in them. These were the ones that were causing the errors in my case and if you try to access these URLs with your browser, you will get an error as the destinations do not exist. 

There you go, something you can try and hopefully it will solve your problem! If anyone has another solution or objects to my method, please post your alternative solution here for others to see. 

Thank you! :)

---

### Post by schum3,1415 on 2011-02-01
Hi,

I experienced the same problem while trying to upgrade.

But thx to abhiroopb it works all fine now!

---

