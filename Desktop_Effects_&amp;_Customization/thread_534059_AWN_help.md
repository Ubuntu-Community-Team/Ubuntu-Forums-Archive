---
title: "AWN help"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by Parms on 2007-08-24
I tried the guides for installing AWN, but I get missing files or etc.. Is there a guide that works for 64bit? plus how can I re-install previous files for a clean install... This is what I had happen..

parms@linux:~$ wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) 
--16:10:11--  [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
           => `8434D43A.gpg'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,682 (1.6K) [text/plain]

100%[====================================>] 1,682         --.--K/s             

16:10:12 (61.70 MB/s) - `8434D43A.gpg' saved [1682/1682]

parms@linux:~$ sudo apt-key add 8434D43A.gpg
OK
parms@linux:~$ rm 8434D43A.gpg
parms@linux:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Translation-en_US      
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources     
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Sources
Fetched 14.4kB in 2s (6656B/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
parms@linux:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
parms@linux:~$ 




Then I get this for AWN....

parms@linux:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autotools-dev is already the newest version.
libxdamage-dev is already the newest version.
libxcomposite-dev is already the newest version.
libgnome2-common is already the newest version.
libgnome2-dev is already the newest version.
libgnome-desktop-dev is already the newest version.
libgnome-vfs-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libwnck-dev is already the newest version.
libgconf2-dev is already the newest version.
libglib2.0-dev is already the newest version.
libdbus-glib-1-dev is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
parms@linux:~$ bzr checkout [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator
bzr: ERROR: Target directory "avant-window-navigator" already exists.
parms@linux:~$ cd avant-window-navigator
parms@linux:~/avant-window-navigator$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
parms@linux:~/avant-window-navigator$ 

This is in my sources list...
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

I am successfully running compiz-fusion, any help would be greatly appreciated.

---

### Post by reacocard on 2007-08-24
> **Parms said:**
> I tried the guides for installing AWN, but I get missing files or etc.. Is there a guide that works for 64bit? plus how can I re-install previous files for a clean install... This is what I had happen..

parms@linux:~$ wget [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg) 
--16:10:11--  [http://download.tuxfamily.org/syzygy42/8434D43A.gpg](http://download.tuxfamily.org/syzygy42/8434D43A.gpg)
           => `8434D43A.gpg'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,682 (1.6K) [text/plain]

100%[====================================>] 1,682         --.--K/s             

16:10:12 (61.70 MB/s) - `8434D43A.gpg' saved [1682/1682]

parms@linux:~$ sudo apt-key add 8434D43A.gpg
OK
parms@linux:~$ rm 8434D43A.gpg
parms@linux:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Translation-en_US      
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US           
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources     
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Sources
Fetched 14.4kB in 2s (6656B/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
parms@linux:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
parms@linux:~$ 




Then I get this for AWN....

parms@linux:~$ sudo apt-get install build-essential autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autotools-dev is already the newest version.
libxdamage-dev is already the newest version.
libxcomposite-dev is already the newest version.
libgnome2-common is already the newest version.
libgnome2-dev is already the newest version.
libgnome-desktop-dev is already the newest version.
libgnome-vfs-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libwnck-dev is already the newest version.
libgconf2-dev is already the newest version.
libglib2.0-dev is already the newest version.
libdbus-glib-1-dev is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
parms@linux:~$ bzr checkout [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator
bzr: ERROR: Target directory "avant-window-navigator" already exists.
parms@linux:~$ cd avant-window-navigator
parms@linux:~/avant-window-navigator$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
parms@linux:~/avant-window-navigator$ 

This is in my sources list...
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

I am successfully running compiz-fusion, any help would be greatly appreciated.

for the first one, you forgot to put sudo in front of apt-get update (ie. should be 'sudo apt-get update') the second time, but the repo should still be active in spite of that error, try continuing with the guide from that point ( that actually looks like you have trevino's repo as well as mine? his appears to be the one causing the error, try commenting his out in your sources.list)). for the second, doing an 'rm -rf avant-window-navigator' before doing bzr checkout should fix it, but try method one first since the repo is easier to uninstall and keep up-to-date.

Also, its usually better to post in the thread for the guide, since if you post elsewhere the thread author may not see it and be able to help you (this thread was almost off the page before I caught it)

---

