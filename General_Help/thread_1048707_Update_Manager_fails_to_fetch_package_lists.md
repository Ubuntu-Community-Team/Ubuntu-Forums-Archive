---
title: "Update Manager fails to fetch package lists"
date: 2009-01-23
forum: General Help
---

### Post by venator260 on 2009-01-23
when I try to run apt-get update, I get many error messages that look like this, one for each repo, I would imagine

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to 201.120.135.202:8080 (201.120.135.202). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not connect to 201.120.135.202:8080 (201.120.135.202). - connect (111 Connection refused)


It acts as If I'm not online, but here I am. 

Anyone know what is going on? I have tried multiple servers (in Software Sources). it will ping servers, but will not download the package lists.

Entering that URL into a browser gives a 404 not found error

---

### Post by drs305 on 2009-01-23
the server is probably down. Try another one by opening Software Sources or synaptic (System, Admininstration). Once open, Settings, Repositories, Download From, Other. Select best server.

---

### Post by venator260 on 2009-01-24
I tried that...I have my desktop set up to use the same one, and it worked just fine.

---

### Post by dcstar on 2009-01-24
> **venator260 said:**
> I tried that...I have my desktop set up to use the same one, and it worked just fine.

Then there is something in the network setup/connection that is different.

---

### Post by venator260 on 2009-01-24
Well... I've been on three different networks, no luck. 

I just tried telling Apt to "select best server" on my parents network, and it told me no suitable server was found, as if there is no internet connection, but I am using that connection currently, so it's not like I'm not connected. 


Is there some setting with Apt that could be a problem? I don't recall changing anything dealing with that in the last 7 days (the last time Update Manager worked). I did change my xorg.conf to use a projector with my laptop, but that doesn't seem related.

---

### Post by dcstar on 2009-01-24
> **venator260 said:**
> Well... I've been on three different networks, no luck. 

I just tried telling Apt to "select best server" on my parents network, and it told me no suitable server was found, as if there is no internet connection, but I am using that connection currently, so it's not like I'm not connected. 
........

I will ask again - what is different in the laptop's network setup, have you used Proxy settings/Wireless etc?

---

### Post by venator260 on 2009-01-24
I'm glad you mentioned proxy settings. I did fiddle with them and changed them back, but you have to click "apply system wide" My guess would be that the Update manager runs as root, and I had changed the settings back only for my username. 

Stupid mistake on my part. Thanks for your willingness to help, dcstar

---

### Post by p vs np on 2009-03-05
Hi.
I seem to be having the same problem as what *Venator260* was facing.

I am connecting to the internet through a Wi-Fi connection, which requires a particular proxy,port,ipV4 setting to be set.

The message i get when i try to apply **sudo apt-get update** is as follows:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                                
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US                     
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US               
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_US                 
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US               
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg                        
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US             
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US       
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_US         
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US       
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources                  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                               
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                         
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                                
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                          
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                           
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources                            
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                         
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                     
  Could not connect to 172.16.9.1:8181 (172.16.9.1), connection timed out
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                          
  Unable to connect to 172.16.9.1 8181:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)
Reading package lists... Done              
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://ppa.launchpad.net/c-korn/ubuntu/dists/hardy/Release.gpg](http://ppa.launchpad.net/c-korn/ubuntu/dists/hardy/Release.gpg)  Could not connect to 172.16.9.1:8181 (172.16.9.1), connection timed out

W: Failed to fetch [http://ppa.launchpad.net/c-korn/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/c-korn/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to 172.16.9.1 8181:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  Could not connect to 172.16.9.1:8181 (172.16.9.1). - connect (113 No route to host)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


The message when I try and change the server under Software Sources is as follows:

[B]No suitable download server was found
Please check your internet connection.[/B]

What's going on?

---

### Post by p vs np on 2009-03-05
PS: I am now connected to the Main Server and the changes made in the IP while logging in is reflected system-wide.

---

