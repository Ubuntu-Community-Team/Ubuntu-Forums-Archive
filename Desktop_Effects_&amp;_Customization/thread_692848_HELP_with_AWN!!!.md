---
title: "HELP with AWN!!!"
date: 2008-02-10
forum: Desktop Effects &amp; Customization
---

### Post by hananias on 2008-02-10
after i installed AWN. I have the AWN app. in the accessories column, also there's the AWN Preferences and Manager in the PREFERENCES column. When I click on any of them...nothing happens! I tried using command F and 2 run 'avant-window-navigator' I see the application w/h an icon...but nothing happens.I just can't open nothing!

Something similar happen when i tried cairo-dock. it installed (i think), but there's no icon, i can't find it how to open it from my menubar...(i see it's installed and the plugins in synaptic)...but that's it. I restarted the computer, I read many forums and try to install different ways....nothing.

by the way...I'm running Ubuntu Gutsy on PPC ibook g4 1.2ghz, 1.25ram, compiz-fusion and widgets layers...all the goodyes....well almost:(

Can anybody please help me???

---

### Post by rune0077 on 2008-02-10
Try running it from a terminal. Open a terminal and type 

```
avant-window-navigator
```

It should give you an idea of what the error is. Post the output here if you're in doubt.

---

### Post by nilarimogard on 2008-02-10
You have to enable visual effects: System > Preferences > Appearance. If you can't, than it's because of you video card driver, so search the forums on how to install drivers for your video card.

---

### Post by hananias on 2008-02-10
thanks for the quick reply guys!  
I tried it on the terminal i get this message...

avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

what does that mean??  I'm very new in Ubuntu...but very impressed  about the progress ubuntu has come to be.

so, why is it in my menubar and not in the computer?   i guess something went wrong in the installation...I don't know if the video card is installed or not...but I thought i was since i'm running compiz-fusion well, even with the widgets layer (had problems before).

---

### Post by rune0077 on 2008-02-10
If you're not having problems with Compiz, you should be able to run AWN fine. I think you missed something in the installation process. Did you install both AWN and the plugins, or just one of them? 

I think you may need to do a reinstall. Try doing a search for AWN here on the forums, there's a few good guides on how to do it.

---

### Post by Rupertronco on 2008-02-10
You don't have to worry about your video card drivers, if Compiz is working, so are they.

Like rune0077 said, if your Compiz is functioning correctly, you should have absolutely no probelm using AWN. The only thing AWN requires is a compositing manager, which is what Compiz is. 

Your best bet would to be as said before, and reinstall. Make sure to use the latest version of the software. As far as installing goes, it's always best to compile it yourself. Here is a link to the AWN wiki that has a great installation guide:

[http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page)

---

### Post by hananias on 2008-02-10
thanks guys for good comments, i appreciate all the help i can get.  i'll try to reinstall...i'll keep up to date how it goes.  thanks

---

### Post by hananias on 2008-02-10
well i tried i to reinstall AWN, but i bump into some problems...
When after i get the  key  i try to do an update, here's the info the  terminal gives me...

root@*****-laptop:~# sudo apt-get update
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy Release.gpg [191B]
Get:2 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy Release                                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release.gpg                            
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy-updates Release                         
Get:4 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]                      
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_US              
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy/main Sources                            
Get:6 [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy Release.gpg [191B]                         
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/main Translation-en_US                       
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/eyecandy Translation-en_US             
Get:7 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release.gpg [189B]                   
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Translation-en_US
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy/multiverse Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/restricted Translation-en_US                 
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/universe Translation-en_US                   
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/multiverse Translation-en_US                 
Get:8 [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates Release.gpg [191B]                 
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates/main Translation-en_US               
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates/restricted Translation-en_US         
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release                                   
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release                                
Get:9 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release [10.9kB]          
Get:10 [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security Release.gpg [191B]          
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/main Translation-en_US         
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/restricted Translation-en_US   
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/universe Translation-en_US     
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/multiverse Translation-en_US   
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy Release            
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/eyecandy Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/eyecandy Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/eyecandy Packages                      
  404 Not Found
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/main Packages                       
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/eyecandy Sources
  404 Not Found
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/universe Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/multiverse Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates/main Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/main Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/universe Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/multiverse Packages
Fetched 11.1kB in 3s (2940B/s)
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release)  Unable to find expected entry  screenlets/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/Release](http://download.tuxfamily.org/syzygy42/dists/gutsy/Release)  Unable to find expected entry  avant-window-navigator/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-powerpc/Packages.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-powerpc/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@******-laptop:~# sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr


Well, I regret to say, I don't know what the terminal just told me...but i know it ain't good.  what's the deal??  
I think something is wrong with my repositories, it fails to fetch, and then fails to download the package.

---

### Post by nilarimogard on 2008-02-10
gksu gedit /etc/apt/sources.list

and remove all the [http://download.tuxfamily.org*]("http://download.tuxfamily.org/syzygy42/dists/gutsy/Release") (but only those!)
They are wrong. Enter this in stead: 
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

---

### Post by rafagomezd on 2008-02-11
Ok, the trouble is not the binaries and not the packages, the real why is this:

HTTP FOR AWN REPOSITORY IS NOT WORKING
INstead [http://.](http://.).. you shoud put ftp://    on synaptics package repositorys, third party edit your tuxfamily line and you should only have TWO like this:


[ftp://download.tuxfamily.org/syzygy42](ftp://download.tuxfamily.org/syzygy42)

[ftp://download.tuxfamily.org/syzygy42](ftp://download.tuxfamily.org/syzygy42)

If you want to add it with terminal you should type:

sudo gedit /etc/apt/sources.list

Then at the end of the document you will find your tuxfamily repositoies, so just change the http for a ftp like this:

#AWN

deb [http://ppa.launchpad.net/bzr/ubuntu](http://ppa.launchpad.net/bzr/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/bzr/ubuntu](http://ppa.launchpad.net/bzr/ubuntu) gutsy main

deb [ftp://download.tuxfamily.org/syzygy42](ftp://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [ftp://download.tuxfamily.org/syzygy42](ftp://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
--------------------------------
"then you should type: sudo apt-get update"

That will reload the sources and you will be able to install AWN with all the libraries, and as you did the procedure like 10100000000 times you wont need the key, SO NOW THIS IS A GOOD INSTALLING ORDER:

UNinstall all from Synaptic Package, then install with the new repository AWN (not the one who says A Mac OS oriented launch bar) only AWN and it will ask for other libraries WICH NOW ARE BEING INSTALLED. say yes and that is all.

TADAAAAAAAAA!!!


So the REAL WHY wasnt that the repository is not working, was only that instad a http repository they made it as ftp repository.

---

### Post by hananias on 2008-02-11
ok, i updated the ftp...file, still get the same result.
as you can see i no longer have http files, but still get 'failed to fetch' error....
yet i still have the unanswerable question...'why?' 

Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy Release.gpg [191B]
Get:2 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy Release                                 
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy-updates Release                         
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Get:4 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]                      
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_US              
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy/main Sources                            
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy/universe Sources                        
Get:6 [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy Release.gpg [191B]                         
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/main Translation-en_US                       
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy/multiverse Sources                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) gutsy-updates/main Sources                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/restricted Translation-en_US                 
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/universe Translation-en_US                   
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/multiverse Translation-en_US                 
Get:7 [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates Release.gpg [191B]                 
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates/main Translation-en_US               
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates/restricted Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Get:8 [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security Release.gpg [191B]                
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/multiverse Translation-en_US        
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy Release                                      
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security Release                             
Hit [ftp://download.tuxfamily.org](ftp://download.tuxfamily.org) gutsy Release.gpg                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/main Packages                              
Get:9 [ftp://download.tuxfamily.org](ftp://download.tuxfamily.org) gutsy/avant-window-navigator Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources                                
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/restricted Packages                  
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/universe Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy/multiverse Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates/main Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/main Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/restricted Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/universe Packages
Hit [http://ports.ubuntu.com](http://ports.ubuntu.com) gutsy-security/multiverse Packages
Ign [ftp://download.tuxfamily.org](ftp://download.tuxfamily.org) gutsy/avant-window-navigator Translation-en_US
Get:10 [ftp://download.tuxfamily.org](ftp://download.tuxfamily.org) gutsy Release [10.9kB]
Fetched 10.9kB in 5s (2074B/s)  
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release)  Unable to find expected entry  screenlets/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Failed to fetch [ftp://download.tuxfamily.org/syzygy42/dists/gutsy/Release](ftp://download.tuxfamily.org/syzygy42/dists/gutsy/Release)  Unable to find expected entry  avant-window-navigator/binary-powerpc/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by hananias on 2008-02-12
ok, i tried all that you guys said...still same result...why?:(

---

### Post by andrewsomething on 2008-02-12
I don't think that repo has a powerpc binary. You're using a mac right? .

AWN from Hardy has been backported to Gutsy. If you enable the gutsy-backports repo in Software Sources you can get it that way for ppc. There are also debs on Getdeb.net or you could build from source following the instructions on the wiki.

[https://edge.launchpad.net/ubuntu/+source/avant-window-navigator](https://edge.launchpad.net/ubuntu/+source/avant-window-navigator)

---

### Post by hananias on 2008-02-14
First of all I want to say thanks for all your help and good advice...but despite all the advice i get.  It's still no go! 
I can't figure out how to use and run linux the way the real LEOPARD runs in my ibook g4. 
AWN is just another example of some of the problems I run with. Small and Big issues stop me from actually installing it in the internal drive. (i dual boot Gutsy from ext. firewire drive). 

I can't get wireless to work, for get it!  but it's ok (ethernet's ok)

Sometimes (very rare...but it happens) Compiz shuts off! (start over session)

when i start up, or log in and press widgets key (F9) the widgets don't stay where i left them...and some don't start up (I have to manually start them)

and of course the famous AWN, cairo-dock, kiba-dock...I can't install any of the fancy docks (no offense gdesklets, but they do have the eye candy) anyways I'm using gdesklets for the toolbar for now.

I have been impressed with the programs available, the graphics are pretty good, but leopard still blows it out of the water!  In the other hand leopard can be boring with no effects (cube, wobbling...etc.)
Linux has great online help/assistance and forums.  
The bottom line is, I guess you have to be a genius to use Linux, and have a decent computer.  I thought I did...guess not. ibookg4 PPC- 1.07Ghz, 1.25 ram, 10.5.1 os x.

I'm a little discourage trying to finish this Linux Mac-theme...if any one has a very easy tutorial 'how to', I'm willing to try it...

---

### Post by rune0077 on 2008-02-14
Hey, sorry you can't get it working. Maybe give cairo-dock a try, since the project has been picked up again and is now in a .deb package, so installation couldn't be easier. You can get it here: [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724). Just download both one called cairo-dock and the one called plug-ins (you don't need the sources), put them in the same director and unpack the cairo-dock .deb. Then you can run it from the terminal (or with alt+F2):

```
cairo-dock
```

I have used AWN for a long time, but I have to say, this new cairo-dock version is really awesome. I have officially ditched AWN.

---

### Post by skankster on 2008-02-14
"I can't get wireless to work, for get it! but it's ok (ethernet's ok)"

Have you tried wicd? I had many intermittent issues with wireless and switched wicd in for the network manager and since then (about a week) it's worked flawlessly.

---

### Post by PriceChild on 2008-02-14
Why don't you just use leopard if you have a mac, and want ubuntu to be like it?

---

### Post by rune0077 on 2008-02-14
> **PriceChild said:**
> Why don't you just use leopard if you have a mac, and want ubuntu to be like it?

Um, maybe he doesn't want to have to pay for new software? Or, maybe he likes to be able to modify his software? Looking like and being like are two different things.

---

### Post by hananias on 2008-02-16
Because of this forums and the good and fast help I get here, is a good reason to stick around with linux.  I like leopard, i'm happy with it.  It's easy, way better than windows!  (I can't believe I just said that)...the transaction (from xp to leopard) was easy.  Mac is just easy.  But yes, I love the flexibility and control Linux has and gives me to my computer.  I believe Linux can be much more with a little more work.  I hope the guys in ubuntu continue their great work they're doing!
Thank you guys for your advice, I'll give it a try.  Let you know how it goes.

---

### Post by hananias on 2008-02-16
> **rune0077 said:**
> Hey, sorry you can't get it working. Maybe give cairo-dock a try, since the project has been picked up again and is now in a .deb package, so installation couldn't be easier. You can get it here: [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724). Just download both one called cairo-dock and the one called plug-ins (you don't need the sources), put them in the same director and unpack the cairo-dock .deb. Then you can run it from the terminal (or with alt+F2):

```
cairo-dock
```

I have used AWN for a long time, but I have to say, this new cairo-dock version is really awesome. I have officially ditched AWN.

Thanks for the post...I've already tried this deb file, and even now still nothing happens.  I reinstall the plugins first, then the dock.deb...when I f-2 run cairo-dock...nothing happens.  when i run the code in the terminal I get this message...

-bash: /usr/bin/cairo-dock: cannot execute binary file

I really don't know what that means...:confused:
any suggestions??

---

### Post by hananias on 2008-02-16
Does anyone know why I can't install properly the cairo-dock.deb file??  When I run the deb, it acts normal and installs...but I can't find any icons in my menus...i can find it in my folders, but when i try to run it...nothing happens.  I use the run command, also nothing happens, i even tried to run in the terminal but I get message, "cannot execute binary file" 
Help please.

---

### Post by rune0077 on 2008-02-16
You don't have to type in the whole path in terminal or a launcher. Just "cairo-dock". If that doesn't work, there's something very odd going on. Try reinstalling it, but first uninstall it (if you used the deb package you can do this through Synaptic, just search for cairo dock and select "Remove completely for both the dock and the plugins).

---

### Post by hananias on 2008-02-17
I did a complete removal, and then fresh install again.  still get same message

"bash: /usr/bin/cairo-dock: cannot execute binary file"

I guess I have a very odd problem.  Why me??

---

### Post by hananias on 2008-02-17
The crazy thing about this is...I installed the same deb. files on a crapy Acer Aspire 3000wlmi (terrible graphic card no effects!) 1gram, but still i can install cairo, kiba, and awn but because of lack of graphic support it doesn't look good...there's a big black bar in  behind the dock.  Why can't my ibookg4 PPC run simple small docks, but it can handle compiz-fusion, widgets layer, transparency, etc. Doesn't make any sense...

---

### Post by SkiesOfAzel on 2008-02-20
> **hananias said:**
> The crazy thing about this is...I installed the same deb. files on a crapy Acer Aspire 3000wlmi (terrible graphic card no effects!) 1gram, but still i can install cairo, kiba, and awn but because of lack of graphic support it doesn't look good...there's a big black bar in  behind the dock.  Why can't my ibookg4 PPC run simple small docks, but it can handle compiz-fusion, widgets layer, transparency, etc. Doesn't make any sense...
 Actually this is not at all crazy, it's perfectly natural. The debs you are trying to use on your ibook are compiled for the i386 architecture so they don't work on a power pc . What you need to do in order to run awn or cairo dock is compile them yourself. Don't worry, it's not that hard.
First ,open a terminal. Then , create a folder to use for all the projects you compile , and enter it :
```
mkdir projects
cd projects
```
Now create a folder for the cairo-dock project and enter it :
```
mkdir cairo-dock
cd cairo-dock
```
Get the dependencies ...
```
sudo aptitude install subversion build-essential autoconf libtool intltool libcairo2-dev libgtk2.0-dev librsvg2-dev libglitz1-dev libglitz1-glx-dev libcairo2 librsvg2-2 libglitz1 
```
and the source code :
```
svn checkout http://svn.berlios.de/svnroot/repos/cairo-dock/trunk
```
Now go to the folder containing the source code
```
cd trunk/cairo-dock
```
create the configure script :
```
autoreconf -isvf
```
then configure
```
./configure
```
compile 
```
make
```
and install
```
sudo make install
```
That's it ! Cairo dock is now installed :)  (but don't close the terminal just yet ;) ).
You will probably want to install plugins for cairo dock.
```
cd ../plug-ins
```
You are now on the plugins folder. In order to see all the plugins 
```
ls -la
```
for every plugin that you want installed
```
cd <name of the plugin>
autoreconf -isvf
./configure
make
sudo make install
```
Don't forget to return to the root of the plugins (cd ..) every time you compile one so that you can go to the next.
Now run cairo-dock through a terminal or better through the run dialog (hit alt+f2) and enjoy the fruit of your labor :) .
If you want cairo dock to start with gnome, go to system -> preferences -> sessions on the panel main menu and click the Add button. Put dock in name and cairo-dock in command and click ok.

 If you want to try awn , follow the instructions found [here]("http://ubuntuforums.org/showpost.php?p=2307772&postcount=1") to compile it from source.

---

