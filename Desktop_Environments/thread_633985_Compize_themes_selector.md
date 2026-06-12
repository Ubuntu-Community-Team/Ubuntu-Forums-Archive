---
title: "Compize themes selector?"
date: 2007-12-07
forum: Desktop Environments
---

### Post by Jungle-Cat on 2007-12-07
Hey all,
When I first properly used Ubuntu, I was using 7.04 (fiesty fawn, yes?). I installed Beryl on that using a series of apt-get commands which I read on the how-to-install page at the beryl-project page. After I had done that, I could go and setup themes that came with it, using "Emerald Theme Manager" I tnink it was (this is Compiz, yes? yeah I have a bad memory...).

Now that I'm using Ubuntu again, I'm at 7.10 Gutsy Gibbon. Reading up on it, it comes with the new Compiz Fusion, which incorporates Beryl and Compiz features.

My question is quite simple, where is the equivalent theme manager to select Emerald themes? Or do I have to set the window manager to Emerald/Compize first?

Also, I'm not sure, but I'm guessing I actually have no idea what I'm talking about.

Thanks

//edit
It's all coming back now.
I used apt and installed emerald-theme-manager. Since gutsy comes preisntalled with compiz fusion, and emerald is compiz, I'm not sure why emerald doesnt change themes. So, I'm assuming I need to set Emerald/compiz as the window manager. How do I do this?

////edit
Now I'm quite sure I have no idea what I'm doing. Can someone tell me what I should install to complement compiz-fusion?

---

### Post by approaching on 2007-12-07
no, you are right, make sure that compiz is running by either typing compiz --replace, or verifying you have wobbly windows (coolest verification in the world btw). make sure you have installed emerald (preferably via synaptic). then go to the ccsm and enable windowing. you can  now go into emerald (thats the command, but it should be in your System>Preferences>emerald as well) and change your theme!

---

### Post by Jungle-Cat on 2007-12-08
cheers;
looking at gnome-look, there are "emerald" and also "metacity" themes. metacity ones are far more popular, so does emerald theme manager also load metacity themes?

---

### Post by Tenken on 2007-12-08
Nope, emerald only manages .emerald themes. Metacity is the default window manager for gnome and you can choose to use it as your window manager instead of emerald, but I found it doesn't handle transparency very well.

---

### Post by Jungle-Cat on 2007-12-08
So where can I get a metacity theme manager and select metacity as my window manager?

---

### Post by Tenken on 2007-12-08
Metacity themes are managed in Gnome by going to System->Preferences->Appearance->Theme, clicking the Customize button and choosing an option from the Window Border tab. metacity --replace should replace the emerald manager.

---

### Post by Jungle-Cat on 2007-12-08
Hm... now I don't think metacity is what I'm looking for. Ubuntu comes preinstalled with compiz-fusion, as such it uses compiz themes.

So how do I add compiz themes to Ubuntu? Argh I'm so confused...

note; the file I downloaded from gnome-look.org, from the compiz section has the file extension of .cgwdtheme, if that helps let you know wth I'm doing!

---

### Post by John Azelvandre on 2007-12-08
> **approaching said:**
> no, you are right, make sure that compiz is running by either typing compiz --replace, or verifying you have wobbly windows (coolest verification in the world btw). make sure you have installed emerald (preferably via synaptic). then go to the ccsm and enable windowing. you can  now go into emerald (thats the command, but it should be in your System>Preferences>emerald as well) and change your theme!

Hi everyone.  I just upgraded to Gutsy today, and I'm playing around with this Compiz Fusion stuff.  I have everything set - Compiz Fusion installed, Emerald installed.  But there are no themes to choose from in Emerald!  In what I've quoted above, it says to "go to the ccsm and enable windowing ..."  

What's that?  What is ccsm?  How can I get some themes to play around with?

Probably a dumb question, but ... :confused:

---

### Post by Jungle-Cat on 2007-12-08
CCSM is the Compiz-Fusion config tool. God only knows why the creators of Ubuntu didn't include it, it can be obatined from the repos. The package name is compizconfig-settings-manager. So, in the terminal run;
sudo apt-get install compizconfig-settings-manager
Then, you can run ccsm from System>Preferences or just run ccsm

//edt
Whoops, forgot to mention. You can get Emerald themes from gnome-look.org. They have lots of great stuff :)

---

### Post by John Azelvandre on 2007-12-08
Great, thanks!  By the way, I notice that Compiz fusion and my old workspace selector aren't playing nice together.  Compiz fusion keeps minimizing the apps and I can't tell where they are -- which workspace they're on.  Is there a way to get these to behave with each other?  I like having the little graphic that shows me where things are ...

---

### Post by Tenken on 2007-12-08
I think you can rename the theme to .emerald and it will work. To install Compiz (.emerald) themes go to System->Preferences->Emerald Theme Manager and click the install button, navigate to where you downloaded the theme and select it.

---

### Post by Jungle-Cat on 2007-12-09
So emerald themes are compiz themes! That's what I wanted to know!

So I'm trying to isntall the theme manager again... looking up "emerald" in Synaptic doesn't show the theme manager! Does anyone know why?

---

### Post by Tenken on 2007-12-09
I believe it is in the universe repository, so make sure that is enabled.

---

