---
title: "Pithos isn't working"
date: 2011-10-06
forum: Gaming &amp; Leisure
---

### Post by Radical_Dreamer on 2011-10-06
Does anyone know why?  I just used the software center to download it and i got "pandora does not support your client version" 

Anyone know what this means and if I can fix it?

---

### Post by thatguruguy on 2011-10-06
[Bug report]("https://bugs.launchpad.net/pithos/+bug/856035").

---

### Post by Radical_Dreamer on 2011-10-06
Thank, but it says it is fixed but I don't really know where to go to get the fix

"Fixed in development release in 2011-09-22"

But he posted it yesterday, so now I don't even know where to find the solution because the ubuntu version hasn't updated on their site (I think what I want is the 0.3.10-1ubuntu1 but they only have the .9 version for ubuntu so I just don't even know what they mean when some people say the fix has been released).  

Also I tried this kevin mehall update thingie for pithos.  It did stuff in the terminal but it didn't really pan out.

Anyway, sorry for being a noob but I really don't get where or what I am supposed to do (should i just wait?).

---

### Post by thatguruguy on 2011-10-06
No worries, I'll take you through this step-by-step.

Assuming you're using 10.04 or later, open a terminal and type the following:

```
sudo add-apt-repository ppa:kevin-mehall/pithos-daily
```
It will prompt you for your password.

Once it is done, type the following:
```
sudo apt-get update && sudo apt-get upgrade
```

It will ask if you want to upgrade your packages.  Type "y" and hit enter.  That should get you the most recent version of pithos, which should fix your problem.

---

### Post by Radical_Dreamer on 2011-10-07
Thanks for the help but doing that, I get this stuff at the end

radicaldreamer@radicaldreamer-G71G:~$ sudo apt-get update && sudo apt-get upgrade
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:4 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,215 B]                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Fetched 2,832 B in 10s (281 B/s)                                               
W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

And pithos still doesn't work.  Is it something wrong with my computer then?

---

### Post by thatguruguy on 2011-10-07
I think I see your problem.

It appears you went to [https://launchpad.net/~kevin-mehall/+archive/pithos-daily]("https://launchpad.net/%7Ekevin-mehall/+archive/pithos-daily") and tried to follow the instructions on how to add a repository, but you skipped a step.

In the instructions on that page (and, indeed, every ppa hosted on launchpad) it states as follows:
> 
       **Step 2:** Open a terminal and enter:     
             sudo add-apt-repository ppa:user/ppa-name... which is exactly what you did.  That is to say, you opened a terminal and typed:
```
sudo add-apt-repository ppa:user/ppa-name
```Unfortunately, you took that one line out of context. If you go back and look, the full instructions are as follows:
> **Step 1:** On the PPA's overview page, look for the       heading that reads *Adding this PPA to your system*. Make a note       of the PPA's location, which looks like:                  ppa:gwibber-daily/ppa     
             **Step 2:** Open a terminal and enter:     
             sudo add-apt-repository ppa:user/ppa-name     
             Replace ppa:user/ppa-name with the PPA's location that you       noted above.
So, what you *should* have done was note the ppa's location (in this case, ppa:kevin-mehall/pithos-daily), and typed the following:
```
sudo add-apt-repository ppa:kevin-mehall/pithos-daily
```
So, now you have a reference in your sources list to a ppa that doesn't exist, and that may be interfering with retrieval of packages.  Here's how to fix it.

Open your Ubuntu Software Center.  Click on "Edit" in the top menu, and choose "Software Sources..."  When your Software Sources window comes up, click on the "Other Software" tab.

Look for the following two entries in the list of software sources:
> [http://ppa.launchpad.net/user/ppa-name/ubuntu](http://ppa.launchpad.net/user/ppa-name/ubuntu) natty main
[http://ppa.launchpad.net/user/ppa-name/ubuntu](http://ppa.launchpad.net/user/ppa-name/ubuntu) natty main (Source Code)

Remove both of them, and then click the "Close" button. Then, close your Ubuntu Software Center.

Make sure both Ubuntu Software Center and Synaptic are closed. Then, repeat the steps I gave you in my earlier post.

---

### Post by Radical_Dreamer on 2011-10-08
Yeah I remember making that mistake and not thinking much of it at the time.  Anyway, point being, you're advice worked which is awesome.

PS.  What would have happened if I had the software center open when I was using the terminal

---

### Post by thatguruguy on 2011-10-08
YOUR COMPUTER WOULD HAVE EXPLODED!

Actually, if you had the Software Center or synaptic open, you wouldn't have been able to get a lock on your package archive, and apt-get wouldn't work. Only one package manager can be active at a time.

---

