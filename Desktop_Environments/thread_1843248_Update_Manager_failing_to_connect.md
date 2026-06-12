---
title: "Update Manager failing to connect"
date: 2011-09-13
forum: Desktop Environments
---

### Post by BradleyAtkins on 2011-09-13
Hi

I have just installed Natty on a new machine and can use apt-get update and install ok. However my update manager is coming up and telling me I need to install some updates. When I try to do so though I get these errors: -


Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.38-11-generic_2.6.38-11.48_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.38-11-generic_2.6.38-11.48_i386.deb) Could not connect to security.ubuntu.com:80 (91.189.92.166). - connect (111: Connection refused) [IP: 91.189.92.166 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/gir1.2-dbusmenu-glib-0.4_0.4.3-0ubuntu4_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/gir1.2-dbusmenu-glib-0.4_0.4.3-0ubuntu4_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dee/gir1.2-dee-0.5_0.5.18-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dee/gir1.2-dee-0.5_0.5.18-0ubuntu1_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/gir1.2-unity-3.0_3.8.4-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/libu/libunity/gir1.2-unity-3.0_3.8.4-0ubuntu1_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.6.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.6.2-0ubuntu1_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_1.6.2-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/libsyncdaemon-1.0-1_1.6.2-0ubuntu1_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.6.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.6.2-0ubuntu1_all.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.6.2-0ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.6.2-0ubuntu1_all.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.38.11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.38.11.26_i386.deb) Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.38.11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.38.11.26_i386.deb) Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11_2.6.38-11.48_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11_2.6.38-11.48_all.deb) Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11-generic_2.6.38-11.48_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-11-generic_2.6.38-11.48_i386.deb) Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.11.26_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.38.11.26_i386.deb) Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

Any ideas why I am getting these errors when I can update from the command line.

I am using a proxy BTW and have exported my http_proxy, https_proxy and ftp_proxy environment vars in my bashrc file. 

Do I need to define them anywhere else?

I'm a little puzzled that the update manager can see that there are updates to install but can't access them.

Thanks in advance 

Brad

Oops, sorry. Just checked it this morning and apt-get isn't working anymore... :(

Can anyone tell me how to set it up to use apt-get and update manager?

---

### Post by 2F4U on 2011-09-13
Maybe the mirror you use has problems. Did you try changing to a different mirror?

---

### Post by raja.genupula on 2011-09-13
update manager --> settings--> Ubuntu software -->  here change the server and try again 

if you got any error please post them exactly here . 
all the best .

---

### Post by BradleyAtkins on 2011-09-13
In Update Manager I changed settings from UK Server to Main server and got these errors when reloading: -

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/natty-security/InRelease)  
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to gb.archive.ubuntu.com:http:
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to gb.archive.ubuntu.com:http:
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to gb.archive.ubuntu.com:http:
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to archive.canonical.com:http:
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to extras.ubuntu.com:http:
W: Some index files failed to download. They have been ignored, or old ones used instead.

-------------------------------------------------------------

When clicking on "Get Best Server" button: -

No suitable Server was found
Please check your Internet connection.

-------------------------------------------------------------
I can run apt-get update though: -

brad@brad-OptiPlex-755:/etc/apt$ sudo bash
[sudo] password for brad: 
root@brad-OptiPlex-755:/etc/apt# apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease                       
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release     
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security Release.gpg [198 B]          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release                                 
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release [31.4 kB]             
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security Release [31.4 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources [105 kB]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources [14 B]
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources [25.2 kB]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources [1,890 B]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages [315 kB]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages [92.2 kB]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,258 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/main Sources [66.7 kB]      
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/restricted Sources [14 B]   
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/universe Sources [10.6 kB]  
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/multiverse Sources [650 B]  
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/main i386 Packages [175 kB] 
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/universe i386 Packages [37.3 kB]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/multiverse i386 Packages [2,071 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/main TranslationIndex          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/multiverse TranslationIndex    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/restricted TranslationIndex    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/universe TranslationIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/main Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-security/universe Translation-en
Fetched 899 kB in 1s (651 kB/s)
Reading package lists... Done

Do you think that when I open a console my bashrc is dotted in and so my exports are loaded, while Update Manager running from the desktop doesn't see my exported proxy settings?

---

### Post by BradleyAtkins on 2011-09-13
Cracked it.

I was using a PAC file for the proxy info.

I loaded the file in Firefox and pulled out the proxy server address and set the server in my network settings directly.

Now the Update manager can download....

Thanks for the help guys, much appreciated

---