### Post by Jungle-Cat on 2007-12-09
```
boza@deaglan:~$ sudo apt-get update
[sudo] password for boza:
Get:1 http://wine.budgetdedicated.com gutsy Release.gpg [191B]
Get:2 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://packages.medibuntu.org gutsy/free Translation-en_AU                 
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_AU               
Ign http://security.ubuntu.com gutsy-security/main Translation-en_AU           
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_AU             
Hit http://wine.budgetdedicated.com gutsy Release                              
Hit http://packages.medibuntu.org gutsy Release                                
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_AU     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_AU       
Ign http://wine.budgetdedicated.com gutsy/main Packages                        
Ign http://packages.medibuntu.org gutsy/free Packages                          
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_AU     
Hit http://wine.budgetdedicated.com gutsy/main Sources                         
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://security.ubuntu.com gutsy-security Release                
Hit http://packages.medibuntu.org gutsy/free Packages                          
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Hit http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://wine.budgetdedicated.com gutsy/main Packages                        
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources              
Hit http://security.ubuntu.com gutsy-security/multiverse Packages           
Hit http://security.ubuntu.com gutsy-security/multiverse Sources            
Get:4 http://au.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://au.archive.ubuntu.com gutsy/main Translation-en_AU                  
Ign http://au.archive.ubuntu.com gutsy/restricted Translation-en_AU            
Ign http://au.archive.ubuntu.com gutsy/universe Translation-en_AU              
Ign http://au.archive.ubuntu.com gutsy/multiverse Translation-en_AU            
Get:5 http://au.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://au.archive.ubuntu.com gutsy-updates/main Translation-en_AU          
Ign http://au.archive.ubuntu.com gutsy-updates/restricted Translation-en_AU    
Ign http://au.archive.ubuntu.com gutsy-updates/universe Translation-en_AU      
Ign http://au.archive.ubuntu.com gutsy-updates/multiverse Translation-en_AU    
Hit http://au.archive.ubuntu.com gutsy Release                                 
Hit http://au.archive.ubuntu.com gutsy-updates Release                         
Hit http://au.archive.ubuntu.com gutsy/main Packages                           
Hit http://au.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://au.archive.ubuntu.com gutsy/main Sources                            
Hit http://au.archive.ubuntu.com gutsy/restricted Sources                      
Hit http://au.archive.ubuntu.com gutsy/universe Packages                       
Hit http://au.archive.ubuntu.com gutsy/universe Sources                        
Hit http://au.archive.ubuntu.com gutsy/multiverse Packages                     
Hit http://au.archive.ubuntu.com gutsy/multiverse Sources                      
Hit http://au.archive.ubuntu.com gutsy-updates/main Packages                   
Hit http://au.archive.ubuntu.com gutsy-updates/restricted Packages             
Hit http://au.archive.ubuntu.com gutsy-updates/main Sources                    
Hit http://au.archive.ubuntu.com gutsy-updates/restricted Sources              
Hit http://au.archive.ubuntu.com gutsy-updates/universe Packages               
Hit http://au.archive.ubuntu.com gutsy-updates/universe Sources                
Hit http://au.archive.ubuntu.com gutsy-updates/multiverse Packages             
Hit http://au.archive.ubuntu.com gutsy-updates/multiverse Sources              
Fetched 5B in 12s (0B/s)                                                       
Reading package lists... Done
boza@deaglan:~$ sudo apt-get install emerald-theme-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emerald-theme-manager
boza@deaglan:~$ 
```

---

### Post by Jungle-Cat on 2007-12-11
(package not there)

bump

---

### Post by Tenken on 2007-12-12
In Synaptic try searching for just emerald, clicking install on that should auto-select the emerald theme manager package. If nothing is showing up for emerald try double checking your repos.

---

### Post by Tweenk on 2007-12-12
I don't know about the selector problem, it works OK for me.
One thing that is direly missing from Gutsy is the Fusion Icon. Search for it in this forum, there is a link for a .deb package made by one of the users. It allows you to change the window decorator (Metacity vs Emerald) on the fly, and has some other nice options. Once you have it, see whether tweaking the "Loose binding" and "Indirect rendering" options has any effect.

---

### Post by Jungle-Cat on 2007-12-12
Tweenk, could you re-word that? I'm not sure what your telling me I should install.

Can anyone put up a deb package for emerald theme manager? It appears it will be the only way I can get it. To check my repos, I looked it up on packages.ubuntu.org or whatever the domain is, and could only find what I already had in synaptic.

---

### Post by penquin on 2007-12-12
try the following
[http://www.opensourcemirrors.org/ubuntu/pool/universe/e/emerald/libemeraldengine0_0.3~git20070717-0ubuntu1_i386.deb](http://www.opensourcemirrors.org/ubuntu/pool/universe/e/emerald/libemeraldengine0_0.3~git20070717-0ubuntu1_i386.deb)
[http://www.opensourcemirrors.org/ubuntu/pool/universe/e/emerald/emerald_0.3~git20070717-0ubuntu1_i386.deb](http://www.opensourcemirrors.org/ubuntu/pool/universe/e/emerald/emerald_0.3~git20070717-0ubuntu1_i386.deb)

my question is how do I get the themes to stick

I run emerald --replace in terminal and theme is present, but if I close the terminal the theme goes away.

---

### Post by Tenken on 2007-12-12
```
emerald --replace &
``` 
should do the trick. For me installing emerald, picking a theme and restarting X made emerald the perminant window manager.

---

### Post by Jungle-Cat on 2007-12-18
I already have those packages!

I need the actual theme manager

---

### Post by Tenken on 2007-12-18
Looking at my installed packages and the packages list for Gutsy, it looks like there is no emerald theme manager package. If you have emerald installed go to System->Preferences and you should see Emerald Theme Manager, if not try editing your menu to see if it installed but not displayed for some reason.

---

### Post by Jungle-Cat on 2007-12-20
Tenken, I hate you soo much in a good way. The menu icon just wasn't enabled in the "Main Menu" settings. Grrrrr....

---

